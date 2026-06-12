---
title: "HowTo: Change the Default File Manager in Gnome (to Konqueror or Thunar)"
date: 2006-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2006-11-14
If you want to change the default file manager from Nautilus to Thunar, you can do it a bit, but it's tricky.

Remember that in Gnome, Nautilus is not just the file manager--it also draws the desktop, and it's also a CD-burning application.

So, thanks to *ciscosurfer*, the answer is here: changing around some .desktop files in /usr/share/applications

The only problem is when I plug in an external drive, it still pops up in Nautilus. Grrr. Anyone know the answer to that one?

Well, in the meantime, the almost-completely-working script is available here:
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

If you have problems with the script, improve it on the Wiki. Don't post here.

---

### Post by Leonivek on 2006-11-15
Awesome!  :-D It's good to be able to do this... I haven't tried it, mainly because I prefer Krusader right now... :roll: Can you write a script for Krusader or other file managers? [-o<

---

### Post by aysiu on 2006-11-15
> **Leonivek said:**
> Awesome!  :-D It's good to be able to do this... I haven't tried it, mainly because I prefer Krusader right now... :roll: Can you write a script for Krusader or other file managers? [-o<
It's not a very popular request, so I probably won't create a script for it, but if you press Alt-F2 and ```
gksudo nautilus
``` you can modify the commands in /usr/share/applications for File Browser, Home Folder, Open Folder, Network Servers, and Computer to the appropriate commands for Krusader.

---

### Post by urukrama on 2006-11-15
Thank you aysiu. Sounds great! I've been looking for an easy way to do this for some time now.

Unfortunately the script on your site doesn't work for me. When I run the script to make Thunar the default file manager, this is what I get:

```

Making sure Thunar is installed

Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done
Writing extended state information... Done

*[all my repos]*

Fetched 140kB in 3s (44.4kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  amarok amarok-xine kcontrol kdebase-bin kdebase-data kdesktop kfind
  kicker libakode2 libdbus-qt-1-1c2 libifp4 libkcddb1 libkonq4
  libsamplerate0 python-qt3 python2.4-qt3 python2.4-sip4-qt3
The following packages have been kept back:
  avahi-daemon info libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-core4 libavahi-glib1 libavahi-qt3-1
0 packages upgraded, 0 newly installed, 17 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 84.4MB will be freed.
Do you want to continue? [Y/n/?]

```

Is this normal? The packages it wants to remove are KDE, but strangely enough not all my KDE ones (I also have krusader). Could it be because I installed Amarok not through the repos, but built it from source?

(I use Dapper)

---

### Post by aysiu on 2006-11-15
It could be. Damn *aptitude* for being so "smart."

Try opening up the script with a text editor and changing the two *aptitude* references to *apt-get*--see if that makes a difference.

---

### Post by urukrama on 2006-11-15
> **aysiu said:**
> Try opening up the script with a text editor and changing the two *aptitude* references to *apt-get*--see if that makes a difference.

Changed it, and it worked like a charm. Thanks a lot! :KS

---

### Post by aysiu on 2006-11-15
Great. I might work in something that asks if you already have Thunar/Konqueror installed. That way, you can skip that step if you already have it in.

---

### Post by urukrama on 2006-11-15
I just noticed that if I click on a folder on my Desktop it opens with Nautilus, not Thunar. I don't really mind, as I rarely have folders (or anything, really) on my desktop, but I thought I'd let you know. Might be the same issue as the USB thing? When I go to "Properties > Open With" Thunar is there as an option, but I can't select it.

Otherwise the script worked fine (the shortcuts in the Place Menu, panels, etc. all lead to Thunar).

---

### Post by aysiu on 2006-11-15
> **urukrama said:**
> I just noticed that if I click on a folder on my Desktop it opens with Nautilus, not Thunar. I don't really mind, as I rarely have folders (or anything, really) on my desktop, but I thought I'd let you know. Might be the same issue as the USB thing? When I go to "Properties > Open With" Thunar is there as an option, but I can't select it.

Otherwise the script worked fine (the shortcuts in the Place Menu, panels, etc. all lead to Thunar).
I think it's related to the USB thing. If someone can figure that out, please let me know...

---

### Post by urukrama on 2006-11-16
I don't know if this could be it, but in my "/usr/share/applications" I have two entries for everything that involves the file manager (Computer, File Browser, Home, etc.), except for File Management . Under Properties > Launcher some of them have Thunar for both entries, but Computer and Home have one entry with Thunar, the other with Nautilus. File Management has only Nautilus. I know Nautilus does more than just show some files and hence this might be irrelevant, but could it be related to this issue?

I have attached a screenshot with all (?) the relevant entries.

---

### Post by aysiu on 2006-11-16
The script makes a backup copy of all of the files it modifies. That's what all the "duplicates" are that contain *nautilus*.

---

### Post by ciscosurfer on 2006-11-18
> **aysiu said:**
> It's come up several times on these forums that someone has wanted to change the default file manager in Gnome from Nautilus to Konqueror or Thunar.

Until recently, no one had a working answer to that question. I'd thought in the past that we could simply do something like this: ```
sudo dpkg-divert --divert /usr/bin/nautilus.old --rename /usr/bin/nautilus
sudo ln -s /usr/bin/konqueror /usr/bin/nautilus
``` or this ```
sudo dpkg-divert --divert /usr/bin/nautilus.old --rename /usr/bin/nautilus
sudo ln -s /usr/bin/thunar /usr/bin/nautilus
``` But it hasn't worked. In fact, I think the results have been disastrous.

Remember that in Gnome, Nautilus is not just the file manager--it also draws the desktop, and it's also a CD-burning application.

So, thanks to *ciscosurfer*, the answer is here: changing around some .desktop files in /usr/share/applications, and I've created scripts to do that--one for Thunar and one for Konqueror. I've tested both script as well as the "restore Nautilus" script, and they're good for the most part.

The only problem is when I plug in an external drive, it still pops up in Nautilus. Grrr. Anyone know the answer to that one?

Well, in the meantime, the almost-completely-working scripts are available here:
[http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)Thanks for the nod, and I appreciate the attribution. 8)  I'm going to check out your script now! ;)

As for the removable media and desktop folder issues, I am working on a quick fix.  I will post back here when I get it all worked out. :D

---

### Post by ciscosurfer on 2006-11-18
Way to go, aysiu!  Great scripts--totally fantastic!  Super-quick and easy to use.  To make the process go smooth, I did alter the scripts to use apt-get instead of aptitude, which is these cases, makes the most sense.

---

### Post by ciscosurfer on 2006-11-18
I'm all for a Krusader script as well (looks like there are few more files, but I'm sure the script can be easily adjusted).

---

### Post by aysiu on 2006-11-18
I've put it on my to-do list (Krusader and *apt-get*), but no promises about when I deliver. In the meantime, if anyone wants to alter the script and files appropriately, feel free. It's open source.

---

### Post by ciscosurfer on 2006-11-18
> **aysiu said:**
> I've put it on my to-do list (Krusader and *apt-get*), but no promises about when I deliver. In the meantime, if anyone wants to alter the script and files appropriately, feel free. It's open source.I'm working on a few alterations and additions that you may find useful.  I can either post them here or PM when I'm ready to get your email address. ;)

Also, I'm looking into how to modify the scripts to take care of the issues regarding removable drives only opening in Nautilus, etc.

---

### Post by aysiu on 2006-11-18
> **ciscosurfer said:**
> I'm working on a few alterations and additions that you may find useful.  I can either post them here or PM when I'm ready to get your email address. ;)

Also, I'm looking into how to modify the scripts to take care of the issues regarding removable drives only opening in Nautilus, etc.
Please do post here any changes you make or any other suggestions.

I think the problem with the removable drives is the "Open with" .desktop file.

The original file has the command ```
nautilus --no-desktop %U
``` I just swapped that out for ```
thunar %U
``` or ```
konqueror %U
``` but I'm not really sure what %U means...

The deal with icons on the desktop opening with Nautilus can't be helped, as far as I can tell. Nautilus draws the desktop, so icons on the desktop will open with Nautilus.

---

### Post by ciscosurfer on 2006-11-18
In gconf-editor, go to */desktop/gnome/applications*

I haven't had time to mess with these, but there may be hope yet!

I think the %U stands for the users path (or home directory) but I could be wrong...

---

### Post by ciscosurfer on 2006-11-18
There's definitely a lock or some sort on the Open Folder .desktop file as well as the Folder properties Open With tab on folders on the desktop.  I'm now going to try actually deleting the Open Folder .desktop file and if that removes the 'lock'.

---

### Post by aysiu on 2006-11-18
> **ciscosurfer said:**
> In gconf-editor, go to */desktop/gnome/applications*

I haven't had time to mess with these, but there may be hope yet!

I think the %U stands for the users path (or home directory) but I could be wrong...
You are right on!

It's /desktop/gnome/applications/component_viewer/exec

That should be changed to ```
thunar %s
``` and it'll work for external media. I haven't tried it for Konqueror yet.

**Edit**: Never mind. My Nautilus looks too much like Thunar. I got them confused.

---

### Post by ciscosurfer on 2006-11-19
Excellent!  Glad that worked!  

Btw, for folders on the desktop, a simple right-click "Open with Thunar" or "Open with Konqueror" will work just fine.  Yes, it's one extra click, but really, it's not that big of a deal.  I mean, you're already in the place you need to click.  It's not like you have to trudge through directory after directory to get this going.

---

### Post by aysiu on 2006-11-19
> **ciscosurfer said:**
> Excellent!  Glad that worked!  

Btw, for folders on the desktop, a simple right-click "Open with Thunar" or "Open with Konqueror" will work just fine.  Yes, it's one extra click, but really, it's not that big of a deal.  I mean, you're already in the place you need to click.  It's not like you have to trudge through directory after directory to get this going.
No, read my edit.

It didn't work. I thought it did, but it didn't. I'll keep looking if you will...

---

### Post by ciscosurfer on 2006-11-19
> **aysiu said:**
> No, read my edit.

It didn't work. I thought it did, but it didn't. I'll keep looking if you will...Yikes!  I misread you post.  Well, you can always try **Thunar %F   **

-->  /usr/bin/thunar and /usr/bin/Thunar are both available.

---

### Post by aysiu on 2006-11-21
Krusader is now available, but I'm not sure how well it'll work, as it doesn't take location parameters the way Thunar and Konqueror do.

For example, if you have the command: ```
thunar /media
``` Thunar will open in the /media directory. If, however, you have the command ```
krusader /media
``` Krusader won't open at all.

---

### Post by ciscosurfer on 2006-11-21
@aysiu,
I think I'll check out that script!  

I have a FirstClass client removal script that I whipped up (don't know if you got that message from one of the admin or not) and was wondering where you'd like me to post it.  You can PM me if you'd like.

---

### Post by stalefries on 2006-11-28
aysiu, I think I know how to fix^H^H^H temporarily help you with the removable drives thing, though perhaps not in a script. In System>Preferences>Removable Drives and Media, unselect "Browse removable media when inserted". It won't switch to your favorite file manager, but it will stop Nautilus for a bit. Also, any device or folder listed on the desktop will open in Nautilus, I imagine, because Nautilus is the one in charge of the desktop. :/

It seems like it worked, but I can't think of any way to check...

---

### Post by 454redhawk on 2006-12-13
EXACTLY what I have been waiting for. Thanks a bunch. Konqueror seems to working great.

---

### Post by 454redhawk on 2006-12-16
> **ciscosurfer said:**
> 

As for the removable media and desktop folder issues, I am working on a quick fix.  I will post back here when I get it all worked out. :D



Any progress on this issue?

Thanks

---

### Post by adam.tropics on 2007-04-30
Thanks Aysiu and others. The script did most of the work. Then I installed xfdesktop, and started that from gnome-session-preferences (and got rid of nautilus from session preferences). With thunar and associated plugins, my desktop icons were back. Problems I had were trash panel applet, which I just decided to not use, and use the dektop trash from xfdesktop. Totem, which would crash out saying it required nautilus, which was solved by actually uninstalling nautilus, and finally the mount drive, panel applet, which was solved with

```
 sudo ln -s /usr/bin/thunar /usr/bin/nautilus
```I needed the panel applet since xfdesktop/thunar doesn't give me an eject right clik option on my phone (usb mass storage), and manually dealing with it was ugly and a pain  in the backside! Apart from that,

Thanks everyone.

Oh, and this little laptop is zipping along nicely, not quite xubuntu speed, but certainly quicker than gnome with nautilus.

---

### Post by LilYoda on 2007-07-24
Hey that works just fine, thanks!!!  I now have thunar as my default file manager

/congrats

---

### Post by thebeefytaco on 2008-02-01
I modified aysiu's script to make pcmanfm the default file manager in gnome for anyone who wants it.
[http://thebeefytaco.googlepages.com/defaultpcmanfm.sh](http://thebeefytaco.googlepages.com/defaultpcmanfm.sh)

---

### Post by thebeefytaco on 2008-02-01
also this just changes the icon files if you want to actually change the actual default browser
```
sudo gconf-editor
```
goto / -> desktop -> gnome -> applications -> component_viewer and change the value to 'thunar' or 'pcmanfm' or whatever you want to use

---

### Post by starscalling on 2008-02-11
mm
not working at all in gutsy atm ; ;

---

### Post by Ms_Angel_D on 2008-07-04
Is there anyway to get this working with dolphin? I would love to be able to use dolphin in gnome as default.

---

### Post by stinny on 2008-08-06
These scripts contain a potential danger - as the backup process is blind, it simply overwrites the backup files on multiple runs. Thus, restoring to Nautilus after trying all of these scripts at once does not work. To fix this, either use an own backup of the .desktop files, or simply reinstall nautilus in Synaptic (is there a similar command in apt-get?).

However, nice job!

---

### Post by abramdemski on 2009-03-01
Hi,

This is working pretty well for me, on Intrepid Ibex (AMD Turion 64). However, I've got a little complaint: upon startup, a Konqueror window automatically opens. This is slightly annoying. Any clue why?

Thanks.

---

### Post by smudi on 2009-04-29
On Jaunty desktop icons do not appear after switching to Thunar. This is caused by the replacement of /usr/share/nautilus.desktop Exec to 'thunar'.
We know that nautilus is responsible for displaying the dekstop in Gnome - the simple 'nautilus' command just displays the desktop, while 'nautilus --no-desktop %U' opens the file browser. 
When replacing nautilus.desktop Exec from 'nautilus' to 'thunar', the 'nautilus' command doesn't get executed on startup, hence no desktop appears. Instead a thunar browser windows appear, as we just executed a bare 'thunar' command.
Note that this may cause the konqueror windows appearing on startup as well.

Reverting the nautilus.desktop file to its backup version does the trick.

---

### Post by loo0olz on 2009-04-29
i will try 
thanx anyway

---

### Post by bgturk on 2009-05-22
Thanks you for the guide. 
After my bitter experience  nautilus (its handling of samba mount points), it was really a pleasure to delete it. Nautilus, since it is impossible to access anything that it mounts from other application.

---

### Post by Unislash on 2009-08-22
> **smudi said:**
> On Jaunty desktop icons do not appear after switching to Thunar. This is caused by the replacement of /usr/share/nautilus.desktop Exec to 'thunar'.
We know that nautilus is responsible for displaying the dekstop in Gnome - the simple 'nautilus' command just displays the desktop, while 'nautilus --no-desktop %U' opens the file browser. 
When replacing nautilus.desktop Exec from 'nautilus' to 'thunar', the 'nautilus' command doesn't get executed on startup, hence no desktop appears. Instead a thunar browser windows appear, as we just executed a bare 'thunar' command.
Note that this may cause the konqueror windows appearing on startup as well.

Reverting the nautilus.desktop file to its backup version does the trick.

Indeed, it is true that the script doesn't work in Jaunty. I tried reverting the nautilus.desktop file to its backup version and this didn't fix the desktop. To revert nautilus.desktop i simply modified the script and added
```
sudo cp nonautilusplease/nautilus.desktop .
```
right before
```
## This last bit I'm not sure should be included
## See, the only thing that doesn't change to the
## new Thunar default is clicking the files on the desktop,
...
```
and it appears to have reverted correctly, but no beans. Did i do something wrong, smudi? Any other workarounds?

Cheers,
Unislash

---

