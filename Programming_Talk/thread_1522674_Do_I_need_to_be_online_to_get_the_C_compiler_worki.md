---
title: "Do I need to be online to get the C compiler working in Ubuntu?"
date: 2010-07-02
forum: Programming Talk
---

### Post by stirbad on 2010-07-02
Right now I don't have an internet connection for a desktop running Ubuntu, and I was wondering if I need to get it online if I were to get a C compiler working. I do have access to the internet through this laptop and I have a USB stick, so I can transfer files via USB if needed. Anyone have any insight on this?

---

### Post by Bachstelze on 2010-07-02
Depending on which type of Ubuntu CD you have, you might be able to install the compiling toolchain from the CD. I know the Alternate CD has it, but don't know about the Desktop or Server ones.

You can always download the Alternate ISO and install it wrom there, though.

---

### Post by stirbad on 2010-07-02
> **Bachstelze said:**
> Depending on which type of Ubuntu CD you have, you might be able to install the compiling toolchain from the CD. I know the Alternate CD has it, but don't know about the Desktop or Server ones.

You can always download the Alternate ISO and install it wrom there, though.

I didn't see such an option when installing Ubuntu, but then again, I'm completely new to Ubuntu so I may have overlooked it. Is installing the compiling toolchain straightforward if I were to burn an Alternate ISO?

---

### Post by tgalati4 on 2010-07-02
Open a terminal:

sudo apt-get install build-essentials

You only need to be online to download the *-dev packages for anything that you want to build, in addition the the stuff pulled in by build-essentials.

For instance if you want to compile audacity (sound editing program) for your system you would need to pull in several libraries--and you need to be online for that.  You also need to enable the "source" repositories in synaptic or /etc/apt/sources.list.  These source code repositories are separate from the normal binary repositories where you get your updates from.

So, although you don't need to be online to compile, you do need to download quite a few packages (that may or may not be on your distro CD).  Setting up your build environment is critical to successful compiling.

When you start "making" programs, the "configure" program will highlight what libraries/elements are missing from your build environment.  Install them and continue on.  

There will be times that you want to build an application, but you don't have to proper build environment--such as trying to compile the latest Banshee in Dapper Drake.  This will lead you to "Dependency Hell", an apt description for what happens when you try to build new packages inside an old environment and vice versa.

---

