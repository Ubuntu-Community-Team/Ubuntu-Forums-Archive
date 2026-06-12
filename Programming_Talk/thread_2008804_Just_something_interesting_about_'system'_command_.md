---
title: "Just something interesting about 'system' command and daemons"
date: 2012-06-23
forum: Programming Talk
---

### Post by shumifan50 on 2012-06-23
I thought I would share this as it caused me to scratch my head for a while.

What I wanted to do:
1. Use wget to get some XML from a rss feed.
2. Use tinyxml to parse it.
3. implement this in a daemon.

Roughly this is how it worked:
1. use system("wget -O filename <url>");
2. tinyxml loadfile(filename);
This load failed every time with 'empty document' error.
When I looked inside the document it contained the console output from the wget, which caused tinyxml to fail loading the document. By adding the -q option to wget, the problem went away.

As a generalisation: If you can make the program you run with 'system' not produce console output while you are using it in a daemon, this is the best way out. If not, then the output of the program run with system will end up in the one of the files it opens (if your daemon has correctly closed stdin, stdout and stderr ofcourse). If your target program cannot be kept quiet then you might have to open dummy files to let it map its stdin, stdout and stderr to. I tried using redirect wget ... > /dev/null, but it did not work.

I hope this helps somebody.

---

