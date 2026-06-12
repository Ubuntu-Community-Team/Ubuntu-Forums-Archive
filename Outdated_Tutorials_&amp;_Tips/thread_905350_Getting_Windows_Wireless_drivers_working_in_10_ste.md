---
title: "Getting Windows Wireless drivers working in 10 steps"
date: 2008-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by david sousa on 2008-08-30
*I had a little "Intrepid" story last night. It was about 4 o'clock and I thought I was an Hero. I made an upgrade to 8.10 Alpha 4 system. The fact is that I couldn't boot after this. So I gave up and reinstalled Hardy Heron. I had to do the same configurations again. But that's just a a poetic introduction. It suddenly came to my mind to explain like i did in so many threads how to get connected through Windows Wireless Drivers.*

[LIST=1]
[*]So let's do this in simple steps. Imagine that you have just installed Ubuntu: 


[*]You have to be connected with an wired connection or you have will have to download things apart. (not a big deal)


[*]Go at System -> Administration -> Software Sources -> Third-Party Software and check every boxes there


[*]Go at System -> Administration -> Synaptic Packages Manager and search for **ndisgtk**. Mark that for installation and apply it.


[*]If you want to know your wireless card you can type

> lspci 

at the terminal. Go at the last line of the ouput where you have the **Network controller:**. Your wireless card is the "blah blah" next to it. In my case, a Broadcom Corporation BCM4312 802.11b/g (rev 01). Now you can google that or search for your pc network drivers. (easiest way I think)


[*]In both cases you will get an **.exe** file which you can extract at the terminal using the **unzip** command:

> cd <dir where the file is>
unzip <file>

or the **cabextract** command:

> cd <dir where the file is>
cabextract <file>

[*]After this, go here: System -> Administration -> Hardware drivers and check the box there to enable your wireless card which can be restricted.


[*]At System -> Administration -> Windows Wireless drivers you can add the **.inf** file located at the folder where you have extracted the **.exe** file. And if it says **"Hardware present: yes"** then...


[*]just reboot you pc and...


[*]Voilá

[/LIST]
Hope this has been helpful...

---

### Post by jnklein on 2008-12-27
Great guide, worked perfectly for me. Thanks!

---

