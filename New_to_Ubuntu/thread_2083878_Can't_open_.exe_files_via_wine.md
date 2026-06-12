---
title: "Can't open .exe files via wine"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by kupokupo on 2012-11-13
Hey guys, I'm a bit of a Linux noob, but so far I've tried to make it. I had a bunch of problems with the Windows Ubuntu (the one that installs under your windows copy), so I reinstalled the official Ubuntu and removed Windows 7. I've had a lot of problems (due to my inexperience), but I've researched them and fixed them generally. So far, it's okay except I'm having troubles with wine.

I downloaded wine several times actually, and I even reinstalled Ubuntu again just to make sure. I followed generic instructions in general, and ones that had people saying it worked for them. However, if you need a reference, I followed this video for my last wine installation (after I reinstalled Ubuntu). [http://www.youtube.com/watch?v=aSQt9qXduqU](http://www.youtube.com/watch?v=aSQt9qXduqU)
The only difference I had was at around 3:43, when he accepts the terms after (original command was sudo apt-get install wine1.3). At that point, I had the last few lines similar (ldconfig deferred process taking place), but I didn't have the message that said "All done, no errors", and that little part. I didn't pay much attention to it, as the last line was the same, but should I have?

Then, after following all those instructions, it seemed like it worked, except now when I try to open .exe files (right click and click on Wine Windows Program Loader), nothing happens. Like, nothing happens at all. I click on it and I wait and nothing pops up or anything. Is there something I'm doing wrong? To be specific, I was trying to load the League of Legends .exe file, but I also had a problem with the Spotify Installer .exe file, so I don't think it's the files themselves.

tl;dr clicking on .exe files and opening them on Wine Windows Program Loader, and nothing happens at all. How do I get it to run?

Sorry if I was a bit confusing, I can restate my question if needed. All help is greatly appreciated!

EDIT: okay, the problem is that wine thinks i'm running ubuntu in 32 bit when i'm using 64 bit. trying to figure it out now

---

### Post by monkeybrain2012 on 2012-11-13
cd into the directory where your exe file is (e.g if it is on the desktop, in the terminal type "cd Desktop" without quotes, note the capital D)
then type "wine yourprogram.exe" where yourprogram.exe is the name of your .exe file and see what the output is.

---

### Post by kupokupo on 2012-11-13
> **monkeybrain2012 said:**
> cd into the directory where your exe file is (e.g if it is on the desktop, in the terminal type "cd Desktop" without quotes, note the capital D)
then type "wine yourprogram.exe" where yourprogram.exe is the name of your .exe file and see what the output is.

ok so I moved it to Desktop just in case, and I ran it, and this is what I got.

> Log file is being written to C:\users\kupo\Temp\LeagueofLegends.exe.log
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
*** About to try file format org.eclipse.swt.internal.image.WinBMPFileFormat
*** Created newinstance for WinBMP
*** About to try file format org.eclipse.swt.internal.image.GIFFileFormat
*** Created newinstance for GIF
*** About to try file format org.eclipse.swt.internal.image.WinICOFileFormat
*** Created newinstance for WinICO
*** About to try file format org.eclipse.swt.internal.image.JPEGFileFormat
*** Created newinstance for JPEG
*** About to try file format org.eclipse.swt.internal.image.PNGFileFormat
*** Created newinstance for PNG
Exception in thread "LibgcjInternalFinalizerThread" java.lang.NullPointerException
   at 0x00a069ce (Unknown Source)
   at 0x00a06ed2 (Unknown Source)
   at 0x00a06f83 (Unknown Source)
   at 0x009dc15d (Unknown Source)
   at 0x009d910d (Unknown Source)
   at 0x00a3f93d (Unknown Source)
   at 0x009cb512 (Unknown Source)
   at 0x00a3ea77 (Unknown Source)
   at 0x7b83b8ed (Unknown Source)
   at 0x7bc8f1d9 (Unknown Source)
   at 0x7bc77019 (Unknown Source)
   at 0x7bc76feb (Unknown Source)
   at 0x7bc775f1 (Unknown Source)
   at 0x7bc79560 (Unknown Source)
   at 0x7bc79780 (Unknown Source)
   at 0xdeadbaba (Unknown Source)
   at 0x00a499e7 (Unknown Source)
   at 0x00a4a8e6 (Unknown Source)
   at 0x00a0f6c0 (Unknown Source)
   at 0x00a4a4bc (Unknown Source)
   at 0x00aa44c5 (Unknown Source)
   at 0x7bc76f9c (Unknown Source)
   at 0x7bc79b19 (Unknown Source)
   at 0x7bc76f7a (Unknown Source)
   at 0x7bc7fcc4 (Unknown Source)
   at 0xf7602d48 (Unknown Source)
err:seh:setup_exception_record stack overflow 1936 bytes in thread 0009 eip 7bc3eeef esp 00ef0ba0 stack 0xef0000-0xef1000-0x10f0000


---

### Post by monkeybrain2012 on 2012-11-13
How did you install Ubuntu?

---

### Post by kupokupo on 2012-11-13
> **monkeybrain2012 said:**
> How did you install Ubuntu?

At first, I used the Windows Installer thing, but I removed that completely.

The version I'm using right now - I went to the Ubuntu website and burned the .iso onto a DVD (had to use a program for this). Then, I started the computer up and did the regular installation (and replaced Windows 7)

---

### Post by monkeybrain2012 on 2012-11-13
> **kupokupo said:**
> At first, I used the Windows Installer thing, but I removed that completely.

The version I'm using right now - I went to the Ubuntu website and burned the .iso onto a DVD (had to use a program for this). Then, I started the computer up and did the regular installation (and replaced Windows 7)

Ok, check this out

[http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so](http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so)

---

### Post by kupokupo on 2012-11-13
> **monkeybrain2012 said:**
> Ok, check this out

[http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so](http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so)

Oh, I think that's in the .wine folder. 

Yeah, it's at: /home/kupo/.wine/dosdevices/c:/users/kupo/Temp

inside there is the .exe.log file.

EDIT: i didn't ask for it to be there though, all I did was just try and run the .exe from desktop.

---

### Post by monkeybrain2012 on 2012-11-13
Sorry, I edited my post, check the link which seems to describe your problem.

---

### Post by kupokupo on 2012-11-13
> **monkeybrain2012 said:**
> Sorry, I edited my post, check the link which seems to describe your problem.

ok so i'm following the answer (because the question's solution is a bit confusing, unless i should follow that).

I tried:

> wget [https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%7Eppa2_all.deb)
sudo dpkg -i getlibs_2.06-0ubuntu1~ppa2_all.deb

I got a 404 error though, this is it exactly.
> --2012-11-13 18:30:52--  [https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%6Eppa2_all.deb](https://launchpad.net/~jcollins/+archive/jaminppa/+build/1482994/+files/getlibs_2.06-0ubuntu1%6Eppa2_all.deb)
Resolving launchpad.net (launchpad.net)... 91.189.89.223, 91.189.89.222
Connecting to launchpad.net (launchpad.net)|91.189.89.223|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-11-13 18:30:53 ERROR 404: Not Found.

I'm a real noob at this so if I'm missing something obvious, just tell me. When clicking on the question's solution, I just get linked to a wine1.5 and I couldn't see a straightforward solution and I wasn't sure if I should follow that.

EDIT: the website he linked to to install getlibs has the same command as well. what should i do?

---

### Post by monkeybrain2012 on 2012-11-13
I don't know, I clicked that link and it offered to download the deb so it works, maybe you can try again? Once download you can just install the deb by right clicking. The guy who posted the original solution was making it unnecessarily cryptic for new users with wget and dpkg -i and what not

Basically, download and install glib_2.06 which is a deb package. 

Then follow the steps in installing 32 bit library and creating the symbolic link.

Seems that wine thinks that you are running 32 bit machine for some reasons.


EDITED: BTW if you want to install a .deb with the command "sudo dpkg -i .." you need to first cd into the directory where it is, so if it is on the desktop, you need to run 'cd Desktop'. This is a general rule: you have to do things in the correct directory.

---

### Post by kupokupo on 2012-11-13
> **monkeybrain2012 said:**
> I don't know, I clicked that link and it offered to download the deb so it works, maybe you can try again? Once download you can just install the deb by right clicking. The guy who posted the original solution was making it unnecessarily cryptic for new users with wget and dpkg -i and what not

Basically, download and install glib_2.06 which is a deb package. 

Then follow the steps in installing 32 bit library and creating the symbolic link.

Seems that wine thinks that you are running 32 bit machine for some reasons.


EDITED: BTW if you want to install a .deb with the command "sudo dpkg -i .." you need to first cd into the directory where it is, so if it is on the desktop, you need to run 'cd Desktop'. This is a general rule: you have to do things in the correct directory.

i got an error in the second part.

> The following i386 packages will be installed: gnome-keyring:i386
Continue [Y/n]? y
Downloading ...
Installing libraries ...
cp: target `/usr/lib32/' is not a directory
Copying files failed - run getlibs with "sudo getlibs" or as root

it worked fine the second time, but now i'm trying to install the 32 bit library, and after it worked for a while, when it tries to install it, i get an error (even though i did sudo getlibs from the beginning).

i tried this twice (sudo getlibs -p gnome-keyring:i386)

---

### Post by monkeybrain2012 on 2012-11-13
I was going to tell you to symlink /usr/lib32 to /usr/lib or creating /usr/lib32. But there seems to be an easier way from the wine forum on this site.
 
Forget about the above, and install "ia32-libs-multiarch" from software center and run your exe file in the terminal again and see the outputs.

---

### Post by kupokupo on 2012-11-13
> **monkeybrain2012 said:**
> I was going to tell you to symlink /usr/lib32 to /usr/lib or creating /usr/lib32. But there seems to be an easier way from the wine forum on this site.
 
Forget about the above, and install "ia32-libs-multiarch" from software center and run your exe file in the terminal again and see the outputs.

I searched it up, and I have it installed already apparently (except for the add-ons, the only add-on I have is Samba nameservice and authentication integration plugins).

---

### Post by monkeybrain2012 on 2012-11-13
Let's try 

sudo mkdir /usr/lib32 

Then install the 32-bit library.

---

### Post by kupokupo on 2012-11-13
> **monkeybrain2012 said:**
> Let's try 

sudo mkdir /usr/lib32 

Then install the 32-bit library.

ugh. it said file exists for both. here's what i got:

> kupo@kupo:~$ sudo mkdir /usr/lib32
[sudo] password for kupo: 
mkdir: cannot create directory `/usr/lib32': File exists
kupo@kupo:~$ sudo getlibs -p gnome-keyring:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic wine-gecko1.4
  wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
The following i386 packages will be installed: gnome-keyring:i386
Continue [Y/n]? y
Downloading ...
Installing libraries ...
kupo@kupo:~$ sudo mkdir -p /usr/lib/i386-linux-gnu/pkcs11/
kupo@kupo:~$ sudo ln -s /usr/lib32/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so
ln: failed to create symbolic link `/usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so': File exists


HOWEVER, when i ran cd Desktop and the .exe program via terminal, I get the same error message, but it does not have "p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory" (doesn't have this anymore) - I think the file is installed/exists.

I still have this though:

> kupo@kupo:~/Desktop$ wine LeagueofLegends.exe
Log file is being written to C:\users\kupo\Temp\LeagueofLegends.exe.log
*** About to try file format org.eclipse.swt.internal.image.WinBMPFileFormat
*** Created newinstance for WinBMP
*** About to try file format org.eclipse.swt.internal.image.GIFFileFormat
*** Created newinstance for GIF
*** About to try file format org.eclipse.swt.internal.image.WinICOFileFormat
*** Created newinstance for WinICO
*** About to try file format org.eclipse.swt.internal.image.JPEGFileFormat
*** Created newinstance for JPEG
*** About to try file format org.eclipse.swt.internal.image.PNGFileFormat
*** Created newinstance for PNG
Exception in thread "LibgcjInternalFinalizerThread" java.lang.NullPointerException
   at 0x00a069ce (Unknown Source)
   at 0x00a06ed2 (Unknown Source)
   at 0x00a06f83 (Unknown Source)
   at 0x009dc15d (Unknown Source)
   at 0x009d910d (Unknown Source)
   at 0x00a3f93d (Unknown Source)
   at 0x009cb512 (Unknown Source)
   at 0x00a3ea77 (Unknown Source)
   at 0x7b83b8ed (Unknown Source)
   at 0x7bc8f1d9 (Unknown Source)
   at 0x7bc77019 (Unknown Source)
   at 0x7bc76feb (Unknown Source)
   at 0x7bc775f1 (Unknown Source)
   at 0x7bc79560 (Unknown Source)
   at 0x7bc79780 (Unknown Source)
   at 0xdeadbaba (Unknown Source)
   at 0x00a499e7 (Unknown Source)
   at 0x00a4a8e6 (Unknown Source)
   at 0x00a0f6c0 (Unknown Source)
   at 0x00a4a4bc (Unknown Source)
   at 0x00aa44c5 (Unknown Source)
   at 0x7bc76f9c (Unknown Source)
   at 0x7bc79b19 (Unknown Source)
   at 0x7bc76f7a (Unknown Source)
   at 0x7bc7fcc4 (Unknown Source)
   at 0xf757cd48 (Unknown Source)
err:seh:setup_exception_record stack overflow 1936 bytes in thread 0009 eip 7bc3eeef esp 00ef0ba0 stack 0xef0000-0xef1000-0x10f0000


sorry, for some reason i run into problems with everything i try. this is greatly appreciated!

---

### Post by monkeybrain2012 on 2012-11-13
Hmm... sorry, I am afraid this is beyond my ability to help. I don't use wine often and only has it installed on my 32 bit laptop. I didn't even know it has a problem on 64 bit machines until I read your thread. 

Hopefully someone more knowledgeable will help you out. 

Check out the wine subforum, you may find something useful there.

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

Good luck!

---

### Post by kupokupo on 2012-11-13
> **monkeybrain2012 said:**
> Hmm... sorry, I am afraid this is beyond my ability to help. I don't use wine often and only has it installed on my 32 bit laptop. I didn't even know it has a problem on 64 bit machines until I read your thread. 

Hopefully someone more knowledgeable will help you out. 

Check out the wine subforum, you may find something useful there.

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

Good luck!

thank you so much, you've helped a bunch actually. since i don't have much on my computer right now, i'm probably just going to reinstall ubuntu except in 32 bit mode. hopefully it'll work then. thanks!

---

### Post by jerome1232 on 2012-11-13
Always, always check WineHQ's appdb when you are trying to run a program under wine.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141)

I see it's mentioned that there are problems runing it under 64 bit and a 32 bit chroot fixes the problem

---

### Post by kupokupo on 2012-11-13
> **jerome1232 said:**
> Always, always check WineHQ's appdb when you are trying to run a program under wine.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141)

I see it's mentioned that there are problems runing it under 64 bit and a 32 bit chroot fixes the problem

thanks for the clarification, i see the problem now. i started using the 32 bit chroot after searching up how to do it, but for some reason i entered the first command in the terminal and it said something like ldconfig deferred processing now taking place. i did the next command and nothing happened..

regardless, i think i'll just install 32 bit instead, it seems way easier. my computer is new enough to have 64 bit but it seems too much to sacrifice for just speed. thank you though!

---

