# 范例：读取并打印binlog

QDecoder从oracle解析归档日志文件和在线日志文件，生成binlog，并写入kafka，或文件，或socket。
这里提供两个工具，分别从kafka和binlog server读取binlog:

* JBinlogDumpK: 从kafka读取binlog，反序列化成Java object，打印到控制台。
* JBinlogDumpS: 从socket(binlog server)读取binlog，反序列化成Java object，打印到控制台。

## 1. 编译

要求jdk版本： 不低于java 8

```
javac -cp .:lib/commons-cli-1.5.0.jar:lib/protobuf-3.6.1.jar:lib/kafka-clients-3.0.0.jar:lib/log4j-1.2.17.jar:lib/slf4j-api-1.7.30.jar:lib/slf4j-log4j12-1.7.30.jar:lib/qdecoder-binlog.jar src/*.java
```

## 2. 运行JBinlogDumpK: 从kafka读取binlog并打印出来

```
java  -cp .:lib/commons-cli-1.5.0.jar:lib/protobuf-3.6.1.jar:lib/kafka-clients-3.0.0.jar:lib/log4j-1.2.17.jar:lib/slf4j-api-1.7.30.jar:lib/slf4j-log4j12-1.7.30.jar:lib/qdecoder-binlog.jar:src JBinlogDumpK -b 127.0.0.1:9092 -s qdecoder,schema2
```

## 3. 运行JBinlogDumpS: 从socket读取binlog并打印出来

```
java  -cp .:lib/commons-cli-1.5.0.jar:lib/protobuf-3.6.1.jar:lib/kafka-clients-3.0.0.jar:lib/log4j-1.2.17.jar:lib/slf4j-api-1.7.30.jar:lib/slf4j-log4j12-1.7.30.jar:lib/qdecoder-binlog.jar:src JBinlogDumpS -a 127.0.0.1:9191
```

