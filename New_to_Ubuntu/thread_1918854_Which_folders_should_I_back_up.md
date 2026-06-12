---
title: "Which folders should I back up?"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by cjosh on 2012-02-01
I'm about to back up my Ubuntu files and reinstall because I messed up my system. I would like to back up my downloads, documents, and software installations and its configurations, but not any driver stuff or other OS configurations/X server stuff (since I'm convinced that's what messed everything up). Are there any folders to avoid or exclude when backing up (assuming every file is placed where it should be, I haven't deviated too much from default file saving locations)?

Sorry if this sounds incredibly basic, I'm a native Windows user and I'm pretty sure Linux doesn't have a System Restore.

---

### Post by wolfen69 on 2012-02-01
You pretty much said it yourself. Just backup all your personal files, and you might want to also save config files for firefox, banshee, etc.

---

### Post by Double.J on 2012-02-01
> **wolfen69 said:**
> You pretty much said it yourself. Just backup all your personal files, and you might want to also save config files for firefox, banshee, etc.

+1; the recommended back-up technique is to make a copy of your /home directory

Hope it helps :)

---

### Post by cjosh on 2012-02-01
Thanks for the responses. Just to clarify, the config files for software is not located in the home folder? I'd also like to backup my Chromium bookmarks as well.

---

### Post by wolfen69 on 2012-02-01
> **cjosh said:**
> Thanks for the responses. Just to clarify, the config files for software is not located in the home folder? I'd also like to backup my Chromium bookmarks as well.

To see your config files, open your home folder and do Ctrl-H to show your hidden files. You will see folders beginning with a dot (.) Those are your config files. The Chromium file is located in .config

---

### Post by sammiev on 2012-02-01
I just do a full backup to a USB drive every week or two and if I do not think it's worth while at that time I just backup my bookmarks as I love to play. :)

---

### Post by vanhenryjr on 2012-03-08
So in preparation for 12.04 I want to backup my home folder, but do not need to backup etc or any other folders? I plan on a clean install (currently using 11.04)??

Will this include my data from my tomboy notes; I know I will need to reinstall tomboy after I do a clean install of 12.04. 

thank you

---

### Post by bronquel on 2012-03-08
For me personally I use dropbox to back up all my stuff(500mb or so), as i re-install ubuntu with each distro that comes out.  In the future i would recommend that way.  I've even screwed up my linux install on multiple times so i cannot boot into it, and knowing everything is backed up in dropbox i can reinstall without a fear of losing everything.  

For what you want to do, your home folder is where most of what you want is.  Here is the documentation from the tomboy website where tomboy data is stored: [http://live.gnome.org/Tomboy/Directories](http://live.gnome.org/Tomboy/Directories)

---

### Post by ageofsteam on 2012-03-08
1. Backup your home folder and BE SURE TO GET THE HIDDEN FILES, TOO.  It may sound noobish, but it's easy to not get those backed-up if your copy-pasting or using the terminal without checking...  I once lost a lot of settings that way. :(  All the folders starting with ., you need to make sure you get...

2. If you plan on doing this again, it can be useful to make a text file to run in the terminal and automate the backups later on.  I have a folder with backup folders for each program in it, and files named backup.txt in each folder, with contents like this:
```
#LASTRUN 20120127
cd /home/USERNAMEHERE/.mozilla
mkdir -p PATHTOBACKUPFOLDER/firefox/home/USERNAMEHERE/.mozilla
cp -r -u * -v PATHTOBACKUPFOLDER/firefox/home/USERNAMEHERE/.mozilla

```3. Backup usr/share/icons.  If you have custom icons, you might not want to lose them...

4. Doing this in the terminal should backup all the Rhythmbox stuff (just doing the home folder isn't enough):
```
mkdir -p PATHTOBACKUPFOLDER/rhythmbox/home/USERNAMEHERE/.local/share/rhythmbox
cd /home/USERNAMEHERE/.local/share/rhythmbox
cp -r -u * PATHTOBACKUPFOLDER/rhythmbox/home/USERNAMEHERE/.local/share/rhythmbox/

mkdir -p PATHTOBACKUPFOLDER/rhythmbox/usr/share/rhythmbox
cd /usr/share/rhythmbox
cp -r -u * PATHTOBACKUPFOLDER/rhythmbox/usr/share/rhythmbox/

#mkdir -p PATHTOBACKUPFOLDER/rhythmbox/home/USERNAMEHERE/Music
#cd /home/USERNAMEHERE/Music
#cp -r -u * PATHTOBACKUPFOLDER/rhythmbox/home/USERNAMEHERE/Music/

mkdir -p PATHTOBACKUPFOLDER/rhythmbox/home/USERNAMEHERE/.gconf/apps/rhythmbox
cd /home/USERNAMEHERE/.gconf/apps/rhythmbox
cp -r -u * PATHTOBACKUPFOLDER/rhythmbox/home/USERNAMEHERE/.gconf/apps/rhythmbox/
```Or, at least, this is what I use.  And I've restored RB a few times successfully (I have a history of accidentally messing my system and having to reinstall...  Which is also why someone else should probably glance over my advice before you try it, but I can at least say that all of it DOES work for me...)

5. If some of the stuff you're backing up has symbolic links, I think you might have to back it up onto an ext type of filesystem or compress it in an archive- at least, it seems to work that way for me.  Can someone more advanced confirm this?  There may be some workaround...

Hopefully this is a bit helpful?

---

### Post by vanhenryjr on 2012-03-08
> **bronquel said:**
> For me personally I use dropbox to back up all my stuff(500mb or so), as i re-install ubuntu with each distro that comes out.  In the future i would recommend that way.  I've even screwed up my linux install on multiple times so i cannot boot into it, and knowing everything is backed up in dropbox i can reinstall without a fear of losing everything.  

For what you want to do, your home folder is where most of what you want is.  Here is the documentation from the tomboy website where tomboy data is stored: [http://live.gnome.org/Tomboy/Directories](http://live.gnome.org/Tomboy/Directories)

My home is almost 30 GB! I assume all my music is there.

---

### Post by bronquel on 2012-03-15
> **vanhenryjr said:**
> My home is almost 30 GB! I assume all my music is there.

It is not to hard to get up to those sizes with a free account.  I'm up to 18 gb or so, and just added 5gb with tips from lifehacker posted yesterday: [http://lifehacker.com/5893262](http://lifehacker.com/5893262)  (the article tells how to get 3gb, and the comments tell you how to get another 2gb)  

I also don't put my home directory in dropbox - just files i need, like homework, personal code projects, etc.

---

