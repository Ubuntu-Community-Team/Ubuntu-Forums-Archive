---
title: "HOWTO: Getting Sony Network Walkman working under Linux"
date: 2006-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by tomplast on 2006-06-30
NOTE! I have now attached an ogg video where you see how I list the mp3s on my Sony NW-E75 and then upload a new one. Maybe that one will help you more.

For those of you who has a Sony Network Walkman mp3 player can now cry out of joy because here is the solution ;).

1. Download my compressed file which contents are allready compiled. If you don't want to use my pre-compiled files you will have to either download the source file I have as well attached to this post, it wasn't hard to compile so if you wanna go for it don't be worried ;).

2. Plugin your Sony NW mp3 player.

3. Open up a console and run the following files for each task:

* Dumping the songs currently on your player: ./mple-dump /path/to/player

Please specify the correct path to your mp3 player or else it will not succeed. For me the path is /media/usbdisk but look at your configuration as it could differ.



* Removing a song: ./mple-rm /path/to/player/ Tracknumber

Replace /path/to/player as before with the correct path to your mp3 player as before, also replace Tracknumber with the tracknumber of the song you want to remove (tracknumbers are listed when you dump the song contents).



* Uploading a new song to your player. This will be done in 2 steps (really 3 ) and the first thing we must do is to run ./mple-dump /path/to/player if there is no songs in the player atm, if you happends to allready have some songs on the player you can skip that step and continue on with the next step which is to run: ./mple-load -m /path/to/player  -p Song.mp3



Note that I'm not the creator of this wonderful program so don't thank me for anything. I just wanted to tell you about this :). There may be a GUI in the source but I'm too much novice to get it working (if it's there?. Creating a GUI wouldn't be sucha hard task either. Anyhow, I hope this help some of you.

---

### Post by Laurier on 2006-06-30
It **error getting pblist: No such file or directory**'s on me. I have an NW-A1000 mounted at /media/usbdisk. 

Could it be my device isn't supported? I've hear reports Sony's own drag and drop file tool won't work with the purple pebbles either.

---

### Post by Hairy_Palms on 2006-06-30
i had one of these, it was terrible, it didnt even work properly with the proper software in windows then its just died after less than a months use. im currently waiting for sony to send it back in the post repaired.
thx though, ill try this when i get it back. 

it would be easy to make a gui for this, if noone else does i might try making one when i get my walkmen back.
*note to anyone not currently an owner DONT BUY THESE MP3 PLAYERS THEY SUCK!!!

---

### Post by tomplast on 2006-06-30
[QUOTE=Laurier]It **error getting pblist: No such file or directory**'s on me. I have an NW-A1000 mounted at /media/usbdisk. 

Could it be my device isn't supported? I've hear reports Sony's own drag and drop file tool won't work with the purple pebbles either.[/QUOTE]

Yeah I'm terrible sorry, it's a little ackward to use but it works. I guess that you will have try different combinations or something because I tried several times and succeded. I will post as soon as I'm sure of how I did it.

The two commands that I used were:

./mple-test /media/usbdisk
sudo ./mple-load -m /media/usbdisk -p . 

I don't know if it had something todo with sudo or that I placed the mp3songs together with mple. Try it and see if it works for you.

---

### Post by hikitsu4 on 2006-07-01
[quote=tomplast]Yeah I'm terrible sorry, it's a little ackward to use but it works. I guess that you will have try different combinations or something because I tried several times and succeded. I will post as soon as I'm sure of how I did it.

The two commands that I used were:

./mple-test /media/usbdisk
sudo ./mple-load -m /media/usbdisk -p . 

I don't know if it had something todo with sudo or that I placed the mp3songs together with mple. Try it and see if it works for you.[/quote] When i try to play the files it says only "NO DATA". I used format first then used those two commands, those two worked but not to play.

---

### Post by tomplast on 2006-07-01
[QUOTE=hikitsu4]When i try to play the files it says only "NO DATA". I used format first then used those two commands, those two worked but not to play.[/QUOTE]

Maybe you're player is not supported or maybe the program is incomplete, I don't truely know :(. And btw, you did unmount your mp3player afterwards right? Because I hope that you know that all changes are only applied when unmounting the device, so if you just unplugged there would be no changes but I hope that you are aware of that.

---

### Post by hikitsu4 on 2006-07-01
[quote=tomplast]Maybe you're player is not supported or maybe the program is incomplete, I don't truely know :(. And btw, you did unmount your mp3player afterwards right? Because I hope that you know that all changes are only applied when unmounting the device, so if you just unplugged there would be no changes but I hope that you are aware of that.[/quote] I did and i got a NW-E403, right now i got a catalog named
"esys" and in that i got pblist0.dat and pblist1.dat, and in that folder i got another folder called nw-mp3 and in that folder i got the files mp0001.dat-mp0003.dat.

---

### Post by tomplast on 2006-07-01
[QUOTE=hikitsu4]I did and i got a NW-E403, right now i got a catalog named
"esys" and in that i got pblist0.dat and pblist1.dat, and in that folder i got another folder called nw-mp3 and in that folder i got the files mp0001.dat-mp0003.dat.[/QUOTE]

The names of the files and folders have no capitals in them right? I have a similar catalog structure on my mp3player, if you have messenger we can take it  there. My MSN is [email]spaceprogrammer@hotmail.com[/email]

---

### Post by jordg on 2006-07-12
Hi,

I have a N50.
It mounts OK.

./mple-dump /a
Folder: TEST3
  empty folder
Folder: TEST2
  empty folder

Any help appreciated.

Thanks

---

### Post by ekx27 on 2006-09-02
Well, I have a NW-E75, and it is not working...

I have also compiled the program from the sources ([http://www.waider.ie/hacks/workshop/c/mple/]("http://www.waider.ie/hacks/workshop/c/mple/")) and it's not working better... :( 
But there is a graphical interface :) (the same as the windows one)

Sorry for the bad english, but i'm french :p

---

### Post by happy-and-lost on 2006-09-23
> **Hairy_Palms said:**
> *note to anyone not currently an owner DONT BUY THESE MP3 PLAYERS THEY SUCK!!!

No, the software and firmware sucks, but they are still the best sounding (Hear one of these and those over-hyped iPod thingies sound like fingernails on blackboards) and best looking (well, in black anyway) players on the market. :P

---

### Post by Gnowm on 2006-11-17
I found this little gem today.

[http://www.atraclife.com/forums/lofiversion/index.php/t2178.html](http://www.atraclife.com/forums/lofiversion/index.php/t2178.html)  is the forum article.

[http://sourceforge.net/projects/nwe00xmp3man](http://sourceforge.net/projects/nwe00xmp3man)  is the location of the software. His name is Patrick Balleux and he certainly seems to know his stuff, and very quick new feature additions as well.

Cheers

---

### Post by ekx27 on 2006-12-02
Well, this software isn't working with my Sony NW-E75...
I think that my MP3 player will never work under Linux... :???:

---

### Post by lenniboy on 2007-08-13
Got my Walkman working following this HOWTO:

[http://www.lynchconsulting.com.au/blog/index.cfm/2006/9/26/Sony-NWE005F-working-in-Linux--HOWTO]("http://www.lynchconsulting.com.au/blog/index.cfm/2006/9/26/Sony-NWE005F-working-in-Linux--HOWTO")


Note: It's important that you copy the jar file on your Walkman root directory. Took me forever to work that one out!

---

### Post by calsaverini on 2008-04-29
Neither are working on my NW-E002.

---

### Post by calsaverini on 2008-04-29
But this is working very very well!!!

[https://sourceforge.net/projects/symphonic/](https://sourceforge.net/projects/symphonic/)

It's still alpha, but it works.

Just download the .jar file, execute with a java -jar JSymphonic_0.2.1a.jar and a GUI will show up.

Pretty functional.:guitar:

---

### Post by sir_blargh on 2008-08-10
> **calsaverini said:**
> But this is working very very well!!!

[https://sourceforge.net/projects/symphonic/](https://sourceforge.net/projects/symphonic/)

It's still alpha, but it works.

Just download the .jar file, execute with a java -jar JSymphonic_0.2.1a.jar and a GUI will show up.

Pretty functional.:guitar:

Awesome, thanks for letting us know about Symphonic.  It's the replacement to nwe00xmp3man and works well with my NW-507!  Thanks again for pointing this out!

---

### Post by delhist on 2008-08-11
Tried Symphonic, but it requires a DvID.dat file created by Sony MP3 File Manager for "protected" players. MP3FM doesn't support my NW-E005B, though Symphonic is said to support it. Where can I get this file?

---

### Post by delhist on 2008-08-11
Excuse me, but I can't understand. There were no such files on my E005, and it isn't listed as an applicable model for MP3 File Manager on the Sony site. So I have no way of getting the DvID.dat file as it should be created by MP3FM which doesn't seem to support my player.

---

### Post by illdemon on 2008-11-26
Wow, it works perfect on my NW-A607, thank you veery much, U rock:guitar:

---

### Post by binhdv on 2009-03-09
> **sir_blargh said:**
> Awesome, thanks for letting us know about Symphonic.  It's the replacement to nwe00xmp3man and works well with my NW-507!  Thanks again for pointing this out!

When I run java in the terminal, I've told that it doesn't have ffmpeg. and I can not install ffmpeg by the Synaptic Package Manager (I use Ubuntu 7,04) How can I do ?

(sorry, for my English, I'm vietnamese)

---

### Post by HandleWithCare on 2009-03-10
It is all in the readme. 

Sadly, this doesn't work for my nw-e95. Windows is still required...

---

