---
title: "Trying to update from an old ubuntu installation to 14.04 LTS"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by braydon2 on 2014-05-07
Ok this might be in the wrong section but oh well.

So I had a disk of Ubuntu it had an old installation of it I that is what I installed. The layout from the new Ubuntu and this one look completely different does Ubuntu update everything so I get to the version of 14.04?!?!

---

### Post by slickymaster on 2014-05-07
> **braydon2 said:**
> Ok this might be in the wrong section but oh well.

So I had a disk of Ubuntu it had an old installation of it I that is what I installed. The layout from the new Ubuntu and this one look completely different does Ubuntu update everything so I get to the version of 14.04?!?!

What version of Ubuntu is installed in that disk?

Upgrade is the process of going from an earlier version of Ubuntu to a newer version of Ubuntu with an installed system. To avoid damaging your running system, upgrading should only be done from one release to the next release (e.g. Ubuntu 13.10 to Ubuntu 14.04) or from one LTS release to the next (e.g. Ubuntu 12.04 LTS to Ubuntu 14.04 LTS).
If you wish to 'skip' a version, you can backup your data and do a fresh installation, or progressively upgrade to each successive version. For example, to upgrade from Ubuntu 13.04 to Ubuntu 14.04, first upgrade to 13.10, then upgrade 13.10 to 14.04

---

### Post by braydon2 on 2014-05-07
I don't know what version it is I cant remember how would I find out?

---

### Post by slickymaster on 2014-05-07
Just run the following command in a terminal window and it will tell you:```
lsb_release -a
```

---

### Post by LastDino on 2014-05-07
Seeing as this is fresh install, irrespective of what version it is, just download 14.4LTS and do fresh install.

---

### Post by braydon2 on 2014-05-07
> **LastDino said:**
> Seeing as this is fresh install, irrespective of what version it is, just download 14.4LTS and do fresh install.
So your saying just download it and replace my current Ubuntu Installation?

---

### Post by LastDino on 2014-05-07
> **braydon2 said:**
> So your saying just download it and replace my current Ubuntu Installation?

Yes, take backup of whatever data you want to preserve though. And don't select ''replace'' option in installation when it asks for ot, that seems to erase everything. Use ''do something else''.

Less hassle, less time and higher probability of stability.

---

### Post by braydon2 on 2014-05-07
> **LastDino said:**
> Yes, take backup of whatever data you want to preserve though. And don't select ''replace'' option in installation when it asks for ot, that seems to erase everything. Use ''do something else''.

Less hassle, less time and higher probability of stability.


I have nothing on there that I want to preserve right now.

---

### Post by grahammechanical on 2014-05-07
If it is ubuntu Precise Pangolin (12.04) then you can upgrade directly to Trusty Tahr (14.04) but I would wait a few weeks or even until after 24th July as 14.04 will itself receive an upgrade from 14.04 to 14.04.1.

If it is Ubuntu Saucy Salamander (13.10) then you can upgrade directly to Trusty Tahr (14.04) but I would wait a few weeks or even until after 24th July as 14.04 will itself receive an upgrade from 14.04 to 14.04.1.

Any other version of Ubuntu will have reached End of Life. It is more complicated to upgrade from an End of Life release. And this is why it is being suggested that you download the ISO image of the latest Ubuntu (14.04) and test it out and then install. If you look at the login screen you will see a label telling you what version it is that you have already installed.

Regards.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by deadflowr on 2014-05-07
> **braydon2 said:**
> I have nothing on there that I want to preserve right now.

If the computer has only Ubuntu on it, then just use the replace option.

If however it has another system on it (Windows, or another linux system) then "something else" would be preferable.
This is because sometimes the installer misreads the users intent and simply replaces the whole disk when using the replace option.
Whether this is user error or not is something to be debated.

---

### Post by LastDino on 2014-05-07
> **deadflowr said:**
> If the computer has only Ubuntu on it, then just use the replace option.

If however it has another system on it (Windows, or another linux system) then "something else" would be preferable.
This is because sometimes the installer misreads the users intent and simply replaces the whole disk when using the replace option.
Whether this is user error or not is something to be debated.

Indeed, but I clearly remember it not asking anything regarding partitions after clicking ''replace'', I don't think it is meant to erase partition table with existing OS too. I dunno, I might have been the odd case or it might indeed be me lacking on some coffee. It's still better to be safe than sorry, especially with new users.

---

### Post by deadflowr on 2014-05-07
> **LastDino said:**
> Indeed, but I clearly remember it not asking anything regarding partitions after clicking ''replace'', I don't think it is meant to erase partition table with existing OS too. I dunno, I might have been the odd case or it might indeed be me lacking on some coffee. It's still better to be safe than sorry, especially with new users.

It usually doesn't ask about partitions.
The benefit of replace is it automatically sets up the partitioning scheme.
The disadvantage is that it sets it up in a way that might be troublesome later on.
The installer creates a main partition, usually sda1, then makes an extended partition, usually sda2, then creates a logical partition on sda5. So if later on you need a primary partition (which are only the first four partitions) you need to jump through a few hoops to set it up.

---

### Post by LastDino on 2014-05-07
> **deadflowr said:**
> It usually doesn't ask about partitions.
The benefit of replace is it automatically sets up the partitioning scheme.
The disadvantage is that it sets it up in a way that might be troublesome later on.
The installer creates a main partition, usually sda1, then makes an extended partition, usually sda2, then creates a logical partition on sda5. So if later on you need a primary partition (which are only the first four partitions) you need to jump through a few hoops to set it up.

Tell me about it! It only preserved my 4GB SWAP partition from older OS and putted rest of the 1TB HD into ''/''.  I think that only spells problems ;)

---

### Post by braydon2 on 2014-05-07
> **deadflowr said:**
> It usually doesn't ask about partitions.
The benefit of replace is it automatically sets up the partitioning scheme.
The disadvantage is that it sets it up in a way that might be troublesome later on.
The installer creates a main partition, usually sda1, then makes an extended partition, usually sda2, then creates a logical partition on sda5. So if later on you need a primary partition (which are only the first four partitions) you need to jump through a few hoops to set it up.


I think I already setup the partition would I need to do it again?

---

### Post by deadflowr on 2014-05-07
> **braydon2 said:**
> I think I already setup the partition would I need to do it again?

If you've set up a partitioning scheme that works for you, then use the "something else" option.
Simply because you can make sure that it doesn't replace it with a wholly new one.

To use something else, find the partition you want to use and highlight it, then click "Change /or Edit".
Select the mount point (usually /, but if using separate partitions for /home, you can as well).

And then set the filesystem type. (It will say do not use partition, simply click on it and ,strangely, the normal default filesystem type ext4, is way up at the top of the list.)

If you have swap, you can leave it be.
The installer will find it, without you needing to do anything about it.

---

### Post by braydon2 on 2014-05-07
> **deadflowr said:**
> If you've set up a partitioning scheme that works for you, then use the "something else" option.
Simply because you can make sure that it doesn't replace it with a wholly new one.

To use something else, find the partition you want to use and highlight it, then click "Change /or Edit".
Select the mount point (usually /, but if using separate partitions for /home, you can as well).

And then set the filesystem type. (It will say do not use partition, simply click on it and ,strangely, the normal default filesystem type ext4, is way up at the top of the list.)

If you have swap, you can leave it be.
The installer will find it, without you needing to do anything about it.

Ok and will this login screen show?
  My Computer does not support some unity stuff.

[IMG]http://i1-news.softpedia-static.com/images/news2/Ubuntu-12-04-LTS-Will-Get-Chameleonic-Login-Screen-2.jpg[/IMG]

---

### Post by LastDino on 2014-05-07
It would be easier to answer that if you tell us your computer specs.

---

### Post by braydon2 on 2014-05-08
> **LastDino said:**
> It would be easier to answer that if you tell us your computer specs.

POS Dell Tower. Had Win XP, Pre-Installed 1 HDD 120GB, Installed 2 500GB HDDs' Unkown But ok Graphics card. Doesn't support unity for ubuntu.

CD Drive(Supports Big and Small Disks.)(No DVD-ROM.)
Floppy Disk Area.
1 Free Space for ADDITIONAL Item(s)
Graphics Card: PROBABLY Nvidia /OR A VERY OLD AMD.

---

### Post by deadflowr on 2014-05-08
> **braydon2 said:**
> POS Dell Tower. Had Win XP, Pre-Installed 1 HDD 120GB, Installed 2 500GB HDDs' Unkown But ok Graphics card. Doesn't support unity for ubuntu.

CD Drive(Supports Big and Small Disks.)(No DVD-ROM.)
Floppy Disk Area.
1 Free Space for ADDITIONAL Item(s)
Graphics Card: PROBABLY Nvidia /OR A VERY OLD AMD.

So you seem to be running something.
Though it seems to be missing some info.
Preferably CPU and RAM size would help.

But anyway, is this, as the screenie shows, a VM? (Virtualbox)

---

### Post by kansasnoob on 2014-05-08
> **braydon2 said:**
> POS Dell Tower. Had Win XP, Pre-Installed 1 HDD 120GB, Installed 2 500GB HDDs' Unkown But ok Graphics card. Doesn't support unity for ubuntu.

CD Drive(Supports Big and Small Disks.)(No DVD-ROM.)
Floppy Disk Area.
1 Free Space for ADDITIONAL Item(s)
Graphics Card: PROBABLY Nvidia /OR A VERY OLD AMD.

I have managed to install Ubuntu on hardware that won't run Unity by choosing Install Ubuntu from the Advanced Welcome page:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

Then be absolutely certain NOT to select auto-login when you enter your username and password.

After the installation completes and you boot the new OS the first time, once you get to the login screen you can press Ctrl + Alt + F1 which will open a terminal and type:

```
sudo apt-get install gnome-panel
```

Press enter and follow the prompts. When the package installation is complete you can just:

```
sudo reboot
```

And then when the login screen appears again just [click on the GNOME foot next to your username]("http://ubuntuforums.org/attachment.php?attachmentid=250349&d=1392455047") and [select GNOME FLashback (Metacity)]("http://ubuntuforums.org/attachment.php?attachmentid=250350&d=1392455047") as the desired session.

Or you could install Lubuntu or Xubuntu instead - it's all a matter of choice.

---

### Post by braydon2 on 2014-05-08
> **kansasnoob said:**
> I have managed to install Ubuntu on hardware that won't run Unity by choosing Install Ubuntu from the Advanced Welcome page:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

Then be absolutely certain NOT to select auto-login when you enter your username and password.

After the installation completes and you boot the new OS the first time, once you get to the login screen you can press Ctrl + Alt + F1 which will open a terminal and type:

```
sudo apt-get install gnome-panel
```

Press enter and follow the prompts. When the package installation is complete you can just:

```
sudo reboot
```

And then when the login screen appears again just [click on the GNOME foot next to your username]("http://ubuntuforums.org/attachment.php?attachmentid=250349&d=1392455047") and [select GNOME FLashback (Metacity)]("http://ubuntuforums.org/attachment.php?attachmentid=250350&d=1392455047") as the desired session.

Or you could install Lubuntu or Xubuntu instead - it's all a matter of choice.


Ok thanks! Also do you thanks you could help me with this?  [http://ubuntuforums.org/showthread.php?t=2222912](http://ubuntuforums.org/showthread.php?t=2222912)

---

