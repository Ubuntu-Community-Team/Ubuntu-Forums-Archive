---
title: "Is Ubuntu the right thing for me?"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by yourname2 on 2014-03-21
1) Will Ubuntu run on my "Toshiba satellite a110-275" from 2006? [http://www.toshiba.co.uk/discontinued-products/satellite-a110-275/](http://www.toshiba.co.uk/discontinued-products/satellite-a110-275/)
2) I would like to connect my computer and phone(nokia asha 501) to share files, calendar, install and uninstall apps, do the settings etc. is that possible just like that or do I need to change the os on my phone as well?
3) At one point I might have to install Autodesk Inventor (once I have a new pc) is Ubuntu and Inventor still not compatible?

Hi guys,

I guess me and technology just drifted apart over the last few years, my phone could only make calls and write msg before it broke down(poor little soldier died of old age and too much beer) and to browse the internet I didn't need a 2000€ facebook-machien so I never changed from my first computer. So now I got a basic smart phone(Nokia Asha 501) for 60€ (hopefully a good choice). Since I have to go back to school and therefore can't afford a new one I should take better care of my computer.
A lot of the knowledge that you might see as a given can easily sound like gibberish to me, so please keep that in mind when some of my questions sound silly to you. I also wrote the essential questions on top for the people who don't want to read the whole text. All right, here they come and thanks in advance...

My computer a Toshiba satellite a110-275 from 2006 behaves just like his age requires, the old man is slow, grumpy and shuts down occasionally in the middle of the day.
I hope to get him back to his prime with a new os and maybe some parts that are changeable. In the near future I mainly need it to create presentations and....ahh I don't know...all the other stuff you do in University. 
So would ubuntu run on my current system and if not what can I do so it will?

Once that is done I would like to keep my fancy new phone(it's shiny) on one page with my computer so I can edit my calendar, e-mails, some files and what not, on the go and just kind of sync it with my computer once I come home or get wifi around also I would like to manage the settings of my phone and apps on my computer. How do I do that?

At one point I would like to work with Autodesk Inventor again (I do realize that I would need a new pc for that) is there any way it could run on a Linux system? From what I read it seemed that it won't.

Oh and quick bonus question: the nokia page from my phone sad I can only expand the memory up to 32G with a micro-sd, why can't I put a 64G card in it?

Allright that's about it, thanks again.

---

### Post by Topsiho on 2014-03-21
I have a Satellite A50 and run Xubuntu 12.04 on it perfectly. Lubuntu might be another possibility in the Ubuntu family, except maybe for pae:
The processor in my A50 doesn't have support for pae (physical address extension) and can't run the modern Ubuntu's, and if it could run Ubuntu, then it would be very slow.
Xubuntu and Lubuntu is the same as Ubuntu generally, except they use a lightweight desktop in stead of Unity, and another choice of standard applications. The same repositories and kernel and so on, so if you need a special application which is in Ubuntu, but not in Xubuntu or Lubuntu, you just install it from the repositories.

The other questions I can not answer, sorry for that :)

And: next month the new LTS Ubuntu, and other xUbuntu's will become available.

Topsiho

---

### Post by grahammechanical on 2014-03-21
What is Autodesk Inventor? A program compiled to run on Microsoft's Windows? Programs for Windows are never compatible with Linux. If the owner of the software does not produce a Linux version then the software is not compatible with Linux.

We do have something called Wine and sometimes Windows programs using Wine will work to an acceptable degree. Sometimes not. See, if you can find what you want here.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Linux cannot resurrect the dead. At some point hardware becomes obsolete. Your machine may not have reached that point. The way to find out is download and burn a Ubuntu ISO image to DVD or USB memory stick and run a Live Session. You should try these three kiinds of Ubuntu. One version may run better on your machine than another. One version may suit your tastes better than another.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Regards

---

### Post by Rob Sayer on 2014-03-21
Autodesk Inventor is a windows program, and you would indeed want a new computer.  It does a lot of 3D modelling.  The only way you could run it in linux would be in a virtual machine (maybe Wine but that's unreliable).  And it'd have to be a very powerful machine too.

Ubuntu should definitely run on your xp machine.  Whether you get full 3D accelerated video depends upon the linux support for the video, but intel gma's are usually safe.

I wouldn't install the unity desktop version of ubuntu on a machine like that.  Try lubuntu or xubuntu.  Unity (or some other desktops like cinnamon) require 3D acceleration just by themselves.  Basically, you need a machine capable of running Windows 7 to run them properly.

Ubuntu is definitely the linux distro to choose for beginners.  No one else has the quality of tech support.

The best thing for you would be to download both the lubuntu and xubuntu live images.  Not the 64 bit ones, the 32 bit (i386).  Do an md5sum on the downloaded .iso's, burn them, and try each for yourself.

I've used both desktops and lubuntu runs faster but it's harder to configure.  I think xubuntu is probably better for a novice.

---

### Post by Mark Phelps on 2014-03-21
Regarding "connecting" the Nokia phone with your PC running Ubuntu ...

Like many others, I use a Samsung Galaxy S3 phone, and until very recently, could not "connect" it to any Linux distro.  It now is able to do that, but what really happens is that Ubuntu "mounts" the two filesystems resident on the phone -- the internal filesystem and the SD card filesystem.  That allows for data transfer, but not really anything else.

Installing and uninstalling apps, changing settings -- as far as I know, these are out of reach of "connecting" the phone to a Linux distro.  But then, I've not "rooted" my phone, so that may be possible if you do that.

As to running AutoDesk Inventor in Wine, the WineHQ ratings page for this, containing mostly Garbage ratings, make it clear that this can't be done: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5719]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5719")

---

### Post by yourname2 on 2014-03-24
Hey, 

thank you guys, you helped a lot.
I will get started with trying out ubuntu, lubuntu and xubuntu next weekend.

cheers

---

