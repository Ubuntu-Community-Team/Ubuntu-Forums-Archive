---
title: "Over my head"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by deeptendu on 2008-09-30
I just switched to ubuntu this weekend since my computer came with Windows Vista and it had all but totally quit on me. Anyway, I love it so far except for installing 32 bit programs since I had unwittedly received the 64 bit version. For me **dpkg -i --force-architecture **is not working.
This is the error it gave me:
[B] error processing MEGA-4-02.i386.rpm (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 MEGA-4-02.i386.rpm[/B]
The program I need is MEGA [http://www.megasoftware.net/mega_linux.html](http://www.megasoftware.net/mega_linux.html) which needs Wine to work. I downloaded alien and tried to use the instructions on the site to go from .rpm->.deb but the file it created was just called MEGA-4 and under properties it said some content was unreadable. Wine however seemed to download ok and is now avalible under 'Applications'.
So do I need to go to .deb for --force-architecture to work? Is there any way to do this without alien?

Thanks for any help in advance.

---

### Post by steveneddy on 2008-09-30
Not to sound like a smarty pants, but have you tried searching the 64 bit forums?

[http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

---

### Post by phidia on 2008-09-30
Install the ia32-libs package and maybe the getlibs package too. getlibs is avaiable as a deb. Hopefully that will get you running.

---

### Post by nightcrawler27 on 2008-09-30
Wow this is rough...unfortunately Wine nor Alien are not always that reliable and apparently the developers of MEGA don't seem to be that into Linux. On top of that you are doing this with a 32 bit app on a 64 bit system. Did you use the command "sudo alien -k name-of-package.rpm"? Aside from that, or possibly getting the source code and compiling the app yourself, my first reaction would be to either try it on 32 bit Ubuntu or install a VM package like VirtualBox or VMWare and install Vista under a VM to use the application.

Nightcrawler27

> **deeptendu said:**
> I just switched to ubuntu this weekend since my computer came with Windows Vista and it had all but totally quit on me. Anyway, I love it so far except for installing 32 bit programs since I had unwittedly received the 64 bit version. For me **dpkg -i --force-architecture **is not working.
This is the error it gave me:
[B] error processing MEGA-4-02.i386.rpm (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 MEGA-4-02.i386.rpm[/B]
The program I need is MEGA [http://www.megasoftware.net/mega_linux.html](http://www.megasoftware.net/mega_linux.html) which needs Wine to work. I downloaded alien and tried to use the instructions on the site to go from .rpm->.deb but the file it created was just called MEGA-4 and under properties it said some content was unreadable. Wine however seemed to download ok and is now avalible under 'Applications'.
So do I need to go to .deb for --force-architecture to work? Is there any way to do this without alien?

Thanks for any help in advance.

---

### Post by deeptendu on 2008-09-30
I did use **alien -k MEGA-4-02.i386.rpm** but I tried it again and it said:
**File "MEGA-4-02.i386.rpm" not found.**

I have ia32-libs and have installed getlibs but this is what it gave me:
[B]getlibs -p MEGA-4-2.i386.rpm
The following i386 packages will be installed: MEGA-4-2.i386.rpm
Continue [Y/n]? y
W: Unable to locate package MEGA-4-2.i386.rpm
E: No packages found
MEGA-4-2.i386.rpm was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install[/B]

The file is on my desktop and I'm sure I've been inputting the name right since I've copied it straight from the files properties.

---

### Post by karlr42 on 2008-09-30
Move the file to your home directory-
```
mv ~/Desktop/MEGA-4-02.i386.rpm ~
```

Then it should work.

---

### Post by deeptendu on 2008-09-30
OK, I moved the MEGA file. Used alien. This created a file named MEGA-4 (still doesn't end with .deb). Tried this:
** dpkg -i --force-architecture MEGA-4 **

[B]dpkg-split: error reading MEGA-4: Is a directory
dpkg: error processing MEGA-4 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 MEGA-4[/B]

Went back to original installation instructions:
[B] yum install rpm
There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named cElementTree

Please install a package which provides this module, or
verify that the module is installed correctly.
[/B]
And then:
[B] rpm -i MEGA-4-02.i386.rpm
error: Failed dependencies:
	/bin/sh is needed by MEGA-4-02.i386
	wine is needed by MEGA-4-02.i386
[/B]

I'm so very very lost.

---

### Post by Tatty on 2008-10-01
Ignore the bit in the instructions about YUM - that is the red hat package management system and is not used in debian based distros (like Ubuntu).

lets see what files you now have cd to the directory you are working in (I presume it is the Desktop if you followed karlr42) and list the file contents, then copy and paste here:

```
cd ~/Desktop
ls -l
```

---

### Post by JoshuaRL on 2008-10-01
First off, just a little tip.  You can input code or terminal commands and output in [noparse]```
 
```[/noparse] tags.  For instance:
```

sudo apt-get install this-is-code

```

> **deeptendu said:**
> OK, I moved the MEGA file. Used alien. This created a file named MEGA-4 (still doesn't end with .deb). Tried this:
** dpkg -i --force-architecture MEGA-4 **

[B]dpkg-split: error reading MEGA-4: Is a directory
dpkg: error processing MEGA-4 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 MEGA-4[/B]

Went back to original installation instructions:
[B] yum install rpm
There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named cElementTree

Please install a package which provides this module, or
verify that the module is installed correctly.
[/B]
And then:
[B] rpm -i MEGA-4-02.i386.rpm
error: Failed dependencies:
	/bin/sh is needed by MEGA-4-02.i386
	wine is needed by MEGA-4-02.i386
[/B]

I'm so very very lost.

I'd like to say thanks for telling me about yum.  I didn't know we had that, thought that was only for Red Hat based stuff.  So I installed it just to see what it would do.  And when I tried to run an update, I came up with the same broken python module.  I found [this thread](http://www.linuxquestions.org/questions/fedora-35/yum-celementtree-python-485194/) that may fix it, but I couldn't get it to work since it seems to need to have yum running.

I think your problem here is that you are trying to run with two converters.  First for 64bit to 32bit, then from RPM to APT.  So you would need to cut down on either one or the other.  So try to find a 64bit version of MEGA.  But I'll be honest, I couldn't find one.  So your best bet may be to either reinstall a 32bit version of Ubuntu, or run a virtualized 32bit.

---

### Post by nowshining on 2008-10-01
first u didn't cd to the Desktop/ if it was on ur desktop, 2nd do sudo apt-get install fakeroot, then instead of sudo put fakeroot in front of the alien command with the -d option, etc.. to make a deb, from there either double-click on it or sudo dpkg -i nameofpackage, etc.. u can use tab completion...

edit: either way  after u install the item, go back to the terminal and issue sudo ldconfig as this resets the libs and makes any not available available for use by any programs that need them, where they could be found, etc...

---

### Post by nightcrawler27 on 2008-10-01
As many suggestions as we might be able to provide in this thread, what JoshuaRL and I have both mentioned is probably the best course of action. If you can get your system in order as far as 32/64 bit goes and/or use some form of virtual environment, it would make life a lot easier for you both now and in the future...provide an environment that will best run your application, rather than forcing the application to work in your environment. Even if the conversion, etc is successful, there is still a good chance that your application will not run as well as you expect.

Nightcrawler27

> **JoshuaRL said:**
> 

I think your problem here is that you are trying to run with two converters.  First for 64bit to 32bit, then from RPM to APT.  So you would need to cut down on either one or the other.  So try to find a 64bit version of MEGA.  But I'll be honest, I couldn't find one.  So your best bet may be to either reinstall a 32bit version of Ubuntu, or run a virtualized 32bit.

---

### Post by deeptendu on 2008-10-01
In responce to Tatty:
[B]total 4
drwxr-xr-x 5 root root 4096 2008-09-30 20:03 MEGA-4[/B]

In responce to nowshining:
[B]fakeroot alien -d MEGA-4-02.i386.rpm
mkdir: cannot create directory `MEGA-4': File exists
unable to mkdir MEGA-4:  at /usr/share/perl5/Alien/Package.pm line 257.[/B]

---

### Post by nowshining on 2008-10-01
> **deeptendu said:**
> In responce to Tatty:
[B]total 4
drwxr-xr-x 5 root root 4096 2008-09-30 20:03 MEGA-4[/B]

In responce to nowshining:
[B]fakeroot alien -d MEGA-4-02.i386.rpm
mkdir: cannot create directory `MEGA-4': File exists
unable to mkdir MEGA-4:  at /usr/share/perl5/Alien/Package.pm line 257.[/B]

remove the mega-4 directory and try again...

---

