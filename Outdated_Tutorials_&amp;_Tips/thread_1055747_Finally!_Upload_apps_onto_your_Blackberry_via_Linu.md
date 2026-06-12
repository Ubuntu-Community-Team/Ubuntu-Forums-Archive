---
title: "Finally! Upload apps onto your Blackberry via Linux!"
date: 2009-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by DirtDawg on 2009-01-31
I recently got a BlackBerry, but I was very sad to learn there was no way to upload java applications (cod files) onto the phone using Linux. As a result, I was restricted to finding and installing only 'jad' files I found on the net. But the good developers at Barry-devel have added a java uploader with their latest release! And I do mean *latest*, like two days ago.

Which brings me to:
[COLOR="Red"]Warning! The code I post about here is brand-spanking new. In the unlikely event it 'bricks' your phone, do not blame me or the developers. You are using this software at your own risk![/COLOR]

Furthermore, I have only tested this out on my Blackberry 8130 on Ubuntu 8.10 (Ibex). Your mileage may vary.

There are installation instructions [here]("http://www.netdirect.ca/software/packages/barry/cvs.php") and dependencies are listed [here]("http://www.netdirect.ca/software/packages/barry/dependencies.php"). You will need both the packages under the heading Master Dependencies as well as the Dependency Packages for Debian stable found at the bottom of the page. I installed the basic needed dependencies (including anything noted for 'CVS builds only') as well as the GUI dependencies and ended up with about 66 Megs of newly installed libraries.

If you know what you're doing when it comes to compiling this sort of thing, go to it! Otherwise, I am posting this brief recap of what I did to install Barry successfully. However, please note the [previously mentioned guide]("http://www.netdirect.ca/software/packages/barry/cvs.php") is extremely thorough and well-written. Please use the guide you are reading now if you feel you need an example of the installation process or the resulting bjavaloader command.

I used the git method, which requires git to be installed:
```
sudo apt-get install git-core
```
Next, download a copy of the latest build with git:
```
git clone git://repo.or.cz/barry.git barry
```
This creates a directory called 'barry' in whatever directory you ran the git command in (I used my home directory). Next, go into the barry folder and run the buildgen.sh script:
```
 cd barry
./buildgen.sh
```
Hopefully no errors. If you got an error, make sure you have both automake and libtool installed. Next, run the configure command. I ran with only the GUI option which provides a simple GUI for the barrybackup command since I am not interested in syncing or using the boost feature. If you are interested in these features, please install the required dependencies and use the appropriate flag. Note that you don't need the GUI for bjavaloader as bjavaloader is part of the base package:
```
./configure --enable-gui
```
Finally, make and install. Since this is development software, it's likely you'll be met with an error or two. I know I had my share. You can try getting help here or, even better, at the [barry-devel mailing list]("https://lists.sourceforge.net/lists/listinfo/barry-devel"). Sign up, ask questions and report bugs! They love it.
```
make
sudo make install
```
FYI, I tried checkinstall in place of make install, but got no love.

Now with any (aka: lots of) luck, you should have barry installed.

Understand that using barry is not a case of finding 'barry' in your applications menu or running 'barry' in a commmand line. Barry consists of several smaller commands you use separately and they can be found in your /usr/local/bin directory:
```
ls /usr/local/bin
```
There's plenty of documentation about using btool and barrybackup (not a bad one to utilize before going any further), but what we're interested in is bjavaloader. Use this command to see the options available to you:
```
bjavaloader -h
```
The commands are relatively straight forward, but let's run through a few important commands anyway. To install an application, simply use the 'load' command:
```
bjavaloader load coolapp.cod
```
After your Blackberry and computer finish chatting, the application should appear alongside the others you have installed on your phone. Now, it is important to understand you cannot remove the app by using the 'delete' command from your phone! You must use bjavaloader to remove applications installed with bjavaloader. So, to remove said app, first find it using the dir command:
```
bjavaloader dir
```
This will return lots of output like you see below. Just look for the app in question. In this case, 'coolapp':
```
...<clip>
 2008
  net_rim_bluetooth                                 
                            0x7810 4.5.0.7700 1335760 Fri Aug 15 11:24:32 2008
  net_rim_ecmascript                                
                            0x7880 4.5.0.7700 1766600 Fri Aug 15 11:25:20 2008
  net_rim_ecmascript_resource                       
                            0x7910 4.5.0.7700 1744000 Fri Aug 15 11:25:29 2008
  net_rim_ecmascript_resource__en                   
                            0x7940 4.5.0.7700 5220000 Fri Aug 15 11:25:31 2008
  net_rim_ecmascript_regexp                         
                            0x7970 4.5.0.7700 2566000 Fri Aug 15 11:25:17 2008
  net_rim_ecmascript_resource__fr                   
                            0x79a0 4.5.0.7700 1760000 Fri Aug 15 11:25:34 2008
  net_rim_ecmascript_resource__es                   
                            0x79d0 4.5.0.7700 1760000 Fri Aug 15 11:25:33 2008 

  CoolApp                                        
                            0x13a2 2.3.200000 6557960 Tue Oct 28 14:33:03 2008
  GoogleMail                                        
                            0x1455 2.0.600000 4507040 Wed Oct  1 14:22:25 2008
  BBNotePad                                         
                            0x1522 1.1.200000 1218880 Tue Jan  6 04:45:11 2009
  GoogleMaps                                        
                            0xe030 3.00000000 3037600 Sat Jul 21 17:48:59 2007
```
Then use the erase command to remove it:
```
bjavaloader erase CoolApp
```
After your phone and computer stop chatting again, the app should be gone. Ta-daa!

I hope this makes someone else as happy as myself. I stumbled over a patch announcement in barry-devel and the developers were extremely helpful and good natured with my questions. Be sure to give them some love (the monetary kind, if possible) for their hard work.

Good luck!

---

### Post by richardrblc on 2009-03-02
i could use some help when i try to load i get this error googled no retrun
"bjavaloader: symbol lookup error: bjavaloader: undefined symbol: _ZN5Barry4Mode10JavaLoaderC1ERNS_10ControllerE" any id
ads
:popcorn:

---

### Post by DirtDawg on 2009-03-03
> **richardrblc said:**
> i could use some help when i try to load i get this error googled no retrun
"bjavaloader: symbol lookup error: bjavaloader: undefined symbol: _ZN5Barry4Mode10JavaLoaderC1ERNS_10ControllerE" any id
ads
:popcorn:

I'm sorry but I don't have any idea what that means. The software is very cutting edge so there's plenty of opportunity for things to go wrong.

The developers have a [mailing list]("http://sourceforge.net/mailarchive/forum.php?forum_name=barry-devel"). Posting info is [here]("https://lists.sourceforge.net/lists/listinfo/barry-devel"). You can post without signing up. The developers are very friendly, would likely appreciate hearing of your error and may be able to help you fix it.

Sorry I can't help you further.

---

### Post by kevdog on 2009-03-03
Thanks for the writeup.  I tried the barry package a few months back and could never get the gui flag to work with the svn build.

---

### Post by DirtDawg on 2009-03-03
> **kevdog said:**
> Thanks for the writeup.  I tried the barry package a few months back and could never get the gui flag to work with the svn build.

Did you ever manage to get it working? Just curious.

---

### Post by kevdog on 2009-03-04
No -- this never worked for me:
./configure --enable-gui

I just simply did the plain old
./configure

skipping the gui, and this worked.

---

### Post by binbash on 2009-03-04
Cheers, it works

---

### Post by davidpodhola on 2009-04-09
In case of those strange "symbol lookup error" please make sure you have NO Berry .deb installed (use "sudo aptitude search barry" to be sure).

---

### Post by P Minix on 2009-04-21
btool: error while loading shared libraries: libbarry.so.0: cannot open shared object file: No such file or directory
pat@pat:/usr/local/bin$ bjavaloader
bjavaloader: error while loading shared libraries: libbarry.so.0: cannot open shared object file: No such file or directory

Everything built without errors (after installing automake and libtools); then same error as other methods.  

You should consider added a command line test for automake and libtools to the front of your instructions.

---

### Post by P Minix on 2009-04-29
BTW sudo fixes the " libbarry.so.0 " error.  So, need to run that down too.

---

### Post by DirtDawg on 2009-04-30
> **P Minix said:**
> BTW sudo fixes the " libbarry.so.0 " error.  So, need to run that down too.

So you use 'sudo bjavaloader' to avoid the libbarry.so error?

---

### Post by P Minix on 2009-05-08
Yes, sudo fixes many woes.  Been distracted trying to recover from 9.04 upgrade issues and will get back to this soon.

---

### Post by djg5826 on 2009-07-31
I am QUITE the newb to linux.  I'm trying to install barry on my computer but I get the following error message:

juan@GrayFamily:~/barry$ ./buildgen.sh
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `..'.
libtoolize: copying file `../ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `../m4'.
libtoolize: copying file `../m4/libtool.m4'
libtoolize: copying file `../m4/ltoptions.m4'
libtoolize: copying file `../m4/ltsugar.m4'
libtoolize: copying file `../m4/ltversion.m4'
libtoolize: copying file `../m4/lt~obsolete.m4'
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `..'.
libtoolize: copying file `../ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `../m4'.
libtoolize: copying file `../m4/libtool.m4'
libtoolize: copying file `../m4/ltoptions.m4'
libtoolize: copying file `../m4/ltsugar.m4'
libtoolize: copying file `../m4/ltversion.m4'
libtoolize: copying file `../m4/lt~obsolete.m4'
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `..'.
libtoolize: copying file `../ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `../m4'.
libtoolize: copying file `../m4/libtool.m4'
libtoolize: copying file `../m4/ltoptions.m4'
libtoolize: copying file `../m4/ltsugar.m4'
libtoolize: copying file `../m4/ltversion.m4'
libtoolize: copying file `../m4/lt~obsolete.m4'
configure.ac:177: warning: macro `AM_ICONV' not found in library
configure.ac:20: installing `./config.guess'
configure.ac:20: installing `./config.sub'
configure.ac:10: installing `./install-sh'
configure.ac:10: installing `./missing'
examples/Makefile.am: installing `./depcomp'
configure.ac:177: error: possibly undefined macro: AM_ICONV
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.


Please help!!!

---

