---
title: "locked out as system admin ubuntu 8.04"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by mhrpinca on 2008-05-04
I’m locked out of my system as administrator. I’m new and of course it was accidental here’s  what I did system, administrator, users and groups, properties, user privileges, and then I unticked administer the system, oooooops. Now I can’t sudo any thing I can’t update I cant run synaptic basically I cant admin my system so what do I do to fix it???????
Here is what I’ve tried 
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
and I tried typing start which warns me that I’m about to run in super user mode when I hit ok it drops me back down to a command prompt that says root but It doesn’t start the gui as super user and won’t let me fix the problem via the prompt I guess I’m screwed????
So does anyone know how I can find my virtualbox files so I can back them up and just reinstall ubuntu 
I want to be able to save my windows xp that I installed via virtual box …… thanks

heres my original post [http://ubuntuforums.org/showthread.php?p=4876574#post4876574](http://ubuntuforums.org/showthread.php?p=4876574#post4876574)

---

### Post by HunterThomson on 2008-05-04
You can boot up into BackTrack Live CD and then back up anything you want.

One time I put my account in the administrator group and then could not log into my computer at all LOL. The administrator can not log in by default.

Mybe just boot up into the Ubuntu Live CD you are root on a live cd. I just boot up my USB BackTrack3 with problems like that,

---

### Post by Tiede on 2008-05-04
You don't have to reinstall ubuntu. Ecerything is fine.

Reboot the computer. When the message Loading grub appears, press Esc (or down arrow) repeatedly. Scroll to the recovery option, and press enter.
The system will boot to a root shell.
Once there, type ```
startx
``` which will switch to a Graphical User Interface.
From there, go to System->Administration->Users and Groups, and fix everything back.

**WARNING: **Do **NOT** stay on longer and linger while root. After you are done, it is imperative that you logout of there and continue with your own account.
Good luck.

---

### Post by HunterThomson on 2008-05-04
> **Tiede said:**
> Reboot the computer. When the message Loading grub appears, press Esc (or down arrow) repeatedly. Scroll to the recovery option, and press enter.
The system will boot to a root shell.
Once there, type ```
startx
``` which will switch to a Graphical User Interface.
From there, go to System->Administration->Users and Groups, and fix everything back.

**WARNING: **Do **NOT** stay on longer and linger while root. After you are done, it is imperative that you logout of there and continue with your own account.
Good luck.

I wish I new that:lolflag:

---

### Post by HunterThomson on 2008-05-04
could you also just type that in the shell you get with fail safe mode?

---

### Post by mhrpinca on 2008-05-04
i tried that it just kicks me back to the terminal although as root user with no gui... i dont know much about linux but, when i normaly log in (before i had problems as admin) i had a problem with my desk top efects and my window decorations i have the compiz icon installed and i would have to reload the window manager to get my desk top to run corectly so i wondeer if the gui is crashing when i type startx, also i noticed there was an earlier version of /etc/sudoers file when i tried sudo visudo it also gave me a crash error and told me another progarm was using the file i was trying to change....
also earlier in the day iw ent to a site called sheilds up and it told me port 21 was open this port was being used bysamba share iwas also on an open network i dont think this is the problem but i dont know enough about linux to tell. the rest of the time my system has passed, any ideas?

---

### Post by mhrpinca on 2008-05-04
ok heres a new twist typeing startx doesnt work. but typing sudo start x does bring up the desk top, now when i go to system administration users and groups and click it it tells me the configuration can not be loaded and iyt says you are not allowed to acess the system configuration

---

### Post by Tiede on 2008-05-04
In a terminal, try ```
gpasswd -a username groupname
```
Replace usename with your username, and groupname with the admin group.
This is safer than the original option since there is less opportunity to mess up by making a typo. This alternatve was found on [nerdnotes.wordpress.com](http://nerdnotes.wordpress.com/2006/10/31/gpasswd-and-less-f/)

I am leaving the other just a a reference. Please only use it if no other alternatives are found.



--- Try top first --- Just found it thinking there HAS to be a better way.

try this:
It is very DANGEROUS if used improperly, so use with care.
```
 usermod -a -G adm mhrpinca
```
where adm is the admin group and mhrpinca your local username.
the -a is VERY important, so copy and paste rather than retype this.
usermod modifies which group the user belongs to.
-G lets you specify the groups you want the user belong to.
-a asks usermod to *append*the user to the named groups. Otherwise, the user is **removed** from ALL groups not specified on that line.
Please see ```
man usermod
``` if my explanation is not clear or you are left with questions.

---

### Post by Tiede on 2008-05-04
> **HunterThomson said:**
> could you also just type that in the shell you get with fail safe mode?
Yes, you can. I just wanted to make sure the least opportunities for mistakes were presented. You can't make a typo error when you tick a box on a GUI app. But he'll need to use the terminal after all, I'm afraid, since he says startx doesn't work for him in recovery mode. Probably should check on that...

---

### Post by mhrpinca on 2008-05-04
cool thanks Tiede i typed the first one you sugested gpasswd -a username groupname this gave me back my addministartive privilidge my synaptic package manager is back i can unlock users and groups, looks like every thing is good is there any thing i need to clean up after doing all that was listed above???

and how do i mark this as solved??????
 thanks again guys

---

### Post by Tiede on 2008-05-06
You don't need to do anythingelse, that should be all that's needed.
Just go have some fun!
And, to mark this as solved you can go to the top of this page, click on thread tools and select mark as solved. --taken from this [wiki page](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads).

---

### Post by shashidharan on 2008-06-23
I had a similar problem. One difference is, i had modified my root password and had also unchecked the  administrator privileges for (first)user. This locked me out silly. *(I didnt know about "startx"   so had to boot from the login window)*. I logged into root using my new admin pasword, using the SU command.  Then did "~# sudo gpasswd -a username groupname". If i remember right, i had to use the sudo prefix. Could you confirm whether the above procedure is valid? Disclaimer: "Please do not try this at home"

---

