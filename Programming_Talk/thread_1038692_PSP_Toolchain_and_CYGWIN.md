---
title: "PSP Toolchain and CYGWIN"
date: 2009-01-13
forum: Programming Talk
---

### Post by angelsniper45 on 2009-01-13
SO ive recently migrated over to linux, and im a psp developer and ive been wondering where i can find the package to install the psp toolchain and cygwin resources on ubuntu. 

anybody know where these are?

---

### Post by HyperHacker on 2009-01-14
You don't need Cygwin on Ubuntu. Installing the PSP toolchain is a pain though. This is how I did it.

> **HyperHacker said:**
> OK, so here's all the hoops I had to jump through to get this thing installed and working! It's like solving some kind of ancient riddle. Lots of Googling, experimentation, and totally misleading error messages. And these scripts re-download, re-build etc everything every time they run, which can take hours, so if you don't do everything precisely right, you can end up spending an hour waiting just to see if it'll work this time. Argh!
This is installing on 32-bit Xubuntu 8.10 on December 14th 2008. YMMV. Good luck.
(hint: "~/" is a shortcut for "/home/yourusername/", and make sure you substitute "hyperhacker" for your own username.)

First off, run a bunch of command similar to [this](http://www.guztech.nl/index.php?option=com_content&view=article&id=49:setting-up-the-psptoolchain&catid=38:psp&Itemid=56), but not quite.
```
cd ~
sudo su
apt-get install gcc-4.2 autoconf automake bison flex gcc make libncurses5-dev libusb-dev patch subversion texinfo wget libgmp3-dev
mkdir psp
cd psp
```(There's at least one more thing I forgot the name of, but the script will error out and tell you what it is. Note that when it says "foo" it actually means install "libfoo-dev", most of the time...)
Now go [here](http://forums.exophase.com/showthread.php?t=7675) and download "PSP Custom Firmware 4.01 M33-2 Update". You will need this later. (Someone remind me to upload a mirror of this somewhere.)
Then:```
svn co svn://svn.ps2dev.org/psp/trunk/psptoolchain psptoolchain
cd psptoolchain
export PSPDEV=/usr/local/pspdev
export PATH=$PATH:$PSPDEV/bin
mkdir -p /usr/local/pspdev
chmod a+rxw /usr/local/pspdev
chown hyperhacker:hyperhacker /usr/local/pspdev
./toolchain.sh
```The last line will take at least an hour to run, possibly two or three. Pray it works.
```
cd ..
svn co svn://svn.ps2dev.org/psp/trunk/psplibraries psplibraries
apt-get install libtool
cd psplibraries
cp /usr/share/misc/config.guess ./build/freetype/builds/unix
```Stop here, because it needs to build some sort of IR keyboard demo or something (WTF?).
In the .rar file you downloaded earlier, for some reason is an "SDK" folder. Copy that entire folder into /usr/local/pspdev - you should end up with /usr/local/pspdev/SDK, with the contents: include, lib, psp-packer, samples, readme.txt.
Continue (and the next line will again take about half an hour):```
./libraries-sudo.sh
chown -R hyperhacker:hyperhacker /usr/local/pspdev
```Now add these lines to the end of ~/.bashrc using any text editor: (Note that this is a hidden file)```
export PSPDEV="/usr/local/pspdev"
export PSPSDK="$PSPDEV/psp/sdk"
export PATH="$PATH:$PSPDEV/bin:$PSPSDK/bin"
```


FINALLY, everything is installed, now if you want you can set up psplink:
```
cd ../psptoolchain/build/psplinkusb
make release
cd ../usbhostfs_pc
make
cd ../pspsh
make
```Now you can copy the PSPLink executable to your PSP (copy the ~/psp/psptoolchain/build/psplinkusb/release_oe/psplink folder to /PSP/GAME on your memory stick, or whatever you'd normally do to install homebrew), run it, run the PC-side app (in ~/psp/psptoolchain/build/psplinkusb/usbhostfs_pc), and use it as described in the manual. Except the part where it tells you to load a .elf file, that doesn't work with recent versions, so just continue on to making and loading the .prx. If all goes well you'll see a trippy graphic on the PSP screen.

That was nuts, now go out for a beer or something, you've earned it. I'm going to sleep. @_@Have fun.

---

### Post by angelsniper45 on 2009-01-14
on the first set of lines that you run, it gets the information i need but then right before installation it says abort, im using root permissions and normal permissions. whats wrong?

---

