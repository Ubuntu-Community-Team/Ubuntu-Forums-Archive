---
title: "[SOLVED] I need help creating &amp;quot;Stricter defaults&amp;quot; for Ubuntu"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by pixarinc on 2008-11-04
Even though my ATI radeon 7500 graphics card does not allow me to enjoy the unholy desktop navigation that compiz offers, I'm still blown away by Ubuntu. From sampling the entire OS through the cd, to being able to USE EVERYTHING (i.e. browse the web) AS it's installing!!! I still can't get over the fact that I don't have to install my router program, update any drivers, upgrade to SP whatever. So many things to appreciate my head's gonna explode... Maybe I'm just easy. I'm a Microsoft user.

Which brings me to this; I've been an xp user all my life and I have no experience whatsoever with any other OS or Linux distro. I'm following this article on tightening default security:

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)
 &
[https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults)

Now... I can't even do the very first thing they recommend. From my understanding, it's making "shared memory" read only. These are the instructions:

"To change this setting, edit the /etc/fstab file to include the following line:

tmpfs     /dev/shm     tmpfs     defaults,ro     0     0"

Huh? Okay, so I searched around but could not find much. I managed to find the terminal. And I managed to find out how to access /etc/fstab with this line: sudo nano /etc/fstab. 

Now I'm in what to me looks like a text with lines of codes and comments. Where do I put "tmpfs /dev/shm tmpfs defaults,ro 0 0" and how exactly do I save and exit? It says to exit "X^" but I have no idea what that means. I don't plan on asking you guys to help me on every single step in this security guide; tomorrow I'm borrowing an Ubuntu beginners book and I'll learn the ropes but I'd like to "secure" it and experiment until then.  

Thank you very much,
pixarinc.

---

### Post by crazyness003 on 2008-11-04
CONGRATS YOU KNOW HOW TO ACCESS TERMINAL. Trust me, it took me 3 days to figure it out when i started..okay not 3 days but still.

There's a better way of accessing that file with a real gui app.
```
[COLOR=SeaGreen]gksu[/COLOR] gedit /etc/fstab 
```What you're doing is using [COLOR=Green]gksu[/COLOR] (the GUI version of [COLOR=Red]sudo[/COLOR] [[COLOR=Red]su[/COLOR]per user [COLOR=Red]do[/COLOR]]) to open gedit (its the GNOME version of notepad, or wordpad in win) with the file in /etc/fstab (the first slash is called "root" or "filesystem")

EDIT: Forgot to mention, if you're using Kubuntu (the KDE version) and not Ubuntu (the GNOME version), then replace anywhere that i said *gedit* with *kate*. Its the KDE version of notepad etc.

Now as for the 
```
tmpfs     /dev/shm     tmpfs     defaults,ro     0     0"
```Id behave at what you put in fstab. Its not necessarly good to f-up your fstab (its like screwing with the boot.ini file in windoze). Honestly i dont even know what that piece of code does (sorry didnt follow your links, kinda late here right now).

First, id back it up. Open the file in gedit (with [COLOR=SeaGreen]gksu[/COLOR]). then hit save as... and name it like fstab.backup. Close gedit, then run the command again, then mess around. So if you do tank it (break it), you can just boot into a liveCD and replace the broken fstab with your spiffy original fstab.backup (make sure you remove the *.backup* part)

Then just go to the last line, hit return (enter) to make a new line and paste the code. You might have to do a restart, since fstab has to reload again to get the changes working. And there you have it.

Again be warned, fstab is not a plaything and [COLOR=Red]sudo[/COLOR] (or [COLOR=SeaGreen]gksu[/COLOR]) is like electricity, if you dont know what your doing, you'll get a shock of reality

---

### Post by asmoore82 on 2008-11-04
"X^" is geek short-hand for Control+X I think ...

but you would probably be much more comfortable editing the file with "gedit" ...
press Control+C to exit nano without saving and run this in that terminal:
```
gksudo gedit /etc/fstab
```

---

### Post by crazyness003 on 2008-11-04
> **asmoore82 said:**
> "X^" is geek short-hand for Control+X I think ...

but you would probably be much more comfortable editing the file with "gedit" ...
press Control+C to exit nano without saving and run this in that terminal:
```
gksudo gedit /etc/fstab
```

And theres my screwup. [COLOR=Red]gksu[/COLOR] or [COLOR=Red]gksudo[/COLOR] is what you'd use for gui apps, and [COLOR=Red]sudo[/COLOR] for terminal apps. (they do the EXACT same thing, but it does make a difference)

RANT...RANT

Thanks for pointing that out asmoore82

---

### Post by pixarinc on 2008-11-04
*And* it has superior support, surprise surprise!

Thank you crazyness003 and asmoore82. Gedit makes quitting and saving a whole lot easier and I will definitely backup all my system files before tinkering with them.

---

### Post by crazyness003 on 2008-11-04
> **pixarinc said:**
> _*And* it has superior support, surprise surprise!_

Thank you crazyness003 and asmoore82. Gedit makes quitting and saving a whole lot easier and I will definitely backup all my system files before tinkering with them.

Huh?

Anyway, we never formally welcomed you to the forums. So 
Welcome to **THE MOST AWESOME, RIDICULOUS, AND INFORMATIVE FORUM THAT CONTAINS INFORMATION ABOUT YOUR NEW UBUNTU INSTALLATION!**
...we're still working on the name (TMARaIFTCIAYNUI is the acronym)

Oh and when you ask a question and are satisfied with the answer, please use the _**[COLOR=Red]Thread Tools[/COLOR]**_ link (located at top of page, right above your first post), and hit [COLOR=Red]Mark as SOLVED[/COLOR]. It basically says that your problem is solved, so people don't get confused...i guess.

Have fun

---

### Post by pixarinc on 2008-11-04
Thanks for the welcome. I just meant that ubuntu also has superior support compared to Microsoft, in addition to their being superior in every other aspect. :)  

I have another question though :p So now it's time to make "SSH" safer... but I can't seem to find it. I type gksudo gedit /etc/ssh/sshd_config into the console but all I get is an empty page. I'm supposed to replace existing lines of code in the document but it's just blank...

ETA: Nevermind, I'm just going to assume for now that it worked. I'm going to install a firewall and a rootkit detector and my system should be "safe" for now until I learn more advanced security measures tommorow. Thanks.

---

### Post by crazyness003 on 2008-11-04
> **pixarinc said:**
> Thanks for the welcome. I just meant that ubuntu also has superior support compared to Microsoft, in addition to their being superior in every other aspect. :)  

I have another question though :p So now it's time to make "SSH" safer... but I can't seem to find it. I type gksudo gedit /etc/ssh/sshd_config into the console but all I get is an empty page. I'm supposed to replace existing lines of code in the document but it's just blank...

ETA: Nevermind, I'm just going to assume for now that it worked. I'm going to install a firewall and a rootkit detector and my system should be "safe" for now until I learn more advanced security measures tommorow. Thanks.

You know, im not sure if you're just paranoid or if you like to "foolproof" secure your box, but i think you're going a little overboard. But then again, thats what freedom is all about. Im sorry if I cant help you there, i dont even use ssh (i dont even know what that is ;p)
And just so you know, nothing is "safe," as long as its connected to the interwebs, you _*might*_ get attacked. Again, _*might*_!
But as for spyware/viruses...you're 99.9% covered with no need for security tools. Its like Lysol® Disinfecinting Spray for your computer-machine! :p

---

