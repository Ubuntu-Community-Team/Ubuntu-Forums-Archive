---
title: "Help with writing bash script to start Hbase"
date: 2015-04-02
forum: New to Ubuntu
---

### Post by vahagn-yeghikyan on 2015-04-02
Hi,

I am experimenting with apache nutch. Every time I restart mt computer I should do the same starting commands, hence, I decided to write a bash script. 
Commands are the following:

```

export JAVA_HOME=~/Java
export SOLR_HOME=~/<SOLR_FOLDER>
export HBASE_HOME=~/<HBASE_FOLDER>
export HUE_HOME=~/<HUE_FOLDER>

```

1. Start hbase

```


sh -x HBASE_HOME/bin/start_hbase.sh
```

2. start hbase services

```
sh -x $HBASE_HOME/bin/hbase-daemon.sh start thrift
```
```
sh -x $HBASE_HOME/bin/hbase-daemon.sh start thrift2
```
```
sh -x $HBASE_HOME/bin/hbase-daemon.sh start rest
```

3. Start Solr

```
cd $SOLR_HOME
$JAVA_HOME/bin/java -jar start.jar
```

This command should necessarily be executed from the $SOLR_HOME folder. Otherwise I get errors.

4. Start Hue
```
sh -x $HUE_HOME/build/env/bin/hue runserver
```


Now the problems.
1. If I execute the command 1 directly from the command prompt, hbase starts normally, while if I run the script it keeps on asking for my password to start the zookeeper. Even if I provide it,  the hbase does not start. What is the problem?
2. Seems to work
3. This command in contrast to the previous ones does not release the shell and keeps on logging. Is there a way to run it silently and to make it release the shell?
4. The same as for 3.


Thanks in advance.

---

### Post by Mark_Hagan on 2015-04-06
For 3 and 4 I think you could use the '&' ampersand character to run in the background. You would probably also want to redirect any output from the command to a file e.g. like a log file. Also, you should consider whether or not you want the process to run as a daemon process i.e. it will continue to run even when you log out of your terminal session (for as long as the machine is running obviously!). To do the latter you need to use the 'nohup' command

For example,

```

sh -x $HUE_HOME/build/env/bin/hue runserver >> mylogfile.txt 2>&1 &

```

Or
```

nohup sh -x $HUE_HOME/build/env/bin/hue runserver >> mylogfile.txt 2>&1 

```

if you want to log out and leave them running.

---

