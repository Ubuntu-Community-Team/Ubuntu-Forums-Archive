---
title: "install from a tar.bz2 file"
date: 2020-06-07
forum: New to Ubuntu
---

### Post by furioususer on 2020-06-07
I'm trying to install the portable 4kvideodownloader from here: 
[https://www.4kdownload.com/downloads](https://www.4kdownload.com/downloads)

I have now a file named: 4kvideodownloader_4.12.4_amd64.tar.bz2
I extract this and I get a folder by the name of 4kvideodownloader.

There is no install file. There is however a Readme file that is useless: it only informs about license and what you can do with the program. Not the usual helpful Readme file. 

So I google and I get the following instructions: after I extract and **ls** to the correct path I should write:

*./configure*
*sudo make*
*sudo make install*
 
When I start writing the first command I get this error msg: **bash: ./configure: No such file or directory**

Here it stops. I don't know what else to do. I've read several pages but they haven't helped at all. 

---------------------
May I also say, why is there always so much time and text wasted on instructing people how to extract a zipped file?! 70% of the instructions on this issue focuses on how to extract a zipped file (even going as far as instructing on how to open the Readme file from the Terminal), and not the actual problem at hand. Not the first time either! I don't know if it's just my Ubuntu LTS (I have 16.04) but there is a GUI just like Windows: right-click and extract. Simple! Some of you helpful and nice people are really still living in the old days of Linux where it was all Terminal. Sorry, I needed to vent a bit after read tons and tons of instructions on "how to unzip" every time I come across a problem I need to troubleshoot.

---

### Post by CelticWarrior on 2020-06-07
You're also making it hard than it needs to be, for yourself.
They provide a ready-made .deb file. Just download and install like any other software.

---

### Post by #&amp;thj^% on 2020-06-07
All i did was right click and chose to extract here in my /Downloads.
Now you will see a file named "4kvideodownloader.sh" in the new folder>> just throw that in your terminal, and should be good to go
@CelticWarrior I think poster wanted the portable version.

---

### Post by furioususer on 2020-06-07
You're exactly right: I want specifically the portable version.

May I ask how I should "throw" [COLOR=#000000]4kvideodownloader.sh[/COLOR] in the Terminal? What command should I use?

---

### Post by #&amp;thj^% on 2020-06-07
> **furioususer said:**
> You're exactly right: I want specifically the portable version.

May I ask how I should "throw" [COLOR=#000000]4kvideodownloader.sh[/COLOR] in the Terminal? What command should I use?

Just grab the file **4kvideodownloader.sh** and drop it in a open terminal.

---

### Post by ActionParsnip on 2020-06-08
[https://dl.4kdownload.com/app/4kvideodownloader_4.12.4-1_amd64.deb?source=website](https://dl.4kdownload.com/app/4kvideodownloader_4.12.4-1_amd64.deb?source=website)

Grab the deb and install

---

### Post by TheFu on 2020-06-08
> **1fallen said:**
> Just grab the file **4kvideodownloader.sh** and drop it in a open terminal.

That only works with specific terminals.  Caja drag-n-drop into an lxterm doesn't do anything, at least on 16.04.  That's the reason I don't make suggestions using a GUI and lean towards terminal commands. Additionally, I try to use terminal commands that don't assume specific stuff too much.

Often, posters here assume we have exactly the same system they do and don't tell us the OS version or DE being used, so we have to guess?  The different GUIs between 16.04 --> 18.04 --> 20.04 can be vastly different.

16.04 had Unity by default.
18.04 had a Gnome3 thing.
20.04 still has Gnome3, but with Snaps which restrict what does and doesn't work in the name of convenience and security. Also, 20.04 has moved from python2 to python3, so lots of python2 programs are broken.  I agree with the python3 change, but not the snap change. I was impacted by both of those changes.

The last year or so, lots of new GUI programs have not worked on 16.04. The underlying libraries have all moved forward and 3rd party development teams aren't too interested in supporting a mostly out of support release.

Anyways, I hopped onto a 16.04 system, grabbed the "portable" version, moved it to /tmp/, ran 
```
tar jxvf 4kvideodownloader_4.12.4_amd64.tar.bz2
```
then **cd 4k*** (I'm too lazy to type much )
looked at the files there.  No readme/README or anything matching *t.  There is a 4k*.sh, so I looked at it.  

It will run the program from any directory where all these files and subdirectories are installed. I know this from 25+ yrs as a programmer on many different platforms. At least, the is the intent for that shell script.   It seems to include many bloated, full, Qt5 library files  too. Ouch.  Ok, to end the suspense, I run it:
```
$ ./4kvideodownloader.sh 
/tmp/4kvideodownloader/4kvideodownloader-bin: /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.27' not found (required by /tmp/4kvideodownloader/libQt5WebEngineCore.so.5)
/tmp/4kvideodownloader/4kvideodownloader-bin: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.22' not found (required by /tmp/4kvideodownloader/libQt5WebEngineCore.so.5)
/tmp/4kvideodownloader/4kvideodownloader-bin: /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.27' not found (required by /tmp/4kvideodownloader/libQt5Gui.so.5)
/tmp/4kvideodownloader/4kvideodownloader-bin: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /tmp/4kvideodownloader/libQt5Core.so.5)
/tmp/4kvideodownloader/4kvideodownloader-bin: /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.27' not found (required by /tmp/4kvideodownloader/libavcodec.so.58)
/tmp/4kvideodownloader/4kvideodownloader-bin: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.27' not found (required by /tmp/4kvideodownloader/libavformat.so.58)
/tmp/4kvideodownloader/4kvideodownloader-bin: /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.27' not found (required by /tmp/4kvideodownloader/libmp3lame.so.0)
```
The devs seem to have assumed glibc of v2.27, but 16.04 has glibc of v2.23.  I stopped there.
```
sudo apt search libc-bi
libc-bin/xenial-updates,now 2.23-0ubuntu11 amd64 [installed]

```
I'd be afraid to force a newer version since everything on 16.04 will be dependent on v2.23.

Sorry for the terminal stuff. I don't know how to do it differently.

---

### Post by monkeybrain20122 on 2020-06-08
well I have succeeded in running a precompiled app on 16.04 that depends on  glibc-2.27 in a safe way without messing with system's glibc, but it requires compiling some prerequisites from source.

Here is how I did it.
first note the runtime libraries that the binary depends on

```
ldd /path/to/binary/you/want/to/run
``` (i.e the .bin file)

compile glibc 2.27 from source, install it somewhere in my $HOME. Get[ patchelf]("https://github.com/NixOS/patchelf"), compile. Then run
```
patchelf --set-interpreter /path/to/glibc2.27/install/directory/ld-linux-x86-64.so.2 --set-rpath /path/to/glibc2.27/install/directory/ /path/to/the/bin/fie
```
You only need to run it once and it will look for the correct  glibc version (instead of v2.23). That fixed the glibc problem but then it will complain that some run time libraries are missing.  So just do
```
export LD_LIBRARY_PATH=list of lib directories from first step separated with semi colons
```

You can either create a script that with the above line and then run the binary and put it in your $PATH (say ~/bin) or prepend the EXEC= line in .desktop file 
so it becomes ```
EXEC=env LD_LIBRARY_PATH=... /path/to/binary
```

In this case can just edit the .sh file if needed.

**EDITED:** I just realized this is the new user subforum after I posted, my answer may not be appropriate. Hopefully others may find it useful. I just discovered patchelf myself.

---

