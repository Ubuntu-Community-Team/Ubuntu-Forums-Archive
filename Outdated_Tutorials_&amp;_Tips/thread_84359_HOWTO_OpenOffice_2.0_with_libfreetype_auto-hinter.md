---
title: "HOWTO: OpenOffice 2.0 with libfreetype auto-hinter"
date: 2005-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by almann.goo on 2005-10-30
**Overview**
This weekend I decided to join the Ubuntu world and install Breezy on my system that was previously Fedora Core 3.  Overall I was quite happy with the install and after enabling the Autohinter via "dpkg-reconfigure fontconfig" I was quite happy that my GTK2/GNOME applications had fonts anti-aliased the way I like them (a lot like how Fedora looks).

One problem that I ran into however was that no matter what I configured, OpenOffice 2.0 still didn't quite look right.  Using Luxi as my default font, OpenOffice did anti-alias it, but it looked a little strange (and actually looked like my other GNOME applications before I enabled the libfreetype Autohinter).  Doing some searching on the forums and Google, my results seemed to indicate that the Ubuntu/Debian package of libfreetype enabled the bytecode interpreter that looks somewhat terrible on LCDs (I run a 20" LCD).  Other sources during this search indicated that no matter what fontconfig settings were made, OpenOffice used the bytecode interpreter if it was enabled.

**A Solution**
To get around this problem I decided to build a new DEB of the libfreetype package.  Overall not a terribly complex solution and may not in itself warrant a HOWTO, but since it wasn't trivial to fix I thought I should share my steps.  Disclaimer:  Although I have been using Linux for some time now, I am by no means an expert, especially on Ubuntu systems--so this may not be the best way to solve the problem so if you have a better one please let me know!

**Getting the Source Package**
Create a directory to use for building and change into it.

```
mkdir freetype-build
cd freetype-build
```

Get the sources for libfreetype6.

```
apt-get source libfreetype6
```

Install any dependencies needed for building the package (need root for this).

```
sudo apt-get build-dep libfreetype6
```

**Change the Source Package**
Switch into the source directory created by Apt.  Depending on the version the directory may be named differently, as of this writing it is "freetype-2.1.7".

```
cd freetype-2.1.7
```

Edit the "changelog" file in the "debian" directory. (I use vim, but any editor will of course work like gedit for instance)

```
vim debian/changelog
```

I dug into the Makefile (actually the rules file) and it seems to extract it with a regular expression from the top of the file.  At the current time of this writing, the top of file looks like this:

```
freetype (2.1.7-2.4ubuntu1) breezy; urgency=low

  * Slightly relax the header check on Type1 fonts, enabling wider display of
    PDFs, et al; based on a change to FreeType CVS (closes: Ubuntu#10087).

 -- Daniel Stone <daniel.stone@ubuntu.com>  Thu, 12 May 2005 12:41:38 +1000
```

Using your favorite text editor add an entry that adds to the version slightly this is to prevent apt-get from trying to install the "official" version over your custom one.  Of course when a new version of libfreetype6 becomes available it will overwrite your custom package--for this minor change I find that okay, but if you don't you can consider other techniques like package "pinning" which I won't get into here.  I made an entry on the top that looks something like this (note the additional minor up version):

```
freetype (2.1.7-2.4ubuntu1-nobytecode1) breezy; urgency=low

  * Disabled patch for Bytecode Interpreter.

 -- Almann Goo <almann.goo@somewhere.com>  Sat, 29 Oct 2005 21:30:00 -0500
```

Now edit the "rules" file in the "debian" directory.

```
vim debian/rules
```

Find the line that patches in the enabling of the bytecode interpreter.  It should look something like:

```
patch -p0 -i $(patchdir)/030-bytecode-interpreter.diff
```

Comment out the line with "#" so the line looks like this:

```
#patch -p0 -i $(patchdir)/030-bytecode-interpreter.diff
```

**Build the Package**
After making these slight changes, build the package:

```
fakeroot dpkg-buildpackage -rfakeroot -b -uc -us
```

This will create unsigned versions of the package in the parent directory.  Change to that directory.

```
cd ..
```

You should see the built packages, libfreetype6_XXXXX.deb where XXXXX is the version of your freetype.

**Install the Package**
Install the package using "dpkg"

```
sudo dpkg -i libfreetype6_2.1.7-2.4ubuntu1-nobytecode1_i386.deb
```

Of course, use the filename of the deb you created (the above example shows the one I built on my own machine).

**Conclusion**
Hopefully, if I wrote my instructions right and you followed them correctly, you should now have a libfreetype that has no bytecode interpreter and OpenOffice 2.0 will look as good (IMO) as the rest of your GTK2+/GNOME applications.

Again, you may have to repeat this when a new version of libfreetype comes out, though by using "pinning" you can of course avoid that scenario.

Hope this is helps anyone having this problem! :) 

Best Regards,
Almann

---

### Post by simber on 2006-01-03
looking at your solution, and trying to aply it, i couldnt find the freetype 2.1.7 
 directory after the comand :

sudo apt-get build-dep libfreetype6

i dont know if maybe you missed to write something 

please help me cause your the only one who has posted a solution like that and im very interested in making openoffice behave like the rest of the system 

im using a lcd 17"

i would appreciate your help

---

### Post by CiberAmigo on 2006-01-03
Not to show off, but I have libfreetype6 installed. Don't now when I did it but it might happens to be that You are missing some or one archive!

Wich archive do You have availeble on Your system?

Cencerly CiberAmigo

---

### Post by Footissimo on 2006-03-11
[QUOTE=simber]looking at your solution, and trying to aply it, i couldnt find the freetype 2.1.7 
 directory after the comand :

sudo apt-get build-dep libfreetype6

i dont know if maybe you missed to write something 

please help me cause your the only one who has posted a solution like that and im very interested in making openoffice behave like the rest of the system 

im using a lcd 17"

i would appreciate your help[/QUOTE]

I had that problem, but went ahead and installed the dependencies *then* went back a step and went for the source again and it worked - may be worth a try :)

Thanks for the HOWTO - OOo looks much better :)

---

### Post by Footissimo on 2006-06-07
*replies to self*

Just tried this on Dapper - still works, though you have to update the header bit  in the changelog and comment out a changed line in the rules - for me (and I can't say whether this will completely break everything and make your computer explode, but it seems to be OK).  This worked:

In changelog, add:

```
freetype (2.1.10-1ubuntu2-nobytecode1) dapper; urgency=low

  * Disabled patch for Bytecode Interpreter.

 -- Almann Goo <almann.goo@somewhere.com>  Sat, 5 May 2006 21:30:00 -0500
```

Above this:

```
freetype (2.1.10-1ubuntu2) dapper; urgency=low

  * Update shlibs dependency.  Ubuntu: #5901.

 -- Scott James Remnant <scott@ubuntu.com>  Thu,  6 Apr 2006 05:58:24 +0100
```

..and in rules, search for this to comment out:

```
patch -p1 -d $(freetype_u) -i $(patchdir)/030-bytecode-interpreter.diff
```

---

### Post by Phantom76 on 2006-06-17
That was a great post. Works perfectly on my Dapper too. OOo looks great after this patch! BTW, what other applications use this library?

---

### Post by OneWingedAngel on 2006-07-01
[QUOTE=Phantom76]That was a great post. Works perfectly on my Dapper too. OOo looks great after this patch! BTW, what other applications use this library?[/QUOTE]

On my system, all I've got is the last.fm player (downloaded from the site as a static Qt4 binary). There's probably more, though.

---

### Post by GTvulse on 2006-07-01
I'm sorry to say this, but all this patching and recompiling is Rube Golberg-ish. All you needed to do was:
```

sudo dpkg-reconfigure fontconfig

```
choose "use autohinter", "subpixel rendering always" save and restart X.

[Edit] Ahh! And add:
```
LD_PRELOAD=/usr/liblibfreetype.so.6
```
to the OOo startup script or, better yet, to /etc/environment (the latter works with Dapper).

---

### Post by Janux on 2006-07-01
I have been trying to figure out how to solve that problems, great!
Also it would be nice if someone can upload a package already patched

---

### Post by sclough on 2006-09-19
> **dradul said:**
> I'm sorry to say this, but all this patching and recompiling is Rube Golberg-ish. All you needed to do was:
```

sudo dpkg-reconfigure fontconfig

```
choose "use autohinter", "subpixel rendering always" save and restart X.

[Edit] Ahh! And add:
```
LD_PRELOAD=/usr/liblibfreetype.so.6
```
to the OOo startup script or, better yet, to /etc/environment (the latter works with Dapper).

I tried this and it did not solve the OpenOffice problem.  On the other hand, doing the recompile of the package did finally solve the OO problem.  I've been looking for a solution to this for ages, so it's good to finally get down to the core problem.  Not to hijack the thread, but does anybody know the specifics of the legality of removing the patch?  Is that patch something that Ubuntu is including to just play it safe, or is it an issue that they can't distribute the code without the patch?  I find it hard to believe Apple can patent smooth fonts in a way that it affects using Linux fonts under X windows, but anything is possible I guess.  Of course, it still doesn't look as good as my OSX machine, but it is a lot closer.  Don't get me wrong, I'm against software patents, but I'm just wondering if this is a violation or not since it seems odd that it would be patched since it produced much better results unpatched.

---

### Post by noend on 2006-11-15
This happend because some FreeType's internal features are no longer provided starting with the 2.2.0 release.

Reason of that I have downloaded "libfreetype6_2.1.10-1_i386.deb" and have extracted the file "libfreetype.so.6.3.8" (It also was  attached here). Copy it to /usr/local/lib so we can get it handy with this workaround.

Open a terminal window and issue the following:

env LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8 soffice

OpenOffice should look OK now.

If you do not want to write the above everytime, add into /usr/bin/soffice at line 46 (leave the current line 46 unchanged, just hit enter on it to move exiting code 1 line below) the following:

export LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8 soffice

Now everything should work without writing env.... everytime.

Hope it helps.

---

