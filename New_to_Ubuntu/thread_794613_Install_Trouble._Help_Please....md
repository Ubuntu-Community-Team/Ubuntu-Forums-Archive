---
title: "Install Trouble. Help Please..."
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-05-14
Hey, so im trying to install Ubuntu on an older machine using the Alternate CD. When i select the install option the screen just goes black, with a  blinking _ in the top left corner, it looks like a console almost, but there are no borders, the whole screen is black except that one part, and i can not type or anything. 

Can anyone help me get past this? that would be great.

---

### Post by spiderbatdad on 2008-05-14
Does the alternate cd offer you the choice to press F6, to enter boot parameters, from the install options screen? You would press F6 and at the end of the kernel line that appears delete any text after 'ro' and add noapic nolapic

Or press F6 and read the dialogue for more options, like Press F1 to read more options...press F3 for examples...etc.

---

### Post by Codemastadink on 2008-05-14
> **spiderbatdad said:**
> Does the alternate cd offer you the choice to press F6, to enter boot parameters, from the install options screen? You would press F6 and at the end of the kernel line that appears delete any text after 'ro' and add noapic nolapic

Or press F6 and read the dialogue for more options, like Press F1 to read more options...press F3 for examples...etc.

From the installer options screen if i hit F6 it brings up a little box with a few things, 2 being "noapic" and "nolapic" if i hit enter while they are highlighted it puts an x by them.

I put an x by them and ran the installer and it came to another blank screen and displayed 

"Starting system log daemon: syslogd, klogd." 

Thats all it says and will not go past that screen

---

### Post by spiderbatdad on 2008-05-14
Unfortunately I have never used the alternate cd, so I can't advise you specifically, but now you are aware of some of the possibilities. If you feel like you have exhausted all the possibilities, it is entirely possible the disk you have is not installable. I have had a disk that verified with md5sum, but I could not get it to install on an old HP laptop. I gave up for several months, and one day downloaded a new image and burned a new disk...booted with options noapic nolapic and viola...xubuntu has been running on that machine for 6 months now.

---

### Post by dtrot55 on 2008-05-14
what is the specs of this older machine....i tried to install ubuntu on one of my older machines and found out that my specs didnt meet the requirements

---

### Post by Codemastadink on 2008-05-14
> **dtrot55 said:**
> what is the specs of this older machine....i tried to install ubuntu on one of my older machines and found out that my specs didnt meet the requirements

Pentium 3 667Mhz
128Mb RAM
8Mb Video
idk about the hard drive. i seem to remember just over a gig idk

---

### Post by dtrot55 on 2008-05-14
Well in my experience..128mb of ram wasn't enough for me either...so you will probably have to go get puppy linux or some version of linux that will run on machines with 128mb of RAM....because i had the same issue...the cd would boot up and then it would go black and do nuthing.  So i think that is your issue.

Puppy Linux worked just fine for me too.

---

### Post by spiderbatdad on 2008-05-14
Xubuntu is suitable to that amount of ram.

---

### Post by dtrot55 on 2008-05-14
hehe forgot about xubuntu...yeah go try that..sure it will work just fine. Thanks for the refresher spider

---

### Post by Codemastadink on 2008-05-14
> **dtrot55 said:**
> Well in my experience..128mb of ram wasn't enough for me either...so you will probably have to go get puppy linux or some version of linux that will run on machines with 128mb of RAM....because i had the same issue...the cd would boot up and then it would go black and do nuthing.  So i think that is your issue.

Puppy Linux worked just fine for me too.

Well, It has gotten into the install process before but frozen along the way. Every like 1 out of 20 times i try it it works, it says it needs at least 64mb to install so idk, i was gunna put more ram in later anyways, do you think if i do that now then it would install?

---

### Post by dtrot55 on 2008-05-14
did you try puppy linux or xubuntu?? Because both should work for you just fine.  I dont know if those two OS's have a limit on the processor to...a 667mhz is pretty old..but i doubt thats the issue...I would keep checking this post and also it doesnt hurt to try more memory...and maybe your cd drive is messed up? because im sure your machine is to old to boot off a removeable item...so don't give up

---

### Post by Codemastadink on 2008-05-15
> **dtrot55 said:**
> did you try puppy linux or xubuntu?? Because both should work for you just fine.  I dont know if those two OS's have a limit on the processor to...a 667mhz is pretty old..but i doubt thats the issue...I would keep checking this post and also it doesnt hurt to try more memory...and maybe your cd drive is messed up? because im sure your machine is to old to boot off a removeable item...so don't give up

I know the Cd drive isn't broken. it was a spare that i had and i tested it on my good computer first. I think it may be the Hard Drive, im gunna hook it up to a different computer right now and see if it works. The comuter stopped working a while ago and i just barely got it back and running. it wouldnt even turn on before and ive replaced some parts already, i think pretty much everything is broken lol well i'll keep trying then. 

Thanks a bunch for everything guys

---

### Post by Codemastadink on 2008-05-15
> **Codemastadink said:**
> I know the Cd drive isn't broken. it was a spare that i had and i tested it on my good computer first. I think it may be the Hard Drive, im gunna hook it up to a different computer right now and see if it works. The comuter stopped working a while ago and i just barely got it back and running. it wouldnt even turn on before and ive replaced some parts already, i think pretty much everything is broken lol well i'll keep trying then. 

Thanks a bunch for everything guys
Well, i checked the Hard Drive and it works, but it just cant be booted into, which is no problem, but i can read all of the files on it so it isnt broken. Idk guys any more suggestions?

---

