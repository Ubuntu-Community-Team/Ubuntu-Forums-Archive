---
title: "How to get readable bookmarks in Mozilla using ubuntu"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by nightcrawler1924 on 2013-01-09
Hi,

I'm having a problem getting my bookmarks off old computer.  I used Ubuntu to get into the system and I went into bookmarks and was able to export the file to desktop HTML - but it is not readable.

I want to transfer it to my mozilla on my new system and can't seem to do this.

I also can get into HD.  I keep getting mounting 113 error.  I wanted to try and save my pics and files if anyone can help it would be greatly appreciated.

Thank you!

---

### Post by vasa1 on 2013-01-09
> **nightcrawler1924 said:**
> ...  I used Ubuntu to get into the system and I went into bookmarks and was able to export the file to desktop HTML - but it is not readable. ...
What do you mean by "not readable"?

---

### Post by Pletched on 2013-01-09
Read here [http://support.mozilla.org/en-US/kb/restore-bookmarks-from-backup-or-move-them](http://support.mozilla.org/en-US/kb/restore-bookmarks-from-backup-or-move-them)

---

### Post by nightcrawler1924 on 2013-01-09
I mean when I click on the file there is just a bunch of code and not the actually bookmark names.  It's not readable.

On the second reply, I did read that and tried to move them by saving the file on my external... and that didn't work either.

Thank you both for your help.

This is terrible.  Why is it so hard to save the bookmark files in Mozilla.  I never had a problem with Google or IE.  I have been at this for days.  Any one else have an idea.

Thank you.

---

### Post by howefield on 2013-01-09
> **nightcrawler1924 said:**
> I mean when I click on the file...

What is the file name ?

Are you unable to boot the old computer ?

> **nightcrawler1924 said:**
> This is terrible.  Why is it so hard to save the bookmark files in Mozilla.

It really isn't, Firefox > Bookmarks > Show all Bookmarks > Import and Backup > Export Bookmarks to HTML... and then import the html file back into your new installation.

---

### Post by nightcrawler1924 on 2013-01-09
Yes, I can only get in using ubuntu.  I can't get into safe mode either.  That's why I'm trying to save my files, docs and bookmarks.  I tried to repair and got a 0xc00000e9 error.

[HTML]It really isn't, Firefox > Bookmarks > Show all Bookmarks > Import and Backup > Export Bookmarks to HTML... and then import the html file back into your new installation.
[/HTML]

Okay.  What is the correct way?  I read to do it that way on Mozilla Support.  Please help.

---

### Post by howefield on 2013-01-09
> **nightcrawler1924 said:**
> I mean when I click on the file there is just a bunch of code and not the actually bookmark names. 

Is it a .json file ?

If so, import it into your new Firefox with...

Firefox > Bookmarks > Show all Bookmarks > Import and Backup > Restore > Chose File > ect

---

### Post by nightcrawler1924 on 2013-01-09
I tried it with HTML and Json and neither worked.  Is there anyway to open the bookmark file so I can see the bookmark names?

Also where do I find my pictures and documents?  I couldn't find them using ubuntu.

Thank you for helping.

---

### Post by iMac71 on 2013-01-09
> **nightcrawler1924 said:**
> Yes, I can only get in using ubuntu.  I can't get into safe mode either.  That's why I'm trying to save my files, docs and bookmarks.  I tried to repair and got a 0xc00000e9 error.the following link might be somehow helpful: [http://www.tomshardware.co.uk/forum/281900-14-error-0xc00000e9-computer-start-hard-drive-suspected](http://www.tomshardware.co.uk/forum/281900-14-error-0xc00000e9-computer-start-hard-drive-suspected)

---

### Post by fantab on 2013-01-09
> **nightcrawler1924 said:**
> I tried it with HTML and Json and neither worked.  Is there anyway to open the bookmark file so I can see the bookmark names?

Also where do I find my pictures and documents?  I couldn't find them using ubuntu.


Using Ubuntu LiveCD/LiveUSB you have to mount the WINDOWS partitions (assuming that your old computer is/was using windows). To do this open the Files (File Manager) listed as HOME... on the right side you will find "DEVICES"; click to open all the listed devices (which are essentially your Windows Partitions) in Linux they will be listed as /dev/sda1 or /dev/sda2 etc... or it will just show as 50GB filesystem or 100GB filesystem...

If you can do this and if you HDD partitions are not corrupted then you WILL be able to rescue your DATA by copying it to a USB drive etc...

As for your bookmarks try to copy the "Bookmark' Files and Folders you may have, take them to a borrowed computer and see if you can access them from the browser on another computer...

---

### Post by nightcrawler1924 on 2013-01-09
Imac, I tried it and can't get into safe mode or command prompt.  I found that link yesterday.

How come I can get on the system with ubuntu?  And I did do as you said, it won't let me mount.  I get 113 error codes.

Any other ideas how I could just get my bookmarks, pics and Docs?

Thank you all for the help!  It is greatly appreciated.

---

### Post by fantab on 2013-01-09
> **nightcrawler1924 said:**
> How come I can get on the system with ubuntu?  And I did do as you said, it won't let me mount.  I get 113 error codes.

Any other ideas how I could just get my bookmarks, pics and Docs?

You can boot with Ubuntu LiveCD or USB because it does not boot from HDD.  What does "DISKS" utility tell you about your HDD? What does GParted tell you about your HDD? These utilities are present on your Ubuntu, use them and tell us what happens, with Screen shots if possible.

To recover your Data, perhaps you can try [**TEST DISK**]("http://www.cgsecurity.org/wiki/TestDisk") (there are no guarantees though). There are more links about Test Disk[ **HERE**]("http://ubuntuforums.org/showpost.php?p=12443356&postcount=3"). You might find this [**LINK**]("https://help.ubuntu.com/community/DataRecovery") useful too.

There are also many Windows specific Data Recovery tools that you can run from bootable CD or USB.. try them out.

Good Luck....

---

### Post by NikTh on 2013-01-09
Test disk and /or Photorec will recover files , lot of files as @fantab suggested. 

Then difficult part is when the files recovered, how you will find the files you want. Testdisk will not recover the files with original names. And maybe the recovered data will be some GBs .. and some hundreds of folders and thousands of files.
Good luck with recovery.

---

### Post by nightcrawler1924 on 2013-01-09
Okay here's some pics of the disks utilities.

I'm not even sure what i'm looking for.

I'm working on G parted

---

### Post by nightcrawler1924 on 2013-01-09
Okay here's the rest and thank you all again and again.

---

### Post by nightcrawler1924 on 2013-01-09
One more.  Sorry.

Thanks!

---

### Post by Pletched on 2013-01-09
If it's possible I think you could attach your old profile to profiles.ini in ~/.mozilla/firefox/profiles.ini. This keeps all the bookmarks, extensions, and settings.

current ~/.mozilla/firefox/profiles.ini
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=5b3q5lt4.default
```

new profile added ~/.mozilla/firefox/profiles.ini
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=5b3q5lt4.default

[COLOR="RoyalBlue"][Profile1]
Name=karp
IsRelative=1
Path=myplace/karp[/COLOR]
```

Close all instances of firefox and open as firefox -ProfileManager and select the old profile.

---

### Post by nightcrawler1924 on 2013-01-09
Okay.  Find the file and just type it out as you did right?

Thank you so much for your help.

So there's no way to get the real bookmark list that I could just take a pic of?

---

### Post by Pletched on 2013-01-10
I didn't say it will work, but it might be possible. With new versions brings new settings so profiles made in earlier versions might not be compatible with newer versions.

You also need your old profile folder. Place it in firefox's configuration folder ~/mozilla/firefox.

Set the Path variable (in ~/mozilla/firefox/profiles.ini) to relative path from firefox folder ~/mozilla/firefox.

if the profile folder name is ~/mozilla/firefox/3oairj.karp the path is
```
Path=3oairj.karp
```

overview
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=5b3q5lt4.default

[Profile1]
Name=karp
IsRelative=1
[COLOR="Red"]Path=3oairj.karp[/COLOR]
```

---

### Post by nightcrawler1924 on 2013-01-10
Okay that's not working either.

I'm almost afraid to ask but how would I get my favorites off IE using ubuntu?  Any chance of this working and I have to say I doubt it when I can't even find IE when using ubuntu.  I onlt see Mozilla.

Thanks for all the help everyone.  it's appreciated!

---

### Post by iMac71 on 2013-01-10
> **nightcrawler1924 said:**
> Okay that's not working either.

I'm almost afraid to ask but how would I get my favorites off IE using ubuntu?  Any chance of this working and I have to say I doubt it when I can't even find IE when using ubuntu.  I onlt see Mozilla.

Thanks for all the help everyone.  it's appreciated!IE runs only in Windows systems.
Many years ago there was an Apple version, but it was discontinued.
Therefore if you wish to use IE, you should install Virtualbox and create a virtual Windows machine or, alternatively, partition the HD where is Ubuntu and create a dual boot with Windows alongside Ubuntu itself.

---

### Post by nightcrawler1924 on 2013-01-11
This is insane!  4 days to just try and save my files and favorites.

They have to make something better to help us when our systems go down.  Ugh...

It wouldn't let me into the hard drive so I did a search with the files and I at least found some of my pics.  I was sooooo Happy.  Now it would be nice after all this time if I could find the Fav folder and documents.

Thanks so much for the help.  Really really thank you!  :)

---

### Post by howefield on 2013-01-11
> **nightcrawler1924 said:**
> This is insane!  4 days to just try and save my files and favorites.

They have to make something better to help us when our systems go down.  Ugh...

The famous "They" have a lot to answer for !!

Where do **you** fit in all of this ?

Don't let your frustration cloud your judgment, and think twice about blaming someone else for **your** lack of backup strategy.

---

### Post by iMac71 on 2013-01-11
> **nightcrawler1924 said:**
> This is insane!  4 days to just try and save my files and favorites.if you can somehow use IE, then the following link might be helpful:
[http://support.microsoft.com/kb/211089/en-us](http://support.microsoft.com/kb/211089/en-us)

---

