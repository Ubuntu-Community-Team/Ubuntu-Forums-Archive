---
title: "[SOLVED] Split string with quotations in python"
date: 2008-04-19
forum: Programming Talk
---

### Post by Jacks0n on 2008-04-19
Hi,

I'm writing a small web-server in python, and am up to writing a class to handle the configuration page. What I want to do is convert the command (string) into a list, but items with quotes around them should be appended as one item. eg..

```

IndexPage "/var/www/folder with spaces/index.html"
ServerName 'Name of Web Server'
CGIDirectory "/cgi bin directory"

to...

['IndexPage', '/var/www/folder with spaces/index.html']
['ServerName', 'Name of Web Server']
[CGIDirectory, '/cgi bin directory']

```

So my question is, are there any common/clean solutions to this? Also detecting EOL errors would be handy, where strings haven't been closed. From what I can see, I can use split('#') and look for elements starting and ending with a quotation mark, but it seems like a lot of work for a simple problem.

- Thanks, Jackson

---

### Post by ghostdog74 on 2008-04-19
if the format of your config file is always like the one you posted
```

for lines in open("file"):
    lines = lines.strip().split(" ",1)
    lines[1] = lines[1].replace('"',"").replace("'","")
    print lines

```
output:
```

# ./test.py
['IndexPage', '/var/www/folder with spaces/index.html']
['ServerName', 'Name of Web Server']
['CGIDirectory', '/cgi bin directory']



```

---

### Post by gumpish on 2010-08-11
Just a note for anyone else looking for a better answer to this...

Python as of 2.3 has a shlex module with the function split(...) which will keep quoted tokens together in the resulting array (using "shell like syntax").

>>> import shlex
>>> shlex.split('this feature "is pretty" useful')
['this', 'feature', 'is pretty', 'useful']

---

