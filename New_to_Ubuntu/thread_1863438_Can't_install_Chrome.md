---
title: "Can't install Chrome?"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Nutopia on 2011-10-17
Hi,

Version 11.10

I'm trying to install Google Chrome. I downloaded the 32bit deb package from Chrome's website. When I try to run it, the Ubuntu Software Center opens up with the following error: "The file /home/.../google-chrome-stable_current_i386.deb could not be opened"

I've tried re downloading the package. I also am not getting a hit for Chrome when I do a search directly in Software Center. 

Any idea what's going on here? It used to work in previous versions of Ubuntu.

---

### Post by Nutopia on 2011-10-17
Ok, I ran the install through terminal using

sudo dpkg -i

but now, when I open Chrome it crashes immediately.

---

### Post by alphacrucis2 on 2011-10-17
You could try chromium instead. It's chrome without the google stuff. I think chromium is in the repos.

---

### Post by kc1di on 2011-10-17
> **Nutopia said:**
> Ok, I ran the install through terminal using

sudo dpkg -i

but now, when I open Chrome it crashes immediately.

run the following command from a terminal Chrome will then work.
sudo apt-get install libnspr4-0d libnss3-1d libxss1 libcurl3

---

### Post by Nutopia on 2011-10-17
Chromium doesn't work either - same problem. 

I ran that command - it didn't do anything. I'm all up to date with those files:

libcurl3 is already the newest version.
libcurl3 set to manually installed.
libnss3-1d is already the newest version.
libnss3-1d set to manually installed.
libxss1 is already the newest version.
libnspr4-0d is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by powersurge360 on 2011-10-17
In order to install chrome (and a few other troublesome packages) I ran

sudo dpkg -i <path_to_deb_file>

sudo apt-get install -f

And it worked. Maybe try that?

---

### Post by Nutopia on 2011-10-17
> **powersurge360 said:**
> In order to install chrome (and a few other troublesome packages) I ran

sudo dpkg -i <path_to_deb_file>

sudo apt-get install -f

And it worked. Maybe try that?

I have chrome installed using the first command. the second command shows that everything is already up to date.

---

### Post by powersurge360 on 2011-10-17
When you boot chrome from the commandline (with the command google-chrome) what does it say? Please post output.

---

### Post by Nutopia on 2011-10-17
well, this is greek to me:

[3:3:44881060370:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
Inconsistency detected by ld.so: dl-open.c: 597: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

---

### Post by powersurge360 on 2011-10-17
A quick google search found this:

[http://code.google.com/p/chromium/issues/detail?id=91962](http://code.google.com/p/chromium/issues/detail?id=91962)

Are you using the proper version of chrome for your OS? Maybe double check that you installed the 32-bit if you're on 32-bit or 64-bit if you're on 64-bit.

---

### Post by Nutopia on 2011-10-17
> **powersurge360 said:**
> A quick google search found this:

[http://code.google.com/p/chromium/issues/detail?id=91962](http://code.google.com/p/chromium/issues/detail?id=91962)

Are you using the proper version of chrome for your OS? Maybe double check that you installed the 32-bit if you're on 32-bit or 64-bit if you're on 64-bit.

Yeah, I found that page, too. I don't quite understand what their describing as the solution, though. Much less what to do next 	:confused:

---

### Post by powersurge360 on 2011-10-17
And you've double checked that you have the right package for your architecture?

I'm afraid I'm tapped at this point if that doesn't work. The best I can recommend is to try chromium or midori in the mean time.

---

### Post by Nutopia on 2011-10-17
Yeah, I have the right package. I tried the 64-bit one just for fun and it said 'wrong architecture'

Edit to add:
I'm getting the same problem with Chromium

---

### Post by powersurge360 on 2011-10-17
One last thing, does:

locate libsoftokn3.so

find anything? It could be that you have to install that but I don't know.

---

### Post by Nutopia on 2011-10-17
It is installed here:

/usr/lib/firefox-7.0.1/libsoftokn3.so

---

### Post by powersurge360 on 2011-10-17
That's likely the culprit. I've got one in

/usr/lib/x86_64-linux-gnu/nss/libsoftokn3.so

and one in 

/usr/lib/i386-linux-gnu/nss/libsoftokn3.so

I'll see what I can dig up about installing it.

---

### Post by powersurge360 on 2011-10-17
Hmmm... Not finding anything, but perhaps you could just make a symlink to the one in your firefox directory.

sudo ln -s <complete_path_to_existing> /usr/lib/i386-linux-gnu/nss/libsoftokn3.so

^ That *may* fix it, and while it couldn't hurt, it's probably not a satisfactory solution for the long term. If it works, awesome, but if someone else smarter comes along and tells you that this was a Bad Idea, you should probably listen.

---

### Post by Nutopia on 2011-10-17
That's odd - it says the file exists. I did another search from root and the search still didn't find it. I went straight the directory and it is listed there. 

This is really odd... I do appreciate your help, though!

---

### Post by powersurge360 on 2011-10-17
Well, I'm going to give you a brief explanation of what the problem is so you are informed going forward because I am not comfortable telling you to play with the permissions of a shared object.

----SKIP IF YOU JUST WANT TO FUTZ WITH PERMISSIONS----
When programs are compiled some things are statically linked, ie become a non-removable part of the binary and other things are dynamically linked. This creates a shared object. A .so.

Chrome is evidently trying to link against your shared object, but is unable to because of (probably) permissions. It doesn't have to rights to either read or execute (I don't know which of the two it needs)
----END SKIP----

So, running

sudo chmod a+rwx <complete_path_to_existing>

might fix it, and I would probably do it if it were my system. That being said, there might be some unexpected consequences later on down the line, so do it at your own risk. It will *probably* be fine to do this.

---

### Post by Nutopia on 2011-10-17
Thanks for the explanation. I do have a basic understanding of things, so I was comfortable taking your suggestion. I actually tried changing the permissions earlier, hehe. 

Still no luck - same error. 

My 11.10 upgrade is basically FUBAR. I have to run in gnome just to do anything. When I try to use Ubuntu or Ubuntu 2d, I don't get any sort of meaningful menubar at the top nor that Unity Launcher panel. I tried enabling them through the graphics settings... nothing.

I'm doing a manual backup of basically the entire system. I used this system for programming a series of LAMP based websites over the past few years, and now I'm looking at wiping it all out. I'm definitely not happy about that... it's going to be a lot of work to get things set up again, if I even remember everything I did. This really sucks. I hadn't updated Ubuntu in ages since the first version of 10, and now I end up with this. Grrr.

---

### Post by Rob Broccoli on 2011-10-19
I'm having the exact same errors as Nutopia.   I had Chromium installed  and working well under Natty.  After the upgrade to Oneiric, Chromium  would stall when trying to load some pages (I think, but am not sure,  that the problem was with encrypted pages).  Then today (two days later)  Chromium stopped working entirely.  Same error that Nutopia had.
      I'm posting because I have one more crumb of information that I  can't figure out, but may help someone smarter than me figure this out.   The original error was:

[FONT=Fixedsys][3:3:4662708576:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
Inconsistency detected by ld.so: dl-open.c: 597: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

[FONT=Arial]When I added a symlink to /usr/lib, Chromium still died, but with a different error.  The symlink was...

[FONT=Fixedsys] ln -s /usr/lib/x86_64-linux-gnu/nss/libsoftokn3.so /usr/lib/libsoftokn3.so
[FONT=Arial]
(Yes I have a 64-bit system and the Chromium 64 bit package)
The new error was:

[FONT=Fixedsys][3:3:5060188369:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: NSS error code: -8023
Inconsistency detected by ld.so: dl-open.c: 597: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

[FONT=Arial]Maybe NSS error code -8023 means something to somebody?

Other things I've tried:  re-install via Synaptic.  Complete removal and install via Synaptic.  Direct download the package from Google.  Removed all chromium files in my .config directory.  Logged in as a new user.  Changed permissions on ALL occurrences of libsoftokn3.  No luck.  I'm stumped. 
 Fortunately Firefox is still working fine.
[/FONT][/FONT][/FONT][/FONT]
[/FONT][/FONT]

---

### Post by Rob Broccoli on 2011-10-26
Update:  epiphany is crashing too, so it's not really a Chrome problem.  My best guess is that I somehow got a 32-bit library on my 64-bit machine, or maybe there's just a missing link in one of the libraries.  
      Wish I knew how to track down which library is causing the problem.  I used 'ldd' to find some missing dependencies in /usr/lib32, but fixing them didn't solve my problem.
    At this point, my system isn't quite fubar, but close enough that I'm seriously considering starting from scratch.

---

### Post by Rob Broccoli on 2011-10-28
Success!  Although I'm not sure exactly how.  After doing these reinstallations,  Chromium and Epiphany started working again:
"[FONT=Fixedsys]Reinstalled the following packages:
libgl1-mesa-dri (7.11-0ubuntu3)
libgl1-mesa-glx (7.11-0ubuntu3)
libglapi-mesa (7.11-0ubuntu3)
libgle3 (3.1.0-7)
libglib-perl (2:1.223-1build1)
libglib2.0-0 (2.30.0-0ubuntu4)
libglib2.0-data (2.30.0-0ubuntu4)
libglibmm-2.4-1c2a (2.30.0-0ubuntu1)
libglu1-mesa (7.11-0ubuntu3)[/FONT] 
"
And this is the page that helped me the most:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/859188](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/859188)

I screwed around with the NSS libraries for a long time, since that was where the original Chrome error pointed.  Nothing helped.  

But I noticed the other errors with Epiphany and other things seemed to point to a graphics library problem.  Hence the re-install of everything libGl  related.
I suspect that Wine might be at fault, since that uses a lot of 32-bit stuff.  As does Skype.  Before I did the reinstall above, I removed everything to do with Wine and Skype.  
But it is also possible that it was something to do with the MESA libraries-- I had recently installed fglrx (my Xorg log suggested that I needed it), then immediately removed it because it was causing all kinds of trouble. 

And P.S.-- Even though Chrome isn't crashing, it is still throwing this error:
ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied

---

### Post by Rob Broccoli on 2011-10-28
PS. ATTN: Moderator: I realize I have rather strayed from "Absolute Beginner Talk" and I doubt that I've helped the original poster with his problem. 
Is it possible my posts would more helpful in a different forum?  I spent many hours wrestling with this problem-- I really hope I can spare someone else the same struggle.

---

### Post by Rob Broccoli on 2011-10-28
It looks like it was  fglrx after all.  Something was wrong with the install/uninstall scripts for it:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/855943](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/855943)

It's probably fixed by now.  I must have been unlucky and gotten it at the time when the scripts were not working right.

---

### Post by brucealdridge on 2011-11-03
Thanks Rob, re-installing those fixed the issue for me

---

