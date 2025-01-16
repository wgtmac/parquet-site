---
title: "Implementation status"
linkTitle: "Implementation status"
weight: 8
---

This page summarizes the features supported by different Parquet
implementations.

*Note*: This is a work in progress and we would welcome help expanding its scope.

### Legend
The value in each box means:
* ✅: supported
* ❌: not supported
* (blank) no data

Implementations:
* `C++`: [parquet-cpp](https://github.com/apache/arrow/tree/main/cpp/src/parquet)
* `Java`: [parquet-java](https://github.com/apache/parquet-java)
* `Go`: [parquet-go](https://github.com/apache/arrow-go/tree/main/parquet)
* `Rust`: [parquet-rs](https://github.com/apache/arrow-rs/blob/main/parquet/README.md)



### Physical types

| Data type                                 | C++   | Java   | Go    | Rust  |
| ----------------------------------------- | ----- | ------ | ----- | ----- |
| BOOLEAN                                   |       |        |       |       |
| INT32                                     |       |        |       |       |
| INT64                                     |       |        |       |       |
| INT96 (1)                                 |       |        |       |       |
| FLOAT                                     |       |        |       |       |
| DOUBLE                                    |       |        |       |       |
| BYTE_ARRAY                                |       |        |       |       |
| FIXED_LEN_BYTE_ARRAY                      |       |        |       |       |

* \(1) This type is deprecated, but as of 2024 it's common in currently produced parquet files


### Logical types

| Data type                                 | C++   | Java   | Go    | Rust  |
| ----------------------------------------- | ----- | ------ | ----- | ----- |
| STRING                                    |       |        |       |       |
| ENUM                                      |       |        |       |       |
| UUID                                      |       |        |       |       |
| 8, 16, 32, 64 bit signed and unsigned INT |       |        |       |       |
| DECIMAL (INT32)                           |       |        |       |       |
| DECIMAL (INT64)                           |       |        |       |       |
| DECIMAL (BYTE_ARRAY)                      |       |        |       |       |
| DECIMAL (FIXED_LEN_BYTE_ARRAY)            |       |        |       |       |
| DATE                                      |       |        |       |       |
| TIME (INT32)                              |       |        |       |       |
| TIME (INT64)                              |       |        |       |       |
| TIMESTAMP (INT64)                         |       |        |       |       |
| INTERVAL                                  |       |        |       |       |
| JSON                                      |       |        |       |       |
| BSON                                      |       |        |       |       |
| LIST                                      |       |        |       |       |
| MAP                                       |       |        |       |       |
| UNKNOWN (always null)                     |       |        |       |       |
| FLOAT16                                   |       |        |       |       |

### Encodings

| Encoding                                  | C++   | Java   | Go    | Rust  |
| ----------------------------------------- | ----- | ------ | ----- | ----- |
| PLAIN                                     |       |        |       |       |
| PLAIN_DICTIONARY                          |       |        |       |       |
| RLE_DICTIONARY                            |       |        |       |       |
| RLE                                       |       |        |       |       |
| BIT_PACKED (deprecated)                   |       |        |       |       |
| DELTA_BINARY_PACKED                       |       |        |       |       |
| DELTA_LENGTH_BYTE_ARRAY                   |       |        |       |       |
| DELTA_BYTE_ARRAY                          |       |        |       |       |
| BYTE_STREAM_SPLIT                         |       |        |       |       |

### Compressions

| Compression                               | C++   | Java   | Go    | Rust  |
| ----------------------------------------- | ----- | ------ | ----- | ----- |
| UNCOMPRESSED                              |       |        |       |       |
| BROTLI                                    |       |        |       |       |
| GZIP                                      |       |        |       |       |
| LZ4 (deprecated)                          |       |        |       |       |
| LZ4_RAW                                   |       |        |       |       |
| LZO                                       |       |        |       |       |
| SNAPPY                                    |       |        |       |       |
| ZSTD                                      |       |        |       |       |

### Other format level features

|                                           | C++   | Java   | Go    | Rust  |
| ----------------------------------------- | ----- | ------ | ----- | ----- |
| xxxHash-based bloom filters               |       |        |       |       |
| Bloom filter length (1)                   |       |        |       |       |
| Statistics min_value, max_value           |       |        |       |       |
| Page index                                |       |        |       |       |
| Page CRC32 checksum                       |       |        |       |       |
| Modular encryption                        |       |        |       |       |
| Size statistics (2)                       |       |        |       |       |


* \(1) In parquet.thrift: ColumnMetaData->bloom_filter_length

* \(2) In parquet.thrift: ColumnMetaData->size_statistics

### High level data APIs for Parquet feature usage

| Format                                       | C++   | Java   | Go    | Rust  |
| -------------------------------------------- | ----- | ------ | ----- | ----- |
| External column data (1)                     |       |        |       |       |
| Row group "Sorting column" metadata (2)      |       |        |       |       |
| Row group pruning using statistics           |       |        |       |       |
| Reading select columns only                  |       |        |       |       |
| Page pruning using statistics                |       |        |       |       |
| Page pruning using bloom filter              |       |        |       |       |


* \(1) In parquet.thrift: ColumnChunk->file_path

* \(2) In parquet.thrift: RowGroup->sorting_columns
