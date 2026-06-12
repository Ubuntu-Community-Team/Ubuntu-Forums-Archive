---
title: "Are there any &quot;powersave&quot; options in gnome for use on a laptop running on battery"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by hovzio on 2008-08-24
Hi, I am have recently installed kde-desktop on my ubuntu box just to check out kde. So far I am really impressed, for me it is still slightly inconcieveable having two desktop environments installed on os :guitar: It doesn't get any better!

I noticed that in the power applet provided by kde I am given the option of adjusting up the "CPU policy" for AC and/or battery mode. This is really neat, my battery lasts a whole hour longer when I put it in powersave mode. How can I do this in Gnome and Xfce? Is there a configuration file for this somewhere? Any help is highly appreciated, thanks :)

---

### Post by eightmillion on 2008-08-24
I don't know about gnome since I'm a KDE guy myself but there is something that you can use in any desktop environment that can extend battery life. It's called powertop.
> sudo apt-get install powertop
You run it from a terminal and it helps you shutdown unneeded services. Also you can run the KDE power applet in XFCE and Gnome. You can call it from the command line with the command **guidance-power-manager**

---

### Post by RSingh on 2008-08-24
there is one but its hidden

open terminal: gconf-editor

apps >> gnome-power-manager >> ui

tick the option "cpufreq_show"

this will show the neccessary options in power manager

---

### Post by RSingh on 2008-08-24
accidental double post

---

### Post by hovzio on 2008-08-25
> **RSingh said:**
> there is one but its hidden

open terminal: gconf-editor

apps >> gnome-power-manager >> ui

tick the option "cpufreq_show"

this will show the neccessary options in power manager. 


Really cool! Thanks a lot. Just a few questions: the default on frequency for ac is 85, and for batt its 25. Is there a reason for ac being set to 85, is it alright to put it on 100? (I assume so I just want to make sure.)

I am also wanting to do this in Xubuntu, does gconf-edt. work for xubuntu? What I am really after is some sort of configuration file for the power settings, I am assuming that gconf is just a graphical frontend to some file. I've looked around /etc but haven't found anything. Would be very, very appreciative if someone could point me in the right direction. Thanks

---

### Post by cespinal on 2008-08-25
> **RSingh said:**
> there is one but its hidden

open terminal: gconf-editor

apps >> gnome-power-manager >> ui

tick the option "cpufreq_show"

this will show the neccessary options in power manager

Thanks for this, i will try it out too... 

big question? why is it hidden??? that makes absolutely no sense...

---

### Post by pauper on 2008-08-25
On gutsy:
```
less /etc/laptop-mode/laptop-mode.conf
```

[http://www.mjmwired.net/kernel/Documentation/laptops/laptop-mode.txt](http://www.mjmwired.net/kernel/Documentation/laptops/laptop-mode.txt)

Read "Caveats" before any testing.

---

### Post by RSingh on 2008-08-28
> **cespinal said:**
> Thanks for this, i will try it out too... 

big question? why is it hidden??? that makes absolutely no sense...

no idea, one thing i can say its a neat feature that should be available by default...:)

---

