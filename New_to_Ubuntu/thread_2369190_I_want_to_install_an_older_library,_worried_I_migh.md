---
title: "I want to install an older library, worried I might break something"
date: 2017-08-19
forum: New to Ubuntu
---

### Post by bvz on 2017-08-19
Hi,

I'm trying to get Mudbox up and running on my 16.04 LTS install.

One of the things it is complaining about is not being able to find: 

```
libgstapp-0.10.so.0
```

Doing a little sleuthing, it looks like 16.04 installs a later version of this library.  I am finding:

```
libgstapp-1.0.so.0
```

in

```
/usr/lib/x86_64-linux-gnu
```


I would like to install the older library, and have found a library that apparently has the correct version in it:

```
libgstreamer-plugins-base0.10-0
```


```
bvz@t5500-Linux:/usr/lib/x86_64-linux-gnu$ apt list libgstreamer-plugins-base0.10-0
Listing... Done
libgstreamer-plugins-base0.10-0/xenial-updates,xenial-security 0.10.36-2ubuntu0.1 amd64
N: There is 1 additional version. Please use the '-a' switch to see it
bvz@t5500-Linux:/usr/lib/x86_64-linux-gnu$ apt list -a libgstreamer-plugins-base0.10-0
Listing... Done
libgstreamer-plugins-base0.10-0/xenial-updates,xenial-security 0.10.36-2ubuntu0.1 amd64
libgstreamer-plugins-base0.10-0/xenial 0.10.36-2 amd64
```


My fear is that if I install this package, that it might overwrite or somehow disable the existing libraries.  Is there a way to install this older library in a separate location, like say /usr/lib/libgstreamer-plugins-base0.10-0 and then update my LD_LIBRARY_PATH to add this locations as well?

(second, bonus question) If I run apt-install libgstreamer-plugins-base0.10-0 will I get both of the packages that showed up when I ran:
```

apt list -a libgstreamer-plugins-base0.10-0
```

---

### Post by bvz on 2017-08-19
Edit:

I found this page:

[https://packages.ubuntu.com/xenial/amd64/libgstreamer-plugins-base0.10-0/filelist](https://packages.ubuntu.com/xenial/amd64/libgstreamer-plugins-base0.10-0/filelist)

It shows the files in the package I described above.  I did a quick search to see if any of those files exist on my current system, and they don't.  So does that mean I can just run

sudo apt install libgstreamer-plugins-base0.10-0

and it will install these files alongside my current files and everything will be hunky dory?


Edit:

Well, I gave it a shot.  I ran the apt-install and this was the output:

```
bvz@t5500-Linux:~$ sudo apt install libgstreamer0.10-0
[sudo] password for bvz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gstreamer0.10-tools gstreamer0.10-plugins-base
The following NEW packages will be installed:
  libgstreamer0.10-0
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 646 kB of archives.
After this operation, 2,724 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 libgstreamer0.10-0 amd64 0.10.36-1.5ubuntu1 [646 kB]
Fetched 646 kB in 1s (501 kB/s)             
Selecting previously unselected package libgstreamer0.10-0:amd64.
(Reading database ... 275838 files and directories currently installed.)
Preparing to unpack .../libgstreamer0.10-0_0.10.36-1.5ubuntu1_amd64.deb ...
Unpacking libgstreamer0.10-0:amd64 (0.10.36-1.5ubuntu1) ...
Setting up libgstreamer0.10-0:amd64 (0.10.36-1.5ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link

```

But when I look in /usr/lib/x86_64-linux-gnu/ none of the files that I would have expected to be there are there.

---

### Post by vocx on 2017-08-19
> **bvz said:**
> Hi,

I'm trying to get Mudbox up and running on my 16.04 LTS install.

One of the things it is complaining about is not being able to find: 

```
libgstapp-0.10.so.0
```

Doing a little sleuthing, it looks like 16.04 installs a later version of this library.  I am finding:

```
libgstapp-1.0.so.0
```
My fear is that if I install this package, that it might overwrite or somehow disable the existing libraries.  Is there a way to install this older library in a separate location, like say /usr/lib/libgstreamer-plugins-base0.10-0 and then update my LD_LIBRARY_PATH to add this locations as well?

You seem to be somewhat knowledgeable on the libraries behavior. I don't think you can break your system. Basically, if you want to restore the library that the system normally uses you just need to reinstall the current package.

Now, the question is why is that "mudbox" program using the older library and not the current? Is it possible for you to get the newer version so that it uses the newer library? Maybe you can get the source code, and recompile it so it calls the current version instead of the old version.

In one case, I also required the older version of a library, say, "libpng.4.so", while the system had "libpng.5.so". So what I did was, I got the previous version's package, extracted the single file "libpng.4.so", and placed it in the directory with the executable requesting that library. Or maybe I placed it in the "/lib" directory for the program. Basically, you have to put it somewhere that the program is expecting that library.

If it is only one library you need, maybe you don't need to install the entire .deb package. The .deb package, usually also has some post-processing instructions to overwrite the files, move files, create symlinks and so on, so this could introduce instability into your system. You could just extract the single .so file that you need and put it in the appropriate directory and test if that works, as I did in my case above.

Of course, this gets tricky if the executable is expecting a file that is symbolically linked to another file; for example, it may be requesting "libpng.so", but it is currently linked to "libpng.5.so", and you need "libpng.4.so". I'm not sure what I'd do in that case.

It's also tricky if you need to consider many .so libraries that depend on each other. For example, suppose you successfully extracted only "libpng.4.so", but now it is also asking for "libjpg.4.so", and the current version is "libjpg.5.so". Then you would need again to search for all such older dependencies, and it can become tricky to get many files that way.

---

### Post by vocx on 2017-08-19
> **bvz said:**
> Edit:

I found this page:

[https://packages.ubuntu.com/xenial/amd64/libgstreamer-plugins-base0.10-0/filelist](https://packages.ubuntu.com/xenial/amd64/libgstreamer-plugins-base0.10-0/filelist)

Well, I gave it a shot.  I ran the apt-install and this was the output:

```
bvz@t5500-Linux:~$ sudo apt install libgstreamer0.10-0

```

But when I look in /usr/lib/x86_64-linux-gnu/ none of the files that I would have expected to be there are there.

If you want to see exactly what files are installed with a given package, use "dpkg -L".
```

dpkg -L libgstreamer0.10-0

```

It seems to me that the 0.10 version is only a virtual package that contains no files any more in the "xenial" repository, as it has been superseded by the 1.0 version. So, I would try to get the latest package where it was still used, and extract the needed ".so" file from it, as I mentioned in my previous post.

---

### Post by bvz on 2017-08-19
Thanks! 

I took your suggestion and found a package that had the necessary files. I installed that and now I have the libraries I need. I looked in the directory and can see that the files live quite nicely side by side.

Mudbox no longer complains about missing libraries. It still doesn't run, but now it appears to be an issue around licensing. It is a commercial package from Autodesk that is originally packaged as an rpm and doesn't come with instructions or the ability to run on Ubuntu out of the box. I'll be purchasing a license now, but I didn't want to commit the money until I had at least a semblance of an idea that I could make it work under Ubuntu.

Thanks again for your help.

---

### Post by bvz on 2017-08-20
Ok, so I got my license from Autodesk and installed it and Mudbox starts up just fine.  But it quickly stops with an error:

void Mudbox::LoadPlugins(): Failed to load the following plugin(s):
/usr/autodesk/mudbox2017/bin/plugins/libGeneralImage.so


So doing some (a lot) of googling, it popped up that I should run this command:

ldd -r /usr/autodesk/mudbox/bin/plugins/libGeneralImage.so

The output of this is:

```
bvz@t5500-Linux:/tmp/mudboxTempInstall$ ldd -r /usr/autodesk/mudbox/bin/plugins/libGeneralImage.so
	linux-vdso.so.1 =>  (0x00007ffcde9e2000)
	libMudboxFramework.so => /usr/autodesk/mudbox/bin/plugins/../../lib/libMudboxFramework.so (0x00007fe02c6fe000)
	libtiff.so.3 => not found
	libQtCore.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtCore.so.4 (0x00007fe02c202000)
	libQtGui.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtGui.so.4 (0x00007fe02b530000)
	libQtOpenGL.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtOpenGL.so.4 (0x00007fe02b232000)
	libGLU.so.1 => /usr/lib/x86_64-linux-gnu/libGLU.so.1 (0x00007fe02afc3000)
	libGL.so.1 => /usr/lib/nvidia-375/libGL.so.1 (0x00007fe02ad1f000)
	libQtXml.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtXml.so.4 (0x00007fe02aadb000)
	libQtSql.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtSql.so.4 (0x00007fe02a89c000)
	libQtSvg.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtSvg.so.4 (0x00007fe02a645000)
	libQtWebKit.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtWebKit.so.4 (0x00007fe028bcf000)
	libQtScript.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtScript.so.4 (0x00007fe028738000)
	libQtNetwork.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/libQtNetwork.so.4 (0x00007fe0283f0000)
	libimf.so => /usr/autodesk/mudbox/bin/plugins/../../lib/libimf.so (0x00007fe027f34000)
	libsvml.so => /usr/autodesk/mudbox/bin/plugins/../../lib/libsvml.so (0x00007fe027056000)
	libirng.so => /usr/autodesk/mudbox/bin/plugins/../../lib/libirng.so (0x00007fe026e4f000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fe026b45000)
	libiomp5.so => /usr/autodesk/mudbox/bin/plugins/../../lib/libiomp5.so (0x00007fe026810000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fe02648e000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fe026277000)
	libintlc.so.5 => /usr/autodesk/mudbox/bin/plugins/../../lib/libintlc.so.5 (0x00007fe02601c000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fe025dff000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fe025a34000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fe025830000)
	libBase.so => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libBase.so (0x00007fe02553b000)
	libMarkingMenus.so => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libMarkingMenus.so (0x00007fe0252f8000)
	libGestura.so => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libGestura.so (0x00007fe0250ac000)
	libQtDBus.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libQtDBus.so.4 (0x00007fe024e2c000)
	libphonon.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libphonon.so.4 (0x00007fe024bc9000)
	libclmint.so.4 => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libclmint.so.4 (0x00007fe02475e000)
	libCg.so => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libCg.so (0x00007fe0237f7000)
	libCgGL.so => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libCgGL.so (0x00007fe023679000)
	libsynHub.so => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libsynHub.so (0x00007fe023064000)
	libAutoCam.so.1 => /usr/autodesk/mudbox/bin/plugins/../../lib/../lib/libAutoCam.so.1 (0x00007fe022097000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fe021e7d000)
	libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007fe021c7a000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fe021a72000)
	libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fe021761000)
	/lib64/ld-linux-x86-64.so.2 (0x000055cac0223000)
	libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007fe02153b000)
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007fe021291000)
	libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007fe02103e000)
	libSM.so.6 => /usr/lib/x86_64-linux-gnu/libSM.so.6 (0x00007fe020e35000)
	libICE.so.6 => /usr/lib/x86_64-linux-gnu/libICE.so.6 (0x00007fe020c1b000)
	libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007fe020a11000)
	libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007fe0207cd000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007fe0205bb000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fe020281000)
	libGLX.so.0 => /usr/lib/nvidia-375/libGLX.so.0 (0x00007fe020050000)
	libGLdispatch.so.0 => /usr/lib/nvidia-375/libGLdispatch.so.0 (0x00007fe01fd82000)
	libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007fe01f9f9000)
	libgstapp-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstapp-0.10.so.0 (0x00007fe01f7ec000)
	libgstinterfaces-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstinterfaces-0.10.so.0 (0x00007fe01f5da000)
	libgstpbutils-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstpbutils-0.10.so.0 (0x00007fe01f3b5000)
	libgstvideo-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstvideo-0.10.so.0 (0x00007fe01f198000)
	libgstbase-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstbase-0.10.so.0 (0x00007fe01ef3e000)
	libgstreamer-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0 (0x00007fe01ec4e000)
	libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007fe01ea4a000)
	libxml2.so.2 => /usr/lib/x86_64-linux-gnu/libxml2.so.2 (0x00007fe01e68f000)
	libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007fe01e489000)
	libXt.so.6 => /usr/lib/x86_64-linux-gnu/libXt.so.6 (0x00007fe01e21f000)
	libpulse-mainloop-glib.so.0 => /usr/lib/x86_64-linux-gnu/libpulse-mainloop-glib.so.0 (0x00007fe01e01a000)
	libpulse.so.0 => /usr/lib/x86_64-linux-gnu/libpulse.so.0 (0x00007fe01ddc9000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fe01db59000)
	libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007fe01d950000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fe01d727000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fe01d504000)
	libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007fe01d2e2000)
	libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007fe01d0c7000)
	liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007fe01ce46000)
	libicuuc.so.55 => /usr/lib/x86_64-linux-gnu/libicuuc.so.55 (0x00007fe01cab2000)
	liblzma.so.5 => /lib/x86_64-linux-gnu/liblzma.so.5 (0x00007fe01c88f000)
	libpulsecommon-8.0.so => /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-8.0.so (0x00007fe01c614000)
	libjson-c.so.2 => /lib/x86_64-linux-gnu/libjson-c.so.2 (0x00007fe01c408000)
	libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007fe01c1bc000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fe01bfb8000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fe01bdb1000)
	libicudata.so.55 => /usr/lib/x86_64-linux-gnu/libicudata.so.55 (0x00007fe01a2fa000)
	libsystemd.so.0 => /lib/x86_64-linux-gnu/libsystemd.so.0 (0x00007fe01a274000)
	libwrap.so.0 => /lib/x86_64-linux-gnu/libwrap.so.0 (0x00007fe01a06a000)
	libsndfile.so.1 => /usr/lib/x86_64-linux-gnu/libsndfile.so.1 (0x00007fe019e01000)
	libasyncns.so.0 => /usr/lib/x86_64-linux-gnu/libasyncns.so.0 (0x00007fe019bfa000)
	libgcrypt.so.20 => /lib/x86_64-linux-gnu/libgcrypt.so.20 (0x00007fe019919000)
	libnsl.so.1 => /lib/x86_64-linux-gnu/libnsl.so.1 (0x00007fe0196ff000)
	libFLAC.so.8 => /usr/lib/x86_64-linux-gnu/libFLAC.so.8 (0x00007fe01948a000)
	libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007fe0191e1000)
	libgpg-error.so.0 => /lib/x86_64-linux-gnu/libgpg-error.so.0 (0x00007fe018fcc000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007fe018dc3000)
	libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007fe018b97000)
undefined symbol: TIFFWriteEncodedStrip	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)
undefined symbol: TIFFGetField	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)
undefined symbol: TIFFSetField	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)
undefined symbol: TIFFReadRGBAImageOriented	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)
undefined symbol: TIFFOpen	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)
undefined symbol: TIFFSetErrorHandler	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)
undefined symbol: TIFFClose	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)
undefined symbol: TIFFReadScanline	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)
undefined symbol: TIFFWriteDirectory	(/usr/autodesk/mudbox/bin/plugins/libGeneralImage.so)

```


It looks like Mudbox cannot find: libtiff.so.3

If I run this command:

```
cd /
sudo find . | grep -i libtiff.so.3
```

I get:

```
./usr/lib/libtiff.so.3
```

So I add "/usr/lib/" to my LD_LIBRARY_PATH, but running the same ldd command gives me the same output.

Is there some other way to indicate to the system where a shared library lives?

---

### Post by vocx on 2017-08-20
First of all, please edit your post to use "CODE" tags to display the terminal output. You are using "QUOTE" tags. The buttons are close to each other in the advanced editor and many people mistake them.

> **bvz said:**
> 

```
void Mudbox::LoadPlugins(): Failed to load the following plugin(s):
/usr/autodesk/mudbox2017/bin/plugins/libGeneralImage.so
```


I would copy the "libtiff.so.3" file and place the copy in the "plugins/" folder next to that "libGeneralImage.so".

The program needs to look for libraries in that directory, so it should find "libtiff.so.3" as well, I presume.

By the way, your use of the find command is hilarious. You do not need to pass it to "grep", as "find" can already do that.
```

find /usr -iname 'libtiff.so.3'

```

My system does not have ".so.3" but it has ".so.5". So, in any case, that Mudbox program seems to link old libraries.

---

### Post by bvz on 2017-08-20
> **vocx said:**
> First of all, please edit your post to use "CODE" tags to display the terminal output. You are using "QUOTE" tags. The buttons are close to each other in the advanced editor and many people mistake them.


I would copy the "libtiff.so.3" file and place the copy in the "plugins/" folder next to that "libGeneralImage.so".

The program needs to look for libraries in that directory, so it should find "libtiff.so.3" as well, I presume.

By the way, your use of the find command is hilarious. You do not need to pass it to "grep", as "find" can already do that.
```

find /usr -iname 'libtiff.so.3'

```

My system does not have ".so.3" but it has ".so.5". So, in any case, that Mudbox program seems to link old libraries.


Ha! Yeah, I am getting up to speed on Linux in a very short time so some of my command constructs may be a little weird :)

Thanks again so much for your help so far.  I finally got Mudbox to work (kind of), and I don't think I could have worked it out without your help.

Also, thanks to deadflow for fixing my quote tags.


Here is what I had to do:

First, for some weird reason, this morning I could not find libtiff.so.3 on my system anywhere.  My bizarre find command from last night did not work. Searching the actual directory it was supposed to be in didn't work.  Nothing.

So I searched for it online and found a repository where a version of it lived.  I downloaded that, extracted the file, and tried putting it in all kinds of different locations.  I tried in /usr/lib, /usr/lib/x86_64-linux-gnu with no avail.  I tried putting it next to libGeneralImage.so like you suggested and even tried it in /usr/autodesk/mudbox/lib (which is where a lot of the libraries that showed up from the ldd command lived).  None of those worked.

As a last resort, I tried making a symlink called libtiff.so.3 that pointed to libtiff.so.5.2.4 that already was installed on my system.

That worked.  Or at least it worked mostly.  Mudbox seems to run now.  It spit out three lines complaining about some tiff related functions:

```
 TIFFFetchNormalTag: Warning, Incompatible type for "RichTIFFIPTC"; tag ignored.
TIFFReadDirectory: Warning, Unknown field with tag 37724 (0x935c) encountered.
TIFFFetchNormalTag: Warning, Incompatible type for "RichTIFFIPTC"; tag ignored.
```

But it hasn't prevented me from using the tool.

I suspect that whatever library I had downloaded above was completely incompatible even though it was a libtiff.so.3 version.  The newest libtiff.so.5 seems to be mostly compatible, with a few exceptions that I am seeing in the form of those warnings.  I am going to ignore those for now, but keep an eye on it in case they cause actual trouble.  If they do, then I suppose I am going to have to see which version of libtiff is in a current Redhat repository (because Mudbox is certified to run on RedHat) and try to extract that I think.  Maybe?  I don't know.

As far as why Mudbox uses such old libraries on a tool they call "Mudbox 2017"... well that is a completely different story.  Mudbox was a really promising tool when it was first developed.  Then it was purchased by Autodesk and basically left to languish.  They release a "new" version every year but mostly it is just bug fixes and the very rare, occasional feature addition.  It is basically just one step above abandonware which is really sad. Every year they promise to get serious about making it a real product again, but they are so far behind their main competitors (ZBrush and 3DCoat) that it is laughable.  The only real reason for anyone to use it (including me) is that: 

a) it is cheap.  $70 for a year's subscription vs. between $400 and $1500 for the competition (though 3DCoat has an entry level version that is only $100 and that license is perpetual).
b) it is super easy to use. ZBrush is famous for having the most bizarre interface of ANY product on the market now. The learning curve on just how to open and save a file is almost as much as learning all of mudbox. (I kid, of course, but not really by all that much). Also, ZBrush is Mac and Windows only.  3DCoat is much more standard, but since it is a more capable product it is also more complex.  Mudbox, for the simple use cases that I am encountering, is just perfect.

Eventually I want to switch to 3DCoat... but for now I am thrilled to get Mudbox working.

I have encapsulated everything I did to get it running into a single script.  I will post that script elsewhere on this forum in case the one other person on the planet that wants to use Mudbox with Ubuntu needs some help. :)

Thanks again for your help. It was invaluable in helping me learn how a lot of this stuff works.

---

### Post by vocx on 2017-08-20
> **bvz said:**
> Ha! Yeah, I am getting up to speed on Linux in a very short time so some of my command constructs may be a little weird :)

Thanks again so much for your help so far.  I finally got Mudbox to work (kind of), and I don't think I could have worked it out without your help.

That's great.

> 
...
As a last resort, I tried making a **symlink called libtiff.so.3 that pointed to libtiff.so.5.2.4** that already was installed on my system.

That worked.  Or at least it worked mostly...

I suspect that whatever library I had downloaded above was completely incompatible even though it was a libtiff.so.3 version.  The newest libtiff.so.5 seems to be mostly compatible, with a few exceptions that I am seeing in the form of those warnings.  I am going to ignore those for now, but keep an eye on it in case they cause actual trouble.  If they do, then I suppose I am going to have to see which **version of libtiff is in a current Redhat repository** (because Mudbox is certified to run on RedHat) and try to extract that I think.  Maybe?  I don't know.

Yes, I think that could work, getting the same version as Redhat.

Good thing about this is that you actually understand what you are doing and can try different things to make it work, and backtrack your steps in case it doesn't.

> 
I have encapsulated everything I did to get it running into a single script.  I will post that script elsewhere on this forum in case the one other person on the planet that wants to use Mudbox with Ubuntu needs some help. :)

Thanks again for your help. It was invaluable in helping me learn how a lot of this stuff works.
Yes, please document and post your process. Many times professionals need help with commercial software that is not your typical free software package. Usually documentation is scarce, so having some detailed instructions is nice.

---

