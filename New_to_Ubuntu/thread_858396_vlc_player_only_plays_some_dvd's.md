---
title: "vlc player only plays some dvd's"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by stripey on 2008-07-13
I can play all dvd's through VLC player on windows but on ubuntu it plays only some of them.

when i try and open the files i get this message.

The filename "VTS_02_0.VOB" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

---

### Post by Dr Small on 2008-07-13
Just open the DVD in VLC.

---

### Post by bumanie on 2008-07-13
In vlc File --> open disk Also ensure you have multimedia codecs enabled. > sudo apt-get install restricted-extrasAlso follow this [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by stripey on 2008-07-14
i have installed the restricted extras... 

i can play certain dvd's in VLC fine as it is installed now but when i try to open others the screen just opens for a second and stops.
i can see no correlation between the ones that open and the ones that don't!

---

### Post by Ryadt on 2008-07-14
Try enabling medibundu repos.
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install w32codecs
```

hope this solves it.

---

### Post by stripey on 2008-09-07
i have recently upgraded to gutsy and i have checked all the restricted extras and repos etc but i am still having the same problems, VLC will play certain DVD's but not others.

and since the upgrade movie player has stopped giving me the install plugins box and now just freezes when i put in a new dvd.

i have no idea what to try now, all of the DVD's work fine under windows!

---

### Post by egalvan on 2008-09-07
First, SOAP-BOX MODE ON
Windows is a different system, working under deifferent legal and financial models from Gnu/Linxu,
It is closed and proprietary.
Companies pay good money to keep things secret.

Linux is open, and the closed/proprietary crowd doesn't like this

SOPE-BOX MODE OFF

That said, here is an EXCELLENT How-To.


[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


I used it to get DVD (among other things) working perfectly on three different installs.

ErnestG


P.S.
The only thing left to get running is HD-DVD playback.

But hey, that doesn't work under Windows either! and I have an HP Multi-Media machine with Windows XP Multi-Media Edition, HD-DVD player and a legal, store-bought copy of Bourne on HD-DVD. It still accuses me of being a pirate. :twisted::evil:

---

### Post by egalvan on 2008-09-07
> **stripey said:**
> i have recently upgraded to gutsy

Oh, and one more question...

Is there a reason you are staying with Gutsy?

All my successes with DVD/CD etc came under Hardy, 8.04.1 to be exact.

It may be a factor.

---

### Post by stripey on 2008-09-07
no i have upgraded to hardy, that was just me having a brain fart!
i have been to that link before but i am going to try again :)

---

### Post by stripey on 2008-09-07
So, i have tried everything that has been suggested and VLC still won't work.

I think that i have been messing around too much and there is just too much VLC **** on my system and it is causing problems,

is there anyway i can completely remove everything and start again without doing clean install?

also VLC appears twice in the 'open with menu'. is this normal? do i have 2 programs on my system, is this the problem?

---

### Post by egalvan on 2008-09-07
> **stripey said:**
> I think that i have been messing around too much and there is just too much VLC **** on my system and it is causing problems,

is there anyway i can completely remove everything and start again without doing clean install?

also VLC appears twice in the 'open with menu'. is this normal? do i have 2 programs on my system, is this the problem?

Yes, there is a way to completely remove everything, but better minds than mine will have to chime in here...:)

as for a program appearing twice, well, it doesn't sound right, :confused: but again, I'm not that up on Linux.

---

### Post by oldos2er on 2008-09-07
> **stripey said:**
> i have recently upgraded to gutsy and i have checked all the restricted extras and repos etc but i am still having the same problems, VLC will play certain DVD's but not others.

and since the upgrade movie player has stopped giving me the install plugins box and now just freezes when i put in a new dvd.

i have no idea what to try now, all of the DVD's work fine under windows!

 Have you installed libdvdcss2? It's in the Medibuntu repository. See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mahiyar on 2008-09-08
I am no expert, but I too was having a similar problem. The thing I found out is that somehow for each dvd chapter the VLC opens a new window. Just do "Alt + Tab" and it might be ok.

---

### Post by stripey on 2008-09-10
so still with the vlc/dvd problem. I have removed VLC and cleaned the system. However VLC still appears on the 'open with' menu and if i search VLC in the file system there is whole load of vlc files.

is this causing problems???

if so how do i fix it?

---

### Post by kansasnoob on 2008-09-10
Read post #13 and #14 in this thread:

[http://ubuntuforums.org/showthread.php?t=915582&page=2](http://ubuntuforums.org/showthread.php?t=915582&page=2)

I know it might not all apply to you, but I've found no video that I can't play properly with that combination.

One thing, while I'm fiddling with such things I always bust out the old spiral notebook and keep track of everything I'm removing and installing, that way I can easily revert.

---

### Post by stripey on 2008-09-10
well after some extreme messing and uninstalling and reinstalling everything, the videos seem to play in all players, but the play back on some is choppy and i am looking at a black screen.

i feel that i have made a lot of progress though

but any hints on solving this playback problem would be greatly appreciated!

thanks :)

---

### Post by kansasnoob on 2008-09-10
Try something simple like:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
 sudo apt-get -f install
```

-f install may resolve unmet dependencies.

And I'm assuming that you already have the Medibuntu repo and libdvdcss2:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And I'm assuming you're using Hardy!

---

### Post by SunnyRabbiera on 2008-09-10
Try another app, I personally like xine myself.

---

### Post by stripey on 2008-09-11
that is more or less what i did and its perfect!! touch wood, on both players :)

thanks

---

