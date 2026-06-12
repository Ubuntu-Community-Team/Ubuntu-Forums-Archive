---
title: "HOWTO: Use -vo xvidiv with MPlayer as a normal user (svgalib_helper module)"
date: 2007-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by DanPT on 2007-08-18
*Note:For those with who first install MPlayer and get [Error Message - Error Opening/Initializing Video Out (-vo) Device] it mean that the -vo device selected does not work.If you use the version installed from ubuntu package right click on the player and select preference. Go to the Video tab and select an other -vo device. xv should work with most system. xvidix is faster but you need to follow my guide to make it work

[SIZE=3]**Short:**[/SIZE]

With MPlayer the xvidiv ( vidix ) driver use less processor than the xv. (In xv the X.org process use more processor in addition to Mplayer. In xvidix X.org use 0% cpu. Therefore less cpu total is use in xvidix mode) According to MPlayer Doc  "[The] main goal of this interface [xvidix] is to maximize the speed of video playback." 

The problem is with a fresh install of Ubuntu and the MPlayer provide by ubuntu package, you need root access to use the xvidix since the xvidix driver scan your hardware to detect your video card. A normal user have a -vo error( Error Message - Error Opening/Initializing Video Out (-vo) Device ). If you start gmplayer with the terminal you can see that it try to do a pci scan and cannot. You can use sudo gmplayer and it will work but it not a convenient  workaround.

[**Reference:** Mplayer vidix Documentation]("http://www.mplayerhq.hu/DOCS/HTML/en/vidix.html")

The doc recommend to use the svgalib_helper module to correct this situation. However the instruction can be confusing and some significant tweak need to be done.  It's pretty simple when you know what need to be done but I spend the last few day pulling my hair out trying to  figured out how to make it work properly. There are several small essential step that are not mention. 

[**Reference: **This thread by geearf has been helpful although it was confusing at first.]("http://ubuntuforums.org/showthread.php?t=68491")

[SIZE=3]**Software/System used:**[/SIZE]

I'm on Ubuntu Feisty on a Celeron 2.4GHz

I have a Ati radeon 9200 with the open source driver 

The MPlayer use is the package provide by apt-get (or add/remove) (ver: 1.0 rc1 [2:1.0~rc1-0ubuntu9.1]) **mplayer **

I need the package **libgtk2.0-dev**

svgalib_helper module source was download from [Easy MAMECAb]("http://easymamecab.mameworld.net/html/svgalib.htm") (ver. 1.9.25)
```
[http://easymamecab.mameworld.net/html/svgalib.htm](http://easymamecab.mameworld.net/html/svgalib.htm)
```I need the source code of MPlayer (I will only recompile a very small element, libdha, I'm not recompiling Mplayer.)
```
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
```[SIZE=5]**Details:**[/SIZE]

**[SIZE=4]Getting the software[/SIZE]**

**1) **First  if not already done you can install the MPlayer package most of you reading this should have the MPlayer already installed and can skip to the next step
```

sudo atp-get install mplayer

```**2)** You will need libgtk2.0-dev to run the ./configure for MPlayer source
[**Reference:** MPlayer/Compile]("https://help.ubuntu.com/community/MPlayer/Compile?highlight=%28Mplayer%29")

```

sudo apt-get install libgtk2.0-dev

```**3)** Download MPlayer source from the [MPlayer website ]("http://www.mplayerhq.hu/design7/dload.html") (Ver. 1.0rc1)

**4)** Download svgalib source from [Easy MAMECAb]("http://easymamecab.mameworld.net/html/svgalib.htm")
(* I do not recommend to download the other svgalib_helper only version in the reference in the [Mplayer doc]("http://www.mplayerhq.hu/DOCS/HTML/en/vidix.html"), it give me errors. The Easy MAMCab version work well)
The version used in this guide is 1.9.25

**5)** Extract the tarball for simplicity sake I put everything  in my home folder (~/)
```

tar xvpfz svgalib-1.9.25.tar.gz -C ~/
tar xvpfj MPlayer-1.0rc1.tar.bz2 -C ~/

```**[SIZE=4]Making svgalib_helper[/SIZE]**

**6)** Go to the svgalib_helper folder it's under svgalib-1.9.25/kernel
```

cd ~/svgalib-1.9.25/kernel/svgalib_helper

```**7) **In main.c svgalib_helper include 2 linux header that no longer exist (config.h and devfs_fs_kernel.h) you can comment them out it does not seem to affect the functionality of svgalib_helper
[**Reference:** Credit to dozier768 thread ]("http://ubuntuforums.org/showthread.php?t=353019")
```

gedit main.c

```*Note: gedit is the default editor in gnome you can use nano for console or whatever editor you want

Put Comment before line 1 and line 20 to remove them
```

[COLOR=Blue]//[/COLOR] #include <linux/config.h>

...

[COLOR=Blue]//[/COLOR] #include <linux/devfs_fs_kernel.h>

```**[noparse]8)[/noparse] **Compile, install and modprobe the svgalib_helper module
```

make
sudo make install
sudo modprobe svgalib_helper

```**9) **Add the module to /etc/modules so it load on boot
```

sudo gedit /etc/modules

```Just add
```

svgalib_helper

```and save

**[SIZE=4]Making libdha[/SIZE]**

**10)**First we need to run ./configure in the MPlayer source folder 

Since we are not interested in recompiling MPlayer no option is need in ./configure 
```

cd ~/MPlayer-1.0rc1/
./configure

```**11) ** You need to copy the svgalib_helper source folder to the libdha folder.
```

cp -rf ~/svgalib-1.9.25/kernel/svgalib_helper/ ~/MPlayer-1.0rc1/libdha/

```**12)** Compile and install the libdha
```

cd ~/MPlayer-1.0rc1/libdha
make
sudo make install

```[B]

13)[/B] The install will create libdha.so.1.0  and libdha.so.1 in the /usr/local/lib/ folder. The original libdha.so.1 and libdha.so.1.0 are located in the /usr/lib/ folder. 

*The libdha.so.1 is only a symbolic link to libdha.1.0 so we only need to copy the real file libdhs.so.1.0

So backup the original libdha.so.1.0 then copy the new libdha to the /usr/lib folder
[**Reference:** npu post from this thread]("http://ubuntuforums.org/showthread.php?t=68491&page=2")
```

sudo mv /usr/lib/libdha.so.1.0 /usr/lib/libdha.so.1.0.backup

sudo cp /usr/local/lib/libdha.so.1.0 /usr/lib/

```**14)** Almost done. You need to run make device under the svgalib_helper folder.
```

cd ~/MPlayer-1.0rc1/libdha/svgalib_helper/
sudo make device

```**15)**Now you can add the "make device" script to /etc/init.d/bootmisc.sh so the script is executed at each boot to make the device [**Reference:** greearf comment in this thread]("http://ubuntuforums.org/showthread.php?p=623024#post623024")
```

sudo gedit /etc/init.d/bootmisc.sh

```I add the following code at the beginning of the file after the introduction comment
```

### svgalib_helper make device script
rm -f /dev/svga /dev/svga?
mknod -m 666 /dev/svga c 209 0
mknod -m 666 /dev/svga1 c 209 1
mknod -m 666 /dev/svga2 c 209 2
mknod -m 666 /dev/svga3 c 209 3
mknod -m 666 /dev/svga4 c 209 4
### End of svgalib_helper script

```Now I cross my finger and hope I didn't forget anything. If all went well you should be able to start mplayer normally and choose xvidix in the preference or use -vo xvidix in the command line

**[SIZE=4]Cleaning up[/SIZE]**

**15)**Remove the source code folder from your home. I only keep the tarball as archive.

```

rm -rf ~/MPlayer-1.0rc1
rm -rf ~/svgalib-1.9.25

```So tell me if it work.

---

