1.处理大文件的聚合操作：
（1）CHUNK_SIZE设置每次读取的Chunk大小，根据实际内存大小设置，不宜过小
（2）从文件里读取数据进行聚合：aggregate_from_file_chunk
（3）从DataFrame进行聚合：aggregate_from_df_chunk
```python
# examples
opts = ['count','unique']
test_out = aggregate_from_file_chunk(test_file,test_out,'file_id','api',opts)
# test_file is the path of origin data, this operation is to groupby['file_id']
# aggregate operation on column ['api'] then merge the result on test_out
test_out = aggregate_from_file_chunk(test_file,test_out,['file_id','api'],'index',api_opts)
# test_file is the path of origin data, this operation is to groupby['file_id','api']
# aggregate operation on column ['index'] then merge the result on test_out
test_out = aggregate_from_df_chunk(test,test_out,'file_id','api',opts)
# test_file is origin data in DataFrame, this operation is to groupby['file_id']
# aggregate operation on column ['api'] then merge the result on test_out
test_out = aggregate_from_file_chunk(test,test_out,['file_id','api'],'index',api_opts)
# test_file is origin data in DataFrame, this operation is to groupby['file_id','api']
# aggregate operation on column ['index'] then merge the result on test_out

```
