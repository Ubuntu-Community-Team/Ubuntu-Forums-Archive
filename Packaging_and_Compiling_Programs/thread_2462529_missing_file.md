---
title: "missing file"
date: 2021-05-22
forum: Packaging and Compiling Programs
---

### Post by him610 on 2021-05-22
I was following this article, [https://www.howtogeek.com/428988/how-to-install-software-using-git-on-linux/](https://www.howtogeek.com/428988/how-to-install-software-using-git-on-linux/) attempting to locally build ascii-boxes from the downloaded contents of  boxes-master.zip
I followed all of the steps in the article except the *git clone*... step - could not get that to work which is why I downloaded the zip file. (newbie issue probably)
After unzipping the file boxes-master.zip, I executed the make step....
```

hugh@b450m:~/build/boxes-master$ make && make test
| For compilation info please refer to the boxes compilation FAQ
| at https://boxes.thomasjensen.com/docs/faq.html#q5
mkdir out
sed -e 's/--BVERSION--/2.1.0/; s/--GLOBALCONF--/\/usr\/share\/boxes/' src/boxes.in.h > out/boxes.h
sed -e 's/--BVERSION--/2.1.0/; s/--GLOBALCONF--/\/usr\/share\/boxes/' doc/boxes.1.in > doc/boxes.1
make -C src BOXES_PLATFORM=unix LEX=flex YACC=bison build
make[1]: Entering directory '/home/hugh/build/boxes-master/src'
make -C ../out -f ../src/Makefile BOXES_PLATFORM=unix ALL_OBJ="parser.o lex.yy.o boxes.o cmdline.o discovery.o generate.o input.o list.o parsecode.o parsing.o query.o regulex.o remove.o shape.o tools.o unicode.o" \
    CFLAGS_ADDTL="-O " STRIP=true flags_unix boxes
make[2]: Entering directory '/home/hugh/build/boxes-master/out'
make[2]: Nothing to be done for 'flags_unix'.
flex --header-file=lex.yy.h ../src/lexer.l
bison --warnings=all --verbose --defines=parser.h --output=parser.c ../src/parser.y
gcc -I. -I../src -Wall -W -O    -c -o parser.o parser.c
In file included from ../src/parser.y:27:
boxes.h:34:10:[COLOR="#FF0000"] fatal error[/COLOR]: unitypes.h: No such file or directory
   34 | #include <[COLOR="#FF0000"]unitypes.h[/COLOR]>
      |         [COLOR="#FF0000"] ^~~~~~~~~~~~[/COLOR]
compilation terminated.
make[2]: *** [<builtin>: parser.o] Error 1
make[2]: Leaving directory '/home/hugh/build/boxes-master/out'
make[1]: *** [Makefile:54: build] Error 2
make[1]: Leaving directory '/home/hugh/build/boxes-master/src'
make: *** [Makefile:41: build] Error 2

```

As you can see file, unitypes.h is missing. I determined it is called by six files.
```

hugh@b450m:~/build/boxes-master/src$ grep  unitypes.h *.*
boxes.in.h:#include <unitypes.h>
input.c:#include <unitypes.h>
regulex.h:#include <unitypes.h>
tools.c:#include <unitypes.h>
tools.h:#include <unitypes.h>
unicode.h:#include <unitypes.h>

```

Searching for the missing file locally and in github was unsuccessful.

I sent an email to the owner, Thomas Jenson, of ascii-boxes explaining my issue with the missing file. 
This being my first attempt (newbie) to build from downloaded code, **is there anything else I should have done??**

Build System:
```

~/build/boxes-master$ inxi -BCMSDm
System:    Host: b450m Kernel: 5.8.0-53-generic x86_64 bits: 64 Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASRock model: B450M/ac serial: <superuser/root required> 
           UEFI: American Megatrends v: P1.50 date: 10/14/2019 
Memory:    RAM: total: 15.57 GiB used: 12.32 GiB (79.2%) 
           RAM Report: permissions: Unable to run dmidecode. Root privileges required. 
CPU:       Topology: 6-Core model: AMD Ryzen 5 2600 bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 1373 MHz min/max: 1550/3400 MHz Core speeds (MHz): 1: 1377 2: 1376 3: 2789 
           4: 1267 5: 1374 6: 1270 7: 2615 8: 1270 9: 1448 10: 1458 11: 1375 12: 1264 
Drives:    Local Storage: total: 1.06 TiB used: 49.97 GiB (4.6%) 
           ID-1: /dev/nvme0n1 vendor: Western Digital model: WDS500G2B0C-00PXH0 
           size: 465.76 GiB 
           ID-2: /dev/sda vendor: Seagate model: ST500LM012 HN-M500MBB size: 465.76 GiB 
           ID-3: /dev/sdb vendor: Western Digital model: WD1600BJKT-00F4T0 size: 149.05 GiB

```

Please advise. Thanks

---

### Post by &amp;KyT$0P# on 2021-05-22
Try searching [here]("https://packages.ubuntu.com/#search_contents") for "packages that contain files named like" [FONT=Courier New]unitypes.h[/FONT] for your distro codename.  Then try installing the relevant package from those search results, which in this case appears to be [FONT=Courier New]libunistring-dev[/FONT] .

---

### Post by him610 on 2021-05-23
Followed your advice and found *libunistring-dev (0.9.10-4)* 
The file listing shows it contains */usr/include/unitypes.h* 
Downloaded * libunistring2_0.9.10-4_amd64.deb* 
Somehow, last night, I the package in the system.
```

hugh@b450m:~/build/libunistring$ dpkg -l libunistring2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version      Architecture Description
+++-===================-============-============-=================================
ii  libunistring2:amd64 0.9.10-4     amd64        Unicode string library for C

```

When I attempt the make command again; results are the same as in original post.
The must be something I am doing, or not doing that gives same error indications.

Correct me if I am wrong, once * libunistring2:amd64 0.9.10-4 * is in the system library, whatever is in the library (unitypes.h in this case) should be available to be included in a build when * make* is run.
I rebooted, just in case, and still got the same results.
```

hugh@b450m:~/build/boxes-master$ sudo make && make test
| For compilation info please refer to the boxes compilation FAQ
| at https://boxes.thomasjensen.com/docs/faq.html#q5
make -C src BOXES_PLATFORM=unix LEX=flex YACC=bison build
make[1]: Entering directory '/home/hugh/build/boxes-master/src'
make -C ../out -f ../src/Makefile BOXES_PLATFORM=unix ALL_OBJ="parser.o lex.yy.o boxes.o cmdline.o discovery.o generate.o input.o list.o parsecode.o parsing.o query.o regulex.o remove.o shape.o tools.o unicode.o" \
    CFLAGS_ADDTL="-O " STRIP=true flags_unix boxes
make[2]: Entering directory '/home/hugh/build/boxes-master/out'
make[2]: Nothing to be done for 'flags_unix'.
gcc -I. -I../src -Wall -W -O    -c -o parser.o parser.c
In file included from ../src/parser.y:27:
boxes.h:34:10:[COLOR="#FF0000"] fatal error[/COLOR]: unitypes.h: No such file or directory
   34 | #include <[COLOR="#FF0000"]unitypes.h[/COLOR]>
      |          [COLOR="#FF0000"]^~~~~~~~~~~~[/COLOR]
compilation terminated.
make[2]: *** [<builtin>: parser.o] Error 1
make[2]: Leaving directory '/home/hugh/build/boxes-master/out'
make[1]: *** [Makefile:54: build] Error 2
make[1]: Leaving directory '/home/hugh/build/boxes-master/src'
make: *** [Makefile:41: build] Error 2

```
Do you have any other suggestions?

---

### Post by &amp;KyT$0P# on 2021-05-23
[FONT=Courier New]libunistring2[/FONT] is not [FONT=Courier New]libunistring-dev[/FONT] .  The [FONT=Courier New]libunistring2[/FONT] package only contains the binary shared library.  It does not contain the files needed to *compile* programs that use that library.

Please check the output of
```
apt-cache policy libunistring-dev
```

---

### Post by him610 on 2021-05-23
Thanks for sticking with this. Never thought it would turn into a rabbit hole.
```

hugh@b450m:~$ apt-cache policy libunistring-dev
libunistring-dev:
  Installed: (none)
  Candidate: 0.9.10-2
  Version table:
     0.9.10-2 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```

---

### Post by &amp;KyT$0P# on 2021-05-23
> **him610 said:**
> ```

hugh@b450m:~$ apt-cache policy libunistring-dev
libunistring-dev:
  Installed: (none)

```

Again, you need to have install that package.

---

### Post by him610 on 2021-05-23
Ok, I went here, [https://packages.ubuntu.com/source/hirsute/libunistring]("https://packages.ubuntu.com/source/hirsute/libunistring") and downloaded 
libunistring_0.9.10-4.debian.tar.xz
After extraction, all the files went into folder debian - contents
```

hugh@b450m:~/build/libunistring/debian$ ll
total 104
drwxrwxr-x 5 hugh hugh    20 May 23 19:05 ./
drwxrwxr-x 3 hugh hugh     7 May 23 19:05 ../
-rw-r--r-- 1 hugh hugh  7762 Jun  1  2020 changelog
-rw-r--r-- 1 hugh hugh  1617 Jun  1  2020 control
-rw-r--r-- 1 hugh hugh  6067 Jun  1  2020 copyright
-rw-r--r-- 1 hugh hugh    18 May 28  2016 docs
-rw-r--r-- 1 hugh hugh    63 May 28  2016 gbp.conf
-rw-r--r-- 1 hugh hugh    20 May 28  2016 libunistring2.install
-rw-r--r-- 1 hugh hugh 22682 Jun  1  2020 libunistring2.symbols
-rw-r--r-- 1 hugh hugh 22497 Dec 28  2017 libunistring2.symbols.hurd-i386
-rw-r--r-- 1 hugh hugh   390 May 28  2016 libunistring-dev.doc-base
-rw-r--r-- 1 hugh hugh    22 May 28  2016 libunistring-dev.info
-rw-r--r-- 1 hugh hugh   120 May 28  2016 libunistring-dev.install
-rw-r--r-- 1 hugh hugh    59 Jun  1  2020 not-installed
drwxrwxr-x 2 hugh hugh     6 May 23 19:05 patches/
-rw-r--r-- 1 hugh hugh   541 Jun 11  2017 README.source
-rwxr-xr-x 1 hugh hugh   540 Jul 11  2019 rules*
drwxrwxr-x 2 hugh hugh     3 May 23 19:05 source/
drwxrwxr-x 2 hugh hugh     3 May 23 19:05 upstream/
-rw-r--r-- 1 hugh hugh   203 Dec  3  2017 watch

```

Should the files have been extracted as root? 
If you don't mind, I need some coaching here (feel like a total novice). I assume the files listed need to be somehow loaded/compiled into the local environment. I took a class in C about 30 or so years ago, but I never earned my living as a programmer - I worked in software configuration management and software testing.
I see the file, *rules** is executable. I expect it gets executed with one of the system compile tools.

Please advise -

---

### Post by &amp;KyT$0P# on 2021-05-23
I only suggested using packages.ubuntu.com to look up the relevant package, not for actually downloading packages.  Just install it the normal way,
```
sudo apt-get install libunistring-dev
```

(And you shouldn't be messing with hirsute packages on your focal system without a specific reason.  When searching packages.ubuntu.com by file, make sure you set the drop-down to search focal, since you're working on a focal system.)

---

### Post by him610 on 2021-05-23
I think I had tried this earlier, and now it feels like groundhog day.
```

hugh@b450m:~/build/libunistring$ sudo apt-get install libunistring-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libunistring-dev : Depends: libunistring2 (= 0.9.10-2) but 0.9.10-4 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I also tried * sudo apt-get install -f libunistring-dev* with same results.
Looks like there is a conflict with two versions of  *libunistring2*
How do I resolve the unmet dependencies and repair the broken packages?

---

### Post by him610 on 2021-05-23
How do I remove the 0.9.10-4 version and make the 0.9.10-2 version current?
```

hugh@b450m:~/build/libunistring$ apt-cache policy libunistring2
libunistring2:
  Installed: 0.9.10-4
  Candidate: 0.9.10-4
  Version table:
 *** 0.9.10-4 100
        100 /var/lib/dpkg/status
     0.9.10-2 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```

---

### Post by &amp;KyT$0P# on 2021-05-24
Try
```
sudo apt-get install libunistring2/focal
```

---

### Post by him610 on 2021-05-24
OK, making some progress. These three commands were successful ....
```

$ sudo apt-get install libunistring2/focal
...
~/build/libunistring$ apt-cache policy libunistring2
...
sudo apt-get install libunistring-dev

```
However, another fatal error - missing file similar to the one documented in post #1.
```

hugh@b450m:~/build/boxes-master$ make && make test
| For compilation info please refer to the boxes compilation FAQ
| at https://boxes.thomasjensen.com/docs/faq.html#q5
make -C src BOXES_PLATFORM=unix LEX=flex YACC=bison build
make[1]: Entering directory '/home/hugh/build/boxes-master/src'
make -C ../out -f ../src/Makefile BOXES_PLATFORM=unix ALL_OBJ="parser.o lex.yy.o boxes.o cmdline.o discovery.o generate.o input.o list.o parsecode.o parsing.o query.o regulex.o remove.o shape.o tools.o unicode.o" \
    CFLAGS_ADDTL="-O " STRIP=true flags_unix boxes
make[2]: Entering directory '/home/hugh/build/boxes-master/out'
make[2]: Nothing to be done for 'flags_unix'.
gcc -I. -I../src -Wall -W -O    -c -o parser.o parser.c
In file included from boxes.h:35,
                 from ../src/parser.y:27:
../src/regulex.h:42:10: [COLOR="#FF0000"]fatal error[/COLOR]: pcre2.h: No such file or directory
   42 | #include [COLOR="#FF0000"]<pcre2.h>[/COLOR]
      |          [COLOR="#FF0000"]^~~~~~~~~[/COLOR]
compilation terminated.
make[2]: *** [<builtin>: parser.o] Error 1
make[2]: Leaving directory '/home/hugh/build/boxes-master/out'
make[1]: *** [Makefile:54: build] Error 2
make[1]: Leaving directory '/home/hugh/build/boxes-master/src'
make: *** [Makefile:41: build] Error 2


```
I will close this thread as solved since the original missing file issue was successfully addressed. I will also follow the posts in this thread while attempting to address the current missing file. 

@halogen2 You have been so helpful and patient as we worked through this issue. Thank you. Should we ever meet in person, the beer or coffee (your choice) is on me. Have a nice day, you earned it:)

---

