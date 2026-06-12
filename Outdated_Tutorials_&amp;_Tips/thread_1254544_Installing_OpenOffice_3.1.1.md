---
title: "Installing OpenOffice 3.1.1"
date: 2009-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by scouser73 on 2009-08-31
Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m19_native_packed-1_en-US.9420**

You can remove the existing version of OpenOffice if you wish with this command: [B]sudo apt-get remove openoffice*.*
[/B]
Copy and paste **OOO310_m19_native_packed-1_en-US.9420** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb**

Once you've done that you'll find OpenOffice 3.1.1 in Office.

---

### Post by AlNaimi on 2009-08-31
Thanks scouser73
For more:
[http://webupd8.blogspot.com/2009/08/openofficeorg-311-released-downloads.html](http://webupd8.blogspot.com/2009/08/openofficeorg-311-released-downloads.html)

---

### Post by sports fan Matt on 2009-09-01
Downloaded it and its throwing up errors..cant run the writer or anything with it..just waiting for it to be updated.  Scouser's method works but its pretty much not going to work..anyone else confirm this?

---

### Post by mdebusk on 2009-09-02
> **sox fan Matt said:**
> Downloaded it and its throwing up errors..cant run the writer or anything with it..just waiting for it to be updated.  Scouser's method works but its pretty much not going to work..anyone else confirm this?

Same here. Got the following on Writer:

```
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
```

---

### Post by gradinaruvasile on 2009-09-02
Works just fine in 9.04.

---

### Post by Hagar Delest on 2009-09-02
Works fine also with xubuntu 8.04. Note that you don't need the copy/paste explained in first post. Easier to run a mere dpkg -i *.deb in each folder (/debs and /desktop-integration. With the terminal history yo udon't eve have to re-type the commands.

See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) You have to remove the installed version, it's incompatible with the Ubuntu version.

If still problems, try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by ishmael2k on 2009-09-02
I tried it also, no luck. Keeps throwing out errors. Removed it and going back to 3.0.

This is in 9.04

---

### Post by Hagar Delest on 2009-09-02
What errors exactly???

---

### Post by drs305 on 2009-09-02
Karmic 64-bit:  OOo_3.1.1_LinuxX86-64_install_en-US_deb.tar.gz

Worked for me, although I used the default install folder of /opt/openoffice.org3 after uninstalling my old OO package.

---

### Post by ishmael2k on 2009-09-02
> What errors exactly???

It opens up the document recovery box

"Due to an unexpected error OO crashed. All files you were working on will now be saved. The next time OO is launched your files will be recovered automatically."

Of course there are no files to recover because it has yet to be used. 

It then just loops saying the same thing each time I open it.

3.01 works fine.

I tried your method also with the same results.

???

---

### Post by ibutho on 2009-09-02
Works perfectly fine for me on Linux Mint 7 (Ubuntu 9.04), so its strange that others are having problems. Are you sure the old version was completely uninstalled?

---

### Post by ishmael2k on 2009-09-02
> **ibutho said:**
> Works perfectly fine for me on Linux Mint 7 (Ubuntu 9.04), so its strange that others are having problems. Are you sure the old version was completely uninstalled?

I believe so. I used Synaptic to do so and removed all instances of OO listed.

---

### Post by ishmael2k on 2009-09-02
OK I tried it one more time with the same exact results. I must be missing something but don't have time right now to mess with it.

Will re-do 3.01 until I free up a couple of hours.

---

### Post by mdebusk on 2009-09-03
> **Hagar de l'Est said:**
> If still problems, try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

This solved my problem. Thank you! :)

---

### Post by ImbaDaimon on 2009-09-03
Works for me (Ubuntu jaunty 9.04).

Ty a lot.

---

### Post by kogger on 2009-09-04
I had the same problem with crashing and weird document recovery, but resetting my profile fixed it. Thanks. =)

---

### Post by speedwell68 on 2009-09-05
I found the easiest way of ugrading to the latest OpenOffice is to install Ubuntu Tweak from GetDeb and the simply add the OpenOffice repository from there and then let the update manager do it's thing.

---

### Post by PascalGR on 2009-09-08
Seamlessly worked for me too (Ubuntu 9.04).

1) From Synaptics completely removed all openoffice.org packages
2) Deleted all directory structure .openoffice.org from the home directory
3) Installed all .deb files: sudo dpkg -i *.deb desktop-integration/*.deb

and voila!

---

### Post by fooman on 2009-09-09
> **speedwell68 said:**
> I found the easiest way of ugrading to the latest OpenOffice is to install Ubuntu Tweak from GetDeb and the simply add the OpenOffice repository from there and then let the update manager do it's thing.

i agree....using the repos will grab any future updates and unistalling any older versions will not be necessary.

heres a "how to" for upgrading via the launchpad repositories:

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

---

### Post by Micronaut on 2009-09-10
works here on Linux Mint 7. Had to reset profile to avoid the document recovery error.

---

### Post by waj1122 on 2009-09-10
[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

The above worked quick and easy on Xubuntu 9.04

Thank you for the post.

---

### Post by Lee Kaelin on 2009-09-13
Worked perfect for me! :)

Though its far easier to to run **dpkg -i *.deb** in each folder than follow the script in the first post. 

Installed perfectly on my Jaunty box, though I used 64bit to suit my install. 

Cheers for the heads up. :D

---

### Post by Hagar Delest on 2009-09-13
Indeed. And the commands are kept in the history. So you don't have even to retype them at next upgrade!

---

### Post by fsando on 2009-09-17
> **ishmael2k said:**
> OK I tried it one more time with the same exact results. I must be missing something but don't have time right now to mess with it.

Will re-do 3.01 until I free up a couple of hours.


Just had the same issue - but after a logout/login they disappeared - so it might be some settings it needs that are not registered yet.

I'm running ubuntu 8.10 intrepid

EDIT: Today the issue returned and there were no solution - had to return to 2.4

EDIT2: removed/renamed the folder ~/.openoffice.org
Restarted openoffice.org 3.1.1 it works (at least for now)

---

### Post by RedStarYellowSun on 2009-11-30
It works for me.
I'm using Ubuntu 9.10.
Unfortunately, I cannot update. It reports:
"Status
Checking for updates failed.

Description
Could not establish Internet connection update32.services.openoffice.org."

What is this?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by Hagar Delest on 2009-12-01
The internal check for updates in OOo has always been rather flaky. Better download the debs from the site when a new version has been released (every 3 months).

---

