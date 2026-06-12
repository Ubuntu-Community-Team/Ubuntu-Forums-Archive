---
title: "ati radeon hd"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by JoojiSan on 2012-02-17
I try ubuntu 10.04 and I have problems with the video drivers.
It can't find any property driver.
When I wrote in terminal:
lspci -nn | grep VGA

it shows:

00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]

I read ubuntu documentation
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
,and try to install firs fglrx driver, than completely remove it, and try with X.org - no changing.
After all i try some commands from the ubuntu documentation about RadeonHD 
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
.....nothing

what to do??

HEEEELP ME PLEACE!!!!

---

### Post by ajgreeny on 2012-02-17
What exactly is the problem you have?

---

### Post by JoojiSan on 2012-02-17
> **ajgreeny said:**
> What exactly is the problem you have?
  
Ubuntu can't find any property drivers.
I can't use any desktop effect, and all 3D don't work.
Sound also doesn't work.
I am not new, but amateur in linux.
I sped two day, trying to fix this, but nothing.

---

### Post by marin123 on 2012-02-17
What model is your card? If it's older, ATI don't support it anymore.
What 3D did you try?

Default driver is pretty good (I have ATI graphics with Xorg driver), and if you don't have proprietary drivers for installation, it doesn't mean your Ubuntu is broken.

---

### Post by ajgreeny on 2012-02-17
[LIST=1]
[*]Let us see the output in terminal of command ```
sudo lshw -C display
``` which will give more details than the **lspci** command.
[*]Have a look at the website at [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check) which has a simple script you can download and run to check if your hardware is able to run compiz.
[/LIST]

---

### Post by JoojiSan on 2012-02-18
lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]

sudo lshw -C display
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:80000000-8fffffff(prefetchable) ioport:4000(size=256) memory:90400000-9043ffff

My CPU is AMD E-300 apu with radeon hd on board for notebook, and my ubuntu is 64bit.
Can be that a problem, because the VGA is 32bit, or what that "width" mean.

I know, that if ubuntu can't find property driver doesn't mean broken, but I try a  simple 3D game and it doesn't work. I can't start advanced desktop  settings too.

I don't have sound too, but this is maybe another problem. 

Is it possible my VGA to be newer for Lucid?
Because I was on Ubuntu 11.10 and everything was fine, only the operating speed was killing me. .  That's the reason to change the version.

**Thank You** for the respond!

---

### Post by marin123 on 2012-02-18
> **JoojiSan said:**
> lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]

sudo lshw -C display
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:80000000-8fffffff(prefetchable) ioport:4000(size=256) memory:90400000-9043ffff

My CPU is AMD E-300 apu with radeon hd on board for notebook, and my ubuntu is 64bit.
Can be that a problem, because the VGA is 32bit, or what that "width" mean.

I know, that if ubuntu can't find property driver doesn't mean broken, but I try a  simple 3D game and it doesn't work. I can't start advanced desktop  settings too.

I don't have sound too, but this is maybe another problem. 

Is it possible my VGA to be newer for Lucid?
Because I was on Ubuntu 11.10 and everything was fine, only the operating speed was killing me. .  That's the reason to change the version.

**Thank You** for the respond!

Did you have Windows on that laptop? Could you play games?

I think that your onboard card isn't capable of Compiz (desktop effects) or games.

And, it isn't a problem with 64 bit Ubuntu, or the fact it is older.
Can you tell me your experiences with 11.10? Why did you leave it? Were the applications that were slow or the desktop? Example, how did Firefox work?

---

### Post by JoojiSan on 2012-02-18
> **marin123 said:**
> Did you have Windows on that laptop? Could you play games?

I think that your onboard card isn't capable of Compiz (desktop effects) or games.

And, it isn't a problem with 64 bit Ubuntu, or the fact it is older.
Can you tell me your experiences with 11.10? Why did you leave it? Were  the applications that were slow or the desktop? Example, how did Firefox  work?

No I don't have windows.

Firefox works pretty good.
I need PhotoshopCS5, and I can't run it.
I work with very big files in size of 1GB, with HDR functions and... It may be will work slow. 
My cpu was showing allways 70-95% for every operation, when I used 11.10. 
Or I am wrong, because the RAM is in half using. 
Before that I was with Ubuntu 10.10 and everything was fine.
How do you thing? Should I go again to 11.10?
The speed of Lucid exiting me every time.

If I go to newest ubuntu, which version will be better for my mashine 32bits ot 64bits?

---

### Post by JoojiSan on 2012-02-18
I fix the problem with the VGA
The drivers was Radeon HD 6300. I install it from amd site. 

Thanks for the responding.
Now I've got problems with the sound.  :)

---

### Post by marin123 on 2012-02-18
Open a new thread, and post me the link :)

Write what problem so you have, what is your soundcard and did it work in other Ubuntus.

---

### Post by pedja_portugalac on 2012-02-18
On my wifes Acer Aspire One 722 official AMD ATI Radeon HD from Ubuntu repository won't work. It's also 64bit system. I was on AMD ATI page and Downloaded corect proprietary driver for Linux 64bit system. I allowed it to execute as a program and then I switch to tty1 (ctrl+alt+F1). There I run
```
cd Downloads
sudo ./amd-ati.........wothever_name_of_driver
```
Fallowing the procedure and answering to some questions, then
```
sudo reboot
```
Everything works great now for her. Try it, I hope it works for you to.

---

### Post by JoojiSan on 2012-02-19
> **marin123 said:**
> Open a new thread, and post me the link :)

Write what problem so you have, what is your soundcard and did it work in other Ubuntus.


Thanks man!

---

