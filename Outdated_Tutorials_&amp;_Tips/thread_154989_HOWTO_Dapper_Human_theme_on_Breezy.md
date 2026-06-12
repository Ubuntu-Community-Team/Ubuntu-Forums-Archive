---
title: "HOWTO: Dapper Human theme on Breezy"
date: 2006-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by psychicdragon on 2006-04-04
Hi all.

This is a backport of the gtk2-engines-ubuntulooks package in Dapper, which includes the Ubuntulooks GTK+ theme engine and the new Human theme. The theme has been renamed to Human-Dapper so it won't overwrite the current Breezy Human theme.

There are already some themes up on Gnome-Looks.org that depend on the Ubuntulooks engine, so I thought some others might want this.


Get the package here: **[gtk2-engines-ubuntulooks_0.9.9-1_i386.deb]("http://rapidshare.de/files/16876915/gtk2-engines-ubuntulooks_0.9.9-1_i386.deb.html")** (I had to upload it to rapidshare because I have no webspace.)


**Installing:**```
sudo dpkg -i gtk2-engines-ubuntulooks_0.9.9-1_i386.deb
```

Have fun.

---

### Post by caeza on 2006-04-15
Thank you very much!
I was looking for it.

---

### Post by xXx 0wn3d xXx on 2006-04-15
Is there a way to get the new dapper icons on breezy ? I like them but I can't get them. Can someone who is on dapper go under their icons/theme folder and upload it ? Make sure to zip it.

---

### Post by dabear on 2006-04-15
[QUOTE=MasterChief1234]Is there a way to get the new dapper icons on breezy ? I like them but I can't get them. Can someone who is on dapper go under their icons/theme folder and upload it ? Make sure to zip it.[/QUOTE]
Here you go, dappers human-icons:

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=dabear]Here you go, dappers human-icons:[/QUOTE]
Let me see if I can get them to work...thank you very much for uploading them.

---

### Post by psychicdragon on 2006-04-29
Hi,

Anyone who installed this theme may need to remove it before upgrading to Dapper. I haven't upgraded myself yet, but there is a possibility of it conflicting with the Dapper gtk2-engines-ubuntulooks package because the version number is the same. 

Just a heads up.

---

### Post by brian g on 2006-05-08
not working for me.. and ideas?

```
brian@bertha:~$ sudo dpkg -i gtk2-engines-ubuntulooks_0.9.9-1_i386.deb
Password:
(Reading database ... 97464 files and directories currently installed.)
Preparing to replace gtk2-engines-ubuntulooks 0.9.9-1 (using gtk2-engines-ubuntulooks_0.9.9-1_i386.deb) ...
Unpacking replacement gtk2-engines-ubuntulooks ...
Setting up gtk2-engines-ubuntulooks (0.9.9-1) ...
brian@bertha:~$

```

---

### Post by SkyNet2029 on 2006-05-08
Very nice indeed..  Sticking with my OSX icons though :-) That logout icon looks so much smoother methinks. 

Anyway... Your install that you posted (Brian) shows a succesful dpkg install. All that is left is for you to manually change up your theme preferences via the System/Preferences/Themes from your Menu Bar. (The Dapper-Human is listed under Theme Details/Controls tab.

Thanks again for the port!

---

### Post by brian g on 2006-05-08
[QUOTE=SkyNet2029]Very nice indeed..  Sticking with my OSX icons though :-) That logout icon looks so much smoother methinks. 

Anyway... Your install that you posted (Brian) shows a succesful dpkg install. All that is left is for you to manually change up your theme preferences via the System/Preferences/Themes from your Menu Bar. (The Dapper-Human is listed under Theme Details/Controls tab.

Thanks again for the port![/QUOTE]
thanks. i had looked there but i didn't realize tehy were not in alphabetical order.

---

### Post by phorque on 2006-05-09
I, on the other hand, much prefer the breezy human icon theme to the dapper one. Anyone know where I can get the old one?

---

### Post by marioparris on 2006-05-15
Hey, I'm new to Ubuntu and I just installed the package. 

The Human-Dapper controls are installed just fine, but isn't supposed to change the Window Borders too? If it is I can't find the window-border in there. If its called Human Dapper just like the control theme, then its not there.

---

### Post by marioparris on 2006-05-15
Nevermind I figured it out :o) Installed ClearLooks 2 from gnome-look.org

---

