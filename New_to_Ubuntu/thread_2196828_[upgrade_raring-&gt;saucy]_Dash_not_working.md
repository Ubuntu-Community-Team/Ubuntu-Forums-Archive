---
title: "[upgrade raring-&gt;saucy] Dash not working"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-12-31
Hello all!

My Dash is not displaying any Lenses other than the "Social networking lens". Screenshot attached.

This happened after the upgrade from Ubuntu 13.04 (Raring Ringtail) to Ubuntu 13.10 (Saucy Salamander).

Any ideas on how to fix this?

Thanks in advance.

---

### Post by deadflowr on 2013-12-31
Don't know the fix, but can you search and bring up any apps, or you folder stuffs?

---

### Post by xsaucysalamander on 2013-12-31
Maybe reboot

---

### Post by monkeybrain20122 on 2013-12-31
Go to System Settings > Security And Privacy > Files and Applications and check if it is turned off..

---

### Post by Jonathan Precise on 2014-01-01
@deadflowr: Searching does nothing.
@xsaucysalamander: This has been here for weeks
@monkeybrain: It is turned on.

I did a fresh install on another computer, and the dash worked! So it isn't a problem with ubuntu 13.10. It seems to be a problem on upgrade.

---

### Post by Jonathan Precise on 2014-01-01
Anyone?

(Yes, I'm bumping this thread after 2 hours. It's because I have to run everything through "Run a command" Alt+F2, and this gets very annoying. :x)

---

### Post by monkeybrain20122 on 2014-01-01
Just a guess. Open the file manager, press ctrl+h to show hidden files, then go to .local/share/ and rename the folder zeitgeist  to something else, like zeitgeist-old. Then reboot and see if it fixes your problem. If it does just delete zeitgeist-old (or you can delete it even if it doesn't as long as it doesn't get worse, if it does get worse, remove the new zeitgeist folder which has been generated automatically and then remame zeitgeist-old back to zeitgeist)

---

### Post by Jonathan Precise on 2014-01-01
Ok will do that.

---

### Post by Jonathan Precise on 2014-01-01
Didn't work. Help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by monkeybrain20122 on 2014-01-01
I found these 
[http://ubuntuforums.org/showthread.php?t=2067256](http://ubuntuforums.org/showthread.php?t=2067256)
[http://askubuntu.com/questions/225519/applications-not-showing-in-unity-dash](http://askubuntu.com/questions/225519/applications-not-showing-in-unity-dash)
Good luck. Otherwise maybe a fresh install is in order. It is tricky to trouble shoot a blotched upgrade as so many seemingly unrelated things could go wrong. I always recommend creating a separate /home partition and do fresh install everytime you need to upgrade the OS, much faster and safer.

---

### Post by deadflowr on 2014-01-01
If you create a second user, can that user use the dash properly?

---

### Post by Jonathan Precise on 2014-01-02
@deadflowr: Nope :(

***

@monkeybrain20122: The problem is that ```
unity --reset
``` is deprecated: ```
ERROR: the reset option is now deprecated
``` :( :(

Tried reinstalling: [FONT=Courier New]unity-lens-applications, unity-lens-files[/FONT], The google-drive scope, and [FONT=Courier New]hud[/FONT]. Tried purging them and installing them again. It's the same broken dash.

---

### Post by deadflowr on 2014-01-02
Try reinstalling the ubuntu-desktop metapackage
but first clean apt.
run
```
sudo apt-get clean
``` 
and 
```
sudo apt-get autoclean
```
then 
```
sudo apt-get update
```
then 
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by Jonathan Precise on 2014-01-02
:( Still the same after following those steps. :( :( Even killing /usr/bin/X and logging back in, still the same. :(

---

### Post by monkeybrain20122 on 2014-01-02
Probably a clean install is the way to go. It will be a lot faster than trouble shooting this. 
Backup the data and also save your sources.list and sources.ist.d

make a list for your installed programs so can be reinstalled easily [http://ubuntuforums.org/showthread.php?t=261366&page=12](http://ubuntuforums.org/showthread.php?t=261366&page=12)

Then do a clean install. After that replace the sources.list and sources.list.d with the backup (if you use ppas)
Then reinstall programs following link above.

---

### Post by chkneater on 2014-01-02
Yeah its definitely an upgrad prob... 13.10 is still relatively new and I hate to say it but a full install is your best bet.  What happened with me tho, is using the LIVEDVD I checked the "install 13.10 alongside 13.04" and it overwrote it anyways, so don't unmount 13.04 when it asks you during install otherwise it will try to overwrite it evidently.

Also one thing I did after getting my all my stuff erased when trying to upgrade was a made a seperate NTFS partition to save important things and also so I can unplug my ext HDD and access files using a windows system.  Just a tip, not necessary.

---

### Post by Jonathan Precise on 2014-01-02
Is there any alternative to re-installing, as currently I do not have a back-up drive? I have too many programs I have made (that are packaged but have not installed them to any directory in my $PATH variable), a lot of google-chrome bookmarks I want to conserve, a lot of customized files in the config directory /etc and /usr/share, a ton of 3rd-party repositories (that were disabled manually on upgrade), a whole xampp installation with mediawiki moodle phpbb and wordpress, and a whole other bunch of stuff I just don't wan't to loose.

(I have made backups to another partition that is now very low on space :(, which is why since I-don't-remember-when I have stopped backing up.)

Help?

---

### Post by monkeybrain20122 on 2014-01-02
Your chrome settings are in .config/google-chrome. If you back this up  and move it to the new installation you will save all your bookmarks,  addons and the open tabs when you reinstall chrome. So that is not a problem. 

I think it is probably one of the customized files in the config directories that messed up your dash so I wouldn't save those. Not sure what you mean by packages that you have made but not installed. Do you means something you "make" but have not done "make install"?  With checkinstall you can create a .deb in the build directory and you can save those, but I don't know how to create the .deb without installing it at the same time.

You may be able to move the xammp installation as all the files are in a single folder in /opt if I remember correctly.

So probably not much disk space will be required for these..

P.S. upgrade usually works only if you have a relatively pristine system. If you have a heavily customized system with a lot third party apps, ppas etc then you should definitely do a clean install instead (I have a separate /home so that is rather easy in terms of keeping settings and data)

---

### Post by Jonathan Precise on 2014-01-02
> **monkeybrain20122 said:**
> Not sure what you mean by packages that you have made but not installed. Do you means something you "make" but have not done "make install"?

No, I'm a developer, and have made a couple of .debs. However, I have them installed to a non-standard directory (my home directory)

---

### Post by monkeybrain20122 on 2014-01-02
> **Jonathan Precise said:**
> No, I'm a developer, and have made a couple of .debs. However, I have them installed to a non-standard directory (my home directory)

So if they are installed everything should be in a few directories in your /home, right? ($HOME/bin, $HOME/lib, $HOME/include, $HOME/share etc) Can you just move those?

---

### Post by Jonathan Precise on 2014-01-03
Nope. They're all in different sub-directories of home corresponding to the program's name (for example: /home/*myuser*/Network Troubleshooter/nettroubleshooter).

More specifically, those programs are scripts, not binaries like synaptic or ubiquity.

As for the backup partition, it's my Windows partition, and right now it is half full, and (Windows 8.1) is unbearably slow (even though I bought this computer in 2013 :shock:).

Help?

---

### Post by Jonathan Precise on 2014-08-08
Sorry for the delay, but actually this was fixed when I upgraded to 14.04 LTS. Hurray!
*Thread marked as solved*

---

### Post by Jonathan Precise on 2014-08-08
Sorry for the delay, but actually this was fixed when I upgraded to 14.04 LTS. Hurray!
*Thread marked as solved*

---

