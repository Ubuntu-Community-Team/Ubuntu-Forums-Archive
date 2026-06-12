---
title: "Ubuntu: using PHP exec to call Lucene Search Engine"
date: 2008-03-20
forum: Programming Talk
---

### Post by milu07 on 2008-03-20
Hello,

My machine is Ubuntu 7.10. I am working with Apache Lucene. I have done with indexer and tried with command line Searcher (the default command line included in Lucene package: [http://lucene.apache.org/java/2_3_1/demo2.html](http://lucene.apache.org/java/2_3_1/demo2.html)). When I use this at command line: 

java Searcher -query algorithm

it works and returns a list of results to me. Here 'algorithm' is the keyword to search.

However, I want to have a web search interface written in PHP, I use PHP exec() to call this Searcher from my PHP script:

exec("java Searcher -query algorithm ", $arr, $retVal);
[I also tried: exec("java Searcher -query 'algorithm' ", $arr, $retVal)]

It does not work. I print the value of $retVal, it is 1.

I come back and try: exec("java helloWorld ", $arr, $retVal); 

It works and prints out the "hello World" message and $retVal is 0. Here the helloWorld.java has only System.println("hello World"); Notice that the PHP script, helloWorld.java and Searcher.java are in the same directory, which is accessible from the Web.

In the command line Searcher.java of Lucene, it imports many libraries, is this the problem?

[I]import org.apache.lucene.analysis.Analyzer;
import org.apache.lucene.analysis.standard.StandardAnalyzer;
[/I]....

Could you please help?

Thank you,

---

### Post by mssever on 2008-03-21
I've never so much as heard of Lucene, but I have a couple of troubleshooting suggestions:

First, have you checked for any messages printed, particularly messages to stderr? It's very likely that you'll find a clue that way. I don't remember if PHP has a built-in way to get stderr. If not, you can add 2>&1 to your command to redirect stderr to stdout.

Second, if the above turns up nothing, make sure that either your working directory is correct or you're using absolute paths. EDIT: On re-reading your post, I noticed that you already addressed this.

---

### Post by milu07 on 2008-03-21
Thank you very much for your help.

I add 2>&1 to my command to redirect stderr. And this is what I get:

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/lucene/analysis/Analyzer

The Searcher.java actually has imported Lucene libraries:

import org.apache.lucene.analysis.Analyzer;
import org.apache.lucene.analysis.standard.StandardAnalyz er;
....

And when I run in command line it works. I guess this is the problem of path. However, I do not know how to fix it because it works in command line ($CLASSPATH points to the .jar file of Lucene library). May be PHP does not know $CLASSPATH. So, I add Lucene lib to $PATH:

export PATH=$PATH:/usr/lib/lucene-core-2.3.1.jar:/usr/lib

However, I get the same error message.
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/lucene/analysis/Analyzer

Could you please help?

Thank you

---

### Post by mssever on 2008-03-21
I'm no Java programmer, so I don't know about the CLASSPATH, but you should echo out the PATH and/or CLASSPATH as your script sees it. It's very likely not what you expect it to be.

You can explicitly set environment variables from PHP. If that doesn't work, do something like [php]exec('export SOMEVAR=foo; java whatever');[/php]

---

### Post by milu07 on 2008-04-17
Thank you very much for your help.

---

### Post by wwwjscom on 2008-08-01
Any luck getting htis working?  I need to do the exact same thing - get Lucene working through PHP.

Thanks.

---

