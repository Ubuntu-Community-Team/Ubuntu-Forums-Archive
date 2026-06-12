---
title: "shell script that hangs putty"
date: 2010-09-23
forum: Programming Talk
---

### Post by Mr_G on 2010-09-23
Hey,

I have a shell script as follows

#!/bin/bash


echo "Enter server number "

read server

echo " Enter path"

read domainpath

if   [ "$server" != "" ] && [ "$domainpath" != "" ]
then
case $server in


1) ssh  user@server1 "sudo grep $domainpath /usr/local/apache/logs/error_log |less";;
2) ssh  user@server2 "sudo grep $domainpath /usr/local/apache/logs/error_log |less";;
3) ssh  user@server3 "sudo grep $domainpath /usr/local/apache/logs/error_log |less";;
4) ssh  user@server4 "sudo grep $domainpath /usr/local/apache/logs/error_log |less";;
5) ssh  user@server5 "sudo grep $domainpath /usr/local/apache/logs/error_log |less" ;;

    *) echo "$server invalid option" ;;
esac
else
echo " Error: Path or Server Number cannot be blank "
exit
fi

The problem is that once the script executes it displays a huge amount of logs even for a particular domain.
Once I kill the script by pressing control c or q putty seems to hang.
Any idea y or How can I improve the script.?

---

### Post by Bachstelze on 2010-09-23
Try moving less out of ssh:

```
ssh user@server1 "sudo grep $domainpath /usr/local/apache/logs/error_log" |less
```

---

### Post by Mr_G on 2010-09-23
> **Bachstelze said:**
> Try moving less out of ssh:

```
ssh user@server1 "sudo grep $domainpath /usr/local/apache/logs/error_log" |less
```

But then how wud you scroll up and down?

---

### Post by TuxLyn on 2010-09-24
You should consider using **dialog**.

---

### Post by Bachstelze on 2010-09-24
> **Mr_G said:**
> But then how wud you scroll up and down?

You still have less, but running on the local machine, where you have a terminal to run it on. ;) When you run [font=monospace]ssh command[/font], no terminal is allocated on the remote machine, so less can't work.

---

### Post by geirha on 2010-09-25
That'll also break if domainpath happens to contain any characters that are special to the shell or grep. Use printf to quote/escape special characters, and use grep's -F option to avoid it being treated as a regex.

```
ssh user@host "grep -F $(printf %q "$domainpath") logfile" | less
```

[http://mywiki.wooledge.org/BashFAQ/096](http://mywiki.wooledge.org/BashFAQ/096)

---

### Post by Mr_G on 2010-10-06
sorry for the delay guys
But I tried the above script with less as well as more
more is better .
The problem is that I need to call the scirpt via another script
Indiviually the script works but when I call the script via another the putty console
hangs after a control c
Any clue as to why?

---

### Post by CharlesA on 2010-10-06
Is it prompting for a password?

Try running it from a terminal on a linux box and see if the same thing happens.

---

