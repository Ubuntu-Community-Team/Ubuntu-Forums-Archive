---
title: "Problems compiling in a post-commit svn script!"
date: 2008-07-07
forum: Programming Talk
---

### Post by Khao on 2008-07-07
Hey there! I am working on a project with a few friends so I set up a little SVN server on my server computer.

I have a post-commit script that does the following : 
Make a backup of the files on the server (a simple copy)
Checkout the files in a specified folder on the server
Run a shell script called Compile that contains the needed line to compile my program

This post-commit script works when I execute directly in the command-line, but when activated from the svn post-commit, everything works (copy and checkout), the first few lines in my Compile script runs fine (create a directory and put the includes in it) but the line that contains the g++ script doesn't work.

Anybody have an idea as of why everything works BUT the line to compile my program?

Here's my post-commit script :

```
#!/bin/bash
cd /
rm -r /ServerBCK
cp -r /Server /ServerBCK
rm -r /Server
svn checkout svn://[XXXXXXXXXXXXXXXXX]/Server --username XXXXXX --password XXXXXXX
cd /Server
./Compile

```

This will checkout in /Server so all my files are there after the post-commit script

And here's my Compile script

```
#!/bin/bash
cd /Server
mkdir include
cp Server.hpp include/Server.hpp
cp Encrypt.hpp include/Encrypt.hpp
cp MysqlManager.hpp include/MysqlManager.hpp
g++ -I../include -I/usr/include/mysql -I/usr/include/mysql++ -lmysqlpp Server.cpp -o Server
```

---

### Post by matja on 2008-07-07
> **Khao said:**
> 
```

#!/bin/bash
[COLOR="Red"]cd /Server[/COLOR]
mkdir include
cp Server.hpp include/Server.hpp
cp Encrypt.hpp include/Encrypt.hpp
cp MysqlManager.hpp include/MysqlManager.hpp
g++ [COLOR="Red"]-I../include[/COLOR] -I/usr/include/mysql -I/usr/include/mysql++ -lmysqlpp Server.cpp -o Server

```


Wouldn't this mean that you add "/include" to the search path for headers, not "/Server/include" that you created? I don't see how this would be affected by whether you run the script directly or if svn calls it, however, so if you don't get any warnings about g++ being unable to find your headers, please ignore this post!

Regards, Mattias

---

### Post by Khao on 2008-07-07
I changed the path to -I/Server/include and also changed ./Compile to ./Server/Compile (and removed cd /Server before)
It does the same, but at least I have an error message! 
> Attention : 'post-commit' hook failed with error output:
collect2: cannot find 'ld'
Any idea what this can be?

---

### Post by matja on 2008-07-08
Well, ld is the linker run at the end of the compile process to glue it all together. My first thought was that when svn calls the script, it lacks some directories in the PATH environment variable that it needs. On my system, however, g++ and ld are in the same directory, so it's unlikely that this is the problem unless you happen to keep them in separate directories (or g++ is located in multiple directories with and without ld). Maybe you could add
```
echo $PATH > svn-path
```
to your script and check to see that ld is located in one of the directories listed in the created svn-path file just to be sure.

Before you do, I should tell you that I have no experience of the server side of svn what so ever, so maybe this is something obvious to someone who does ;)

---

