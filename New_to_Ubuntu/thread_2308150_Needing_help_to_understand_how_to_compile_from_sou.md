---
title: "Needing help to understand how to compile from source"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by Myke_Nogueira on 2015-12-31
Hi, Ubuntu forums! I'm a newcomer into Linux, and just got into some troube trying to compile software. Here's what happened

I downloaded the libimobiledevice-1.2.0 tarball, and used ./configure to built it. But then, after the process started, terminal got stuck in this error:

[B]checking for libusbmuxd... no
configure: error: Package requirements (libusbmuxd >= 1.0.9) were not met:

No package 'libusbmuxd' found[/B]

I proceeded to fix this. First, tried using "sudo apt-get install libusbmuxd", but that doesn't worked. All I got was a message saying it way impossible retrieve the package. Finally, after using Google, could get it downloaded. 

Thought is was ok, but..when trying to compile **libusbmuxd**, terminal showed this:

[B]Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libxml-2.0', required by 'libplist', not found


[/B]That's basically it. I kept downloading stuff that required more downloads. Just want the software to run. Is there any way to list everything that has to be downloaded before using ./configure?  The result of this madness is: I can't get anything that needs compling to work. I tried compiling minidlna also, got stucked in the same thing. Do you guys have any advice on this? Help would be really appreciated.

---

### Post by steeldriver on 2015-12-31
In Ubuntu, the pieces that you need to build software that depends on a library are usually split out into a separate -dev package: in this case, **libusbmuxd-dev**

There's a utility called **auto-apt** however personally I tend to just figure out the dependencies myself

If the repo contains a version of the thing you're trying to install, and the dependencies haven't changed much, then apt-get build-dep is sometimes helpful

---

### Post by sandyd on 2015-12-31
If your using anything newer than Ubuntu 14.04 LTS, (and is not a EOL release), you should have [libusbmuxd]("https://launchpad.net/ubuntu/+source/libusbmuxd")

In the future, you can find packages with the command:
```

apt-cache search libusbmuxd
```

That being said, the configure command says it is missing "libxml".
When compiling a program, you will need what is called the "development libraries/files" of any required libraries/software. In Ubuntu, this is a separate package.

In Ubuntu, the naming convention is usually <packagename>-<dev> for the development files for a library or software. Sometimes, the version of the library is tacked on. The library is called libxml, so you can use apt-cache to search for it, and find that the package is called "libxml2", and the package for the development files is called libxml2-dev.

Enjoy :)

---

### Post by Myke_Nogueira on 2015-12-31
Thank you, guys! That was really helpfull! Just one more thing, the -dev packages won't require other dependencies to work, right?

---

### Post by sandyd on 2015-12-31
> **Myke_Nogueira said:**
> Thank you, guys! That was really helpfull! Just one more thing, the -dev packages won't require other dependencies to work, right?

If there are any dependencies that the -dev packages require, apt will pull them in automatically.

---

### Post by oldos2er on 2015-12-31
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by kevdog on 2016-01-01
It sounds like you already have the build-essential package installed from within Ubuntu.  Usually when I want to compile from source, there is a specific reason.  I usually have to ask myself before compiling -- why am I compiling this and not using the package contained within the Ubuntu repositories?  Sometimes the answer is because its not in the repository, I want a newer version, I need special features etc.  Usually when I choose to compile, I either scour the webpage from where I'm getting the source code.  Often the source code is from a git repository and it contains a wiki page where it lists specifically the dependencies or libraries it needs to compile.  If it isn't listed there, then sometimes there is a README file that contains this information.  If all else fails I just run the ./autogen.sh script first (if there is one), and then the ./configure script. As you found out the ./configure process checks for the dependent libraries and oftentimes stops when it can't find the dependency.  As mentioned above, you need to learn how to found the library it's requesting.  This is definitely where the apt-cache search command works.  Here is what I get when I run the apt-cache search command for your library:

```

kevdog@ubuntu-server:~$ apt-cache search libusbmux
libusbmuxd-dev - USB multiplexor daemon for iPhone and iPod Touch devices - devel
libusbmuxd2 - USB multiplexor daemon for iPhone and iPod Touch devices - library
libusbmuxd2-dbg - USB multiplexor daemon for iPhone and iPod Touch devices - debug

```

As mentioned above you want the -dev package when compiling from source so you would install the libusbmuxd-dev.  Since Ubuntu is a very widely used Linux install, oftentimes if the project has a wiki page they will specifically list the names of the -dev library that Ubuntu/Debian uses.  These library names however if your using a different linux distribution. For example here is the equivalent in my Arch distribution:

```

[kevdog@MacArch ~]$ pacaur -Ss libusbmux
extra/libusbmuxd 1.0.10-1 [installed]
    USB Multiplex Daemon
aur/libusbmuxd-git 1.0.10.r2.g6799f3b-1 (6, 0.19)
    The usbmuxd communication interface library

```

You can see the package names are slightly different.  I would just keep running the ./configure script until all the necessary libraries are installed (using a combination of apt-cache search and apt-get install).  Oftentimes the ./configure script will say you don't have optional libraries installed, so make a mental note if you think you need these and install the necessary optional libraries if you think you need them. 

Oftentimes what you want to do however, this is often a ppa available. I usually look in the Ubuntu repositories first for the package, search the web for a ppa, and then if unsuccessful compile from source.  Hopefully that helps

---

