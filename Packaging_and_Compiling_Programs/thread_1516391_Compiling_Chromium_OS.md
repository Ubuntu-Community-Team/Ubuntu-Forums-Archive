---
title: "Compiling Chromium OS"
date: 2010-06-23
forum: Packaging and Compiling Programs
---

### Post by Penguin Guy on 2010-06-23
I had a shot at compiling Chromium-OS and everything seemed to go okay, but it won't boot. Is it something I did wrong, or a Chromium problem? Anyone else compiled it? Any suggestions?

Here are the commands I entered to compile it and install it to my USB drive:
[PHP]
cd ~/Desktop
sudo apt-get install git-core subversion
svn co http://src.chromium.org/svn/trunk/tools/depot_tools
export PATH="`pwd`/depot_tools:$PATH"
gclient config http://src.chromium.org/git/chromiumos.git
gclient sync
cd chromiumos.git/src/scripts
./make_chroot
./enter_chroot.sh
cd ~/trunk/src/scripts
./setup_board --board=x86-generic
./build_packages --board=x86-generic
./build_image --board=x86-generic
exit
./image_to_usb.sh --from=../build/images/x86-generic/0.7.47.2010_06_13_0333-a1 --to=/dev/sdb
[/PHP]

---

### Post by kaustavdm on 2010-07-23
```
[COLOR=#000000][COLOR=#0000bb]export PATH[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#dd0000]"`pwd`/depot_tools:$PATH" [/COLOR][/COLOR]
```This is just a guess, aren't the double quotes in the wrong places? Will it be something like this? :

```
[COLOR=#006000][FONT=monospace]$ export PATH=`pwd`/depot_tools:"$PATH"[/FONT][/COLOR]
```This is what is mentioned in [http://dev.chromium.org/developers/how-tos/install-gclient](http://dev.chromium.org/developers/how-tos/install-gclient)

---

### Post by Penguin Guy on 2010-07-23
> **kaustavdm said:**
> This is just a guess, aren't the double quotes in the wrong places? Will it be something like this? :

```
export PATH=`pwd`/depot_tools:"$PATH"
```
It doesn't make a difference either way, but it's usually considered good practice to place the entire assignment in quotes. Anyway, that isn't the part that's causing the problem.

---

### Post by kaustavdm on 2010-07-23
Ok. I'm downloading the source now. I'll try to compile it and report back. Presently, I want to run it in Virtualbox OSE. So, i'll try to build an ISO image from it.

---

