---
title: "Installing antivirus for a tar"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Absolute-Zero on 2008-06-04
I had a lot of trouble to install anti virus from tar

here is my code, that i have used to type in to terminal and install it

can anyone tell me if i was doing something wrong ? or if the file is not instlled and if it is how cna i open it or start it ?

absolute-zero@Artificial-Intelligence:~$ tar -xzvf /home/absolute-zero/aegis-virus-scanner-2.0.0.targz
tar: /home/absolute-zero/aegis-virus-scanner-2.0.0.targz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
absolute-zero@Artificial-Intelligence:~$ tar -xzvf /home/absolute-zero/aegis-virus-scanner-2.0.0.tar.gz
aegis-virus-scanner-2.0.0/
aegis-virus-scanner-2.0.0/lib/
aegis-virus-scanner-2.0.0/lib/Aegis/
aegis-virus-scanner-2.0.0/lib/Aegis/Monitor.pm
aegis-virus-scanner-2.0.0/lib/Aegis/Config.pm
aegis-virus-scanner-2.0.0/lib/Aegis/Scanner.pm
aegis-virus-scanner-2.0.0/lib/Aegis/I18N.pm
aegis-virus-scanner-2.0.0/lib/Aegis/UI.pm
aegis-virus-scanner-2.0.0/lib/Aegis.pm
aegis-virus-scanner-2.0.0/share/
aegis-virus-scanner-2.0.0/share/aegis-virus-scanner.desktop
aegis-virus-scanner-2.0.0/share/aegis-virus-scanner/
aegis-virus-scanner-2.0.0/share/aegis-virus-scanner/share/
aegis-virus-scanner-2.0.0/share/aegis-virus-scanner/share/aegis-virus-scanner.glade
aegis-virus-scanner-2.0.0/share/icons/
aegis-virus-scanner-2.0.0/share/icons/aegis-virus-scanner.png
aegis-virus-scanner-2.0.0/src/
aegis-virus-scanner-2.0.0/src/aegis.pl
aegis-virus-scanner-2.0.0/Makefile.in
aegis-virus-scanner-2.0.0/configure
aegis-virus-scanner-2.0.0/COPYING
aegis-virus-scanner-2.0.0/aegis-virus-scanner.spec
aegis-virus-scanner-2.0.0/script.txt
absolute-zero@Artificial-Intelligence:~$ ./configure
bash: ./configure: No such file or directory
absolute-zero@Artificial-Intelligence:~$ cd /home/absolute-zero/aegis-virus-scanner-2.0.0.tar.gz
bash: cd: /home/absolute-zero/aegis-virus-scanner-2.0.0.tar.gz: Not a directory
absolute-zero@Artificial-Intelligence:~$ cd /home/absolute-zero/aegis-virus-scanner-2.0.0.tar.gz
bash: cd: /home/absolute-zero/aegis-virus-scanner-2.0.0.tar.gz: Not a directory
absolute-zero@Artificial-Intelligence:~$ cd /home/absolute-zero/aegis-virus-scanner-2.0.0
absolute-zero@Artificial-Intelligence:~/aegis-virus-scanner-2.0.0$ ./configure
Configuration options:
    prefix: 
Writing Makefile...
Now type 'make' to build.
absolute-zero@Artificial-Intelligence:~/aegis-virus-scanner-2.0.0$ make
perl -ne 's!\@PREFIX\@!!g ; print' < src/aegis.pl > aegis-virus-scanner
absolute-zero@Artificial-Intelligence:~/aegis-virus-scanner-2.0.0$ su
Password: 
root@Artificial-Intelligence:/home/absolute-zero/aegis-virus-scanner-2.0.0# make install
mkdir -p	/share/aegis-virus-scanner \
			/share/aegis-virus-scanner/lib \
			/share/aegis-virus-scanner/share \
			/share/icons/hicolor/48x48/apps \
			/share/applications \
			/bin
install	-m 0755 aegis-virus-scanner /bin/
install -m 0644 share/icons/aegis-virus-scanner.png /share/icons/hicolor/48x48/apps/
install -m 0644 share/aegis-virus-scanner/share/aegis-virus-scanner.glade /share/aegis-virus-scanner/share/
install -m 0644 share/aegis-virus-scanner.desktop /share/applications/
cp -Rp lib/* /share/aegis-virus-scanner/lib/
root@Artificial-Intelligence:/home/absolute-zero/aegis-virus-scanner-2.0.0#

---

### Post by ukripper on 2008-06-04
Should be :
tar -xzvf /home/absolute-zero/aegis-virus-scanner-2.0.0.tar**.gz**

---

### Post by SunnyRabbiera on 2008-06-04
well you really dont need antivirus, but I suggest clam and klam its graphical frontend.
both are in the repositories.

---

### Post by aysiu on 2008-06-04
Why do you need antivirus? Are you using Ubuntu as a mail server or file server?

---

### Post by Absolute-Zero on 2008-06-04
I dont need a ntivirus i am just trying to learn how to install something with tar ending

I just wanna know if it ACTUALLLY IS POSSIBELE TO INSTALL ANYTHING THAT IS NO INT SYNAPTIC

---

### Post by aysiu on 2008-06-04
> **Absolute-Zero said:**
> I dont need a ntivirus i am just trying to learn how to install something with tar ending

I just wanna know if it ACTUALLLY IS POSSIBELE TO INSTALL ANYTHING THAT IS NO INT SYNAPTIC
Cool. Thanks for clarifying.

---

### Post by Joeb454 on 2008-06-04
Of course it's possible, though .tar.gz files *usually* require compiling from source :) Not all the time though

---

### Post by Absolute-Zero on 2008-06-04
Its impossible is in it ? 

I have ubuntu book the official one and it says very easy to compile something from source and they give few steps how to do it, (however they forgot to mention that you gotta be super computer hacker or programmer)

---

### Post by Obnoticus on 2008-06-04
I remember installing VMWare tools on a guest install of ubuntu a while ago, and that wasn't too hard.  I'm sure if you google a bit you'll find a ton of pages with bash commands that will tell you exactly what to do.

[http://ubuntuforums.org/showthread.php?t=323939](http://ubuntuforums.org/showthread.php?t=323939)

This should be a good start.

---

### Post by Joeb454 on 2008-06-04
The only difficult part about compiling is getting the dependencies - if it returns an error ```
missing dependency: libpng-2.0
``` or something like that (I can't remember the exact errors, you would try ```
sudo apt-get install libpng-2.0-dev
``` Always -dev packages, if you are compiling from source :)

---

