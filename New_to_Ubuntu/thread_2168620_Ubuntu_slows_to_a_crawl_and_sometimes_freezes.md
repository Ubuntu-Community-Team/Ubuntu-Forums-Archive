---
title: "Ubuntu slows to a crawl and sometimes freezes"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by mike44 on 2013-08-18
I am a long time admirer/user of Linux having tried a ton of different Distros and i keep coming back to Ubuntu.  It runs GREAT on my laptop, but randomly will start slowing way down(choppy mouse movements, slow typing, that sort of thing) and it will freeze.  Ive looked it up online and tried changing the 'swappiness value' and it sitll seems to do it.  My laptop is an HP DV6T-1300 with a core 2 duo 2.2 ghz and 4 GB RAM.  Not sure what to do or whats causing it.  Any help is greatly appreciated!!!

---

### Post by ahmad3 on 2013-08-18
what version of ubuntu are you on? i dont know that much but i will try to help :)

---

### Post by mike44 on 2013-08-18
I appreciate it!  Im on 13.04

---

### Post by ahmad3 on 2013-08-18
i used to get that sometimes it closes up by it self i installed 12.04 and it worked fine try doing that if possible my friend told me its something about drivers because they changed and what ever :P but i installed 12.10 and its working good now on 13.04 it used to be so slow and buggy firefox took ages to load hope this helps :D

---

### Post by mike44 on 2013-08-18
I may have to try that.  Ive been messing around in the settings and looking for ANYTHING that would lead me in the right direction and i may have found something.  I switched the theme from the default to the Radiance theme and i havent had any issues!...yet...  If this doesnt work i may have to jump down to 12.10 and see how that works.  

Id still like to know what is wrong with the default theme that would cause this?  Or perhaps it was just coincidence that it was fixed when i changed the theme.  Ill keep you posted though!  Thanks again for the help!

---

### Post by ahmad3 on 2013-08-18
yea its a graphics thing thats what they changed to into 13.04

---

### Post by mike44 on 2013-08-18
i figured, but it still seems wierd that one theme works and the other freezes up.  Anyway, i do appreciate your help :)  This isnt really related to this thread, but i want to learn more about what ubuntu has to offer, what i should do to familiarize myself with it...things like that?  Where do i begin?  lol

---

### Post by ahmad3 on 2013-08-18
ubuntu haves alot to offer :) if you want to learn what i know add me on skype: ahmade1700 
i dont really care that i posted my skype here :D

---

### Post by mike44 on 2013-08-18
I dont have skype and it looks like there isnt a download for Ubuntu 13 yet, just 12...according to skypes website anyway...

---

### Post by ahmad3 on 2013-08-18
dont downlaod it throw the website use the terminal i dont know if i will guide you through it here fallow these commands

1- sudo su

then inter your password

2- [COLOR=#414141][FONT=Arial]apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2

then i need to know what version of ubuntu u have 32-bit or 64 

-wget (one of the links below if your 32 or 64)

[/FONT][/COLOR]
[LIST]
[*]Skype 32-bit: wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32) and hit Enter.

[*]Skype 64-bit: wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64) and hit Enter.
[/LIST]

---

### Post by ahmad3 on 2013-08-18
oops i forgot
3- run this command

[COLOR=#414141][FONT=Arial]sudo dpkg -i getskype-*

4- and after thats done do this

[/FONT][/COLOR][COLOR=#414141][FONT=Arial]sudo apt-get -f install

and if its done doing all this stuff you should see skype on the launcher[/FONT][/COLOR]

---

