---
title: "Scripting 101"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2012-02-11
[SIZE=2]Hi,
[/SIZE]
How can I put a file on my desktop and when I click it, it sends a command to a terminal, like: 

echo hello

also, is there a way to insert a pause after that?  like the terminal would wait for a specific period of time or wait for the user to press a key on the keyboard?
Like:

echo hello
pause
echo thank you


And while I am on the subject, is there a good beginners manual to scripting?

---

### Post by raja.genupula on 2012-02-11
> How can I put a file on my desktop and when I click it, it sends a command to a terminal, like: 

echo hello

also, is there a way to insert a pause after that? like the terminal would wait for a specific period of time or wait for the user to press a key on the keyboard?
Like:

echo hello
pause
echo thank you

```
echo " hi " 
sleep 5
echo " that sleep 5 will give you 5 sec delay " 
```
> And while I am on the subject, is there a good beginners manual to scripting?

[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)


Hope that helps .

---

### Post by sudodus on 2012-02-11
You can also read the manual for the script language ***bash*** which is used in the terminal ```
man bash
```

You can find several tutorials browsing the internet for ***bash tutorial***

By the way, the shortcut in 'vanilla' Ubuntu to get the terminal window is ***ctrl + alt +t***

---

### Post by jayshomebrew on 2012-02-11
if you're really used to batch scripting then this tut may be more for you:
(converting dos batch to shell scripts)
[http://tldp.org/LDP/abs/html/dosbatch.html]("http://tldp.org/LDP/abs/html/dosbatch.html")

---

### Post by josephmills on 2012-02-11
IMHO the best bash scripting tuorial/guide is located 
[ HERE](http://mywiki.wooledge.org/BashGuide)

But there are a ton of ways to "skin a cat"

---

