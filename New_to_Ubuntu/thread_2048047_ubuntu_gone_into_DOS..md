---
title: "ubuntu gone into DOS."
date: 2012-08-26
forum: New to Ubuntu
---

### Post by cazzie on 2012-08-26
Hi< i have ubuntu 10.04 and is stuck in DOS, how do i come out of this and go to my usual ubuntu?

---

### Post by Linux_junkie on 2012-08-26
Thats a good trick! DOS is a completely different operating system to Linux.  I think you mean the CLI (command line interface) also known as Linux.

Can you type in startx

If it doesn't run, publish any messages you get here please.

---

### Post by androssofer on 2012-08-26
> **cazzie said:**
> Hi< i have ubuntu 10.04 and is stuck in DOS, how do i come out of this and go to my usual ubuntu?

does it say tty1? or sumthing similar?

if it does try pressing..

ctrl  alt  F7


should get you back.. 

**side note** DOS is a windows things, its called the CLI on GNU/Linux

---

### Post by phibxr on 2012-08-26
Did it work properly earlier, or is this a brand new installation? If it worked earlier, what were the last operations you performed before it stopped working?

If you have any other operating systems installed, are they working properly?

To be able to troubleshoot this, we will really need some more information.

---

### Post by vokevybez on 2012-08-26
maybe you've gone into recover mode? or accessd one of the virtual terminals?

---

### Post by gandaran on 2012-08-26
> **cazzie said:**
> Hi< i have ubuntu 10.04 and is stuck in DOS, how do i come out of this and go to my usual ubuntu?
did you remove something that removed ubuntu-desktop too?
if that was the case then re-install ubuntu desktop from the command line prompt then reboot.

---

### Post by cazzie on 2012-08-26
> **androssofer said:**
> does it say tty1? or sumthing similar?

if it does try pressing..

ctrl  alt  F7


should get you back.. 

**side note** DOS is a windows things, its called the CLI on GNU/Linux
thanks for message, if this is the case, what do i do next?

---

### Post by ubudog on 2012-08-26
> **cazzie said:**
> thanks for message, if this is the case, what do i do next?

Does pressing Ctrl+Alt+F7 work?

---

### Post by linuxman72 on 2012-08-26
When you entered command line, had the computer been running normally? if not, then restart the computer. after it shows the loading screen for the brand of the computer(like dell) then hold down shift. a menu should come up. select the version of linux you are using,making sure it does not say "recovery mode" after it.(it should be the top one) your computer should start normally.

---

### Post by cazzie on 2012-08-26
> **cazzie said:**
> thanks for message, if this is the case, what do i do next?
Hi, ive tried this , so i will tell more, its ubuntu 9.10 , i was looking on ebay the last time i was viewing from laptop so the next time i tried to get on it just went into this black screen with this writing on

---

### Post by cheat117 on 2012-08-26
> **cazzie said:**
> Hi, ive tried this , so i will tell more, its ubuntu 9.10 , i was looking on ebay the last time i was viewing from laptop so the next time i tried to get on it just went into this black screen with this writing on

i would suspect that you may have accidentally pressed F5 and held control by accident. pressing Ctrl-Alt-F7 may help and startx as a command may also help however.

If neither work then I would write down the errors and type them out for the more experienced users on the forum to help with. :D

---

### Post by cazzie on 2012-08-26
> **linuxman72 said:**
> When you entered command line, had the computer been running normally? if not, then restart the computer. after it shows the loading screen for the brand of the computer(like dell) then hold down shift. a menu should come up. select the version of linux you are using,making sure it does not say "recovery mode" after it.(it should be the top one) your computer should start normally.
Hi, ive followed your advice and it still not worked, apparently had some trouble with this before , im on ubuntu 9.10, i want to at least get laptop up and working so i can buy 12.4 and load this . my hubby said he had, had a few problems just before this. i have a whole list of cammands i wrote down fron the laptop . any ideas????????????????

---

### Post by cheat117 on 2012-08-26
Cazzie, is there anything of importance on the laptop? if not you could always just install right over ubuntu 9.04 with 12.04

To be honest, if you have a liveCD that is ready to go, try putting that in to save whatever is necessary and then install over 9.04

---

### Post by cazzie on 2012-08-27
> **cheat117 said:**
> Cazzie, is there anything of importance on the laptop? if not you could always just install right over ubuntu 9.04 with 12.04

To be honest, if you have a liveCD that is ready to go, try putting that in to save whatever is necessary and then install over 9.04
Hi, thanks, i dont think i mentioned " the laptop is not running, can you please give me more advice,"it does switch on, but does not have its desktop up"

---

### Post by gandaran on 2012-08-27
> **cazzie said:**
> Hi, ive followed your advice and it still not worked, apparently had some trouble with this before , im on ubuntu 9.10, i want to at least get laptop up and working[COLOR="Red"] so i can buy 12.4[/COLOR] and load this . my hubby said he had, had a few problems just before this. i have a whole list of cammands i wrote down fron the laptop . any ideas????????????????
Ubuntu is free, download Ubuntu 12.04 [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) then either install the ISO to a live pen drive or burn to CD, try run live session first to see if everything works okay on the laptop then if it does install over 9.04 but backup anything important to another drive first. 9.04 is very old and unsupported now.

---

### Post by Linux_junkie on 2012-08-27
After reading all the comments in this thread I don't believe you have a problem with the desktop or that you even have Ubuntu.  Your first comment says you have Ubuntu 10.04 then later you say you have 9.10.  You also say that you want to buy 12.04.  Version 12.04 is free you don't pay for it.  


I suspect you are a "troll"

---

### Post by mastablasta on 2012-08-27
perhaps the user had 10.04 installed along with proprietary graphics drivers. and was then prompted to upgrade. they then upgraded to 12.04 which ended up as CLI.

---

### Post by cazzie on 2012-09-02
Hi, i dont think i would be able to upgrade or would i ??????? any ideais?  please

---

### Post by Bashing-om on 2012-09-02
cazzie;

  Yes, you can "up-grade" ..follow the suggestion to download the new 12.04 .iso; in the above post.

Burn it as an image to a cd (or usb device).
set your bios boot order to boot from cd (or usb) first.
insert the live cd into the cd drive.
when ubuntu boots up, choose the "try ubuntu" option... insuring all works good.

If you like what you have as it is presented to you. Install !

A simple process that can be fraught with anxiety.
any questions/assistance needed---> ask !

---

### Post by linuxman72 on 2012-09-02
when you said it didn't work, did you run it in safe mode, or did it just fail? also, what does command line say when it comes up?

---

### Post by cazzie on 2012-09-02
Hi Mastablasta, thanks for your advice, i have downloaded the book and going to have a go with the cd ive just burnt. Thank You.

---

### Post by cazzie on 2012-09-02
it just failed, ive wrote down a whole lot of commands, says,alias break cd chdr command continue eacho avalexecexit export false getapts hash help let local printf pwd read only return set shift sourceest times trap true type ulimit lmask un alias unset wait [ [ E ashaw kbasename cat chmod chroat chut clear cmp op cut deal locut df du dumpkmap echo egrep en v expr false fbset  fdf lush fgrep gunzip gzip hostname if comfig ip kill in loadfont load kmap is mkdir mkfifo mknod mkswap mktemp more mount mu openut pidof printf ps pwd keycodes sh sleep sort stat stty sync tail tee test touch tr truetty umant uname uniq wc wget yes zcat (inltramfs)

---

### Post by cazzie on 2012-09-02
[QUOTE=cazzie;12213035]it just failed, ive wrote down a whole lot of commands, says,alias break cd chdr command continue eacho avalexecexit export false getapts hash help let local printf pwd read only return set shift sourceest times trap true type ulimit lmask un alias unset wait [ [ E ashaw kbasename cat chmod chroat chut clear cmp op cut deal locut df du dumpkmap echo egrep en v expr false fbset  fdf lush fgrep gunzip gzip hostname if comfig ip kill in loadfont load kmap is mkdir mkfifo mknod mkswap mktemp more mount mu openut pidof printf ps pwd keycodes sh sleep sort stat stty sync tail tee test touch tr truetty umant uname uniq wc wget yes zcat (inltramfs
:guitar:this is the cammands i have, can anyone help pleeeaasssee.:confused:

---

### Post by cortman on 2012-09-02
> **cazzie said:**
> [QUOTE=cazzie;12213035]it just failed, ive wrote down a whole lot of commands, says,alias break cd chdr command continue eacho avalexecexit export false getapts hash help let local printf pwd read only return set shift sourceest times trap true type ulimit lmask un alias unset wait [ [ E ashaw kbasename cat chmod chroat chut clear cmp op cut deal locut df du dumpkmap echo egrep en v expr false fbset  fdf lush fgrep gunzip gzip hostname if comfig ip kill in loadfont load kmap is mkdir mkfifo mknod mkswap mktemp more mount mu openut pidof printf ps pwd keycodes sh sleep sort stat stty sync tail tee test touch tr truetty umant uname uniq wc wget yes zcat (inltramfs
:guitar:this is the cammands i have, can anyone help pleeeaasssee.:confused:

The way you're responding makes it difficult to impossible for anyone to  help. I recommend you read [this]("http://www.catb.org/esr/faqs/smart-questions.html"), and come back with some useful  information and grammatically clear, legible posts.

---

### Post by cazzie on 2012-09-08
Actually you are wrong, i bought mine from " theopensourceshop. com and it cost me £9.99 its a boot usb. i may be having problems but i am no troll.  i got it wrong,  9.10 ubuntu on the laptop. ive been trying with all sorts of well meaning advice, nothing has worked.  i want to clear the laptop of this and do a clean upload from the usb , if i could get it to it. any help /

---

### Post by Bashing-om on 2012-09-09
cassi;
  How is it going, not heard from you lately... Still having problems ?

Look at this howto and we take it from there.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

ok ?               <==BDQ

---

