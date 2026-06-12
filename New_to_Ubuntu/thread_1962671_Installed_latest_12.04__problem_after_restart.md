---
title: "Installed latest 12.04  problem after restart"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by rlnelson5 on 2012-04-21
Hello Thanks for your help 
 I installed the latest umbutu 12.04 and installed all the updates 
 After installing and updating drivers I had to restart the computer. 
After doing this the computer runs through the boot screen then turns red/pink for a couple of minutes   and then turns black with the following message 
  ta_id[123]:HDIO_GET_IDENDITY failed for '/dev/sdb':Invalid argument  
  I have removed and reinstalled several times and was able  to get mouse and keyboard  email printer set up drivers ect . I am wondering what to do next. This is on a  hp computer 500 hd 4 gb  dual core  No Windows installed

---

### Post by ubudog on 2012-04-21
Hi there, are you able to log in?

---

### Post by rlnelson5 on 2012-04-21
Hi Thanks for the reply I just tried it again. When I start the computer I get the blue hp boot screen , turns black for just a second then turns pink/red for 20 seconds or so then turns black with the error code I listed above.  I have the user name and password weitten down and I also had checked the auto login box when inially setting Ubuntu up

---

### Post by oklokl on 2012-04-21
Graphics card is a bug.

First, after update

sudo apt-get update

 Try to install the graphics card.

In my case, the graphics card because of a bug.

Installing a graphics card makes makes.


This graphics card is installed, then please try installing.
 # sudo apt-get upgrade

---

### Post by Mark Phelps on 2012-04-21
> **oklokl said:**
> Graphics card is a bug.

What???  I would be very surprised if this has anything to do with the graphics card.

The primary cause for this error is if there is a USB stick plugged in during the boot -- as it's going there to find the boot loader (which is not there).

---

### Post by rlnelson5 on 2012-04-21
Ok I gave up and am reinstalling 12.04 again,   All is going well so far. Every time I do this it is 1+ hrs
 I am not using a usb stick I have a dvd iso image downloaded from the ubuntu web site .  The only usbs  installed are the keyboard and mouse wireless usb adapters.
 When this is fully loaded is there any tests to check that it is installed correctly?.

---

### Post by tmaranets on 2012-04-21
Did you direct download from the site or burned to a cd and then did the installation.?

---

### Post by rlnelson5 on 2012-04-21
downloaded to Firefox and from there to windows burn iso .on a windows 7 computer
 I checked the verify after burning box and it said it burned correctly.  The computer I am installing Ubuntu into is a different computer 


Update   1 after i12.04 installed  Ubuntu desktop comes up  After seeing desktop for a minute , window opens up  saying proprietary drivers are available  It has a recommended driver highlighted   for the Nvidea  video card, I authorized it and it downloaded  and installed
 On restart I had the first message I posted come up again
  I am suspecting that the video card driver is causing this  Is it possible? 

Update 2  Installed 12.04 again installed till desktop is up  had highlight to install prop driver 
  tried second non highlighted Nvidea  driver
 after restart has screen from my first post . 

Update 3  After another install  all went well until restart  . then first message of post came up again  no desktop

---

### Post by oklokl on 2012-04-22
In my case,

Unknown cause of graphics cards have provided a bug.

About finding the cause of it took a long time.

An unknown error is output.

It will not cause the graphics card is the message.

I have resolved to find the cause.


Priority
Do not install anything else.

Please install the graphics card
And rebooting was necessary.


Data is easily Contamination usb.
 cd or dvd is recommended.

 SDHC memory can be installed.

I saw a lot of usb failure...

---

### Post by Gremlinzzz on 2012-04-22
> **rlnelson5 said:**
> Ok I gave up and am reinstalling 12.04 again,   All is going well so far. Every time I do this it is 1+ hrs
 I am not using a usb stick I have a dvd iso image downloaded from the ubuntu web site .  The only usbs  installed are the keyboard and mouse wireless usb adapters.
 When this is fully loaded is there any tests to check that it is installed correctly?.

Its a bug report it,try again in a week or two 12.04 is still beta.
:popcorn:

---

### Post by rlnelson5 on 2012-04-22
Ok  I got the desktop up and did not install driver. Everything is working so far :D 
I downloaded synaptic manager and it updated every item and Ubuntu  is still working 
  I got the email, printer, backup, networking  working 
 . The only trouble I have now is the dvd player is not working  
   I tried all of the programs,  My movies, Brasso and VLC  with no luck.
 When using VLC I just get a yellow traffic cone

---

### Post by grahammechanical on 2012-04-22
I fully understand that now that you have got a working desktop you do not want to mess around with installing video drivers but from this thread you are not the only one having issues with recent Nvidia drivers.

[http://ubuntuforums.org/showthread.php?t=1962600]("http://ubuntuforums.org/showthread.php?t=1962600")

I am running 12.04 with the Nvidia 294.40 driver without problems. I did have issues with some of the earlier drivers.

I recently installed 11.10 and upgraded it to 12.04 as a test and the Nvidia driver was 280.

So, there are issues at the moment with Nvidia drivers.

Regards.

---

### Post by CookieNinja on 2012-04-22
> **rlnelson5 said:**
> Ok  I got the desktop up and did not install driver. Everything is working so far :D 
I downloaded synaptic manager and it updated every item and Ubuntu  is still working 
  I got the email, printer, backup, networking  working 
 . The only trouble I have now is the dvd player is not working  
   I tried all of the programs,  My movies, Brasso and VLC  with no luck.
 When using VLC I just get a yellow traffic cone

If you're trying to play commerical DVD videos, the likely cause is that you don't have the required software installed to decrypt the DVD video for playback.

One of these may be the answer you need. Alas more complicated than it should be, but hopefully the instructions are good enough to help you.

[http://askubuntu.com/questions/70010/troubles-when-trying-to-play-a-dvd](http://askubuntu.com/questions/70010/troubles-when-trying-to-play-a-dvd)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Long time since I was interested in doing this myself, so I've just done a search for instructions that I think are correct.

---

### Post by rlnelson5 on 2012-04-22
Thank you to all:KS 12.04 is up and running including playing DVDs   I downloaded the files per instructions of the last post  Thanks a lot!!!!

---

### Post by CookieNinja on 2012-04-23
> **rlnelson5 said:**
> Thank you to all:KS 12.04 is up and running including playing DVDs   I downloaded the files per instructions of the last post  Thanks a lot!!!!

Good stuff, enjoy! Hopefully the driver bug will be sorted in the release :-).

---

