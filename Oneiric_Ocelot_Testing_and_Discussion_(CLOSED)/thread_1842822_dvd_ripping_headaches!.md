---
title: "dvd ripping headaches!"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by urbexer on 2011-09-12
Hey all,

A noob here,,,and need help!

Having trouble ripping with dvd's in all programs except thoggen.

Running 11.10 beta. Thoggen rips the dvds, but they playback with a lot of lag. Every other app rips halfway from the dvd and fails with copy protected message...please help, I love ubuntu, but this dvd ripping problem I never had with windows?

Any ideas?

Cheers
Urb

---

### Post by howefield on 2011-09-12
Thread moved to the development forum"*Ubuntu +1 (Oneiric Ocelot)*"

Are you aware that you are running a development release of Ubuntu and not a full release ?

Have you tried Handbrake ?

---

### Post by POWMS on 2011-09-12
Have you tried K9copy?
I find this works the best, with good results ripping to hard drive then burning to disk. Disk to disk in K9 doesn't always work.........

---

### Post by urbexer on 2011-09-12
Sorry for posting in the wrong place.

Yes, am aware that it is beta. Just find it strange that only thoggen can rip successfully...but the completed files are useless!

To be more clear I am just looking to rip the dvd to an .avi or .mkv file

Cheers
Al

---

### Post by urbexer on 2011-09-12
How to install handbrake? None of the ppas from the stubbins server work...i dont have many dvds to rip and I really don't want to revert to windows just to rip some remaining dvds?

Anyone any idea?

---

### Post by meborc on 2011-09-12
> **urbexer said:**
> How to install handbrake? None of the ppas from the stubbins server work...i dont have many dvds to rip and I really don't want to revert to windows just to rip some remaining dvds?

Anyone any idea?

since ubuntu 11.10 is still bet final, some PPA's do not support it

Try compiling from source, you can get the source from here - [http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

Should be as easy as:

1) extract the package
2) cd into the directory
3) ./configure
4) make
5) sudo make install

You might need to install some dependencies first (e.g. build-essential etc.)

---

### Post by cariboo on 2011-09-12
Do you have libdvdcss2 installed, if not, go to /usr/share/doc/libdvdread4, and run the install script:

```
sudo ./install-css.sh
```

---

### Post by urbexer on 2011-09-12
Yeah, I have libdvdcss installed...dvds open and play fine, and rip ok in thoggen. The problem is the playback of files ripped from thoggen is useless.

and so far I haven't been able to get any other program to rip a dvd successfully.

I might have to go back to windows for the mo, and then back to ubuntu at final release...unless any other beta users got a solution?

---

### Post by cariboo on 2011-09-12
I personally use vobcopy, it removes the menus and features, but you still retain the quality, which is more important to me, than extra features that I never watch.. I end up with files in the 3 - 4 GiB range. VLC plays the vobs with no problem.

---

### Post by urbexer on 2011-09-13
Just installed vobcopy, but not showing up in the search for the program...

now i just want to copy the vobs off, any other software?

---

### Post by cariboo on 2011-09-13
Vobcopy is a command line program, there is no gui, so it won't show up in the menus, just open a terminal, and type:

```
vobcopy -l
```

it should automagically find the dvd , and create a  .vob file in your current directory.

---

### Post by garvinrick4 on 2011-09-13
Dvdrip for ripping and VLC for playing the vob.
Goofed around with it for a couple of months and that
is what worked best for me. Can rip into chapters if preferred.
This is just what worked best for me. Only tried 3 or 4 different ripping packages.

---

### Post by |{urse on 2011-09-13
+1 @ vobcopy -l, it works just fine. Another thing that works pretty darn nicely is the fair use wizard   [http://fairusewizard.com/lang_en/fairuse_wizard_dvd_divx_xvid_backup_tool_light_edition.html](http://fairusewizard.com/lang_en/fairuse_wizard_dvd_divx_xvid_backup_tool_light_edition.html)  I've used this in wine a bunch but that was a long time ago so your mileage may vary with current versions.  Just on a sidenote if you ever want to do the opposite and turn an avi, vob, mpeg, etc into a dvd then dvdstyler is easy and fast.

---

### Post by oldos2er on 2011-09-13
> **POWMS said:**
> Have you tried K9copy?
I find this works the best, with good results ripping to hard drive then burning to disk. Disk to disk in K9 doesn't always work.........

K9copy is a little crashy (technical term) for me in 11.10. K3b however is working well for ripping a DVD.

---

### Post by dr_kabuto on 2011-09-14
Is there a reason why handbrake isn't available anymore in the ubuntu repositories? It works so well as dvd ripper...

---

### Post by JohnAStebbins on 2011-09-14
> **dr_kabuto said:**
> Is there a reason why handbrake isn't available anymore in the ubuntu repositories? It works so well as dvd ripper...

It was never available in the official ubuntu repositories.  It has only been available in PPAs. And it is likely that it never will be available in the official repositories.  They don't like HandBrake's build system.

Last release (Nov. 2010):
[https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)

Nightly builds:
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by seeker5528 on 2011-09-14
> **garvinrick4 said:**
> Dvdrip for ripping and VLC for playing the vob.

If you don't care about menus and use VLC, you could always....

Open VLC, 'Media --> Convert / Save --> Disc (DVD, No Menu) --> Convert / Save --> Choose a filename and output profile and click the start button'.

[img]http://home.comcast.net/~seeker5528/Screenshot-VLC1.png[/img]

Later, Seeker

---

### Post by wetch on 2011-10-13
I think all the respondents are missing the point of the OP. I am having the same issue as him and this is the only reference to it I've found after much googling around.. 

Summing up. I cannot copy from a dvd using any means at all (no matter whether encrypted dvd or not), only directly converting from thoggen without first creating a copy of the dvd on the hdd works.

ie I can read a dvd and watch it but just no way to rip contents to hdd. Even just a straight drag and drop copy of an unprotected dvd fails.

None of the other suggested options here works at all...

Any ideas? Anyone?

---

### Post by wetch on 2011-10-13
FYI .. The problem is related I believe to this bug...

[https://bugs.launchpad.net/ubuntu/oneiric/+source/libdvdread/+bug/869003](https://bugs.launchpad.net/ubuntu/oneiric/+source/libdvdread/+bug/869003)

---

