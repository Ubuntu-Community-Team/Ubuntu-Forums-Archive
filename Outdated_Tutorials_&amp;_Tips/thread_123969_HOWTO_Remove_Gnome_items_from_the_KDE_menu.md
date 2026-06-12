---
title: "HOWTO: Remove Gnome items from the KDE menu"
date: 2006-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Adrian on 2006-01-31
**Method 1:**
The problem of removing Kubuntu items from the Gnome menu has been discussed a lot, and a solution can be found here:
[http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

The same method works for removing Gnome items from the KDE menu. You just have to do the operations in the parent directory, and of course change the "OnlyShowIn=KDE" text.

*WARNING! This method consists of console commands operating in super user mode. If you are not careful, you might mess up your system. If this feels uncomfortable, use any of the other two methods instead.*

First of all, create backups of the existing desktop files:

```

mkdir ~/.desktopbackup
cp /usr/share/applications/* ~/.desktopbackup

```

This will save your current menu item data in a hidden folder (in your home folder) called *.desktopbackup*, so you can restore them if anything goes wrong. Doing this is important, since a simple typo (like writing ">" instead of ">>" in the script below) can make your menu items disappear permanently.

Now it is time to start the action! Each menu item is represented by a **<item>.desktop** file. By appending the text **OnlyShowIn=GNOME** to each of them, we will make sure that they are shown in the GNOME menus only.

```

cd /usr/share/applications
sudo -s
for i in *; do echo "OnlyShowIn=GNOME" >> $i; done
exit

```

**Method 2:**
Another, more elegant solution (which I unfortunately have not tried yet) is this small program:
[http://www.kde-look.org/content/show.php?content=31031](http://www.kde-look.org/content/show.php?content=31031)

It will put your Gnome items in a special Gnome menu folder.

**Method 3:**
If you only want to remove *some* of the Gnome applications, or you want total control, you can edit the KMenu manually by right-clicking on the KMenu button and choosing "Menu Editor".
Whatever you do here does not affect the Gnome menu, so Gnome menu items removed will still be available in Gnome.

*Edit: Added the third method.*
*Edit: Replaced Gnome with GNOME*
*Edit: Added some lines about the importance of making backups*

---

### Post by limit223 on 2006-01-31
Thank you for the tip...I used Kmenu Gnome program...everything well organized now...:)

---

### Post by N8K99 on 2006-01-31
This reply is going to be totally helpless, but somehow, I used a GUI tool that was in the System folder to edit the menus. It's probably named something like kmenu. Really easy to do, but that's still not helpful.

---

### Post by N8K99 on 2006-01-31
smeg that's teh name of the menu editor in Kubuntu

---

### Post by souled on 2006-02-01
First I got rid of my KDE icons in Gnome, then I got rid of Gnome icons in KDE. After I logged back in to Gnome, Almost all of my stuff from Applications and System are gone. How can I reverse these changes?

---

### Post by Adrian on 2006-02-01
[QUOTE=souled]First I got rid of my KDE icons in Gnome, then I got rid of Gnome icons in KDE. After I logged back in to Gnome, Almost all of my stuff from Applications and System are gone. How can I reverse these changes?[/QUOTE]

If you used the "OnlyShowIn" method, you have to remove that line from every file in the corresponding directory.

To restore the KDE menu:
```

cd /usr/share/applications
sudo -s
for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done
exit

```

Similary, to restore the Gnome menu:
```

cd /usr/share/applications/KDE
sudo -s
for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done
exit

```

---

### Post by Adrian on 2006-02-01
[QUOTE=N8K99]smeg that's teh name of the menu editor in Kubuntu[/QUOTE]

**kmenuedit** is the menu editor in Kubuntu. You can launch it by right-clicking on the KMenu icon and choosing "Menu Editor".

Smeg is now called Alacarte and is the Gnome menu editor.

---

### Post by louis_nichols on 2006-02-01
Nice advice. Myself, i prefer to see all the apps I can use at any given moment. Unfortunatelly, there's no app as good as krusader or k3b for gnome. Gnome-commander and gnomebaker or nautilus burner aren't as good, in my opinion. Also, smeg kinda lacks the option update menus that kmenu has.

So, my question is the opposite: do you know of a way to make all installed apps show up in gnome menu? Besides debian's "menu", which creates a branch of its own and doesn't see all the apps either. For example, I just installed geda and CDcat and had to include them manually in the menu. Shouldn't there be an easier way?

---

### Post by souled on 2006-02-01
[QUOTE=Adrian]If you used the "OnlyShowIn" method, you have to remove that line from every file in the corresponding directory.

To restore the KDE menu:
```

cd /usr/share/applications
sudo -s
for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done
exit

```

Similary, to restore the Gnome menu:
```

cd /usr/share/applications/KDE
sudo -s
for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done
exit

```[/QUOTE]

Thanks, that did it.

---

### Post by N8K99 on 2006-02-02
[QUOTE=Adrian]**kmenuedit** is the menu editor in Kubuntu. You can launch it by right-clicking on the KMenu icon and choosing "Menu Editor".

Smeg is now called Alacarte and is the Gnome menu editor.[/QUOTE]

You know, I actually used **kmenuedit** just like the way you described- but was unable to find how I did that! I saw in the menu that smeg was called a Menu editor (running KDE 3.5) and put that in my post - I'm trying to be helpful. 

Sorry for any confusion

---

### Post by ykpaiha on 2006-02-02
very good second version worked just fine
I had some issues with dependencies with the .debdo you know where to get the plain gz?
thanks good job

---

### Post by ashrack on 2006-02-02
[QUOTE=louis_nichols]Nice advice. Myself, i prefer to see all the apps I can use at any given moment. Unfortunatelly, there's no app as good as krusader or k3b for gnome. Gnome-commander and gnomebaker or nautilus burner aren't as good, in my opinion. Also, smeg kinda lacks the option update menus that kmenu has.

So, my question is the opposite: do you know of a way to make all installed apps show up in gnome menu? Besides debian's "menu", which creates a branch of its own and doesn't see all the apps either. For example, I just installed geda and CDcat and had to include them manually in the menu. Shouldn't there be an easier way?[/QUOTE]
some apps apperantly just aren't set to put icons in the MENU. 
But I've also found that sometime GNOME MENU isn't updated. So I do ```
killall gnome-panel
```
And then they show up

---

### Post by RaptorRaider on 2006-02-03
Tried this and somehow destroyed my GNOME installation.
The following worked perfectly for removing GNOME apps in KDE, like stated in the startpost:
```
cd /usr/share/applications
sudo -s
for i in *; do echo "OnlyShowIn=Gnome;" >> $i; done
exit
```
After seeing how this worked, in KDE I did the following:
```
cd /usr/share/applications/kde
sudo -s
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
exit
```
Now, however, GNOME crashes when I try to login.

Can anyone with more knowled help me with this?

---

### Post by Adrian on 2006-02-03
[QUOTE=RaptorRaider]Tried this and somehow destroyed my GNOME installation.
The following worked perfectly for removing GNOME apps in KDE, like stated in the startpost:
```
cd /usr/share/applications
sudo -s
for i in *; do echo "OnlyShowIn=Gnome;" >> $i; done
exit
```
After seeing how this worked, in KDE I did the following:
```
cd /usr/share/applications/kde
sudo -s
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
exit
```
Now, however, GNOME crashes when I try to login.

Can anyone with more knowled help me with this?[/QUOTE]

Are you sure you did the last operations in the **/usr/share/applications/kde** directory? Since Gnome crashes, maybe you did it in the **/usr/share/applications** directory instead, where the Gnome applications are located?

To test this theory, do this:
```
cd /usr/share/applications
grep "OnlyShowIn=KDE" *

```
This will list all *Gnome applications* that are told to just show up in KDE. Of course, you don't want these instructions to generate any output (since that means that your Gnome applications will not appear in the Gnome menus).

Please try it and post your results here.

---

### Post by RaptorRaider on 2006-02-03
After "grep "OnlyShowIn=KDE" *", I get the following output:
```
kcmgtk-xdg.desktop:OnlyShowIn=KDE;
smeg-kde.desktop:OnlyShowIn=KDE;
synaptic-kde.desktop:OnlyShowIn=KDE
```
After a reboot, I'm not seeing any of Gnome's applications as you expected.

And BTW, I know I should've said this earlier, but while Gnome is "crashing" I can actually quickly browse the menu's; in Applications I can only see KDE Apps while the Preferences and Administration menu's in System are almost completely empty.

---

### Post by Adrian on 2006-02-03
[QUOTE=RaptorRaider]After "grep "OnlyShowIn=KDE" *", I get the following output:
```
kcmgtk-xdg.desktop:OnlyShowIn=KDE;
smeg-kde.desktop:OnlyShowIn=KDE;
synaptic-kde.desktop:OnlyShowIn=KDE
```
[/QUOTE]

I think that is the desired output. How about trying both restoration procedures described in this post:
[http://www.ubuntuforums.org/showpost.php?p=698174&postcount=6](http://www.ubuntuforums.org/showpost.php?p=698174&postcount=6)
?
Make sure that you use the correct directories.

---

### Post by nmatheis on 2006-02-04
Hello

I'm running x64 Dapper K/Ubuntu.  I ran across this thread and thought it would be nice to segregate the menu items, so that the gnome items would only show up in gnome and kde items would only show up in kde.  Unfortunately, I don't at all like the results i got.  First, I tried this:

Code:
cd /usr/share/applications 
sudo -s 
for i in *; do echo "OnlyShowIn=Gnome;" >> $i; done 
cd /usr/share/applications/kde 
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done 
exit

Then I checked out my menus in gnome and kde - hardly anything there at all, but in a bad way!  Office menu gone, games menu gone, system settings tools gone, synaptic gone, kcontrol center gone, nearly everything gone.  So I rebooted with no change.

So, I thought maybe the tool over at KDE-Apps (METHOD 2 from the initial post here) would work - the kmenu-gnome package.  So I d/l-ed and dpkg-ed it.  All it did was add my gnome menu to the kde one, but there was hardly anything in the gnome menu anyway, so it wasn't really helpful.  So I rebooted with no change.

Then I thought I'd try to remedy the situation by following directions to restore the menus here:

To restore the menus:
Code:
cd /usr/share/applications
sudo -s
for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done 
cd /usr/share/applications/KDE
for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done 
exit

Nothing changed at all.  I rebooted with no change.

So I thought I'd give this a try:

Code:
sudo sed -i '/OnlyShowIn=/d;$a\OnlyShowIn=KDE;' \ /usr/share/applications/kde/*.desktop
sudo sed -i '/OnlyShowIn=/d;$a\OnlyShowIn=Gnome;' \ /usr/share/applications/*.desktop

Nothing.  Reboot - nothing.

So I tried that set of commands in reverse:

Code:
sudo sed -i '/OnlyShowIn=KDE/d;$a\OnlyShowIn=;' \ /usr/share/applications/kde/*.desktop
sudo sed -i '/OnlyShowIn=Gnome/d;$a\OnlyShowIn=;' \ /usr/share/applications/*.desktop

Got an error about no .desktop files in the kde directory (there are, though).  Reboot with no changes.

So...I really need some help getting my menus back in order. Seeing everything that should be there with both ubuntu-desktop and kubuntu-desktop is the first thing i'd like to accomplish.  So, if someone could help me with that, I'd greatly, greatly appreciate it!!!  Then, I'll just use the respective menu editors.

Thanks!
Nikolaus

---

### Post by RaptorRaider on 2006-02-04
[QUOTE=Adrian]I think that is the desired output. How about trying both restoration procedures described in this post:
[http://www.ubuntuforums.org/showpost.php?p=698174&postcount=6](http://www.ubuntuforums.org/showpost.php?p=698174&postcount=6)
?
Make sure that you use the correct directories.[/QUOTE]
I'm pretty sure I used the right directories (though I used "kde" instead of "KDE" :p), and it's still not working.
Most Gnome apps are now appearing in my KDE menu, though I don't think it's all of them, but all (or again perhaps most) KDE apps seem to have appeared in the Gnome menu though I can't see any Gnome app there.

After "for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done" in the applicationsdirectory, I am getting the following output if that might help:
```
cat: kde: Is a directory
bash: kde: Is a directory
```

Also added a screenshot to show what happens when I login to Gnome: it just hangs at "gdesklets" but I can browse the menu's.
[Crap, screenshot is too large. If you think it'll be useful, I'll try to make it smaller]

---

### Post by Adrian on 2006-02-04
OK, I've identified the problem. Sadly there was an error in my original post.

This:
```
for i in *; do echo "OnlyShowIn=Gnome;" >> $i; done
```
is wrong and must be replaced with this (as I've already done in the original post):

```
for i in *; do echo "OnlyShowIn=GNOME" >> $i; done
```

The only difference is the spelling of "GNOME".
(Note that the semicolon is redundant)

The problem is that Gnome doesn't identify itself as "Gnome" (only as "GNOME"), so it doesn't show the menu items.

If your Gnome menu items have disappeared, do this:
```
cd /usr/share/applications
sudo -s
for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done
exit

```

This will remove all previous "OnlyShowIn=" information, and should restore the menus.

Now, if you dare, you can try the revided version of Method 1 (make sure that your menus really are restored first).

---

### Post by nmatheis on 2006-02-04
[QUOTE=Adrian]If your Gnome menu items have disappeared, do this:
```
cd /usr/share/applications
sudo -s
for i in *; do cat $i | grep -v "OnlyShowIn=" > $i; done
exit

```

This will remove all previous "OnlyShowIn=" information, and should restore the menus.
[/QUOTE]
So, I've done this several times by copy/paste so I know I'm not inputing the text incorrectly.  But my Gnome menu never changes.  I've tried the command but modified for KDE in the /usr/share/applications/kde directory, as well.  That hasn't restored anything to my Kmenu, either.

If anyone can help out, that would be great!  I'd much rather fix the menus, learn more about linux at the same time, and not have to reinstall ubuntu.

Thanks!
Nikolaus

---

### Post by RaptorRaider on 2006-02-04
[QUOTE=Adrian]The only difference is the spelling of "GNOME".[/QUOTE]
Argh... I was actually already thinking that might be the problem.

Will try it in a few minutes and post my results.

---

### Post by RaptorRaider on 2006-02-04
Nope, it isn't working.

I again did exactly as you said: first "released" the GNOME apps, then told the GNOME apps only to appear in GNOME and KDE's apps only to appear in KDE.


In KDE, I'm now seeing all my KDE apps plus a very, very small amount of GNOME apps (just Evolution I think).
In GNOME, I'm seeing almost every KDE app (or perhaps all), and a couple of GNOME apps.

Edit:
Actually, I don't think I'm seeing everything in KDE.
For example, I can't find KInfoCenter.
Running "kinfocenter" in a terminal does work but is kinda fucked up: I can only see the DMA-Channels, nothing else.

---

### Post by Adrian on 2006-02-04
Hmm... I've been experimenting with this during the evening. No matter what I write to the desktop files (like "OnlyShowIn=Nonsense"), I can easily restore my menu items by removing all OnlyShowIn lines as described above.

However, I will do my best to help you guys.

What is the output of this:
```

ls /usr/share/applications/

```
?

You should have plenty of desktop files there (if not, they are accidently deleted).

Can you post the contents of the file **/usr/share/applications/xchat.desktop** ?
(Or some other sample desktop file, but that one is rather small)
Then we can take a look and see if something strange has happened to it.

---

### Post by RaptorRaider on 2006-02-04
Plenty (of GNOME apps) indeed (how do I make this scrollable?):
> accessibility-keyboard.desktop
AdobeReader.desktop
alc.desktop
amule.desktop
anjuta.desktop
at-properties.desktop
audacity.desktop
Automatix.desktop
avidemux.desktop
azureus.desktop
background.desktop
bittornado.desktop
blackjack.desktop
bluefish.desktop
bluefish-project.desktop
bmp.desktop
bug-buddy-core.desktop
bug-buddy.desktop
cddb-slave.desktop
dcpp.desktop
default-applications.desktop
defaults.list <-- has a teal color
disks.desktop
display-properties.desktop
dvdrip.desktop
easytag.desktop
eog.desktop
evince.desktop
evolution-2.2.desktop
evolution-2.4.desktop
evolution-mail.desktop
file-roller.desktop
firefox.desktop
font-properties.desktop
freecell.desktop
FrostWire.desktop
gaim.desktop
gataxx.desktop
gcalctool.desktop
gconf-editor.desktop
gdesklets.desktop
gdmflexiserver.desktop
gdmflexiserver-xnest.desktop
gdmphotosetup.desktop
gdmsetup.desktop
gedit.desktop
gfloppy.desktop
gftp.desktop
gimp-2.2.desktop
gksu.desktop
gksuexec.desktop
glines.desktop
gmenu-simple-editor.desktop
gnect.desktop
gnibbles.desktop
gnobots2.desktop
gnome-about.desktop
gnome-about-me.desktop
gnome-app-install.desktop
gnomebaker.desktop
gnome-btdownload.desktop
gnomecc.desktop
gnome-cd.desktop
gnome-cups-icon.desktop
gnome-dictionary.desktop
gnome-font-viewer.desktop
gnomemeeting.desktop
gnome-nettool.desktop
gnome-network-preferences.desktop
gnome-screensaver-properties.desktop
gnome-search-tool.desktop
gnome-settings-mouse.desktop
gnome-settings-sound.desktop
gnome-sound-recorder.desktop
gnome-stones.desktop
gnome-system-log.desktop
gnome-system-monitor.desktop
gnome-terminal.desktop
gnometris.desktop
gnome-ui-properties.desktop
gnome-volume-control.desktop
gnomine.desktop
gnotravex.desktop
gnotski.desktop
gstreamer-properties.desktop
gtali.desktop
gthumb.desktop
gtk-theme-selector.desktop
gucharmap.desktop
hwdb.desktop
iagno.desktop
kcmgtk-xdg.desktop
kde  <-- has a dark blue color (map)
keybinding.desktop
keyboard.desktop
Kino.desktop
language-selector.desktop
mahjongg.desktop
mimeinfo.cache
mplayer.desktop
nautilus-computer.desktop
nautilus.desktop
nautilus-file-management-properties.desktop
nautilus-folder-handler.desktop
nautilus-home.desktop
network.desktop
network-scheme.desktop
ooo2-base.desktop
ooo2-calc.desktop
ooo2-draw.desktop
ooo2-impress.desktop
ooo2-math.desktop
ooo2-writer.desktop
opera.desktop
reclevel.desktop
rhythmbox.desktop
same-gnome.desktop
screem.desktop
serpentine.desktop
services.desktop
session-properties.desktop
shares.desktop
skype.desktop
smeg.desktop
smeg-kde.desktop
sol.desktop
sound-juicer.desktop
speedcrunch.desktop
streamtuner.desktop
synaptic.desktop
synaptic-kde.desktop
template.desktop
themus-theme-applier.desktop
time.desktop
totem.desktop
tsclient.desktop
ubuntu-about.desktop
update-manager.desktop
users.desktop
vino-preferences.desktop
vlc.desktop
vumeter.desktop
window-properties.desktop
wxcas.desktop
xchat.desktop
XMMS.desktop
XMMS-pl.desktop
xsane.desktop
yelp.desktop

"nano xchat.desktop" shows the following (yes, that seems to be the whole file):
> OnlyShowIn=GNOME
Seems normal to me (or were you implying that these files were going to be large?).

---

### Post by Adrian on 2006-02-04
[QUOTE=RaptorRaider]Plenty (of GNOME apps) indeed:[/QUOTE]
That's normal.

> 
"nano xchat.desktop" shows the following (yes, that seems to be the whole file):


This is not normal. Those are supposed to contain a lot more information (like type, icon and so on). My guess is that the contents of the files have been accidently overwritten.

I don't have a really smart solution. I guess I should have given the advice to backup those files in the original post (I will add this now).

I booted the livecd and archived the desktop files that came with it. I've attached that file to this message, so you might want to try replacing your near-empty desktop files with those from the archive. That should give you the default menu items back.

---

### Post by RaptorRaider on 2006-02-04
The strange thing is that all of the KDE apps seem to be working (except perhaps KInfoCenter, also I think I'm having problems with SuperKaramba :-?) and their corresponding .desktop files in /usr/share/applications/kde are just as empty as the xchat.desktop shown above.

Will try the file archive tomorrow, though it seems too empty already; do you recommend me to reinstall everything?
If so, how am I supposed to seperate these menu items when I install "kubuntu-desktop" again?
Would [this]("http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/") be any different?

---

### Post by Adrian on 2006-02-04
> **RaptorRaider]The strange thing is that all of the KDE apps seem to be working (except perhaps KInfoCenter, also I think I'm having problems with SuperKaramba :-?) and their corresponding .desktop files in /usr/share/applications/kde are just as empty as the xchat.desktop shown above.
[/QUOTE]
Maybe KDE is less sensitive to that kind of errors. I think they too are supposed to contain a lot more information.

[QUOTE]
Will try the file archive tomorrow, though it seems too empty already said:**
> 
Hmm... That would solve everything, of course, but it feels sad for me personally.
If the archive solution works fine, an idea is to also burn the Kubuntu live CD and grab the desktop files from it. Then an uninstall/reinstall of the non-default applications should make both of your desktops complete again :)
(However, maybe you find a complete reinstall of the system less time-consuming)

[QUOTE]
If so, how am I supposed to seperate these menu items when I install "kubuntu-desktop" again?
Would [this]("http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/") be any different?
That is exactly the same technique. It should work.

I have a theory about why you get this error. Is it possible that you wrote a single ">" instead of ">>" when following the instructions of the first post? A single ">" overwrites the file while ">>" appends the text to the end of it.

---

### Post by nmatheis on 2006-02-05
i hope you two can work it out without too much problem.  i got impatient, drug my crucial files over to an external hard drive, and did a reinstall with ubuntu.  that did the trick :)  no more pesky menu cross-over!  i think if i want to do kde, i'll just boot up with a kanotix live cd i burned last week.  and adrian, thanks for trying to help us both out!  sorry i was too impatient to wait for a solution.  i have full confidence that given a little more time, you two will work it out.  i just don't have too much to lose by performing a reinstall.  i dual boot with winxp (for the fiancee) and can always use that.  and a usb2 external hard drive makes backing up files regularly easy enough.
anyway, good luck with solving the problem you two!
nikolaus

---

### Post by RaptorRaider on 2006-02-05
[QUOTE=Adrian]I have a theory about why you get this error. Is it possible that you wrote a single ">" instead of ">>" when following the instructions of the first post? A single ">" overwrites the file while ">>" appends the text to the end of it.[/QUOTE]
I doubt that - though I admit I don't remember well, I'm a bit of a copy/paste cowboy.

Will do a reinstall soon, make a backup, do exactly as you said and report whatever happens here.

---

### Post by Adrian on 2006-02-05
Well, I've revided the HOWTO a little now. A step for making backups of the desktop files is now included, so hopefully no more serious accidents will happen. I should have added that from the start, really.

[QUOTE=RaptorRaider]
Will do a reinstall soon, make a backup, do exactly as you said and report whatever happens here.[/QUOTE]
I'll drop in every our or so to check this thread :)
I'm sure that you will have no problems at all now when the unfortunate Gnome/GNOME "bug" is fixed (I'm sorry for that, guys). To be on the safe side, I've tried the script (by cutting and pasting it) on different configurations today.

---

### Post by Adrian on 2006-02-05
[QUOTE=nmatheis]that did the trick[/QUOTE]

I'm happy that you've got your system up and running again :)

---

### Post by RaptorRaider on 2006-02-06
Reinstall complete (some things are not yet functioning properly though), tried again and this time the "OnlyShowIn=GNOME" was correctly **added** to the end of each .desktop file. :)

A (large) disadvantage of this whole method is that every time you install a new application, you have to add the "OnlyShowIn=GNOME" every time to prevent it from showing up in KDE, right?

---

### Post by Adrian on 2006-02-06
[QUOTE=RaptorRaider]Reinstall complete (some things are not yet functioning properly though), tried again and this time the "OnlyShowIn=GNOME" was correctly **added** to the end of each .desktop file. :)
[/QUOTE]
Great :)

[QUOTE=RaptorRaider]
A (large) disadvantage of this whole method is that every time you install a new application, you have to add the "OnlyShowIn=GNOME" every time to prevent it from showing up in KDE, right?[/QUOTE]
That's correct.
I edit the menus manually with kmenuedit whenever I install new software that i DON'T want in both menus. That's because I usually don't install multiple programs at once.

You might want to clean the files (by using the **grep -v** script mentioned above) before you run the "OnlyShowIn=GNOME" script a second time. Otherwise, that line will be added a second time (but that will also work).

---

### Post by RaptorRaider on 2006-02-07
Noticed today that "OnlyShowIn=GNOME" wasn't added correctly to totem.desktop: instead of it being on new line, it was added at the end of something starting with "MimeType="; it was added to the menu in KDE because of that.

---

### Post by Adrian on 2006-02-07
[QUOTE=RaptorRaider]Noticed today that "OnlyShowIn=GNOME" wasn't added correctly to totem.desktop: instead of it being on new line, it was added at the end of something starting with "MimeType="; it was added to the menu in KDE because of that.[/QUOTE]

OK. That desktop file probably didn't end the last row with a newline.
Maybe it's a good idea to write a little more complex script that takes care of situations like that.

---

### Post by Adrian_b on 2006-08-27
I know this is an old topic, but i have some problems.
Some things didn't work, so i started screwing around, now i'm having this when doing grep "OnlyShowIn=" *
```

main-menu-rug.desktop:OnlyShowIn=Gnome;
main-menu-rug.desktop:OnlyShowIn=;
main-menu-rug.desktop:OnlyShowIn=
main-menu-rug.desktop:OnlyShowIn=GNOME
main-menu-rug.desktop:OnlyShowIn=KDE
main-menu-rug.desktop:OnlyShowIn=Gnome
main-menu-rug.desktop:OnlyShowIn=

```
It's all the same, just another .desktop file.

Does anyone have any clue how to remove all that without going trough every .desktop file?

---

### Post by Adrian_b on 2006-08-27
I found out the commands from this topic replaced the whole file with the above.
So all those .desktop files are existant but empty :s

---

### Post by iammeagain on 2007-12-08
> **Adrian said:**
> 

**Method 2:**
Another, more elegant solution (which I unfortunately have not tried yet) is this small program:
[http://www.kde-look.org/content/show.php?content=31031](http://www.kde-look.org/content/show.php?content=31031)

It will put your Gnome items in a special Gnome menu folder.



This worked wonderfully for me. Thanks a ton! :)

There is also one for Gnome to put KDE programs in a special folder. [http://www.gnome-look.org/content/show.php/Gnome+Menu+Extended+%28Debian+Package%29?content=31035&PHPSESSID=5bad75bf2b5737af6f990653e66eaa6f](http://www.gnome-look.org/content/show.php/Gnome+Menu+Extended+%28Debian+Package%29?content=31035&PHPSESSID=5bad75bf2b5737af6f990653e66eaa6f)

---

