---
title: "Reinstall Ubuntu, Separate Home, Removing Previous Install Settings"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by Redblade20XX on 2012-03-02
Hey everyone,

Just have a quick question. I have a tendency to tinker around with Ubuntu and have to reinstall a lot, lol. ;)I use the separate partitions scheme to prevent me from having to back up my necessary home data for the reinstalls I have to perform. In doing so, some of the settings from the previous install is also carried over into the new install such as wine program icons (program doesn't work of course), firefox settings, wallpaper choice, etc. Can anyone tell me a way to remove these carried over settings or point me in the right direction to find some documentation?

Thanks! :p

- Red

---

### Post by fleamour on 2012-03-02
I would use Clonezilla to keep a fresh image handy.  An image is like a Polaroid snapshot of your hard disk drive's contents, & can be reinstalled as often as you like.  The old contents get written over by the image itself.

I started out on XP & wish I'd known about images sooner.  I used to reinstall a lot, but it makes much more sense & saves time & effort to do things properly...

---

### Post by 1clue on 2012-03-02
Rather than putting your /home on a separate partition, you could put a few folders on a separate partition and then link those.  Like Documents, Downloads, Music, whatever it is you want to keep.

That way the settings don't hang around, which tend to be not transportable between Linux distros or major upgrades anyway, but the documents you use DO hang around, and that sort of thing transfers nicely.

---

### Post by oldfred on 2012-03-02
I do the same as 1clue.

I may copy a few settings from one install to another, but have all data and some hidden folders like Firefox & Thunderbird profiles, kmymoney data, etc also in my data partition. So then my /home only has settings and maybe a few small files I have not moved yet. And it then is easy to backup as it is less than 2GB and most of that is my .wine.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Paddy Landau on 2012-03-02
Your settings are stored in hidden files or folders (those that start with a dot) in your home folder.

For example, Firefox settings are stored in a folder called [FONT=Lucida Console].mozilla[/FONT] (note the leading dot).

So, if you go to your home folder in Nautilus and press Ctrl-H to show your hidden files and folders, you can simply delete every dot-file and dot-folder if you like. Immediately log out and in again. That will delete *all* your settings.

Or, if you wish to delete selected settings, delete only the relevant files or folders -- but sometimes it can be hard to find where the settings are stored; some settings are stored in either [FONT=Lucida Console].gconf[/FONT] or [FONT=Lucida Console].gconfd[/FONT], which are generic areas for all sorts of settings.

---

### Post by Redblade20XX on 2012-03-08
Thanks guys for all your responses! Decided to put the actual data on a separate partition and works like a charm. Again thanks! :D

= Red

---

