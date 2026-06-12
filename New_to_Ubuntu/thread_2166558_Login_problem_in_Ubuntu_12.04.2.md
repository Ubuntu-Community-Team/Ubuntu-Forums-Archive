---
title: "Login problem in Ubuntu 12.04.2"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by sivaramakrishnan2 on 2013-08-10
Hi everyone i'm a newbie.... i'm using ubuntu 12.04.2 64 bit alongside with windows 7 os... Everything went so cool until i installed jre by using terminal... after installation i was prompted to go for a reboot... i did so... aft that i got this problem... Once i enter my password, the screen goes off and then returns to the same login screeen... i googled for some help and i found a way of logging in into my system by simply pressing CTRL+ALT+F1 ..... having done so i was able to successfully login... but i got this msg

~bash: /etc/profile: line 34: syntax error: unexpected end of file

while installing jre i followed the steps as told in the below link

[http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux/](http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux/)


i dont know what went wrong... please someone help me!!!

---

### Post by carl4926 on 2013-08-10
> [COLOR=#000000] i'm a newbie....[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]Welcome


> Everything went so cool until i installed jre by using terminal..[/COLOR]Doesn't sound like a newbie thing to be doing...

Were you following a guide of some kind?

---

### Post by sivaramakrishnan2 on 2013-08-10
i just went through the steps shown in the below link

[URL="http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux"]http://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux



[/URL]

---

### Post by 3rdalbum on 2013-08-10
With those instructions, steps 9 and 10 tell you to make some modifications to the /etc/profile file.

And when you log into a text terminal, you get an error about that file.

Your next move should be to look at the /etc/profile file and check that you added those lines correctly:

```
sudo nano /etc/profile
```

If you don't see anything wrong in there, exit Nano (by pressing Control-X and then hitting the N key) and run this command:

```
tail -n 10 /etc/profile
```

and type it in EXACTLY into this forum message so we can see what the last few lines of the file look like.

---

### Post by sivaramakrishnan2 on 2013-08-10
Thank u soooo much 3rdalbum :):):)
Everything works fine now... i've removed the code which i added during installation.... Now i've no problem during login...
once again thank u :)

---

