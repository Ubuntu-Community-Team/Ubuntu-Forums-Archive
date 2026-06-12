---
title: "Hadoop on Ubuntu Talks"
date: 2009-02-02
forum: Programming Talk
---

### Post by noninoni on 2009-02-02
Hi All,
I am new to Hadoop and I jus installed on Ubuntu 8.0.4 LTS as per guidance of a web site. I tested it and found working fine. I tried to copy a file but it is giving some error pls help me out

hadoop@excel-desktop:/usr/local/hadoop/hadoop-0.17.2.1$ bin/hadoop jar hadoop-0.17.2.1-examples.jar  wordcount /home/hadoop/Download\ URLs.txt  download-output
09/02/02 11:18:59 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 1 time(s).
09/02/02 11:19:00 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 2 time(s).
09/02/02 11:19:01 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 3 time(s).
09/02/02 11:19:02 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 4 time(s).
09/02/02 11:19:04 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 5 time(s).
09/02/02 11:19:05 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 6 time(s).
09/02/02 11:19:06 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 7 time(s).
09/02/02 11:19:07 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 8 time(s).
09/02/02 11:19:08 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 9 time(s).
09/02/02 11:19:09 INFO ipc.Client: Retrying connect to server: localhost/127.0.0.1:9000. Already tried 10 time(s).
java.lang.RuntimeException: java.net.ConnectException: Connection refused
        at org.apache.hadoop.mapred.JobConf.getWorkingDirectory(JobConf.java:356)
        at org.apache.hadoop.mapred.FileInputFormat.setInputPaths(FileInputFormat.java:331)
        at org.apache.hadoop.mapred.FileInputFormat.setInputPaths(FileInputFormat.java:304)
        at org.apache.hadoop.examples.WordCount.run(WordCount.java:146)
        at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:65)
        at org.apache.hadoop.examples.WordCount.main(WordCount.java:155)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.apache.hadoop.util.ProgramDriver$ProgramDescription.invoke(ProgramDriver.java:68)
        at org.apache.hadoop.util.ProgramDriver.driver(ProgramDriver.java:139)
        at org.apache.hadoop.examples.ExampleDriver.main(ExampleDriver.java:53)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.apache.hadoop.util.RunJar.main(RunJar.java:155)
        at org.apache.hadoop.mapred.JobShell.run(JobShell.java:194)
        at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:65)
        at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:79)
        at org.apache.hadoop.mapred.JobShell.main(JobShell.java:220)
Caused by: java.net.ConnectException: Connection refused
        at sun.nio.ch.SocketChannelImpl.checkConnect(Native Method)
        at sun.nio.ch.SocketChannelImpl.finishConnect(SocketChannelImpl.java:592)
        at sun.nio.ch.SocketAdaptor.connect(SocketAdaptor.java:118)
        at org.apache.hadoop.ipc.Client$Connection.setupIOstreams(Client.java:174)
        at org.apache.hadoop.ipc.Client.getConnection(Client.java:623)
        at org.apache.hadoop.ipc.Client.call(Client.java:546)
        at org.apache.hadoop.ipc.RPC$Invoker.invoke(RPC.java:212)
        at org.apache.hadoop.dfs.$Proxy0.getProtocolVersion(Unknown Source)
        at org.apache.hadoop.ipc.RPC.getProxy(RPC.java:313)
        at org.apache.hadoop.dfs.DFSClient.createRPCNamenode(DFSClient.java:102)
        at org.apache.hadoop.dfs.DFSClient.<init>(DFSClient.java:178)
        at org.apache.hadoop.dfs.DistributedFileSystem.initialize(DistributedFileSystem.java:68)
        at org.apache.hadoop.fs.FileSystem.createFileSystem(FileSystem.java:1280)
        at org.apache.hadoop.fs.FileSystem.access$300(FileSystem.java:56)
        at org.apache.hadoop.fs.FileSystem$Cache.get(FileSystem.java:1291)
        at org.apache.hadoop.fs.FileSystem.get(FileSystem.java:203)
        at org.apache.hadoop.fs.FileSystem.get(FileSystem.java:108)
        at org.apache.hadoop.mapred.JobConf.getWorkingDirectory(JobConf.java:352)
        ... 21 more
:mad:

---

### Post by myrtle1908 on 2009-02-02
I know nothing about Hadoop but this error:-

```
java.net.ConnectException: Connection refused
```

indicates that for whatever reason (firewall, invalid IP/hostname/port etc) the client was unable to connect to the host.  Can you try something other than the loopback address 127.0.0.1, perhaps your hostname?

---

### Post by noninoni on 2009-02-02
Thanks for the reply. But i need specific to Hadoop on Ubuntu. Because the default net connection / URL is to be configured in some of the conf file. If any one has done this pls help me out. Thanks

---

### Post by GatorGoodNews on 2009-12-01
Perhaps you are getting this exception because you do not have password-less SSH set up, which is needed for Hadoop node communication.

If that does not solve the problem, then you may want to make sure that the namenode is in fact running at port 9000, and not on port 8020 or any other port

---

### Post by pshirishreddy on 2010-04-01
check out your /etc/hosts file 

make sure your localhost is properly defined if not add an entry 

```
127.0.0.1 localhost
```

at the top of the file

---

