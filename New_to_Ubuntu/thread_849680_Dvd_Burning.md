---
title: "Dvd Burning"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by tom-e-totortot on 2008-07-04
i need help burning dvds  from start to finish! thanks1

---

### Post by sayakb on 2008-07-04
For burning DVDs, you may use [Brasero]("http://www.gnome.org/projects/brasero/"). Brasero is included in Ubuntu Hardy Heron 8.04
If you don't have it, install it by typing this at a terminal:
```
sudo apt-get install brasero
```You can start brasero by typing **brasero** at a terminal.
At the Brasero main page, select what action to do. For example, you want to create a Data DVD, so click the appropriate button. On the left side, you can navigate to the files you want to burn. Drag and drop them on the right side. Read the instructions on the right panel for mare ways to add/remove a file. After you are finished, press Burn button.

---

### Post by logos34 on 2008-07-04
use cd/dvd creator in nautilus, or Brasero like LinuxIsInnovation suggested, or GnomeBaker, or (best of all) K3B

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#CD.2FDVD_Burning](http://ubuntuguide.org/wiki/Ubuntu:Feisty#CD.2FDVD_Burning)

---

### Post by sayakb on 2008-07-04
Agree, K3B is very good indeed. But if you are using Gnome, installing K3B will install a big bunch of KDE libraries on your gnome desktop.

---

### Post by lukjad on 2008-07-04
I like k3b. It is simple and has enough options to suit me and not be too complex to the new use.

---

### Post by logos34 on 2008-07-04
> **LinuxIsInnovation said:**
> Agree, K3B is very good indeed. But if you are using Gnome, installing K3B will install a big bunch of KDE libraries on your gnome desktop.

That's the common objection, and it's certainly true that using a kde app in gnome means you need the qt- libraries.  But a lot of people feel even K3b alone is worth it.  It's that good.

---

### Post by sayakb on 2008-07-04
I use K3B with Suse10.3 + KDE4. Again, I agree it is excellent indeed :D

---

### Post by Dissident85 on 2008-07-04
[http://ubuntuforums.org/showthread.php?t=791502](http://ubuntuforums.org/showthread.php?t=791502) <-- that thread might help

---

### Post by jivabill on 2008-08-11
Sounds like everyone likes K3b.  Not my experience.  When I use it K3b works fine and very fast UNTIL it gets to the verify phase and then it freezes.  I wind up having to shut my machine completely down, pull the plug, in order to get rid of K3b.

The other problem I have had is I can't seem to write an appendable CD, one that can have other files added to it later.  

So I am exploring GnomeBaker now.  If anyone can give me advice on my K3b troubles I would like to hear it.
Thanks,
Bill

---

### Post by halitech on 2008-08-11
> **tom-e-totortot said:**
> i need help burning dvds  from start to finish! thanks1

important question here that we don't have the answer to. What type of dvd are you looking to burn? (ie. data, video, picture cd?) Depending on what you are looking to burn with decide the steps you need to take.

---

### Post by jivabill on 2008-08-11
Hi Halitech, nice to meet you.  What I want to do is write a Data DVD containing my system save file (1.9GB) and some other folders of sensitive information. 

FYI what I found with GnomeBaker is that, contrary to posts I have read elsewhere, the current version does not allow multisession capability, all I can do with GnomeBaker is blow a whole DVD on one or two files, whatever  I select in my initial burn.  So I am looking to do multisession CDs and DVDs.
Thanks
Bill

---

### Post by halitech on 2008-08-11
Hi Jivabill,

honestly I've never used Gnomebaker or Nautilus to burn anything (or if I did, it was so long ago that I honestly don't remember). I would say install K3B (plus all the other dependencies it wants) and use it as it does have an option to start and finalize multisessions cds and dvds.

---

### Post by rossjman1 on 2008-08-11
It really depends on what you want to do. First you want to go out and buy some dvds (you probably already did this). If you are going to burn a data dvd, any brand dvd will do as they all have long lifespans and work in all computers. If you're planning on burning a video dvd, then I would suggest the Office Depot brand, in my experience, strike a good balance between quality and cost; they work with most dvd players including the ps2, xbox, and xbox360.
Everyone already told you how to burn a data dvd, so I wont really talk too much about that, but I will trow my 2 cents into the pot. Brasero (Braseo Disk Burning in the menu) works great, and you don't really need to replace it if you don't want to.
If you have a .avi file that you would like to burn onto a dvd so you can watch on your tv the program DeVeDe is a must.
```
 sudo apt-get install devede
```
Open the program from the Applications menu and select Video DVD from the menu. From here you can add your avi file, change the main menu of the dvd, sych the audeo with the video, etc. Be prepared to wait, as converting the avi to an iso will take up to 4 hours. It will save an *.iso file in your home directory (movie.iso by default). Open Brasero and click burn image from the menu. Browse to the iso file that devede just created, and burn (from here it takes 4-10 minutes).

---

### Post by RedRat on 2008-08-11
I have found that when i used Brasero that it would not burn some DVD disks, these were TDK+R. Yet GnomeBaker would burn on them fine, so I would suggest GnomeBaker.

As to multisessions, GnomeBaker will give you the option to "Finalize" the disk. If you don't finalize, you should be able to add files to the disk. However, i must admit, I have not tried that.

---

### Post by jivabill on 2008-08-11
Thank you for your input Halitech.  I have used the Nautilus several times for small burning projects.  And I used GnomeBaker once to see if it would do multisession and found in the help file that they plan to add that later :-).  

So just now I removed K3b from my system and then re-installed it. (the old Windows trick) to see it that would fix anything.  Also I did find how to set K3b for multisession.  And I did a DVD with a multisession.

But the problem that is still hanging out is the one where K3b freezes when I try to specify "verify".  I'll have to try that again since I re-installed K3b and see if that problem has been fixed.
Thanks for your help.
Bill

---

### Post by jivabill on 2008-08-11
Hi RedHat, and thanks for the tip on GnomeBaker.  I'll check that out and see if I can do a multi session DVD that way.
Bill

---

### Post by jivabill on 2008-08-11
Hi Rossjman1, thanks for all the good info.  That will keep me busy for awhile :-).  I have a BIG spindle of DVDs, pretty good ones that my son who is an IT Geek in FL gave me.  So I have quite a bit of ammunition.
Thanks again,
Bill

---

### Post by jivabill on 2008-08-11
An update on GnomeBaker and K3b.

So I tried writing a DVD with GnomeBaker and in the options screen I found the "finalize" checkbox was NOT checked.  Theoretically (it is not covered in the help file) that would mean that more files could be added later.  Not the case.  So I tried writing a DVD with the "finalize" checkbox checked.  Same result, I could not create a multisession DVD. This state of affairs certainly limits the usefullness of GnomeBaker.

In regard to K3b, I found out how to set it so I could create a multisession DVD.  And, after I removed the program and re-installed it I found that the "verify" phase works now. Funny, It thought having to re-install programs was a Winblows thing :-).

So that is my report.  Looks like I will be using K3b to do my CD and DVD burning.

Thanks everyone for the help.
Bill

---

### Post by RedRat on 2008-08-11
> **jivabill said:**
> An update on GnomeBaker and K3b.

So I tried writing a DVD with GnomeBaker and in the options screen I found the "finalize" checkbox was NOT checked.  Theoretically (it is not covered in the help file) that would mean that more files could be added later.  Not the case.  So I tried writing a DVD with the "finalize" checkbox checked.  Same result, I could not create a multisession DVD. This state of affairs certainly limits the usefullness of GnomeBaker.

In regard to K3b, I found out how to set it so I could create a multisession DVD.  And, after I removed the program and re-installed it I found that the "verify" phase works now. Funny, It thought having to re-install programs was a Winblows thing :-).

So that is my report.  Looks like I will be using K3b to do my CD and DVD burning.

Thanks everyone for the help.
Bill
Hey that was a good piece of information. I thought with the unchecked "Finalize" that you could create a multisession DVD. I will K3b and see how it works. Thanks for the info!

---

### Post by RedRat on 2008-08-14
> **jivabill said:**
> An update on GnomeBaker and K3b.

So I tried writing a DVD with GnomeBaker and in the options screen I found the "finalize" checkbox was NOT checked.  Theoretically (it is not covered in the help file) that would mean that more files could be added later.  Not the case.  So I tried writing a DVD with the "finalize" checkbox checked.  Same result, I could not create a multisession DVD. This state of affairs certainly limits the usefullness of GnomeBaker.

In regard to K3b, I found out how to set it so I could create a multisession DVD.  And, after I removed the program and re-installed it I found that the "verify" phase works now. Funny, It thought having to re-install programs was a Winblows thing :-).


So that is my report.  Looks like I will be using K3b to do my CD and DVD burning.

Thanks everyone for the help.
Bill
I just happened to note thaT supposedly GnomeBaker 0.64 does multi-sessions. I got it from:
[http://www.getdeb.net/app/Gnome+Baker](http://www.getdeb.net/app/Gnome+Baker)
The blurb claims multi-session but I have not tried it out.

---

