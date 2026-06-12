---
title: "Installing and patching Unreal Tournament 2004"
date: 2006-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by kahrn on 2006-08-18
This article covers how to install Unreal Tournament 2004 under Ubuntu (6.06, Dapper Drake), however it applies to pretty much all other distributions. It also covers how to patch it, and how to install the additional Mega Pack content.

Update @ 29/8/06 - It is possible to install the mega pack content without Wine if you prefer. See the 1st reply to this thread by stuart.crouch.

To follow this guide you'll need a legal copy of Unreal Tournament 2004, the latest patch, and the UT2004 Mega Pack Install (UT2004MegaPack.exe). You will also need to have wine installed to run the mega pack install, for more information on that search the forums or run automatix. You will also need to have glx enabled.

Ok, lets start out with installing Unreal Tournament 2004.
Insert the UT2k4 DVD into your DVD drive, and wait for ubuntu to mount it, and if it doesn't mount, mount it yourself (e.g. *sudo mount /dev/cdrom /media/cdrom0 -t iso9660* ).
Once the dvd is mounted, open a terminal and navigate to it, and then run the shell install script.

```
cd /media/cdrom0
sudo sh linux-installer.sh
```

You should be presented with an install program, leave all the defaults and skip through it. Wait for the install to finish, and then continue following the article.

Once the install is complete, it is time to install the additional content from the megapack. This can be done by using wine to install it into a seperate directory, and then copying the content from that directory into */usr/local/games/ut2004*.

So go ahead and run UT2004MegaPack.exe. In my case I'll be installing it into *~/.wine/drive_c/temp/*. It is important we install the megapack content and THEN the patch.
```

wine UT2004MegaPack.exe
cd ~/.wine/drive_c/temp/
sudo cp -R * /usr/local/games/ut2004
rm -r ./*
```

Now the additional content has been installed, let's apply the patch. Decompress the path file (it should be a .bz2 or something similar) and then open a terminal to the uncompressed folder (UT2004-Patch).
Now we shall recursively copy the files and folders in the patch folder to the ut2004 folder.

```
cd UT2004-Patch
sudo cp -R * /usr/local/games/ut2004/
```

Now run ut2004, and go to the community section to check that you have the very latest version.

---

### Post by stuart.crouch on 2006-08-27
You dont need wine to install the megapack.  Its just a zip-exe.
Do this instead of the whole wine section and it will save you masses of time on the whole download wine, install wine, configure wine, run wine thing

Install ut2004 as above

Then instead of the wine commands do this -

```

mv ut2004megapack.exe ut2004megapack.zip
unzip ut2004megapack.zip
cd UT2004MegaPack
sudo cp -Rf *  /usr/local/games/ut2004
rm -r ./*

```

Then patch as above.

---

### Post by Hemmer on 2006-08-28
excellent! i didn't really want to put wine on - i have no other need for it

---

### Post by xxrealmsxx on 2006-10-14
It wont let me unmount the cd after I install off of disk 1 (I have the install cd's) what do i do?

---

### Post by xxrealmsxx on 2006-10-14
Ok fixed the problem by copying linux-installer.sh to the desktop and running it there.

thanks for the how to.

---

### Post by unknownkadath on 2006-10-28
Thanks!

A winner is YOU!:)

---

### Post by d3v1ant_0n3 on 2006-10-29
Well thanks:D :D  This guide works perfectly!

Got UT2004 installed, patched and running in ten minutes.

Unfortunately it runs like an arthritic dog on this machine, even with all the settings turned waaaaaay down. Bah.

---

### Post by finalbeta on 2006-10-29
Anyone knows if they are planning to ever release a patch for alsa sound? probably not, but I can hope :o

---

### Post by beastrace91 on 2008-12-25
So I really hate bumping an old thread but after installing UT2k4 it loaded up fine... how ever after running the command listed to patch the game I get this message now in terminal when trying to load the game:

[quote="My Terminal"]./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
[/quote]

Any idea how I can correct this missing file?

~Jeff

---

### Post by beastrace91 on 2008-12-26
I fixed the issue myself, running "sudo apt-get install libstdc++5" got the extra library it needed.

~Jeff

---

