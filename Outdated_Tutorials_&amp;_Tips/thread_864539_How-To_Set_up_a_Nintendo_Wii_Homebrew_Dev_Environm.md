---
title: "How-To: Set up a Nintendo Wii Homebrew Dev Environment in Ubuntu"
date: 2008-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by RATM_Owns on 2008-07-19
[IMG]http://static.hackmii.com/wp-content/themes/cutline-3-column-split-11/images/wrongprivs.jpg[/IMG]
If you have a Wii, you've probably heard of Team Twiizers from [http://hackmii.com/](http://hackmii.com/)
So I started making some simple programs (mostly from looking at some source code of other projects and creating another program) and wrote a simple script to set up one for anybody using Linux who wants one.

So all you have to do is download the attached file, go in the terminal and type
```
chmod +x devkitppc.sh[code]
Or in Nautilus, right click, choose Properties, go under the Permissions tab, and click the "Allow _e_xecuting file as a program" box.

Then either do
[code]./devkitppc.sh
```Or double-click and and choose "Run in Terminal"
It will set up everything you need and download some example source code to see if it is working correctly.

If you want to test your compiled code, go to [http://hbc.hackmii.com/download/](http://hbc.hackmii.com/download/) and download the Twilight Hack and (optional) the Homebrew Channel. Instructions are bundled with the programs.

---

### Post by lunisneko on 2008-08-19
Great script! I was easily able to `make` the template sample, but with one small change. On line 16

```
echo "export DEVKITPRO=$HOME/devkitpro" >> $HOME/.bashrc
```

The 'p' in 'devkitpro' should be capped, like so:

```
echo "export DEVKITPRO=$HOME/devkitPro" >> $HOME/.bashrc
```

---

### Post by RATM_Owns on 2008-08-19
Thanks. I probably wouldn't have noticed that. xP

Here's the new one:

---

### Post by jasex on 2008-09-02
```
thursday@yggdrasil:~$ '/home/thursday/Desktop/devkitppc.sh' 
bash: /home/thursday/Desktop/devkitppc.sh: /bin/bash^M: bad interpreter: No such file or directory

```


:O ?!?!? What is this?

Fixed it... by comparing the top two lines in the different scripts... kthnx

---

### Post by jasex on 2008-09-02
```
thursday@yggdrasil:~$ '/home/thursday/Desktop/devkitppc1.sh' 
: No such file or directoryitppc1.sh: line 4: cd: /home/thursday/devkitPro
--01:19:38--  http://tinyurl.com/5p3gfz%0D
           => `5p3gfz%0D'
Resolving tinyurl.com... 195.66.135.131, 85.255.210.131
Connecting to tinyurl.com|195.66.135.131|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/devkitpro/devkitPPC_r15-i686-linux.tar.bz2?modtime=1210820824&big_mirror=0 [following]
--01:19:38--  http://downloads.sourceforge.net/devkitpro/devkitPPC_r15-i686-linux.tar.bz2?modtime=1210820824&big_mirror=0
           => `devkitPPC_r15-i686-linux.tar.bz2?modtime=1210820824&big_mirror=0'
Resolving downloads.sourceforge.net... 216.34.181.60
Connecting to downloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/sourceforge/devkitpro/devkitPPC_r15-i686-linux.tar.bz2 [following]
--01:19:38--  http://voxel.dl.sourceforge.net/sourceforge/devkitpro/devkitPPC_r15-i686-linux.tar.bz2
           => `devkitPPC_r15-i686-linux.tar.bz2'
Resolving voxel.dl.sourceforge.net... 208.122.32.195
Connecting to voxel.dl.sourceforge.net|208.122.32.195|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 18,679,171 (18M) [application/x-bzip2]

100%[====================================>] 18,679,171   185.79K/s    ETA 00:00

01:21:17 (184.34 KB/s) - `devkitPPC_r15-i686-linux.tar.bz2' saved [18679171/18679171]

--01:21:17--  http://tinyurl.com/5a9p7q%0D
           => `5a9p7q%0D'
Resolving tinyurl.com... 85.255.210.131, 195.66.135.131
Connecting to tinyurl.com|85.255.210.131|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/devkitpro/libogc-20080602.tar.bz2?modtime=1212367882&big_mirror=0 [following]
--01:21:18--  http://downloads.sourceforge.net/devkitpro/libogc-20080602.tar.bz2?modtime=1212367882&big_mirror=0
           => `libogc-20080602.tar.bz2?modtime=1212367882&big_mirror=0'
Resolving downloads.sourceforge.net... 216.34.181.60
Connecting to downloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/sourceforge/devkitpro/libogc-20080602.tar.bz2 [following]
--01:21:18--  http://voxel.dl.sourceforge.net/sourceforge/devkitpro/libogc-20080602.tar.bz2
           => `libogc-20080602.tar.bz2'
Resolving voxel.dl.sourceforge.net... 208.122.32.195
Connecting to voxel.dl.sourceforge.net|208.122.32.195|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 867,630 (847K) [application/x-bzip2]

100%[====================================>] 867,630      186.10K/s    ETA 00:00

01:21:22 (184.53 KB/s) - `libogc-20080602.tar.bz2' saved [867630/867630]

--01:21:22--  http://tinyurl.com/5u3hp2%0D
           => `5u3hp2%0D'
Resolving tinyurl.com... 195.66.135.131, 85.255.210.131
Connecting to tinyurl.com|195.66.135.131|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/devkitpro/wii-examples-20080602.tar.bz2?modtime=1212382296&big_mirror=0 [following]
--01:21:23--  http://downloads.sourceforge.net/devkitpro/wii-examples-20080602.tar.bz2?modtime=1212382296&big_mirror=0
           => `wii-examples-20080602.tar.bz2?modtime=1212382296&big_mirror=0'
Resolving downloads.sourceforge.net... 216.34.181.60
Connecting to downloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://internap.dl.sourceforge.net/sourceforge/devkitpro/wii-examples-20080602.tar.bz2 [following]
--01:21:23--  http://internap.dl.sourceforge.net/sourceforge/devkitpro/wii-examples-20080602.tar.bz2
           => `wii-examples-20080602.tar.bz2'
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15,627 (15K) [application/x-tar]

100%[====================================>] 15,627        --.--K/s             

01:21:24 (124.46 KB/s) - `wii-examples-20080602.tar.bz2' saved [15627/15627]

tar: devkitPPC_r15-i686-linux.tar.bz2\r: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rm: cannot remove `devkitPPC_r15-i686-linux.tar.bz2\r': No such file or directory
: No such file or directoryitppc1.sh: line 10: cd: libogc
tar: ../libogc-20080602.tar.bz2\r: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rm: cannot remove `../libogc-20080602.tar.bz2\r': No such file or directory
: No such file or directoryitppc1.sh: line 13: cd: ../src
tar: ../wii-examples-20080602.tar.bz2\r: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rm: cannot remove `../wii-examples-20080602.tar.bz2\r': No such file or directory
: command not foundtop/devkitppc1.sh: line 19: exit
thursday@yggdrasil:~$ 

```

Should I have run this as sudo?

---

### Post by RATM_Owns on 2008-09-02
Nope. I don't know what really happened. As far as I know, it really should work. Paste this in to a open document:

```
#!/bin/bash 
mkdir -p $HOME/devkitPro/examples/../libogc/../src/ 
cd $HOME/devkitPro 
wget http://tinyurl.com/5p3gfz 
wget http://tinyurl.com/5a9p7q 
wget http://tinyurl.com/5u3hp2 
tar -xvjf devkitPPC_r15-i686-linux.tar.bz2 
rm devkitPPC_r15-i686-linux.tar.bz2 
cd libogc 
tar -xvjf ../libogc-20080602.tar.bz2 
rm ../libogc-20080602.tar.bz2 
cd ../src 
tar -xvjf ../wii-examples-20080602.tar.bz2 
rm ../wii-examples-20080602.tar.bz2 
echo "export DEVKITPRO=$HOME/devkitPro" >> $HOME/.bashrc 
echo "export DEVKITPPC=$DEVKITPRO/devkitPPC" >> $HOME/.bashrc 
source $HOME/.bashrc 
exit 
```

---

### Post by RATM_Owns on 2008-10-17
Here's the newest script, tested myself. It works.

```
#!/bin/bash
echo -n "Directory to install to: "
read insdir
mkdir -p $insdir/src/examples
cd $insdir
wget http://tinyurl.com/5p3gfz -O devkitPPC.tar.bz2
wget http://tinyurl.com/5u3hp2 -O wii-examples.tar.bz2
wget http://fceugc.googlecode.com/files/devkitPro-06102008.zip -O libogc.zip
tar -xvjf devkitPPC.tar.bz2
rm devkitPPC.tar.bz2
unzip -o libogc.zip
rm libogc.zip
cd src/examples
tar -xvjf $insdir/wii-examples.tar.bz2
rm $insdir/wii-examples.tar.bz2
echo "export DEVKITPRO=$insdir/devkitPro" >> ~/.bashrc
echo "export DEVKITPPC=$DEVKITPRO/devkitPPC" >> ~/.bashrc
echo "PATH=$PATH:$DEVKITPPC/bin" >> ~/.bashrc
source ~/.bashrc
```

It doesn't need much to work. It needs:
> bash
echo
read
cd
wget
tar
rm
unzip
source

All of them should come by default.

---

### Post by skedone on 2008-10-28
> **RATM_Owns said:**
> Here's the newest script, tested myself. It works.

```
#!/bin/bash
echo -n "Directory to install to: "
read insdir
mkdir -p $insdir/src/examples
cd $insdir
wget http://tinyurl.com/5p3gfz -O devkitPPC.tar.bz2
wget http://tinyurl.com/5u3hp2 -O wii-examples.tar.bz2
wget http://fceugc.googlecode.com/files/devkitPro-06102008.zip -O libogc.zip
tar -xvjf devkitPPC.tar.bz2
rm devkitPPC.tar.bz2
unzip -o libogc.zip
rm libogc.zip
cd src/examples
tar -xvjf $insdir/wii-examples.tar.bz2
rm $insdir/wii-examples.tar.bz2
echo "export DEVKITPRO=$insdir/devkitPro" >> ~/.bashrc
echo "export DEVKITPPC=$DEVKITPRO/devkitPPC" >> ~/.bashrc
echo "PATH=$PATH:$DEVKITPPC/bin" >> ~/.bashrc
source ~/.bashrc
```

It doesn't need much to work. It needs:


All of them should come by default.


i tried your script but nutting happens mate do i need to put a install directory in at top of script or summit

---

### Post by hak8or on 2008-11-23
I have tried all the scripts in this thread and I keep seeing the exact same problem when making mplayer.

```

zemkacz@vmware-ubuntu:~/mplayer$ make
gx_supp.c
/home/zemkacz/mplayer/source/gx_supp.c: In function 'draw_initYUV':
/home/zemkacz/mplayer/source/gx_supp.c:464: error: 'GX_KCOLOR0' undeclared (first use in this function)
/home/zemkacz/mplayer/source/gx_supp.c:464: error: (Each undeclared identifier is reported only once
/home/zemkacz/mplayer/source/gx_supp.c:464: error: for each function it appears in.)
/home/zemkacz/mplayer/source/gx_supp.c:465: error: 'GX_KCOLOR1' undeclared (first use in this function)
/home/zemkacz/mplayer/source/gx_supp.c:466: error: 'GX_KCOLOR2' undeclared (first use in this function)
/home/zemkacz/mplayer/source/gx_supp.c:467: error: 'GX_KCOLOR3' undeclared (first use in this function)
make[1]: *** [gx_supp.o] Error 1
make: *** [build] Error 2

```

I could make the example files with out a problem but mplayer is the one giving me problems.

Could it be the source of mplayer that is the problem? :confused:

Edit: I got IT workgin! :D
I had to put the lib folder thing into the devkitppc folder :D
Why did I have to do that, and why was it not in the readme but in the google code project info?


Edit yet again:

I now got the exact same error as before
All that I did was check out the GUI addon from google code but I had some various errors so I decided to get rid of the entire mplayer wii package from my home folder.
Also with the gui addon there were some lib folder so I put that into the devkitppc libogc folder.
So to get rid of it I got rid of the entire libogc folder from devkitppc and the entire mplayerwii folder and re-downloaded mplayerwii.
I put its libogc merged with the devkitppc liogc folder and now I am getting the exact same error :(

I was so happy and now I am having the exact same problem, any help would be greatly appreciated :D


Edit:
I am now getting a bunch of totally diffrent errors
```

zemkacz@vmware-ubuntu:~/mplayerwii-read-only$ make
gx_supp.c
In file included from /home/zemkacz/mplayerwii-read-only/source/gx_supp.c:31:
/home/zemkacz/mplayerwii-read-only/source/gx_supp.h:28:20: warning: gccore.h: No such file or directory
In file included from /home/zemkacz/mplayerwii-read-only/source/gx_supp.c:31:
/home/zemkacz/mplayerwii-read-only/source/gx_supp.h:34: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.h:39: error: expected ')' before 'width'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.h:40: error: expected ')' before 'width'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.h:41: error: expected ')' before 'width'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.h:42: error: expected ')' before 'width'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:43: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'whichfb'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:44: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:45: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:48: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:52: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'texturesize'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:54: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'texobj'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:55: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'view'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:56: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'vwidth'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:57: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'Ywidth'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:61: error: expected specifier-qualifier-list before 'Vector'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:66: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'square'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:75: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colors'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:79: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'texcoords'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:87: error: extra brace group at end of initializer
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:87: error: (near initialization for 'cam')
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:87: warning: excess elements in struct initializer
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:87: warning: (near initialization for 'cam')
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:88: error: extra brace group at end of initializer
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:88: error: (near initialization for 'cam')
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:88: warning: excess elements in struct initializer
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:88: warning: (near initialization for 'cam')
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:89: error: extra brace group at end of initializer
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:89: error: (near initialization for 'cam')
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:89: warning: excess elements in struct initializer
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:89: warning: (near initialization for 'cam')
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c: In function 'GX_InitVideo':
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:93: error: 'vmode' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:93: error: (Each undeclared identifier is reported only once
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:93: error: for each function it appears in.)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:93: warning: implicit declaration of function 'VIDEO_GetPreferredMode'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:96: error: 'VI_MAX_WIDTH_PAL' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:98: warning: implicit declaration of function 'VIDEO_Configure'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:100: error: 'xfb' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:100: error: 'u32' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:100: error: expected expression before ')' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:101: error: expected expression before ')' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:102: error: 'gp_fifo' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:102: error: 'u8' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:102: error: expected expression before ')' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:104: warning: implicit declaration of function 'VIDEO_ClearFrameBuffer'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:104: error: 'COLOR_BLACK' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:107: error: 'whichfb' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:108: warning: implicit declaration of function 'VIDEO_SetNextFramebuffer'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:109: warning: implicit declaration of function 'VIDEO_SetBlack'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:109: error: 'FALSE' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:110: warning: implicit declaration of function 'VIDEO_Flush'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:111: warning: implicit declaration of function 'VIDEO_WaitVSync'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:113: error: 'VI_NON_INTERLACE' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c: In function 'GX_SetCamPosZ':
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:118: error: 'camera' has no member named 'pos'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c: In function 'draw_init':
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:125: warning: implicit declaration of function 'GX_ClearVtxDesc'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:126: warning: implicit declaration of function 'GX_SetVtxDesc'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:126: error: 'GX_VA_POS' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:126: error: 'GX_INDEX8' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:127: error: 'GX_VA_CLR0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:128: error: 'GX_VA_TEX0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:128: error: 'GX_DIRECT' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:130: warning: implicit declaration of function 'GX_SetVtxAttrFmt'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:130: error: 'GX_VTXFMT0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:130: error: 'GX_POS_XYZ' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:130: error: 'GX_S16' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:131: error: 'GX_CLR_RGBA' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:131: error: 'GX_RGBA8' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:132: error: 'GX_TEX_ST' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:132: error: 'GX_F32' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:134: warning: implicit declaration of function 'GX_SetArray'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:134: error: 'square' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:134: error: 's16' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:136: warning: implicit declaration of function 'GX_SetNumTexGens'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:137: warning: implicit declaration of function 'GX_SetTexCoordGen'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:137: error: 'GX_TEXCOORD0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:137: error: 'GX_TG_MTX2x4' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:137: error: 'GX_TG_TEX0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:137: error: 'GX_IDENTITY' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:139: warning: implicit declaration of function 'GX_InvalidateTexAll'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:141: warning: implicit declaration of function 'GX_InitTexObj'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:141: error: 'texobj' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:141: error: 'texturemem' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:141: error: 'vwidth' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:141: error: 'vheight' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:141: error: 'GX_TF_RGB565' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:142: error: 'GX_CLAMP' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:142: error: 'GX_FALSE' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c: At top level:
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:145: error: expected ')' before 'pos'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:151: error: expected ')' before 'v'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:171: error: expected ')' before 'width'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:233: error: expected ')' before 'width'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:297: error: expected ')' before 'width'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c: In function 'draw_initYUV':
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:365: warning: implicit declaration of function 'GX_SetNumChans'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:367: error: 'GX_TEXCOORD0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:367: error: 'GX_TG_MTX2x4' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:367: error: 'GX_TG_TEX0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:367: error: 'GX_IDENTITY' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:368: error: 'GX_TEXCOORD1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:368: error: 'GX_TG_TEX1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:463: warning: implicit declaration of function 'GX_SetNumTevStages'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:464: warning: implicit declaration of function 'GX_SetTevKColor'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:464: error: 'GX_KCOLOR0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:464: error: 'GXColor' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:464: error: expected ')' before '{' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:465: error: 'GX_KCOLOR1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:465: error: expected ')' before '{' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:466: error: 'GX_KCOLOR2' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:466: error: expected ')' before '{' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:467: error: 'GX_KCOLOR3' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:467: error: expected ')' before '{' token
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:469: warning: implicit declaration of function 'GX_SetTevKColorSel'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:469: error: 'GX_TEVSTAGE0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:469: error: 'GX_TEV_KCSEL_K1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:470: warning: implicit declaration of function 'GX_SetTevOrder'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:470: error: 'GX_TEXMAP1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:470: error: 'GX_COLOR0A0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:471: warning: implicit declaration of function 'GX_SetTevColorIn'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:471: error: 'GX_CC_RASC' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:471: error: 'GX_CC_KONST' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:471: error: 'GX_CC_TEXC' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:471: error: 'GX_CC_ZERO' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:472: warning: implicit declaration of function 'GX_SetTevColorOp'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:472: error: 'GX_TEV_ADD' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:472: error: 'GX_TB_SUBHALF' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:472: error: 'GX_CS_SCALE_2' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:472: error: 'GX_ENABLE' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:472: error: 'GX_TEVREG0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:473: warning: implicit declaration of function 'GX_SetTevKAlphaSel'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:473: error: 'GX_TEV_KASEL_K0_A' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:474: warning: implicit declaration of function 'GX_SetTevAlphaIn'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:474: error: 'GX_CA_ZERO' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:474: error: 'GX_CA_RASA' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:474: error: 'GX_CA_KONST' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:475: warning: implicit declaration of function 'GX_SetTevAlphaOp'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:475: error: 'GX_TB_ZERO' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:475: error: 'GX_CS_SCALE_1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:477: error: 'GX_TEVSTAGE1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:480: error: 'GX_TEVREG1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:482: error: 'GX_TEVPREV' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:484: error: 'GX_TEVSTAGE2' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:484: error: 'GX_TEV_KCSEL_K0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:485: error: 'GX_TEXMAP2' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:487: error: 'GX_TEVREG2' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:491: error: 'GX_TEVSTAGE3' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:498: error: 'GX_TEVSTAGE4' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:498: error: 'GX_TEV_KCSEL_K2' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:499: error: 'GX_TEXMAP0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:499: error: 'GX_COLORNULL' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:500: error: 'GX_CC_CPREV' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:501: error: 'GX_TEV_SUB' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:501: error: 'GX_DISABLE' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:502: error: 'GX_TEV_KASEL_1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:503: error: 'GX_CA_A0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:503: error: 'GX_CA_TEXA' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:506: error: 'GX_TEVSTAGE5' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:508: error: 'GX_CC_C2' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:510: error: 'GX_TEV_KASEL_K1_A' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:511: error: 'GX_CA_APREV' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:514: error: 'GX_TEVSTAGE6' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:515: error: 'GX_TEXCOORDNULL' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:515: error: 'GX_TEXMAP_NULL' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:521: error: 'GX_TEVSTAGE7' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:521: error: 'GX_TEV_KCSEL_1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:523: error: 'GX_CC_ONE' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:523: error: 'GX_CC_A1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:528: error: 'GX_TEVSTAGE8' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:528: error: 'GX_TEV_KCSEL_K3' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:530: error: 'GX_CC_C1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:535: error: 'GX_TEVSTAGE9' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:542: error: 'GX_TEVSTAGE10' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:544: error: 'GX_CC_C0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:549: error: 'GX_TEVSTAGE11' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:559: warning: implicit declaration of function 'GX_SetBlendMode'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:559: error: 'GX_BM_BLEND' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:559: error: 'GX_BL_SRCALPHA' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:559: error: 'GX_BL_INVSRCALPHA' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:559: error: 'GX_LO_CLEAR' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:560: warning: implicit declaration of function 'GX_SetColorUpdate'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:561: warning: implicit declaration of function 'GX_SetAlphaUpdate'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:565: error: 'GX_VA_POS' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:565: error: 'GX_INDEX8' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:566: error: 'GX_VA_CLR0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:567: error: 'GX_VA_TEX0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:568: error: 'GX_VA_TEX1' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:569: error: 'GX_VTXFMT0' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:569: error: 'GX_POS_XYZ' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:569: error: 'GX_S16' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:570: error: 'GX_CLR_RGBA' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:570: error: 'GX_RGBA8' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:571: error: 'GX_TEX_ST' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:571: error: 'GX_U8' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:574: error: 'square' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:574: error: 's16' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:575: error: 'colors' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:576: error: 'texcoords' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:576: error: 'u8' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:580: error: 'YtexObj' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:580: error: 'Ytexture' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:580: error: 'u16' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:580: error: expected ')' before 'Ywidth'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:581: error: 'UtexObj' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:581: error: 'Utexture' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:581: error: expected ')' before 'UVwidth'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:582: error: 'VtexObj' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:582: error: 'Vtexture' undeclared (first use in this function)
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:582: error: expected ')' before 'UVwidth'
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c: At top level:
/home/zemkacz/mplayerwii-read-only/source/gx_supp.c:588: error: expected ')' before 'width'
make[1]: *** [gx_supp.o] Error 1
make: *** [build] Error 2

```

So where do I put the gccore.h?

---

