---
title: "Transmission 0.7 SVN - Lightweight BitTorrent Client"
date: 2006-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by AppleCrow on 2006-08-22
Transmission is a GTK2 lightweight BitTorrent client, which can easily replace your favorite BitTorrent client.

It "just works" and is well integrated with GNOME Desktop.

Languages supported: EN, ES, FR, IT, PL, RU

**Latest version: 0.7 SVN 806 (2006.08.22)**

Those build are based on snapshots from [http://transmission.m0k.org]("http://transmission.m0k.org").

Packages for Dapper Drake can be found here:[B]
[http://acorbeaux.free.fr/packages]("http://acorbeaux.free.fr/packages")[/B]

---

### Post by domino on 2006-08-24
Thanks fo this. This beats Az if you need a quicky dl. Do you have a changelog?

---

### Post by mejy on 2006-08-24
I'd appreciate a change log too.  Also, is it any less stable to leave running a torrent over night than 0.61, and does it use any more resources?  I've been amazed at how stable and light weight transmission is since I combiled it a few months back.

---

### Post by zenwhen on 2006-08-24
Thanks for posting this. I want to come in here and make sure no one posts about specific private trackers this is banned on. This is prohibited.

---

### Post by Linuturk on 2006-09-07
I've got a big problem with the Transmission deb I got on the forums a month or so back.

It has a serious memory leak, and it fills up my gig of ram in short order (about 60 seconds) and starts on the swap file. After it starts on the swap file, it takes forever for any application to start or to come back from the screensaver. Has this been resolved in this release?

---

### Post by TSP on 2006-09-07
The link don't works for me, i only get a black pahe.
BTW why don0t you make a post or howto to let us now how do you build or compile this good client?

Thanks! Cheers!

---

### Post by kpolice on 2006-09-07
It's easy, you just need gtk and subversion, the packages are subversion and libgtk2.0-dev 

Then just follow the instructions on transmission site:

svn co svn://svn.m0k.org/Transmission/trunk Transmission

then cd to Transmission, do a ./configure , make and finally make install.

---

### Post by Hells_Dark on 2006-12-28
Well, i compiled transmission but how to have the gtk interface ?
After the install i've got transmissioncli but there's not graphical interface.

Thanks.

---

### Post by .tommie on 2007-01-01
How about executing ```
transmission-gtk
``` in terminal window?

Even better: create a new menu item in your Gnome applications menu, putting transmission-gtk as the command.

---

### Post by Linuturk on 2007-04-20
does anyone have a deb of the .7 final release?

---

### Post by megamads on 2007-04-24
Here's a 0.7.1 deb for feisty!

---

### Post by Linuturk on 2007-04-24
OMG thank you soo much!

---

### Post by wh0rd on 2007-04-24
> **megamads said:**
> Here's a 0.7.1 deb for feisty!

Thanks a lot for the package!!!

---

### Post by amgeex on 2007-04-24
Latest packages for Edgy here: [http://transmission.m0k.org/forum/viewtopic.php?t=1506](http://transmission.m0k.org/forum/viewtopic.php?t=1506)

---

### Post by nphx on 2007-04-25
WOW!!!! This torrent client is freakin awesome!!!!!!!

---

### Post by Morbett on 2007-04-25
WOW is right.

This client is amazing.  Everything and all I could ask for.  Simple and just works, looks great too.

---

### Post by haku.spejsr on 2007-04-25
tnx, I heard some good stuff about this torrent client, and I'm fed up with my lil' blue frog, although it has cooler icon ^^ so I'm gonna try it out. cheers!

edit: oh yeah I liek it ... this is what lightweight is all about ...

---

### Post by Darrena on 2007-04-25
I created a proper package and it is available at:
[http://darrenalbers.com/transmission](http://darrenalbers.com/transmission)

I am a little uncertain on the dependencies but I added all that I could determine based on configure, but if anyone finds that I am missing one please let me know and I will update the package.

Instructions are also available on the website for rebuilding the package for other arch's.

---

### Post by Corbelius on 2007-04-27
Feisty Fawn amd64:

[http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/transmission_0.71-0ubuntu1~janvitus_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-janvitus/main-amd64/transmission_0.71-0ubuntu1~janvitus_amd64.deb)

[http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)

---

### Post by embeemb on 2007-04-30
Anything for Dapper ? 8-[

---

### Post by amgeex on 2007-04-30
Well, you could build from source. You need the libevent, gtk2, and openssl dev libraries and maybe other package I forgot about. Search for them in synaptic, it shouldn't be hard to compile.

---

### Post by embeemb on 2007-04-30
Thanks. Downloading and compiling was a breeze! Now a very noob-ish question. To get it to run, I ran transmission-gtk ?

Is that it? Or is there anyway else to run it?

---

### Post by megamads on 2007-05-01
Here's a deb for transmission 0.72 (feisty)

---

### Post by crhylove on 2007-05-07
Thank You!  Finally a decent Linux torrent program (though I still like it less than uTorrent in Windows)!  I recommend you send your .deb files to transmission and let them have it on their website somewhere.  Be nice for a lot of debian/ubuntu peeps who forget to google.  GREAT APP!!

---

### Post by amgeex on 2007-05-07
There are deb packages on the GTK section of the Transmission forum.

---

