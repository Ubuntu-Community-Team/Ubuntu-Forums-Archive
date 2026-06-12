---
title: "Getting an install to run from a .tar.bz2 file?"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by psychmesu on 2011-12-18
I have an application that I would like to run however the installer is located within a .tar.bz2 file. I can't seem to get the application so that it will launch. Any ideas as to what I should be doing? I'm running 10.4.3 if that's helpful. Thanks.

---

### Post by Rex Bouwense on 2011-12-18
Try here:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
By the way welcome to the forums.:popcorn:

---

### Post by MG&amp;TL on 2011-12-18
What app is it? It's probably in the repos.

If not, extract it, then could you post the contents of the extracted directory.

---

### Post by ExileAmongYou on 2011-12-18
A .tar.bz2 file could be a lot of things, since it's basically just the same as a .zip file, i.e. a compressed folder. It could be source code, an installer that the developer has written themselves, or just the application itself. It might be best if you let us know what application it is and provide a link to the site you downloaded it from.

---

### Post by psychmesu on 2011-12-18
> **ExileAmongYou said:**
> A .tar.bz2 file could be a lot of things, since it's basically just the same as a .zip file, i.e. a compressed folder. It could be source code, an installer that the developer has written themselves, or just the application itself. It might be best if you let us know what application it is and provide a link to the site you downloaded it from.

I get that it's akin to a .zip file. What I'm not getting is why I can't extract and run it. I can see what I assume is the installer within the .tar.bz2 file but I can't get it to launch. The application is the Linux viewer for Second Life. The download site is here: 

[http://secondlife.com/support/system-requirements/?lang=en-US](http://secondlife.com/support/system-requirements/?lang=en-US)

The .tar file I received from the download is SecondLife-i686-3.2.4.246439.tar.bz2

---

### Post by lechien73 on 2011-12-18
You could open a terminal window and type:

```
tar jxf SecondLife-i686-3.2.4.246439.tar.bz2
```

Then cd to the SecondLife folder, and type:

```
./install.sh
```

If the install script doesn't have the executable bit set, then type:

```
chmod +x ./install.sh
```

Then try the ./install.sh command again.

---

### Post by astrognome on 2011-12-18
Apparently, you can either install or run the program via the contents of the tar.bz2 file.  Un-tar the package either via the command line (tar -xvf nameofpackage.tar.bz2), or using your file manager by right clicking on the package.  Once extracted, you can either run the application, or install it.

If you install, or run the application, it seems that you would need the correct OpenGL video drivers.

---

### Post by psychmesu on 2011-12-18
> **lechien73 said:**
> You could open a terminal window and type:

```
tar jxf SecondLife-i686-3.2.4.246439.tar.bz2
```

Then cd to the SecondLife folder, and type:

```
./install.sh
```

If the install script doesn't have the executable bit set, then type:

```
chmod +x ./install.sh
```

Then try the ./install.sh command again.

This is what I get:

susan@susan-laptop:~$ tar jxf SecondLife-i686-3.2.4.246439.tar.bz2
tar: SecondLife-i686-3.2.4.246439.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

I am an extreme Linux novice so I'm not sure why it is not finding the file or directory when I can see it in my download folder. I tried it this way as well as trying a sudo command line. Same results with both.

---

### Post by wuweiaa on 2011-12-18
> **psychmesu said:**
> I have an application that I would like to run however the installer is located within a .tar.bz2 file. I can't seem to get the application so that it will launch. Any ideas as to what I should be doing? I'm running 10.4.3 if that's helpful. Thanks.
Step 1: Prep your system for building packages
sudo apt-get install build-essential checkinstall
sudo apt-get install cvs subversion git-core mercurial
sudo chown $USER /usr/local/src
sudo chmod u+rwx /usr/local/src
Step 2: Getting the software you want
tar -xzvf tarballname.tar.gz
tar -xjvf tarballname.tar.bz2
autogen.sh 
make 
Step 3: Resolving Dependencies.
configure: error: Library requirements (gobbletygook) not met, blah blah blah stuff we don't care about
apt-file search missingfilename.pc
sudo apt-get install requiredpackage
Step 4: Build and install.
make
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
By the way welcome to the forums.

---

### Post by azmyth on 2011-12-18
I suspect you're not in the directory that contains the tar file. If you downloaded with a browser then you need to go to the proper directory

```
cd Downloads
tar jxf SecondLife-i686-3.2.4.246439.tar.bz2
```

You can install or you can run it from the directory
```

cd SecondLife-i686-3.2.4.246439
chmod +x secondlife
./secondlife
```

or you can install with the install.sh file

---

### Post by psychmesu on 2011-12-18
> **wuweiaa said:**
> [B]Step 1: Prep your system for building packages
sudo apt-get install build-essential checkinstall
sudo apt-get install cvs subversion git-core mercurial
sudo chown $USER /usr/local/src
sudo chmod u+rwx /usr/local/src
Step 2: Getting the software you want
tar -xzvf tarballname.tar.gz
tar -xjvf tarballname.tar.bz2
autogen.sh 
make 
Step 3: Resolving Dependencies.
configure: error: Library requirements (gobbletygook) not met, blah blah blah stuff we don't care about
apt-file search missingfilename.pc
sudo apt-get install requiredpackage
Step 4: Build and install.
make
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
By the way welcome to the forums.[/B]

And this is what happens:


susan@susan-laptop:~$ sudo apt-get install build-essential checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 libvpx0 linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch xz-utils
Suggested packages:
  gettext debian-keyring debian-maintainers g++-multilib g++-4.4-multilib
  gcc-4.4-doc libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed:
  build-essential checkinstall dpkg-dev fakeroot g++ g++-4.4
  libstdc++6-4.4-dev patch xz-utils
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,696kB of archives.
After this operation, 25.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
susan@susan-laptop:~$ 

Why would it abort?

---

### Post by psychmesu on 2011-12-18
> **azmyth said:**
> I suspect you're not in the directory that contains the tar file. If you downloaded with a browser then you need to go to the proper directory

```
cd Downloads
tar jxf SecondLife-i686-3.2.4.246439.tar.bz2
```

You can install or you can run it from the directory
```

cd SecondLife-i686-3.2.4.246439
chmod +x secondlife
./secondlife
```

or you can install with the install.sh file

I tried both sets of code as well as trying to launch from the install.sh file and it still won't launch. Not sure what I'm doing wrong :confused:

---

### Post by oldos2er on 2011-12-18
Can you please copy and paste all the terminal output here?

---

### Post by ExileAmongYou on 2011-12-18
> **psychmesu said:**
> This is what I get:

susan@susan-laptop:~$ tar jxf SecondLife-i686-3.2.4.246439.tar.bz2
tar: SecondLife-i686-3.2.4.246439.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

I am an extreme Linux novice so I'm not sure why it is not finding the file or directory when I can see it in my download folder. I tried it this way as well as trying a sudo command line. Same results with both.

Okay, so the reason why this failed is that when you opened the terminal, you hadn't navigated to the downloads folder. By default when you open a terminal, you are in your home folder. You can look at the contents of the folder you are currently in by typing "ls", and navigate to a directory using "cd", e.g. "cd Downloads".

An easy way to get to the right folder is to install the "nautilus-open-terminal" package.
```
sudo apt-get install nautilus-open-terminal
```
Then you will be able to open the right folder in the file browser, right click on any empty space in that folder, and choose "Open in terminal" from the menu. Once you have the terminal open in the right directory, you should be able to follow the instructions others have posted, i.e.
```
tar jxf SecondLife-i686-3.2.4.246439.tar.bz2
```

```
cd SecondLife-i686-3.2.4.246439
chmod +x secondlife
./secondlife
```

You don't have to install buildessential and checkinstall like wuweiaa suggested, because you aren't building the application from source code, it's already compiled and you just have to run it.

---

### Post by psychmesu on 2011-12-18
> **ExileAmongYou said:**
> Okay, so the reason why this failed is that when you opened the terminal, you hadn't navigated to the downloads folder. By default when you open a terminal, you are in your home folder. You can look at the contents of the folder you are currently in by typing "ls", and navigate to a directory using "cd", e.g. "cd Downloads".

An easy way to get to the right folder is to install the "nautilus-open-terminal" package.
```
sudo apt-get install nautilus-open-terminal
```
Then you will be able to open the right folder in the file browser, right click on any empty space in that folder, and choose "Open in terminal" from the menu. Once you have the terminal open in the right directory, you should be able to follow the instructions others have posted, i.e.
```
tar jxf SecondLife-i686-3.2.4.246439.tar.bz2
```

```
cd SecondLife-i686-3.2.4.246439
chmod +x secondlife
./secondlife
```

You don't have to install buildessential and checkinstall like wuweiaa suggested, because you aren't building the application from source code, it's already compiled and you just have to run it.

Ok, I see what you're saying by not having called up the correct directory. I made that correction and did get it to launch. It's still not working properly but I think that's an issue I'm going to try to take up with SL support. Thank you all so much for all of your help :)

---

