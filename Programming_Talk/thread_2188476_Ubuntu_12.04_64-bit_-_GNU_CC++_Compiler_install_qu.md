---
title: "Ubuntu 12.04 64-bit - GNU C/C++ Compiler install question"
date: 2013-11-17
forum: Programming Talk
---

### Post by Xinghao_Chen on 2013-11-17
Hello: I am a newbie, for both Ubuntu and C/C++ programming. I asked for advice on the General Help forum but have not received the specific answer. 

[http://ubuntuforums.org/showthread.php?t=2188169](http://ubuntuforums.org/showthread.php?t=2188169)

I am hoping the experts/gurus here can spare me several minutes, help me with explanations and advice to enable me get the GNU C/C++ compiler installed.

Here are the background:

I recently installed Ubuntu 12.04 64-bit on my ThinkPad T400 (Intel DUO 2 T9400, 2.53GHz x 2, 4GB DDR3 RAM) with a DVD install disk made from the amd64 ISO download. The Ubuntu install is on a 32GB Sandisk Cruzer Fit USB memory. The install contains no system updates, just what in the amd64 ISO. (I am holding the system updates in the bay - a previouse system update silenced the speakers and caused other issues with Adobe Flash Player. This is a fresh re-install from the DVD install disk.) Everything seems to work fine.

Now to the core of my question:

I need to install the GNU C/C++ compiler. I was advised on the General Help forum to run 

apt-cache depends build-essential

to check/understand what would be installed and run

sudo apt-get install build-essential

to install the GNU package.

Here are the outputs of the apt-cache depends check:

xinghao@CTC-Ubuntu-64:~$ apt-cache depends build-essential
build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: gcc
  Depends: g++
  Depends: make
  Depends: dpkg-dev
  Conflicts: build-essential:i386
xinghao@CTC-Ubuntu-64:~$ 

My question/concern is the meaning of the "Conflicts" line.

I ran the same apt-cache depends check on the other Ubuntu 12.04 32-bit install (already has the GNU C/C++ compiler installed) on a different ThinkPad; the outputs are the same except absent of the conflicts line. I need to have this "Conflicts" inssue answered/understood before I can be confident to install the GNU package.

Thank you.

---

### Post by Bachstelze on 2013-11-17
It simply means that you can't install the 64-bit and 32-bit versions of build-essential concurrently. The line does not appear on a 32-bit system because then you can't install 64-bit packages anyway, so there's no point in stating it explicitly.

---

### Post by Xinghao_Chen on 2013-11-17
Thanks for the reply. So how do I go about install a 64-bit GNU C/C++ compiler on my 64-bit Ubuntu 12.04 platform?

PS: I thought that, since it would be run on a 64-bit Ubuntu machine, apt-get install would pick the matching 64-bit GNU C/C++ compiler to install. Is this not so?

---

### Post by Bachstelze on 2013-11-17
> **Xinghao_Chen said:**
> 
PS: I thought that, since it would be run on a 64-bit Ubuntu machine, apt-get install would pick the matching 64-bit GNU C/C++ compiler to install. Is this not so?

It is so, what makes you think otherwise?

---

### Post by Xinghao_Chen on 2013-11-17
I am confused and lost here.

I was runing apt-cache depends on a 64-bit Ubuntu, with the intend to run apt-get install build-essential (to install a 64-bit version of the GNU C/C++ package), why apt-cahe gave the "Conflicts" line (as you explained, for 64-bit - 32-bit conflicts)?

---

### Post by Bachstelze on 2013-11-17
> **Xinghao_Chen said:**
> I am confused and lost here.

I was runing apt-cache depends on a 64-bit Ubuntu, with the intend to run apt-get install build-essential (to install a 64-bit version of the GNU C/C++ package), why apt-cahe gave the "Conflicts" line (as you explained, for 64-bit - 32-bit conflicts)?

Because that's how it is, you can't install both the 64- and 32-bit version at the same time. You don't want to do that anyway, so go ahead and install the 64-bit one, what's the problem?

---

### Post by Xinghao_Chen on 2013-11-17
Hum ..., let me sort this:

On a 32-bit Ubuntu, outputs of apt-cache depends do not have the "Conflicts" line because apt-get install will not install a 64-bit package on a 32-bit platform. 

If on a 64-bit Ubuntu apt-get install picks (only) 64-bit package to install, for what purpose the apt-cache depends check gives this "Conflicts" line? To me it would be just like on the 32-bit platform. no Conflicts" line.   

My 64-bit Ubuntu doesn't have any version GNU C/C++ compiler installed. There is no concorrunt 64-bit and 32-bit install conflicts exist. Why it is warning me on the 64-bit Ubuntu and not on the 32-bit one (since the same argument can be made on a 32-bit Ubuntu)? 

This is getting interesting.

---

### Post by Bachstelze on 2013-11-17
> **Xinghao_Chen said:**
> 
On a 32-bit Ubuntu, outputs of apt-cache depends do not have the "Conflicts" line because apt-get install will not install a 64-bit package on a 32-bit platform.

If on a 64-bit Ubuntu apt-get install picks (only) 64-bit package to install, for what purpose the apt-cache depends check gives this "Conflicts" line? To me it would be just like on the 32-bit platform. no Conflicts" line.   

On a 64-bit system, you can install 32-bit version of packages, if you want. Most of the time, you can have both the 32-bit and 64-bit versions of a package installed at the same time. But for build-essential, you can't, that's what the Conflicts line says. But this does not concern you, because you don't want to install the 32-bit version anyway.

There is no need to add a Conflicts line to the pakage on 32-bit systems, because you cannot install 64-bit packages on a 32-bit system anyway. This is not specific to build-essential.

apt-cache depends shows the Conflicts line because it is part of the dependency-related information of the package. That does not mean it concerns you. It is not "warning" you about anything.

---

### Post by Xinghao_Chen on 2013-11-17
Now, this is a clear and precise explanation that I can understand.

Thank you very much for putting my mind to peace this "Conflicts" - I know if I don't understand this and went ahead to install the 64-bit GNU C/C++ compiler package, I would be hunted by the "Conflicts" whenever I may have C/C++ problems. Your expanation plugs the hole.

---

