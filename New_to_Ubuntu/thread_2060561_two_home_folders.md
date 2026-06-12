---
title: "two home folders"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by osprey2000 on 2012-09-20
When I go to Places  > Home Folder it opens fine but within that Home Folder there is another "Home Folder" with a padlock symbol attached to it. 
When i open that folder I get "Owner", when I open that one I get the same folders as was in the original Home Folder.

Could someone please explain what I've done, Google and reading the forums doesn't help


Many thanks

---

### Post by androssofer on 2012-09-20
> **osprey2000 said:**
> When I go to Places  > Home Folder it opens fine but within that Home Folder there is another "Home Folder" with a padlock symbol attached to it. 
When i open that folder I get "Owner", when I open that one I get the same folders as was in the original Home Folder.

Could someone please explain what I've done, Google and reading the forums doesn't help


Many thanks

are they identical? as in same files? and if you add a file to 1 it adds it to the other?

if you could. open a terminal and type:

```
cd
```

then type:

```
pwd
```

it should output something like:

```
/home/<username>
```

where <username> is your username...

and then do:

```
ls
```

this will list the files and folders...

if the home folder within that shows up with a turquoise colour, its called a syslink and would explain it.. if its now.. we'll research some more!

---

### Post by Bartender on 2012-09-20
Did you by chance re-install Ubuntu, using a different username/password?

I created two Home Folders by mistake a few years back.  I'm having difficulty remembering exactly what I did.  

I *think* what happened is this:  I originally installed Ubuntu manually, creating a separate Home Folder partition.  Then I reinstalled a newer version (manually, I believe) and forgot to direct the installer to format the Home partition.  On top of that, I used a different username/password.  

Or I may have just installed the newer version automatically, and it created a new Home inside the OS partition, ignoring the original Home partition.

I ended up with two Home Folders, one "owned" by my old username and the other by the new one.

---

### Post by osprey2000 on 2012-09-20
androssofer...Hi,

I did as you said and am going to try and post the result with this reply but the only touquoise file was JExpressUninstaller.jar and yes the two home files are identical.


Re..Bartender's suggestion, no there has been no re-install

---

### Post by Wim Sturkenboom on 2012-09-20
The padlock might imply that it was copied from a read-only medium (like CD). Did you ever put a backup back? If so, you did it incorrectly ;)

---

### Post by osprey2000 on 2012-09-21
> **Wim Sturkenboom said:**
> The padlock might imply that it was copied from a read-only medium (like CD). Did you ever put a backup back? If so, you did it incorrectly ;)

Wim Sturkenboom,
This may well have happened and if that's the problem do you have any idea as to how to correct it.
My thoughts are in two parts;
1. Work around it
2. In a few months I will be doing a clean install of 12.04 and the problem should go away

---

### Post by drmrgd on 2012-09-21
I'm curious about that 'home' folder that's inside of your home folder.  What are the contents of that folder, and who owns those folders?

```
ls -l ~/
```

```
ls -l ~/home
```

If you find the second home directory inside of /home/owner/home/, then that may be the source of your duplication.  Although I can't imagine why it's been mapped to this location, and I agree with the above poster that there could be a symlink somewhere yet not found that's causing this.

---

### Post by steeldriver on 2012-09-21
might be worth something like

```
find ~ -type l -exec ls -l "{}" \; 2>/dev/null
```

to find / print any symlinks below ~

---

### Post by osprey2000 on 2012-09-21
Hi,

OK first I'm going to post the terminal output/responses to the two previous suggestions.

The I'll try ro post some screen shots of what happens

---

### Post by osprey2000 on 2012-09-21
owner@zeus:~$ ls -l ~/
total 620
drwxr-xr-x  2 owner owner   4096 2011-03-12 15:29 bin
drwxr-xr-x  5 owner owner   4096 2012-09-21 08:03 Desktop
drwx------  9 owner owner   4096 2012-09-21 13:02 Dropbox
drwxr-xr-x  3 root  root    4096 2011-06-20 06:41 Duplicate folder harmless leave alone
drwxr-xr-x  3 owner owner   4096 2012-08-29 15:51 dvdrip-data
drwxr-xr-x  2 owner owner   4096 2012-05-16 09:17 dwhelper
-rw-r--r--  1 owner owner 596272 2011-06-17 12:05 JExpressUninstaller.jar
drwx------  2 owner owner   4096 2011-08-15 17:48 My Music
drwxr-xr-x 19 owner owner   4096 2012-09-21 14:41 Pictures Large File
drwxr-xr-x  2 owner owner   4096 2012-09-20 08:52 Videos
owner@zeus:~$ ls -l ~/home
ls: cannot access /home/owner/home: No such file or directory
owner@zeus:~$ ls -l ~/home
ls: cannot access /home/owner/home: No such file or directory
owner@zeus:~$ find ~ -type l -exec ls -l "{}" \; 2>/dev/null
lrwxrwxrwx 1 owner owner 63 2011-03-12 15:21 /home/owner/bin/opera-widget-mobile-ebook-reader -> /home/owner/.opera-widgets/bin/opera-widget-mobile-ebook-reader
lrwxrwxrwx 1 owner owner 61 2011-03-12 15:00 /home/owner/bin/opera-widget-google-translator -> /home/owner/.opera-widgets/bin/opera-widget-google-translator
lrwxrwxrwx 1 root root 48 2012-09-20 00:46 /home/owner/Duplicate folder harmless leave alone/owner/.local/share/ubuntuone/Purchased from Ubuntu One -> /home/owner/.ubuntuone/Purchased from Ubuntu One
lrwxrwxrwx 1 root root 49 2012-09-20 00:46 /home/owner/Duplicate folder harmless leave alone/owner/.adobe/Acrobat/9.0/Cert/curl-ca-bundle.crt -> /opt/Adobe/Reader9/Reader/Cert/curl-ca-bundle.crt
lrwxrwxrwx 1 root root 14 2012-09-20 00:46 /home/owner/Duplicate folder harmless leave alone/owner/.kde/tmp-zeus -> /tmp/kde-owner
lrwxrwxrwx 1 root root 18 2012-09-20 00:46 /home/owner/Duplicate folder harmless leave alone/owner/.kde/socket-zeus -> /tmp/ksocket-owner
lrwxrwxrwx 1 root root 23 2012-09-20 00:46 /home/owner/Duplicate folder harmless leave alone/owner/.kde/cache-zeus -> /var/tmp/kdecache-owner
lrwxrwxrwx 1 root root 23 2012-09-20 00:47 /home/owner/Duplicate folder harmless leave alone/owner/.pulse/ae5ac84ad884e4e781e046a54d344bea-runtime -> /tmp/pulse-7O79P0PsLB7u
lrwxrwxrwx 1 root root 10 2012-09-20 00:46 /home/owner/Duplicate folder harmless leave alone/owner/.googleearth/instance-running-lock -> /proc/1703
lrwxrwxrwx 1 root root 48 2012-09-20 00:54 /home/owner/.local/share/ubuntuone/Purchased from Ubuntu One -> /home/owner/.ubuntuone/Purchased from Ubuntu One
lrwxrwxrwx 1 owner owner 49 2012-09-21 14:17 /home/owner/.adobe/Acrobat/9.0/Cert/curl-ca-bundle.crt -> /opt/Adobe/Reader9/Reader/Cert/curl-ca-bundle.crt
lrwxrwxrwx 1 owner owner 70 2012-09-20 03:08 /home/owner/Pictures Large File/2011 Spain  Morocco./Morocco slide show/x3.JPG -> /home/owner/Pictures/2011 Spain  Morocco./Todra Marrakesh/S73F0014.JPG
lrwxrwxrwx 1 owner owner 14 2011-01-22 11:53 /home/owner/.kde/tmp-zeus -> /tmp/kde-owner
lrwxrwxrwx 1 owner owner 18 2011-01-22 11:53 /home/owner/.kde/socket-zeus -> /tmp/ksocket-owner
lrwxrwxrwx 1 owner owner 23 2011-01-22 11:53 /home/owner/.kde/cache-zeus -> /var/tmp/kdecache-owner
lrwxrwxrwx 1 owner owner 46 2012-09-21 13:02 /home/owner/.config/google-chrome/SingletonSocket -> /tmp/.com.google.Chrome.SKPLvQ/SingletonSocket
lrwxrwxrwx 1 owner owner 19 2012-09-21 13:02 /home/owner/.config/google-chrome/SingletonCookie -> 5577492321888397534
lrwxrwxrwx 1 owner owner 9 2012-09-21 13:02 /home/owner/.config/google-chrome/SingletonLock -> zeus-1751
lrwxrwxrwx 1 owner owner 23 2012-09-21 13:01 /home/owner/.pulse/ae5ac84ad884e4e781e046a54d344bea-runtime -> /tmp/pulse-v61eqXqmpWaR
lrwxrwxrwx 1 owner owner 10 2012-05-18 09:14 /home/owner/.googleearth/instance-running-lock -> /proc/1703
owner@zeus:~$ ^C
owner@zeus:~$ file:///home/owner/Terminl%20results.doc

---

### Post by osprey2000 on 2012-09-21
Sorry I didn't get that last post right, so I just copied andd pasted into the body of the post.

Here are three screen shots
When I click on "Home Folder I get 3.png
When I click on "home" I get 4.png
When I click on Owner I get 5.png

You will see that now there is nothing in that last folder ( Owner) I removed/deleted all those files as a kind of work-around.

I am still very new to Ubuntu and despite reading a lot am still likely to make mistakes


many thanks

---

### Post by osprey2000 on 2012-09-21
Sorry forgot to mention who owns those folders

The "Home"  folder with the padlock is owned by Root

The " Owner" folder within that Home folder is owned by Owner

---

### Post by drmrgd on 2012-09-21
I'm a bit confused.  In the first screenshot you took above, there was a folder in /home/owner called home.  However, when you ran the 'ls -l' of your home directory, it threw an error because it's not there anymore.  Where did it go?  Then, when you took the next screenshots, suddenly there is a 'Home' folder in your home directory that wasn't there before and doesn't show up when you list the directories from the commandline.  I'm also not seeing "Duplicate Folder...." in the screenshot, but I do see that in your commandline listing.  How many user accounts do you have on this computer?  Something is not matching, but it's not clear what that is.

---

### Post by osprey2000 on 2012-09-21
Just the one user

---

