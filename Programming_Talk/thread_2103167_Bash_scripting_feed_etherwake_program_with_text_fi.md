---
title: "Bash scripting: feed etherwake program with text file"
date: 2013-01-09
forum: Programming Talk
---

### Post by LtPitt on 2013-01-09
Hi all!

I know this is a very stupid question for a programmer but I am not able to find a solution.

I have a program: etherwake.

It is used to wake on lan a PC using its mac address.

I simply want to "feed" etherwake with a mac address contained in a text file.

I've tried

cat filename | etherwake

etherwake < `cat filename`

without any kind of luck...

I always get:

Specify the Ethernet address as 00:11:22:33:44:55

Of course if I do a cimple cat filename I get a perfect mac address, without blank spaces or any kind of strange characters.

What am I doing wrong?

---

### Post by Vaphell on 2013-01-09
try something like this
```
etherwake $( < filename )
```

---

### Post by sisco311 on 2013-01-09
You have to pass the mac address to etherwake as an option. So you can use command substitution:
```
etehrwake $(cat file)
```
Or if you use BASH:
```
etehrwake $(< file)
```

See:
```
man bash | less +/"^ +Command Substitution"
```
and
[http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution)

Pipes are used to connect the output of a command to the input of another one.
[http://mywiki.wooledge.org/BashGuide/InputAndOutput#Pipes](http://mywiki.wooledge.org/BashGuide/InputAndOutput#Pipes)

If your command reads its input from stdin you can use < to redirect the content of a file to it:
```
command < file
```
example:
```
read -r content < file
echo $content
``` 
See:
[http://mywiki.wooledge.org/Redirection](http://mywiki.wooledge.org/Redirection)

---

### Post by LtPitt on 2013-01-09
God bless your help!

I loved the solution and loved even more the explanation.

You gave me a fish and taught me how to fish too...

Thanks!

---

