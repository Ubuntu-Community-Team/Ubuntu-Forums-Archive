---
title: "Encrypted DVD problem"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by deusabscondus on 2013-04-10
I have read the stickies, followed the advice, and now have a operational version of VLC running on my machine (12.04 LTS) but it *still*!!!! won't run an encrypted dvd.
I am exasparated. 

I even re-installed ubuntu 12.04 thinking there might have been some nasty conflict somewhere.

Please, someone who is a wizard with this, respond and give me some good orderly directions.

Thanks kindly in anticipation,

DeusAbscondus

---

### Post by plucky on 2013-04-10
> **deusabscondus said:**
> I have read the stickies, followed the advice, and now have a operational version of VLC running on my machine (12.04 LTS) but it *still*!!!! won't run an encrypted dvd.
I am exasparated. 

I even re-installed ubuntu 12.04 thinking there might have been some nasty conflict somewhere.

Please, someone who is a wizard with this, respond and give me some good orderly directions.

Thanks kindly in anticipation,

DeusAbscondus

Have you installed libdvdcss2 package?

see [Restricted Formats/Playing DVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Good Luck

---

### Post by Derxst on 2013-04-10
Very important notice on the Libdvdcss2 library - "[COLOR=#333333][FONT=Ubuntu]Legal Warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area."

If you are in the United States, the Digital Millennium Copyright Act **MAY** make it illegal for you to install this library. [/FONT][/COLOR]

---

### Post by deusabscondus on 2013-04-12
thanks for response;
yes, i've done this, but STILL no video details being read by VLC, no play!

here is output from

sudo apt-get install libdvdcss2

godfreysown@Textilis:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
godfreysown@Textilis:~$ ^C
godfreysown@Textilis:~$ 


I don't know what else to do

---

### Post by Feathers McGraw on 2013-04-12
Do you really mean encrypted or do you mean "copy protected"?

Try installing [Medibuntu](http://www.medibuntu.org) if you mean the latter, it took me far too long to realise that this is what I needed to play my DVDs in VLC.

Feathers

---

### Post by deusabscondus on 2013-04-14
thanks Feathers; i'm trying that now

---

### Post by deusabscondus on 2013-04-14
Hey Feathers, I did what you suggested - all excited, thinking: "at last, problem solved" ... but alas, after watching all the packages for medibuntu dload and unpackage and get sorted successfully, i go to launch VLC to watch a commercial video (you were correct in your assumption: it is simply vids from a store i wish to play - christ! a humble enough aim) and lo! it won't go, tho it plays vids which my girlfriend has shamelessly ripped for me from innternet....
any other suggestions?
(i've installed libdvdcss2)

---

### Post by coldraven on 2013-04-14
I had three brand new DVDs which would not play. I cleaned the lens and got two of them to play.
I had to clean the lens again to get all three playing.
I used a cotton bud and some methylated spirit but a bit of spit will probably work.
**Very gently** stroke the lens, it is supported by **very** delicate springs.

---

### Post by deusabscondus on 2013-04-14
thanks for the suggestion coldraven, but the drive and components are working fine, as I can play ANY and ALL downloaded material, just not copyrighted material, which indicates it is a problem related to codecs, rather than hardware, cheers, deus

---

### Post by Hadaka on 2013-04-14
Hi, first determine if you are 32 or 64 bit..
```
arch
```
then go here..
[http://ubuntuforums.org/showthread.php?t=1935072&highlight=libdvdcss&page=2](http://ubuntuforums.org/showthread.php?t=1935072&highlight=libdvdcss&page=2)
i just loaded 2 machines with ubuntu 12.04 and it works great with
VLC  
hope this helps

---

### Post by deusabscondus on 2013-04-14
Hadaka, I tried this. Still no go with VLC ... sigh....


DeusAbs

---

### Post by Feathers McGraw on 2013-04-14
I'm surprised that didn't work...

One more thing to check, is the DVD made for your area? DVDs have [region codes]("http://en.wikipedia.org/wiki/DVD_region_code"), e.g. if the DVD is made for America and you try to view it in Europe, it won't work.

Your actual DVD drive itself will be region locked. You can change the location setting, but not very many times, so it's only really worth it if you bought the computer in a different region and have moved with it to a new region that you plan on staying in.

Feathers

---

### Post by deusabscondus on 2013-04-14
thanks Hadaka; did it; still no go
i even upgraded my sys to 12.10, hoping thereby to fix prob, but no such luck...

simmering in futile rage,

preciate your friendly attempt to help me out

Deus Abs

---

### Post by deusabscondus on 2013-04-14
Nope: bought my computer as an ex-Australian government public service unit, 2 years old (now 4 yo)
and am only using videos hired or purchased in Australia.

Very frustrated.

Can you think of any diagnostic clues from following:
VLC rocks along sweet with ANY other form of media except those vids from shop or hire, so,
youtube
dowloaded vids
flash

all work, but the minute i put a commercial vid in machine, VLC goes spastic: won't play and then hangs on me, so that the only way to shut the lil mother down and get my dvd back is to extract it physically from drive while drive is chugging along perpetually, futilely, trying to talk to VLC

any more ideas
thx for persisting Feathers

---

### Post by GregA on 2013-04-15
I suggest you start with a clean install of 12.04.2 LTS.  You can try this with your current install, but I don't know what you've done (or undone) on your system.

Then, do exactly what is listed in item 1 of this link (it's written for 11.10, but should also work for 12.04).  Note that there are two commands that must be accomplished, it's not just a matter of obtaining certain codecs/files.  There is the second command which runs a script.  Libdvdcss2 won't by itself do what you want, VLC won't do what you want either - the solution is what's in the script.

[http://winonux.blogspot.com/2011/12/22-things-to-do-after-installing-ubuntu.html](http://winonux.blogspot.com/2011/12/22-things-to-do-after-installing-ubuntu.html)

---

### Post by coldraven on 2013-04-15
The point that I was trying to make is that commercial DVDs are dual layer. Your player might be able to play single layer but the tiniest bit of dirt or nicotine film will prevent it working properly.

You have plenty of dust in OZ that could be gumming it up :)

---

### Post by Feathers McGraw on 2013-04-15
Well based on the fact that you aren't getting anything at all, I think coldraven may be right here.

When I tried to play commercial DVDs without medibuntu, the DVD would play 20 seconds of anti piracy stuff and then stop when it should have showed the menu.

Would have thought if it was a licencing problem that you'd get the anti piracy bit and no more.



Have you got any commercial DVDs to work at all? I'm thinking if older ones work and new ones are the problem, that might help identify the problem.



Feathers

---

### Post by Feathers McGraw on 2013-04-15
Also, try disabling DVD menus in VLC (see troubleshooting point 1 [here](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)).

Worth a punt!

Feathers

---

### Post by deusabscondus on 2013-04-16
Many thanks to all who responded!

On the edge of the cliff of despair, I dismounted and removed an external back up drive connected to a usb port, then in desultory fashion, went to play a dvd for the nth time, not for a moment expecting anything to have changed, et voila!, I got season 1 of "Spooks" humming along on VLC.

Once again, sincere thx to ALL posters, especially Feathers and those who trudged the whole saga with me.

Warmest,
Deus' Abs

---

### Post by Feathers McGraw on 2013-04-16
Unbelievable!

So... if you reconnect and re-mount that external drive, does it stop working again?

Glad you found a solution, 

Feathers

---

