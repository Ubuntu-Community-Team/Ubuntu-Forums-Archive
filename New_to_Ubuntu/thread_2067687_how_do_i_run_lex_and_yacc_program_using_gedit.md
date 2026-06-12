---
title: "how do i run lex and yacc program using gedit"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by prashant9986 on 2012-10-07
what are the steps which i need to follow when i am compiling and running my program of lex and yacc in the gedit.
its very urgent please suggest me. 

awaiting for your replies.
prashant;););););)

---

### Post by Bashing-om on 2012-10-07
prashant9986; Hi ! Welcome to the forum.

As you ask in "Absolute Beginner" I respond in simplest fashion.
1. Does lexx/yaxx require a header ? 
 #!/usr/bin/env <interpreter>2. Give your script executable permissions.
 ```
chmod +x <myprogram>
```
3.Some people like to keep their scripts in a personal directory.
 Others like to keep their scripts somewhere in the PATH variable.
 Most like to do both at once.  Here's what I suggest you do: ```

mkdir -p "$HOME/bin" echo 'PATH="$HOME/bin:$PATH"' >> "$HOME/.bashrc" exec bash
```
The first command will make a directory called bin in your home directory.  It is traditional for directories that contain commands to be named bin, even when those commands are scripts and not compiled ("*binary*") programs.  The second command will add a line to your .bashrc file which adds the directory we just made to the beginning of the PATH variable.  Every new instance of [BASH]("http://mywiki.wooledge.org/BASH") will now check for executable scripts in your bin directory.  Finally, the third line replaces our current instance of [BASH]("http://mywiki.wooledge.org/BASH") with a new one, which reads the .bashrc file. 
-Compliments to Greg Wooledge-


I hope this answers your request, else:
addition: submit information application specific.

[INDENT]warm regards <==BDQ

[/INDENT]

---

