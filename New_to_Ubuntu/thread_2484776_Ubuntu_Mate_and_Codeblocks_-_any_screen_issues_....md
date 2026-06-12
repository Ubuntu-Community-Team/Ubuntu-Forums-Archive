---
title: "Ubuntu Mate and Codeblocks - any screen issues ..."
date: 2023-03-09
forum: New to Ubuntu
---

### Post by cwmoser on 2023-03-09
I'm getting some crazy display issues while running CodeBlocks 20.03 and wxWidgets.
Not finding any help searching the Internet so I'm wondering if there might be some clues here.
My 22.04 Ubuntu Mate runs perfectly with everything except when I run CodeBlocks.
In the IDE mode the various GUI elements seem to be erratic with corruption - not the software 
I am trying to create but with the actual CodeBlock program itself.
This problem occurs with all the Window managers - Compiz, and the various Marco managers.

Has anyone experienced this or have a clue as to how to fix this?

---

### Post by #&amp;thj^% on 2023-03-09
please try, this workaround and this fixes the problem for me.
```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```
My last use with mate 18.04 this worked, see if it still dose.
I just had to log-out and back in to notice the change.

---

### Post by cwmoser on 2023-03-09
I tried that command but no joy:

$ gsettings set com.canonical.desktop.interface scrollbar-mode normal
No such schema &#8220;com.canonical.desktop.interface&#8221;

---

### Post by cwmoser on 2023-03-10
Here is a Screen Recording demonstration this screen corruption in the IDE:

[https://www.youtube.com/watch?v=aTPA1602rfQ](https://www.youtube.com/watch?v=aTPA1602rfQ)

---

### Post by #&amp;thj^% on 2023-03-10
Carl you have not said what version of "wxWidgets" your currently using?
> Tip

Building some of the samples provided by the wx3.2-examples package may fail because of failure to detect GTK+ files. If so, try this compilation line:

LDFLAGS=$(pkg-config --libs gtk+-3.0) CXXFLAGS=$(pkg-config --cflags gtk+-3.0) make -j$(nproc)

If all else fails, you might need to create symlinks.

---

### Post by cwmoser on 2023-03-10
I've tried wxWidgets 3.2, 3.1, 3.0, and 2.8.

I've tried CodeBlocks from the repositories and just download, compiled and installed the latest version from source.
Same problem.

Could it be x11 vs Wayland issue?  Ubuntu Mate 22.04 uses x11.

---

### Post by #&amp;thj^% on 2023-03-10
> **cwmoser said:**
> I've tried wxWidgets 3.2, 3.1, 3.0, and 2.8.

I've tried CodeBlocks from the repositories and just download, compiled and installed the latest version from source.
Same problem.

Could it be x11 vs Wayland issue?  Ubuntu Mate 22.04 uses x11.
On Debian 12 unstable I use, well long story short I always use x11
Carl give me some time, I'm on fresh install of 22.04.2, I'll try to reproduce your gremlins.

---

### Post by #&amp;thj^% on 2023-03-10
I can't reproduce what your link showed, at least not yet anyway, I'll keep it up and see what results are with more time.
Here is my working install:
```
 apt policy codeblocks-contrib codeblocks
codeblocks-contrib:
  Installed: 20.03-3.1
  Candidate: 20.03-3.1
  Version table:
 *** 20.03-3.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
codeblocks:
  Installed: 20.03-3.1
  Candidate: 20.03-3.1
  Version table:
 *** 20.03-3.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
```
  Here is what I have for wx3 
   ```
apt policy libwxbase3.2-0-unofficial libwxbase3.2unofficial-dev libwxgtk3.2-0-unofficial  libwxgtk3.2unofficial-dev  wx3.2-headers  wx-common 
libwxbase3.2-0-unofficial:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxbase3.2unofficial-dev:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxgtk3.2-0-unofficial:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxgtk3.2unofficial-dev:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
wx3.2-headers:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
wx-common:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
     3.0.5.1+dfsg-4 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages



```
EDIT: 
```
inxi -Gxx | grep compositor
  Display: x11 server: X.Org v: 1.21.1.3 compositor: kwin_x11 driver: X:


```

---

### Post by cwmoser on 2023-03-10
Thanks 1fallen.
Sure would like to get CodeBlocks working properly.

---

### Post by #&amp;thj^% on 2023-03-10
I need to help first, then you can Thank me. ;)
I'm still sailing away on my end, hopefully then I'll be of use to you.

---

### Post by #&amp;thj^% on 2023-03-10
> **cwmoser said:**
> Thanks 1fallen.
Sure would like to get CodeBlocks working properly.
A friend just messaged me, claimed the flatpak version was a better choice.
FTR: I run a completely snap free zone, i wonder if that might be a potential problem? (Just a Guess) 
```
flatpak list | grep codeblocks
Code::Blocks    org.codeblocks.codeblocks       20.03   stable  system
```
I'm not sure your willingness on that just throwing things out to ponder.
This is a complete view for install:
```
flatpak list
Name                Application ID                                  Version    Branch         Installation
Code::Blocks        org.codeblocks.codeblocks                       20.03      stable         system
Mesa                org.freedesktop.Platform.GL.default             22.3.5     22.08          system
Mesa (Extra)        org.freedesktop.Platform.GL.default             22.3.5     22.08-extra    system
nvidia-525-85-05    org.freedesktop.Platform.GL.nvidia-525-85-05               1.4            system
openh264            org.freedesktop.Platform.openh264               2.1.0      2.2.0          system
Freedesktop SDK     org.freedesktop.Sdk                             22.08.9    22.08          system
Breeze GTK theme    org.gtk.Gtk3theme.Breeze                        5.27.2     3.22           s
```

---

### Post by #&amp;thj^% on 2023-03-11
Still good on my end, this is on Debian unstable today:
```
inxi -Gxx | grep compositor
  Display: x11 server: X.Org v: 1.21.1.7 I: xfwm v: 4.18.0 driver:

```
I don't think this is related to a specific compositor just yet, but I wonder if you use a text editor and if so is it "pluma"?
Most or all my codeblock work is done on a Plasma DE and "kate" is mt text editor for that.

---

### Post by cwmoser on 2023-03-11
$ inxi -Gxx | grep compositor
  Display: x11 server: X.Org v: 1.21.1.3 compositor: Compiz v: 0.9.14.1

Currently running Compiz but I get same screen corruption when I run Marco and its variants.

---

### Post by #&amp;thj^% on 2023-03-11
The folks @ CodeBlocks IDE recommend kwrite or kate, if using a text editor. (Vim or Geany)
You have not told me anything about that yet.
I've learned in my many years with Linux details mater. (referring to a text editor)

---

### Post by titaniuman on 2023-03-11
Check your graphics driver: Make sure that your graphics driver is up to date and compatible with your version of Ubuntu Mate. You can check the driver version by running the following command in the terminal: lshw -c video.

---

### Post by cwmoser on 2023-03-12
product: Turks PRO [Radeon HD 6570/7570/8550 / R5 230]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]


No updates for driver since 2015.  Running latest driver.

No other issues except with CodeBlocks.  
What are the requirements from C::B, or is it with wxWidgets?

---

### Post by #&amp;thj^% on 2023-03-12
> **cwmoser said:**
> 
No updates for driver since 2015.  Running latest driver.

No other issues except with CodeBlocks.  
What are the requirements from C::B, or is it with wxWidgets?
Video may be in play here then.
In post #8 I showed you was was needed for both CodeBlocks and wx3
Here is what I have for wx3
```

apt policy libwxbase3.2-0-unofficial libwxbase3.2unofficial-dev libwxgtk3.2-0-unofficial  libwxgtk3.2unofficial-dev  wx3.2-headers  wx-common 
libwxbase3.2-0-unofficial:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxbase3.2unofficial-dev:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxgtk3.2-0-unofficial:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxgtk3.2unofficial-dev:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
wx3.2-headers:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
wx-common:
  Installed: 3.2.0-1.jammy
  Candidate: 3.2.0-1.jammy
  Version table:
 *** 3.2.0-1.jammy 500
        500 https://repos.codelite.org/wx3.2.0/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
     3.0.5.1+dfsg-4 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages


```

---

### Post by cwmoser on 2023-03-14
I've installed the latest from source.

```

$ apt policy libwxbase3.2-0-unofficial libwxbase3.2unofficial-dev libwxgtk3.2-0-unofficial  libwxgtk3.2unofficial-dev  wx3.2-headers wx-common

libwxbase3.2-0-unofficial:
  Installed: 3.2.2.1-1.jammy
  Candidate: 3.2.2.1-1.jammy
  Version table:
 *** 3.2.2.1-1.jammy 100
        100 /var/lib/dpkg/status
libwxbase3.2unofficial-dev:
  Installed: 3.2.2.1-1.jammy
  Candidate: 3.2.2.1-1.jammy
  Version table:
 *** 3.2.2.1-1.jammy 100
        100 /var/lib/dpkg/status
libwxgtk3.2-0-unofficial:
  Installed: 3.2.2.1-1.jammy
  Candidate: 3.2.2.1-1.jammy
  Version table:
 *** 3.2.2.1-1.jammy 100
        100 /var/lib/dpkg/status
libwxgtk3.2unofficial-dev:
  Installed: 3.2.2.1-1.jammy
  Candidate: 3.2.2.1-1.jammy
  Version table:
 *** 3.2.2.1-1.jammy 100
        100 /var/lib/dpkg/status
wx3.2-headers:
  Installed: 3.2.2.1-1.jammy
  Candidate: 3.2.2.1-1.jammy
  Version table:
 *** 3.2.2.1-1.jammy 100
        100 /var/lib/dpkg/status
wx-common:
  Installed: 3.2.2.1-1.jammy
  Candidate: 3.2.2.1-1.jammy
  Version table:
 *** 3.2.2.1-1.jammy 100
        100 /var/lib/dpkg/status
     3.0.5.1+dfsg-4 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages


```

---

### Post by cwmoser on 2023-03-14
I've purchased a cheap nVidia video card off Ebay to replace my Radeon video card to see if that is the cause.

After I receive it I'll post the results.

---

### Post by #&amp;thj^% on 2023-03-17
> **cwmoser said:**
> I've purchased a cheap nVidia video card off Ebay to replace my Radeon video card to see if that is the cause.

After I receive it I'll post the results.

Please do I'm curious to see any changes in CodeBlocks IDE

---

