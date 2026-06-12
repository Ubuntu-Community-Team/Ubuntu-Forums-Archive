---
title: "HOWTO: Install F-Prot with GTK frontend [OUTDATED]"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2005-04-10
Q: **Is viruses, trojans and malware a threat to a linux system as in Windows?**

A: *No, there's a very few viruses to linux and the way a Linux/unix is build up makes it difficult to do any serious damage to the system, in fact I've never heard from people who got their Linux/unix system infected.*

Q: **So why install a anti-virus application/program?**

A: *For an ordinary Linux Home user with only one OS system their's no need for Anti-virus, but people who's running network, server or dual booting with win OS this tool can be very handy to scan and delete viruses.*

Q: **I'm a home user only running Linux do I need it?**

A: *No, a firewall is way better as protection like firestarter.*



First thing, setup your repositories. Here's how you do it: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Next:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libwww-perl
sudo apt-get install libgtk2.0-dev
sudo apt-get install gcc

```

Grab F-prot [here](http://www.f-prot.com/products/home_use/linux/)  and pick the debian/gnu file. (4.6.1)
Download XFPROT-1.14 [here](http://web.tiscali.it/sharp/xfprot/). 
or use the .deb files [click here](http://members.chello.be/sf15418/xfprot-1.13_1.13-1_i386.deb)  (old 1.13 - I havn't tried it).

```

cd /where/you/saved/the/files/
sudo dpkg -i  fp-linux-ws.deb 

```

To compile (the non-.deb file) itself:
Extract xfprot-1.14.tar.gz (eg. right click it and choose extract)

```

cd xfprot-1.14
./configure --with-gtk2 --with-sudo --autodetect --without-debug
make
sudo make install

```

Using the .deb file:
```

cd /where/you/saved/the/.deb/file
sudo dpkg -i xfprot-1.13_1.13-1_i386.deb

```


Open Menu-Editor:
**Name:** F-Prot
**Comment:** Protection Application (or what ever you prefer)
**Command:** xfprot
**Icon:** /usr/local/xfprot/icons/antivirus-48x48.png
**Category:** System Tools



**To Uninstall the compiled xf-prot:**
```

cd xfprot-X.XX
./make uninstall

```

---

### Post by Jad on 2005-04-10
Thank you

---

### Post by Perfect Storm on 2005-04-23
New version of XFProt is avaible (v. 1.11). Updated the Howto.



.:=The AI Dude=:.

---

### Post by Yukonjack on 2005-04-24
Thank you Artificial Intelligence  :wink:

---

### Post by Spudgun on 2005-04-24
Thanks :)

---

### Post by george29 on 2005-04-27
thanks for that little tutorial. very easy to follow.

cheers
george

---

### Post by Ezzet on 2005-04-27
Thank you!

---

### Post by Svenn on 2005-05-03
A.I. you rock !! \\:D/ 

Thanks again 

~Svenn

---

### Post by Benni on 2005-05-05
Nice and easy guide, even to newbies like me ;)
Looks nice and works like hell.
But how is it with uninstalling F-Prot again?
[offtopic]
I just ask, cause i'm sitting here with an Bit Defender linux install, which is a kind of miracle for me now, since there are no files where they're supposed to be.
Seems like i have done a little magic there during my first linux-steps :oops: 
And now i have no idea how to remove it fully (sorry for that bit of offtopic...could be handled with pm's)
[/offtopic]

---

### Post by Perfect Storm on 2005-05-10
When I want to remove something which aren't installed as packages I simply  find the  files/folders and sudo rm -r <folder>, but I'm sure there's an easier way to do it. If you know the structure(s) of linux there will be no problem to find where the file(s) is installed.


The .deb file can be uninstalled via the package management.



.:=The AI Dude=:.

---

### Post by pseudonym on 2005-05-28
Great tip! I used to run f-prot from the command line but this is much sweeter :)

I noticed that the 'f-prot-installer' package has disappeared out of the repositories, along with a lot of other good ones (like liblame0, which I want to rip some mp3s with Sound Juicer). Any idea why? Is this something to do with this 'libc6 transition' I've been hearing about?

---

### Post by foxy123 on 2005-05-29
I have installed f-prot before using f-prot-installer in synaptic. It out it in /usr/lib

The problem is that xfprot is looking for f-prot in /usr/local. Any way to point it to /usr/lib?

---

### Post by mglukhovsky on 2005-06-05
To get xfprot to look for f-prot in the right directory, create a symbolic link between the two directories. Issue the following in a terminal:
```
$ sudo ln -s /usr/lib/f-prot /usr/local/f-prot
```

Cheers!

---

### Post by Perfect Storm on 2005-07-10
*Updated: The xfprot package have changed, so instead of 'cd /xfprot/xfprot-1.11' it's now 'cd xfprot-1.11'. *


.:=The AI Dude=:.

---

### Post by Perfect Storm on 2005-07-22
New version of XF-prot is out (1.12). Updated the Howto to fit it.

---

### Post by Perfect Storm on 2005-07-27
New version of XF-Prot (v1.13)

Updated the Howto and change the install proceedior so the 'Update' button now works.

---

### Post by Perfect Storm on 2005-08-16
F-prot version 4.6 is now avaible

---

### Post by matthew on 2005-08-16
Thanks.

---

### Post by A-star on 2005-08-17
I made a deb file for xfprot available here:
[http://members.chello.be/sf15418/xfprot-1.13_1.13-1_i386.deb](http://members.chello.be/sf15418/xfprot-1.13_1.13-1_i386.deb)

---

### Post by Perfect Storm on 2005-08-17
Okay I'll add the deb file into the HOWTO, then people can choose which way to go.

---

### Post by Perfect Storm on 2005-09-06
New version of F-prot is availble (4.6.1)
The howto is updated.

---

### Post by John.Michael.Kane on 2005-09-06
Ran F-prot after following this guide and it came back with eicar.txt  as an infected file under xfprot-1.13 just wanted you to know. i dont know if it's a test file used to check that fprot is working or not.

---

### Post by Perfect Storm on 2005-09-06
It's a test file to check if everything is running as it should.

---

### Post by John.Michael.Kane on 2005-09-06
Thanks A.I

---

### Post by Name on 2005-09-23
I cant get it to work. The installation looks like it worked. The files are in usr/local/ but when I try to run it I get nothing. Im not sure whats going on.

---

### Post by Perfect Storm on 2005-09-24
Try run it in the terminal and post the outcome. Did you configure or used the .deb file? Please post the configure output from the terminal if you compiled it.

---

### Post by Perfect Storm on 2005-09-24
Updated the Howto. xf-prot version 1.14 is now avaible.

---

### Post by Danielle on 2005-12-07
thanks for the tutorial, AI. i love f-prot. can someone show me how to scan all files?

is it this?:
/

thanks.

---

### Post by 5-HT on 2005-12-07
[QUOTE=Danielle]thanks for the tutorial, AI. i love f-prot. can someone show me how to scan all files?

is it this?:
/

thanks.[/QUOTE]


Hi, yup that would scan the root directory which should include all files.


As an aside, what I also like to do is add the list option so that I get a running output of which files are being scanned.

So for example: ```
f-prot -list / 
```

HTH.



Also, thanks A.I. for creating this thread.

---

### Post by Danielle on 2005-12-09
[QUOTE=5-HT]Hi, yup that would scan the root directory which should include all files.


As an aside, what I also like to do is add the list option so that I get a running output of which files are being scanned.

So for example: ```
f-prot -list / 
```

HTH.
[/QUOTE]
thanks, 5-HT. i'll try that. i've run it once and the only output i saw were the the locked directories and that was it! there wasn't any final report for the scan's stats :confused:

---

### Post by 5-HT on 2005-12-09
hmm... now that you mention access problems I do see a few files that f-prot cannot scan under normal user privilages.

I thought read access to every file under / was available, but I guess in my ignorance f-prot needs more than that to scan.

In that case, if you want to scan every single file, I'd say escalating to more limited privilages via sudo would be best such as 
```
 sudo f-prot -list / 
```

That will get rid of the locked directories, but I'm a little worried about that fact that you never got a scan summary at the end. F-prot always let me know how many files and objects it scanned along with the date of its virus definitions and any viruses it found.

---

### Post by Danielle on 2005-12-09
[QUOTE=5-HT]hmm... now that you mention access problems I do see a few files that f-prot cannot scan under normal user privilages.

I thought read access to every file under / was available, but I guess in my ignorance f-prot needs more than that to scan.

In that case, if you want to scan every single file, I'd say escalating to more limited privilages via sudo would be best such as 
```
 sudo f-prot -list / 
```

That will get rid of the locked directories, but I'm a little worried about that fact that you never got a scan summary at the end. F-prot always let me know how many files and objects it scanned along with the date of its virus definitions and any viruses it found.[/QUOTE]
hi, 5-HT. i booted into XP for the first time since installing Ubuntu so i could update my av and a few other things incase i need to use XP at some point. so i can only guess i didn't use sudo, but i'm sure i didn't. also, i'm not sure which command i used for the scan to get no summary, however, i'm sure if i run...
```
 sudo f-prot -list / 
```
...things will be fine. i'll try it out tomorrow. thanks for the help O:)

---

### Post by 5-HT on 2005-12-13
[quote=Danielle]
...things will be fine. i'll try it out tomorrow. thanks for the help O:)[/QUOTE]

No worries, hope that solves it. 

Just wondering if you've got everything working the way you'd like it to?

---

### Post by Danielle on 2005-12-18
[QUOTE=5-HT]No worries, hope that solves it. 

Just wondering if you've got everything working the way you'd like it to?[/QUOTE]
yes, i have. thanks for the help. O:)

---

### Post by bernat_f on 2007-01-30
hi,
I'm trying to install it but everytime I end with the following error can anyone say me what could I do?

bernat@ubuntu:~/Desktop$ sudo dpkg -i fp-linux-ws.deb
(Reading database ... 138305 files and directories currently installed.)
Preparing to replace fp-linux-ws 4.6.7 (using fp-linux-ws.deb) ...
Unpacking replacement fp-linux-ws ...
Setting up fp-linux-ws (4.6.7) ...
ln: creating symbolic link `/etc/f-prot.conf' to `/usr/local/f-prot/etc/f-prot.conf.default': File exists
dpkg: error processing fp-linux-ws (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 fp-linux-ws

---

### Post by bernat_f on 2007-01-30
solved, I have removed and reinstalled my libraries and now it works, but my problem now is with the configuration. Which options I have to use?, optinon gtk2, don't works.

bernat@ubuntu:~/Desktop/xfprot-1.18$ ./configure --with-gtk2 --with-sudo --autodetect --without-debug
configure: invalid option --with-gtk2
bernat@ubuntu:~/Desktop/xfprot-1.18$ sudo ./configure --with-sudo --autodetect --without-debug
/bin/bash
Checking for bash.....OK

Writing default values to config.h

Setting install and binaries directory prefix to : /usr/local
You can override this with: --with-install-dir=/somedir
Setting xfprot binary directory to: /usr/local/xfprot

Using default value: 'sudo'

Autodetecting f-prot's install directory....please be patient
found: /usr/local/f-prot
Setting xfprot private directory to: ~.xfprot

Running Linux Kernel: 2.6
Checking for konsole.....OK
./configure: 447: gtk-config: not found
test: 447: ==: unexpected operator
/usr/bin/pkg-config
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
test: 447: ==: unexpected operator
You have to install the Gtk+ development (and runtime?) libraries version 2.4.x or superior.

---

### Post by bernat_f on 2007-01-30
Solved I used =

“sudo apt-get install libgtk-dev” 

to install the libgtk-dev package

and

nano configure
replace #!/bin/sh with #!/bin/bash

to edit the first line of the configure file

---

### Post by bernat_f on 2007-01-30
Sorry, but I get a new error while I'm doing the compilation, after using the instruction 'make' the compurter freezes, without reaction to mouse or keyboard, I have copied in another computer what appeared on the screen before it stops working. What should I do now?

bernat@ubuntu:/Desktop/xfprot-1.18$ sudo make
CC-DIS_LINUX –DGTK_2_10 –DNDEBUG –03 –pipe –fomit-frame-pointer –fno-builtin std=gnu99 –include i18n/en_GB.h –include mylib.h –include mygtk.h –include config.h –I/usr/include/gtk-2.0 –I/usr/lib/gtk-2.0/include –I/usr/include/atk-1.0 –I/usr/include/cairo –I/usr/include/pango-1.0 –I/usr/include/glib-2.0 –I/usr/lib/glib-2.0/include –DG_DISABLE_DEPRECATED –DGDK_DISABLE_DEPRECATED –DGDK_PIXBUF_DISABLE_DEPRECATED –DGTK_DISABLE_DEPRECATED DLmsg –DL_err_msg –DL_xsnprintf –DL_xcalloc –DL_xalloc_die –DL_xmake_message –DL_xmalloc –DL_xpclose_nostdin –DL_xfclose_nostdin –DL_xgetcwd –DL_xopen –DL_xopen_die –DL_trim –DL_get_line_from_line –DL_xconcat_path_file –DL_xrealloc –DL_xstrncat –DL_xchmod –DL_xchown –DL_xchdir –DL_xputs –DL_xmkdir –DL_last_char_is –DL_xstrdup –DL_xfgetc_nbuf –DL_xfree –DL_xstrlen –c –o mylib.o o mylib.c

CC –DIS_LINUX –DGTK_2_10 –DNDEBUG –03 –pipe –fomit-frame-pointer –fno-builtin –std=gnu99 –include il8n/en_GB.h –include mylib.h –include mygtk.h –include config.h lgtk-x11-2.0 –lgdk-x11-2.0 –latk-1.0 –lgdk pixbuf-2.0 –lm –lpangocairo-1.0 –lfontconfig –lXext –lXrender –lXinerama –lXi –lXrandr –lXcursor –lXfixes –lpango-1.0 –lcairo –lX11 –lgobject-2.0 –lgmodule-2.0 –ldl –lglib-2.0 –lgtk-x11-2.0 –lgdk-x11-2.0 –latk-1.0 –lgdk_pixbuf-2.0 –lm –lpangocairo-1.0 –lfontconfig –lXext –lXrender –lXinerama –lXi –lXrandr –lXcursor –lXfixes –lpango-1.0 –lcairo –lX11 –lgobject-2.0 –lgmodule-2.0 –ldl –lglib-2.0 –o xfprot-gtk xfprot-gtk.o TextViewWindow.o TextEditWindow.o AboutWindow.o TextCommon.o DialogWindow.o FileSelector.o mygtk.o mylib.o

---

