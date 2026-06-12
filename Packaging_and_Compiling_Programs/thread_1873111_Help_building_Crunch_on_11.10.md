---
title: "Help building Crunch on 11.10?"
date: 2011-10-31
forum: Packaging and Compiling Programs
---

### Post by GrantStoner on 2011-10-31
Has anyone else come across problems building Crunch wordlist generator on *buntu 11.10? Or has anyone had any success? I'm following the generic "tar, cd, make, make install" dance and here's what I get when I attempt the "make":```
[root:/pentest/wordlists/crunch3.1]# ls -lh
total 132K
-rw-r--r-- 1 root root 5.5K 2011-04-06 17:13 charset.lst
-rw-r--r-- 1 root root  16K 2011-07-19 16:42 crunch.1
-rw-r--r-- 1 root root  77K 2011-07-19 17:39 crunch.c
-rw-r--r-- 1 root root  18K 2011-04-06 17:13 GPL.TXT
-rw-r--r-- 1 root root 2.5K 2011-07-19 16:45 Makefile

[root:/pentest/wordlists/crunch3.1]# make
Building binary...
/usr/bin/gcc -Wall -lm -pthread -std=c99  crunch.c -o crunch
crunch.c: In function ‘PrintPercentage’:
crunch.c:541:20: warning: variable ‘finall’ set but not used [-Wunused-but-set-variable]
crunch.c: In function ‘renamefile’:
crunch.c:567:12: warning: variable ‘pidret’ set but not used [-Wunused-but-set-variable]
crunch.c: In function ‘main’:
crunch.c:1310:8: warning: variable ‘loaded’ set but not used [-Wunused-but-set-variable]
crunch.c:1308:8: warning: variable ‘flag4’ set but not used [-Wunused-but-set-variable]
/tmp/ccOLPNq0.o: In function `main':
crunch.c:(.text+0x6511): undefined reference to `pow'
crunch.c:(.text+0x662b): undefined reference to `pow'
crunch.c:(.text+0x6934): undefined reference to `pow'
crunch.c:(.text+0x6a84): undefined reference to `pow'
collect2: ld returned 1 exit status
make: *** [crunch] Error 1
[root:/pentest/wordlists/crunch3.1]#
```

---

### Post by mc4man on 2011-10-31
try adjusting your makefile to put source first, maybe like

```
build: crunch



val:    crunch.c

	@echo "Building valgrind compatible binary..."

	$(CC) $? $(VCFLAGS) $(LFS)  -o crunch 

	@echo "valgrind --leak-check=yes crunch ..."

	@echo ""



crunch: crunch.c

	@echo "Building binary..."

	$(CC) $? $(CFLAGS) $(LFS)  -o $@

	@echo ""
```

---

### Post by GrantStoner on 2011-10-31
Hrm, I will try that! Thanks! I will report back when I'm finally done. I'm have tried wget'ing crunch again since I rm'd it - but the ETA is saying over 12hrs? Wtf?! Eventually I'll get it. Nothing else online is lagging. Weird.

---

### Post by GrantStoner on 2011-10-31
For now I have followed the instructions to get a binary build from the BackBox Linux repositories from the BackBox Wiki here: [http://wiki.backbox.org/index.php/How_to_install_BackBox_repository_on_Ubuntu/Debian_systems](http://wiki.backbox.org/index.php/How_to_install_BackBox_repository_on_Ubuntu/Debian_systems) in the "other systems" section of that page - just in case anyone else wanted a quick-fix solution. I'm using Oneiric (11.10) even though BackBox (and the repo) is for Natty (11.04) but following the instructions works just fine. Although it installs Crunch 3.0.1 and not the latest 3.1 - but this is still fantastic IMO.

---

### Post by GrantStoner on 2011-10-31
Okay, got it finally. Here's what's going on now:```
[root:/pentest/wordlists/crunch3.1]# ls -lh
total 128K
-rw-r--r-- 1 root root 5.5K 2011-04-06 17:13 charset.lst
-rw-r--r-- 1 root root  16K 2011-07-19 16:42 crunch.1
-rw-r--r-- 1 root root  77K 2011-07-19 17:39 crunch.c
-rw-r--r-- 1 root root  18K 2011-04-06 17:13 GPL.TXT
-rw-r--r-- 1 root root 2.5K 2011-10-31 19:37 Makefile

[root:/pentest/wordlists/crunch3.1]# make
Building binary...
/usr/bin/gcc crunch.c -Wall -lm -pthread -std=c99  -o crunch
crunch.c: In function &#8216;PrintPercentage&#8217;:
crunch.c:541:20: warning: variable &#8216;finall&#8217; set but not used [-Wunused-but-set-variable]
crunch.c: In function &#8216;renamefile&#8217;:
crunch.c:567:12: warning: variable &#8216;pidret&#8217; set but not used [-Wunused-but-set-variable]
crunch.c: In function &#8216;main&#8217;:
crunch.c:1310:8: warning: variable &#8216;loaded&#8217; set but not used [-Wunused-but-set-variable]
crunch.c:1308:8: warning: variable &#8216;flag4&#8217; set but not used [-Wunused-but-set-variable]

[root:/pentest/wordlists/crunch3.1]# ls -lh
total 176K
-rw-r--r-- 1 root root 5.5K 2011-04-06 17:13 charset.lst
-rwxr-xr-x 1 root root  48K 2011-10-31 19:41 crunch
-rw-r--r-- 1 root root  16K 2011-07-19 16:42 crunch.1
-rw-r--r-- 1 root root  77K 2011-07-19 17:39 crunch.c
-rw-r--r-- 1 root root  18K 2011-04-06 17:13 GPL.TXT
-rw-r--r-- 1 root root 2.5K 2011-10-31 19:37 Makefile

[root:/pentest/wordlists/crunch3.1]# make install
Creating directories...
/usr/bin/install -d -m 755 -o root -g root /pentest/passwords//crunch
/usr/bin/install -d -m 755 -o root -g root /usr/local/share/man/man1
Copying binary...
/usr/bin/install crunch -m 755 -o root -g root /pentest/passwords//crunch
Copying charset.lst...
/usr/bin/install charset.lst -m 644 -o root -g root /pentest/passwords//crunch
Installing man page...
/usr/bin/install crunch.1 -m 644 -o root -g root /usr/local/share/man/man1

[root:/pentest/wordlists/crunch3.1]# crunch
crunch: command not found
```So it seems to build fine, as you can see above. And looks like it installs fine, but the command isn't found (and "tab-autocompletion" with "crun" produced nothing).

However "man crunch" produces Crunch help - so the man pages installs fine.

---

### Post by SevenMachines on 2011-11-01
It's not installed to a system bin directory, you can use the full path
```
 $ /pentest/passwords/crunch
```
to run it. Probably fixing up the makefile to install to standard locations is a good idea though, hardcoding a makefile to install to /usr/local/ is a little messy

---

### Post by SevenMachines on 2011-11-01
As an aside, backtrack is pretty much the standard pen testing distribution, also based on ubuntu, you might want to give that a look

---

### Post by gandaran on 2011-11-02
having the same problem here and not just with crunch but also with mdk3
so why is the make command failing on ubuntu 11.10 as in the other versions compiling these applications was a piece of cake?

---

### Post by GrantStoner on 2011-11-16
> **SevenMachines said:**
> It's not installed to a system bin directory, you can use the full path
```
 $ /pentest/passwords/crunch
```to run it. Probably fixing up the makefile to install to standard locations is a good idea though, hardcoding a makefile to install to /usr/local/ is a little messy
Thanks, I went to the pentest directory it made and the ran the program that way - works fine.
> **SevenMachines said:**
> As an aside, backtrack is pretty much the standard pen testing distribution, also based on ubuntu, you might want to give that a look
Absolutely not. I refuse to use that "distro". I do not understand making something open-source, something that you know members and user are going to look inside under the hood, and then only telling them to use Google or quit being stupid or any other retarded "support" they give when users come to them with questions. The devs there have the worst god-complex out of any dev team I've ever talked with. Sorry about my rant but I absolutely cannot stand them. I respect them as talented devs but among the rudest nonetheless.
> **gandaran said:**
> having the same problem here and not just with crunch but also with mdk3
so why is the make command failing on ubuntu 11.10 as in the other versions compiling these applications was a piece of cake?
I believe it has something to do with the new versions of gcc/g++ being used by default in 11.10 while going back to using 11.04 allows me compile anything and everything again.

---

### Post by c0nfig on 2012-10-03
The new gcc needs to have the libraries at the end of the compile line.
Hence,  to compile it on ubuntu 11.10 and up all you need to do is to add "-lm" to the end of the compile line. For example:
 
```

crunch: crunch.c
    @echo "Building binary..."
    $(CC) $(CFLAGS) $(LFS) $? -o $@ -lm
    @echo ""


```

---

