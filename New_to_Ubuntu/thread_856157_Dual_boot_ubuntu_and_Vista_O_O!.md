---
title: "Dual boot ubuntu and Vista O_O!"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by bettynoob on 2008-07-11
Hi guys, I am very new to Ubuntu but I have planned to take the plunge and dual boot it on my Vista laptop following lots of recomendations.

So far I have shrunk my hdd ready to accomadate Ubuntu and downloaded the installation file. But, before I do this I was wondering about the drivers for my laptop.

I have googled for hours and can only find results in French so I have no idea what the heck they are talking about.

Does anyone know where I can get Ubuntu drivers for a Sony Vaio VGN-NR11s?

Any advise will be gratefully received!

---

### Post by nothingspecial on 2008-07-11
I have a sony vaio vgn-something and everything apart from the webcam worked straight away. 1st test is to boot up the live cd and see what works.

Welcome by the way.

---

### Post by sharks on 2008-07-11
i think using the live cd may solve ur problem.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If u have any problem using the live cd post it here.

---

### Post by bettynoob on 2008-07-11
> **nothingspecial said:**
> I have a sony vaio vgn-something and everything apart from the webcam worked straight away. 1st test is to boot up the live cd and see what works.

Welcome by the way.

Thank you!

Sorry if this sounds dumb but I'd like to get it right so I don't do any damage to Vista (not like it can get any worse anyway!)

I have downloaded the [Ubuntu CD installer]("http://www.ubuntu.com/getubuntu/download") which is 700MB from the Ubuntu website, and I am currently in the process of downloading [another version]("http://findfiles.com/list.php?string=ubuntu-8.04-dvd-i386.iso&size=3979683840&db=Mirrors") which is 3.71GB. Is there a difference between the two?

---

### Post by sharks on 2008-07-11
i think 3.71 version is the dvd version

---

### Post by bettynoob on 2008-07-11
> **sharks said:**
> i think using the live cd may solve ur problem.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If u have any problem using the live cd post it here.

Ok so I think the download from the Ubuntu site is what you call the live cd?
I'm going away to burn it now, I will let you know how I get on.
Thank you!

---

### Post by kenpogi on 2008-07-11
Hi, I too am rather new to Ubuntu, Google this site "Illustrated dual boot site" it will tell you all you need to know, written by a very savvy Linux guru, I think so anyway.

---

### Post by fatality_uk on 2008-07-11
Once you have burned the CD, checked it for errors, see this site
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
You can restart your PC with it in the CD drive and run the live session. It will et you know if all is working driver wise, such as WIFI etc. As for that Sony model, im pretty sure it will work right out of the box.

---

### Post by nothingspecial on 2008-07-11
Before you install. Back up all your data, just in case.
Whatever you do (if you want to keep vista) [SIZE="6"]don`t[/SIZE] click on "use the entire disk" during the install.
I`ll never forget a post from a kid who`d tried to do a dual boot, but clicked "use entire disk". He completely nuked windows and all the data from his dad`s pc. Ouch!
 Don`t want to worry you, just trying to make sure you get this right.:)

---

### Post by Sealbhach on 2008-07-11
I have a Vaio (see my sig).

On installation, sound doesn't work from headphone jack speakers but it's easly fixed.

Webcam doesn't work.

Other than that it all works really well.

Us this guide here for a dual-boot, it's got screenshots and everyting.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

This the most important bit, make sure you use this option:

[IMG]http://www.psychocats.net/ubuntu/images/installinghardyplus10.png[/IMG]

.

---

### Post by bettynoob on 2008-07-24
Hello again all.
I finally got round to installing Ubuntu yesterday. It installed like a dream! Thanks to all of you for your comments and suggestions.
I can confirm that it dual boots and Vista is still completely intact. All of my hardware all still works perfectly while running Ubuntu.

Now I have another question.
I have several files and folders all backed up to a samba server which I would like to import into Ubuntu.
I have succesfully managed to import things like Open Office docs etc but I have a large IE7 favourites folder which I would like to use in Firefox.

Can anyone suggest the easiest way of transferring these into Firefox.
Also I have applications like Filezilla, RealVNC and AngryIP scanner. I know these will be Windows programs, can anyone suggest a website that provides just Ubuntu software that I could find these sort of things?

Thank you :-)  

Me = Happy new Ubuntu user!

---

### Post by nothingspecial on 2008-07-24
The first thing to do is look in Add/Remove or system > administration > synaptic package manager. There are catagories in there which will help you search for specific software.
 Also check out getdeb [http://www.getdeb.net/](http://www.getdeb.net/)
although as a new user I`d suggest the first method.
Can`t help you with those windows specifics cause I`ve never used that os.

As an afterthought, check this thread, it`s huge but I`ve found loads of stuff reading it.
[http://ubuntuforums.org/showthread.php?t=382137&highlight=apps](http://ubuntuforums.org/showthread.php?t=382137&highlight=apps)

Happy Ubuntuing :)

---

### Post by sharks on 2008-07-24
> 
Now I have another question.
I have several files and folders all backed up to a samba server which I would like to import into Ubuntu.
I have succesfully managed to import things like Open Office docs etc but I have a large IE7 favourites folder which I would like to use in Firefox.

Can anyone suggest the easiest way of transferring these into Firefox.
Also I have applications like Filezilla, RealVNC and AngryIP scanner. I know these will be Windows programs, can anyone suggest a website that provides just Ubuntu software that I could find these sort of things?


Please make a separate thread and please mark this thread solved from thread tools.

---

### Post by Vicfred on 2008-07-24
hmm you care too much about the drivers... that's what vista makes to people <snip> >O<

---

### Post by philinux on 2008-07-24
To manually export the bookmarks from IE7 to firefox. 
IE7 click add to favorites. Now click import and export. At the wizard hit 'next'. Now click favorites and hit next. Now select what favorite folders you want to export. If you want to export all bookmarks, click top level favorites folder and hit next. Now it'll create a file called 'bookmarks.htm'. This by default will be created in My Documents folder (choose a different path if you don't want it to be exported in My Documents) and hit next. Finally click finish.

To import them into firefox. Either copy the file to a usb stick or use the ntfs-3g tool. [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
Click bookmarks -> organize bookmarks . In the bookmark manager window , click file->import. Now select 'from file' and hit next. Now browse to where the exported 'bookmarks.htm' is located.

---

### Post by WRDN on 2008-07-24
> **philinux said:**
> To manually export the bookmarks from IE7 to firefox. 
IE7 click add to favorites. Now click import and export. At the wizard hit 'next'. Now click favorites and hit next. Now select what favorite folders you want to export. If you want to export all bookmarks, click top level favorites folder and hit next. Now it'll create a file called 'bookmarks.htm'. This by default will be created in My Documents folder (choose a different path if you don't want it to be exported in My Documents) and hit next. Finally click finish.

To import them into firefox. Either copy the file to a usb stick or use the ntfs-3g tool. [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
Click bookmarks -> organize bookmarks . In the bookmark manager window , click file->import. Now select 'from file' and hit next. Now browse to where the exported 'bookmarks.htm' is located.

Ubuntu 8.04 already has an NTFS driver, and out of the box, it can read and write to NTFS partitions.

---

### Post by muteXe on 2008-07-24
My vista/ubuntu laptop was working fine until I updated vista with SP1, then the periodic bluescreens began when in vista.
I'm happy to say my laptop is now 100% ubuntu :)

---

