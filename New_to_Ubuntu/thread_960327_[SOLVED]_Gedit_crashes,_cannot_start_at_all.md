---
title: "[SOLVED] Gedit crashes, cannot start at all"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by reg4c on 2008-10-27
Hey, 

well, as the title says my Gedit does not work at all.
Does not work from the terminal with gedit &, or with sudo, or from the menu, or from AWN.

Does not work after a purge reinstall
All I get to is the attached screen and then nothing happens
When I want to close it I must either Force Quit or killall

Hope someone can help,
Cheerio

---

### Post by LowSky on 2008-10-27
Could you run gedit from terminal and copy paste the contents of what it says in terminal.

Thanks

---

### Post by reg4c on 2008-10-27
It does not say anything

```
regac@regac-laptop:~$ gedit
^C
[1]+  Killed                  gedit
```

I let it run for a few minutes.
Also, when it starts one of my cores goes up to 100% usage.

Cheers

---

### Post by LowSky on 2008-10-27
Ok im at work but and not on a linux machine but maybe this will work

Go to you /home folder, show the hidden files, hopefully there is one for gedit. If there is delete the file

then try to start gedit

---

### Post by asgard_command on 2008-10-27
I had this problem after installing Intrepid and playing with the themes a bit, although mine would start eventually say after 20 to 30 seconds. Disabling the File Browser plugin seems to be a temporary fix.

 Bug #280411:

---

### Post by LowSky on 2008-10-27
> **asgard_command said:**
> I had this problem after installing Intrepid and playing with the themes a bit, although mine would start eventually say after 20 to 30 seconds. Disabling the File Browser plugin seems to be a temporary fix.

So your saying its a Compiz issue... :confused:

---

### Post by reg4c on 2008-10-27
> **LowSky said:**
> Ok im at work but and not on a linux machine but maybe this will work

Go to you /home folder, show the hidden files, hopefully there is one for gedit. If there is delete the file

then try to start gedit

I tried this before posting but there aren't any gedit related files AFAIK in home, at least I did not find them

> **asgard_command said:**
> I had this problem after installing Intrepid and playing with the themes a bit, although mine would start eventually say after 20 to 30 seconds. Disabling the File Browser plugin seems to be a temporary fix.

Bug #280411:
I don't have a File Browser in CCSM. Is is there or in somewhere else?


> **LowSky said:**
> So your saying its a Compiz issue... 
I wouldn't say it was a Compiz issue, but then again I am a n00b
This started a couple of days back after an update I think

Cheers

---

### Post by asgard_command on 2008-10-27
> **LowSky said:**
> So your saying its a Compiz issue... :confused:

No. I have no idea actually but when I first installed Intrepid I didn't have the issue. The first time I noticed it was after installing Emerald and playing with my themes since my Hardy theme didn't work with Intrepid, but that could be just a coincidence. There is nothing on the bug report to suggest it is linked with themes but seemed like it was connected in my case.

---

### Post by asgard_command on 2008-10-27
The File Browser plugin is in gedit in preferences/plugins then deselect the file browser plugin. If gedit won't start at all even after waiting I'm not sure how to edit the preferences probably a config file in home somewhere I'm sure someone else will know.

---

### Post by reg4c on 2008-10-27
> **asgard_command said:**
> The File Browser plugin is in gedit in preferences/plugins then deselect the file browser plugin. If gedit won't start at all even after waiting I'm not sure how to edit the preferences probably a config file in home somewhere I'm sure someone else will know.

Y'see, the thing is that, as shown in the screenshot, I cannot see the menubar therefore I cannot access the preferences for Gedit

EDIT: Now, I did something, I am not sure what is it that fixed Gedit and the menu appeared. Went to the plugins and disabled the File Browser Pane and now it starts normally. So far so good: Gedit starts normally.

Marked as solved.
Thanks to all.

---

