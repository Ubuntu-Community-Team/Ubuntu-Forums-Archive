---
title: "Unity doesn't start after cleaning with Ubuntu Tweak"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by emrextreme on 2012-04-29
Unity doesn't start after cleaning with Ubuntu Tweak. I tried to start in failsafex but it says no screen found. I don't know what to do. Thanks in advance.

---

### Post by joetait on 2012-04-29
Can you log in at all? If not, try ctrl+alt+F1. This will take you to a non-GUI screen (like the terminal). You can then log in (you will have to manually type in your username), and then if you run 
```

sudo apt-get upgrade && sudo apt-get update

```Then if you press ctrl-alt-F7 (I think this is uniform, but it may be F?, for some number ?), you should be back at the log in screen. See if it works then.

edit - on re-reading your post, I am not sure if you are even getting to the login screen. Could you clarify, and sorry if not and the above is useless.

---

### Post by lapor on 2012-08-29
Well i have the same problem. After cleaning with ubuntu tweak, i restarted computer, loged in, but after that there is nothing. Ok, there is my wallpaper and mouse pointer, but nothing else.

edit: and i use 12.04 ubuntu

---

### Post by NikTh on 2012-08-29
Hi @lapor , 
Can you open a terminal with Ctrl+alt+t combo ? if yes then try 
```
unity --reset
``` wait about 5-10 minutes and logout and login and see if fixed.
Thanks

---

### Post by lapor on 2012-08-29
I tried this and there is a lot of errors and warning, that compiz (core) couldn't load plugins and in the end it is written: Compiz (core) - Warn: this should never happen, you should probably file a bug about this.

But now I just tried to install fresh version of Ubuntu and computer stopped working. When I turn it on, screen is blank and it seems like processor is not working. Have no idea. Will leave it alone for today and will try something tommorrow.

thanks

---

### Post by josephmills on 2012-08-29
when you get to the black screen press ctrl+alt+f1 
then log in. Time to purge and re-install unity
```
sudo apt-get --purge remove unity 
```
then 
```
sudo apt-get install unity 
```
then 
```
sudo services lightdm restart 
```
anything ? 
if not 
```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y dist-upgrade
```

and restart lightdm again 
```
sudo service lightdm restart
```

Nothing post back.

---

### Post by lapor on 2012-08-30
I tried and nothing changed. I think I broke something with compiz...or not :/

I'll do a fresh install, because I really need computer right now, because I have some exams next week.

Thanks for your help.

---

### Post by lanetherif on 2012-08-31
I have the same problem. It has started after I cleaned the program cache data with Ubuntu-Tweak as if I need space of 600 mb in a 500 gb hard disk. I thought it might be a good idea since there were remnants of KDE programs. 

I can't be exact, but I have seen a lot of program cache going to trash like lib* etc.

I am trying the solutions provided here, starting with unity --reset (It seems to be stuck in "Update run_key"...

---

### Post by kansasnoob on 2012-08-31
Ubuntu Tweak is NOT supported by Ubuntu.

Please report problems with Ubuntu Tweak to Ding Zhou:

[https://launchpad.net/~tualatrix](https://launchpad.net/~tualatrix)

Their PPA says to do just that:

[ATTACH]223472[/ATTACH]

---

### Post by jaycee23 on 2012-08-31
I had exactly the same problem.

Had to do fresh reinstall in the end!

---

### Post by lanetherif on 2012-08-31
I have figured out the solution from an AskUbuntu question. 

Installing AMD/Ati card driver again solves the problem.

@Kansasnoob Don't you think one use of this forum is to provide an archive to encountered problems so that people can find the solution easier?

---

### Post by jaycee23 on 2012-08-31
Only thought I had (after the reinstall) was if you can run ccsm from terminal and check unity ubuntu plugin is ticked as working. 

It might just get things working again.

---

