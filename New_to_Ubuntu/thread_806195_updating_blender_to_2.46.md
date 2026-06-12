---
title: "updating blender to 2.46"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by jellylogix on 2008-05-24
I tried updating blender via the synaptic repository but it has yet to update itself that blender 2.46 is released. I downloaded the .tar.bgz file from the official site, but have no idea whatsoever how to get this to work over my 2.45. I could wait until Ubuntu updates the repository, but I really don't know how long that will take. Any suggestions on finding an easy to install .deb file or anything would be appreciated greatly.

---

### Post by saj0577 on 2008-05-24
Easy way to install a .deb is normally just double click it and a pop up window should appear.

Saj

---

### Post by Sarah L on 2008-05-24
Hey,

The Ubuntu repositories are notorious for being one step behind the latest updates. In fact I've just run into this problem myself today, and I updated a couple of packages (OpenOffice included) that just couldn't wait.

I've just downloaded the archive that you mentioned to test it out. It seems like it should work out of the box!

Simply go to the folder you downloaded it into and type ```
 tar -xvjf blender*
```

This should extract it into its own folder. Enter that directory and run blender by typing ```
./blender
```

---

### Post by jellylogix on 2008-05-24
that will run it from there, but how can I overwrite the blender 2.45 so when i go to Applications->Graphics->Blender and click then it will run 2.46 and NOT 2.45?

---

### Post by Sarah L on 2008-05-24
Under KDE, you can go to the KMenu and right-click on the Blender entry and select Edit Item. Then, under Command, type in the path to your extracted Blender.

I'm not quite sure how to do this under GNOME, but it should be similar. Look for a menu-editing utility and change the path of the launcher to where you extracted Blender.

---

### Post by Joeb454 on 2008-05-24
The ubuntu repo's don't get updated often because Ubuntu is not a rolling release (I believe Gentoo and Arch are rolling releases).

And is there some huge feature/update/bug fix in 2.46 that means you *must* have it immediately? If not I'd just wait and continue using 2.45 :)

---

### Post by jellylogix on 2008-05-24
I've heard many great things about it from my friend, including cloth animations etc... which I would like to "fiddle" with. haha ya so I guess I MUST have it...

---

### Post by Joeb454 on 2008-05-24
hmm, ok ;) Other than editing your menu's to point to the unzipped blender folder, I can only suggest checking [getdeb.net ]("http://www.getdeb.net")to see if they have a .deb file to use.

---

### Post by VitalBodies on 2008-05-26
> **jellylogix said:**
> I tried updating blender via the synaptic repository but it has yet to update itself that blender 2.46 is released. I downloaded the .tar.bgz file from the official site, but have no idea whatsoever how to get this to work over my 2.45. I could wait until Ubuntu updates the repository, but I really don't know how long that will take. Any suggestions on finding an easy to install .deb file or anything would be appreciated greatly.
I would like to see this happen also. I would like to update Blender as major things have been added to the program. 
[http://www.blender.org/development/release-logs/blender-246/]("http://www.blender.org/development/release-logs/blender-246/")
[http://packages.ubuntu.com/hardy/graphics/blender]("http://packages.ubuntu.com/hardy/graphics/blender")

---

### Post by Superkoop on 2008-05-26
This is very easy to do, and I have done it myself. 

Simply DL the binary you need from blender.org (or graphicall.org, depending on your needs). 
Extract that file you download to wherever you wish. I personally have a directory in my /home directory where I place all my programs where there is no .deb.

So to create a menu entry, right click on the application bar, select "edit menus". In the new window that opens, click on "graphics" in the left. Click on the New item button. 

In this popup use the following properties:
Type: Application
Name: Blender
Command: /home/john/Library/blender/blender -w -p 250 32 1024 768
[of course this would be different for you based on where you put blender, and how big your screen resolution is - also note this is made so that blender is windowed]
Comment: [put whatever you want here]

There are other ways you could do this, but this would be the graphical way.

---

### Post by VitalBodies on 2008-05-27
Has anyone checked the Backports or Updates?
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Balachmar on 2008-06-02
Well, I might have a look at how to make a deb for blender this evening. Or whenever I have some spare time. If I am successful I will post a link here.
Or maybe I could even get it uploaded into backports or anything... Who knows...

---

### Post by VitalBodies on 2008-06-02
> **Balachmar said:**
> Well, I might have a look at how to make a deb for blender this evening. Or whenever I have some spare time. If I am successful I will post a link here.
Or maybe I could even get it uploaded into backports or anything... Who knows...

That would be great! 
You might be able to get blender into this site also: 
[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by Balachmar on 2008-06-03
Well, turned out that somebody already did it!
Check his ppa:
[https://launchpad.net/~wgrant/+archive](https://launchpad.net/~wgrant/+archive)
Works for me!

---

### Post by VitalBodies on 2008-06-04
> **Balachmar said:**
> Well, turned out that somebody already did it!
Check his ppa:
[https://launchpad.net/~wgrant/+archive](https://launchpad.net/~wgrant/+archive)
Works for me!

How do you make this work or install it?

---

### Post by fatagnus on 2008-06-04
perfect!
you add those lines to the 'third party repositories' (menu system->administration) and close. Then you'll see that blender will be ready to update.

---

### Post by VitalBodies on 2008-06-04
> **fatagnus said:**
> perfect!
you add those lines to the 'third party repositories' (menu system->administration) and close. Then you'll see that blender will be ready to update.

Thank you that worked! Is there a way to switch to the official Ubuntu version once it becomes available? 
Does one just un-select the 3rd party version?

---

### Post by Balachmar on 2008-06-05
> **VitalBodies said:**
> Thank you that worked! Is there a way to switch to the official Ubuntu version once it becomes available? 
Does one just un-select the 3rd party version?
If you want to switch back, I guess you should just remove the lines from the 3rd party repositories.
And reinstall blender, I think it should go back to the original ubuntu version then. Not 100% sure though, since I have not tried it.

---

### Post by VitalBodies on 2008-06-05
> **Balachmar said:**
> If you want to switch back, I guess you should just remove the lines from the 3rd party repositories.
And reinstall blender, I think it should go back to the original ubuntu version then. Not 100% sure though, since I have not tried it.
Being somewhat new to Ubuntu I do not know the full repercussions of all my actions like using this version of Blender with this version of Ubuntu. I like to stay with what works yet it is fun to use new software if the new changes matter. This was a big step for Blender.

---

### Post by Balachmar on 2008-06-05
> **VitalBodies said:**
> Being somewhat new to Ubuntu I do not know the full repercussions of all my actions like using this version of Blender with this version of Ubuntu. I like to stay with what works yet it is fun to use new software if the new changes matter. This was a big step for Blender.
I haven't detected any regression in functionality.
But if you really want to stay safe, you should wait for it to come into backports. (if you have enabled that a a repository)
But I don't think blender influences the rest of the software.

---

### Post by Shaba1 on 2008-07-02
> **fatagnus said:**
> perfect!
you add those lines to the 'third party repositories' (menu system->administration) and close. Then you'll see that blender will be ready to update.

I put deb [http://ppa.launchpad.net/wgrant/ubuntu](http://ppa.launchpad.net/wgrant/ubuntu) intrepid main

Into synaptic third part repository dialog. All I got was chance to download something called libsane. Am I doing something wrongly?

---

### Post by VitalBodies on 2008-07-25
> **Shaba1 said:**
> I put deb [http://ppa.launchpad.net/wgrant/ubuntu](http://ppa.launchpad.net/wgrant/ubuntu) intrepid main

Into synaptic third part repository dialog. All I got was chance to download something called libsane. 
Am I doing something wrongly?
I had just created a blog post about this. Would you like to test my HOW TO article? The How To helps you install Blender 2.46 into Hardy Heron. 
[http://vitalbodies.wordpress.com/2008/07/25/how-to-install-blender-246-in-ubuntu-hardy-heron/]("http://vitalbodies.wordpress.com/2008/07/25/how-to-install-blender-246-in-ubuntu-hardy-heron/")

Let me know if this helps.

---

### Post by rickyrockrat on 2008-10-28
Just temporarily add (to /etc/apt/sources.list):
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main
Be sure to remove/comment out these two lines when you are done, then run apt-get update.

To your sources, run apt-get update, then apt-get install blender.

The william Grant repos do not contain the 64 bit blender anymore.

The reason I needed 2.46 is for some handy scripts.

---

### Post by VitalBodies on 2008-10-28
> **rickyrockrat said:**
> Just temporarily add (to /etc/apt/sources.list):
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main
Be sure to remove/comment out these two lines when you are done, then run apt-get update.

To your sources, run apt-get update, then apt-get install blender.

The william Grant repos do not contain the 64 bit blender anymore.

The reason I needed 2.46 is for some handy scripts.

Thanks for pointing out this change! 
Thanks for saying how to get the current update! 

What commands did you use? 
sudo apt-get install blender
sudo apt-get upgrade blender

I added your technique to my blog that has a lot of Ubuntu how to articles. 
[http://vitalbodies.wordpress.com/2008/10/28/how-to-install-blender-246-in-ubuntu-hardy-heron-2/](http://vitalbodies.wordpress.com/2008/10/28/how-to-install-blender-246-in-ubuntu-hardy-heron-2/)

I removed Blender and tried your suggestion and it worked. 
I might have had to use the upgrade command if I did not remove Blender. Did you try this with Blender installed or not installed?

---

### Post by rickyrockrat on 2008-10-28
Edit sources, put the intrepid lines in, then:
(with blender 2.45 installed)

sudo apt-get update
sudo apt-get install blender

Then, to keep people from hosing their systems, remove those two intrepid lines and do:
sudo apt-get update.

Oh! And to keep blender from crashing using this script (a CAD plugin for dimensioning)
[http://www.alienhelpdesk.com/python_scripts/caliper](http://www.alienhelpdesk.com/python_scripts/caliper)
You have to load any other scripts first.  Otherwise, when you split the header, it trashes blender (read fast exit).  I also use
[http://wiki.blender.org/index.php/Scripts/Manual/System/4mm_layer_manager](http://wiki.blender.org/index.php/Scripts/Manual/System/4mm_layer_manager)
for layers.

Also, to import .slp files from pro-E, do the following (borrowed from here 
[http://blenderartists.org/forum/showthread.php?t=49161):](http://blenderartists.org/forum/showthread.php?t=49161):)
File-->Import-->Pro Engineer (.slp)
Select the mesh, go into edit mode (TAB key) select all the vertices (A key) and then hit the "P" key and select "All loose parts" option. Your mesh should now be split into the individual parts you made the ProE assembly from.

Last note: to add scripts in linux, put them in ~/.blender/scripts, then go to the scripts menu and click update-menus. Looking in the top of the script file will tell you where it will appear in the menu.

---

### Post by VitalBodies on 2008-10-28
> **rickyrockrat said:**
> Edit sources, put the intrepid lines in, then:
(with blender 2.45 installed)

sudo apt-get update
sudo apt-get install blender

Then, to keep people from hosing their systems, remove those two intrepid lines and do:
sudo apt-get update.


What are the possible dangers involved here? 
Is there a way to ONLY update/affect/upgrade/install Blender?

---

### Post by rickyrockrat on 2008-10-28
You are mixing repositories, so you can get into dependency hell.  I've not personally had it happen, but never want it to.

You'll try to update one thing, and apt will grab the latest version, then it will start down the dependency tree.  If you start to 'fix' this tree, you could wind up down a dark hole fast.

Bottom line is this is a major hack, and I'm lucky it worked in the first place!  It's kinda like using a screwdriver for a prybar. Does it work? Yes. Is it designed to be used that way? No. Don't tempt Murpy!

As to only effecting Blender, no, you have to update the dependencies. There is not a way to do it automatically (i.e. apt).  You can install blender from source or a binary.

---

