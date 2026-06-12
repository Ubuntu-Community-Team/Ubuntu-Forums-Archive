---
title: "HOWTO: ubuntu 10.6 / new iPod nano / gtkpod + cover art"
date: 2006-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by dmjones500 on 2006-12-10
I've just succeeded in getting gtkpod to manage music on my iPod without errors, including uploading album cover art correctly.  I'm writing this whilst the steps are still vaguely fresh in my mind, but I may have omitted a few by mistake.  If you get any errors, post them here and I'm sure I'll remember how I fixed it.

Here are my instructions from an almost fresh install of Ubuntu 10.6.  Where I mention adding or removing packages, I used Synaptic package manager.

*Note: these instructions assume your iPod is already formatted for Windows.  You can do this using iTunes on someone's Windows PC, although I'm sure there is a Linux-only way to do it.*

**Firstly: how I mount my iPod**  

I added the following line to my /etc/fstab file:
```
/dev/sda2   /mnt/ipod   vfat   defaults,user,noauto,sync,umask=000
```

I then created the mount point directory (as root): 

```
mkdir /mnt/ipod
```

but made sure I allowed myself to use it as a non-root user:

```
chown <my_username>.<my_username> /mnt/ipod
```

After this is done, I can just call:

```
mount /mnt/ipod
```

and it works fine. To remove the ipod, I call [FONT="Courier New"]eject /mnt/ipod[/FONT] rather than [FONT="Courier New"]umount /mnt/ipod[/FONT].

**Sorting out the software:**

The first step was to remove the libgpod0 package from the system.  The latest version of gtkpod requires the latest version of libgpod, which is newer than the version that comes with Ubuntu 10.6.  Removing libgpod0 will also remove Rhythmbox and Ubuntu-desktop.  I'm not really sure what the latter does, but it seemed unimportant (<-- anybody??).  I haven't tried reinstalling Rhythmbox, as I'm content with xmms.

Next I installed the latest version of libgpod from source: libgpod 0.4.0 ([http://sourceforge.net/project/showfiles.php?group_id=67873)](http://sourceforge.net/project/showfiles.php?group_id=67873)).

During the running of the configure script, I got the error: “[FONT="Courier New"]C compiler cannot create executables[/FONT]”.  This was solved by adding the libc6-dev package.  After that, it compiled and installed OK.

Next I installed the latest version of gtkpod: gtkpod 0.99.8 (from the same link as above).  Now, this needed a few things installing (using Synaptic again):  

[LIST]
[*]autoconf
[*]flex
[*]libid3tag0 + libid3tag0-dev
[/LIST]

It's possible that I had to install other stuff at this point.  But at no point did Synaptic fail to offer the correct packages.  Note:  I'm not sure if the id3tag-dev package was necessary, but I assumed it was.

After this, gtkpod compiled and installed OK.  However, before it would run successfully, I had to add [FONT="Courier New"]/usr/local/lib[/FONT] to my [FONT="Courier New"]LD_LIBRARY_PATH[/FONT] variable.  I did this by adding the following lines to my [FONT="Courier New"].bashrc[/FONT] file:

```
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
export LD_LIBRARY_PATH
```

Remember to source this file using “[FONT="Courier New"]source ~/.bashrc[/FONT]” if you want this change to take effect immediately.

I could now run gtkpod:

```
gtkpod -m /mnt/ipod &
```

When it ran, I had to select my ipod type when I first selected “Load iPod(s)”.  I chose the sixth generation, silver iPod nano.

Now album art worked perfectly, and songs were uploaded without bother.

Incidentally, I use the software found at [http://kempele.fi/~skyostil/projects/albumart/](http://kempele.fi/~skyostil/projects/albumart/) to download my album art covers.


I hope this helps!!

---

### Post by dmjones500 on 2006-12-13
Turns out things become a bit neater if you use checkinstall to create packages for the new libgpod and gtkpod.

Checkinstall can be installed from the repositories, and its man page explains what to do.  But in short: instead of calling "make install", you issue the command "checkinstall".

If you specify the package names to be "libgpod0" and "gtkpod", it will replace the versions that come with 10.6.

Note:  I successfully re-installed Rhythbox after re-installing using my packages, but it complained that it couldn't use its iPod plugin.  I'm assuming that if you disable the plugin, Rhythmbox will work fine.

I haven't tried reinstalling ubuntu-desktop yet, I'll post info on whether that works tonight.

If you already installed the new gtkpod and libgpod from source, you can do a "make uninstall" in each of the source directories if you want to use checkinstall packages instead.  It seems you have to rebuild the sources though: "make uninstall && make clean && make dist clean && ./configure && make && checkinstall".

---

### Post by pavel_kbc on 2006-12-16
Lmfao 

when  ubuntu 10.6 come out??

LOL @ HOWTO: ubuntu 10.6 / new iPod nano / gtkpod + cover art

---

### Post by dmjones500 on 2006-12-18
Whoops :D

Is there any way to change the title once the thread is created??

---

### Post by Cody Body on 2006-12-19
I'm French and the french forums didn't answer my problem about New iPod Nano.

Thanks a lot.

---

### Post by dmjones500 on 2006-12-20
Update on the Rhythmbox/ubuntu-desktop issue:

I managed to re-install the ubuntu-desktop with no problems.

When Rhythmbox starts it is still complaining that it can't use the ipod plugin, despite me believing that I had disabled the plugin in the menus.  I tried building the latest version of Rhythmbox from source (planning to do a checkinstall to replace the repository versions), but I couldn't get it to configure.  It seems unable to spot my gstreamer pc files in the pk-config directory.

Apparently others on the net have had this problem.  I'll post a solution if I find one...

---

### Post by jdusablon on 2006-12-22
Am I doing something wrong?

Why is my album art STILL not working?

*EDIT*

I forgot to mention that I'm running 6.10 (or 10.6) edgy and I've successfully compiled and installed gtkpod 0.99.8

---

### Post by dmjones500 on 2006-12-23
> **jdusablon said:**
> Am I doing something wrong?

Why is my album art STILL not working?

*EDIT*

I forgot to mention that I'm running 6.10 (or 10.6) edgy and I've successfully compiled and installed gtkpod 0.99.8
Is your cover art stored within your mp3s, or as a separate image within each directory??  (Or both??)

I presented both options to gtkpod - the album cover art downloader I linked to above allowed me to store the image both in the mp3s, and in the directory itself as "folder.jpg".

Then within the gtkpod preferences, on the "track info" tab, I checked "Read cover art from embedded APIC data" as well as "Add coverart from file using the following template", specifying "folder.jpg".

So, in short, I'm not sure which one worked, the folder.jpg file or the encoded images in the mp3s.  But that's all I did, and it worked for me...  Did you install libgpod 0.4.0???

---

### Post by jak on 2006-12-25
> **dmjones500 said:**
> Turns out things become a bit neater if you use checkinstall to create packages for the new libgpod and gtkpod.

Checkinstall can be installed from the repositories, and its man page explains what to do.  But in short: instead of calling "make install", you issue the command "checkinstall".

If you specify the package names to be "libgpod0" and "gtkpod", it will replace the versions that come with 10.6.

Note:  I successfully re-installed Rhythbox after re-installing using my packages, but it complained that it couldn't use its iPod plugin.  I'm assuming that if you disable the plugin, Rhythmbox will work fine.

I haven't tried reinstalling ubuntu-desktop yet, I'll post info on whether that works tonight.

If you already installed the new gtkpod and libgpod from source, you can do a "make uninstall" in each of the source directories if you want to use checkinstall packages instead.  It seems you have to rebuild the sources though: "make uninstall && make clean && make dist clean && ./configure && make && checkinstall".

Rhythmbox: libgpod from source install to the wrong place, do this..
sudo rm /usr/lib/libgpod-0.4.0.so.0
sudo ln -s /usr/local/lib/libgpod-0.4.0.so.0 /usr/lib/libgpod-0.4.0.so.0

should fix rhythmbox -- this simply makes rhythmbox use the new libgpod library

---

### Post by tadtoll on 2006-12-26
> **dmjones500 said:**
> ....

Next I installed the latest version of gtkpod: gtkpod 0.99.8 (from the same link as above).  Now, this needed a few things installing (using Synaptic again):  

[LIST]
[*]autoconf
[*]flex
[*]libid3tag0 + libid3tag0-dev
[/LIST]

It's possible that I had to install other stuff at this point.  

Note: gtkpod configure said it could not find libglade-2.0, which synaptic showed to be already installed, I found mention [on a Red Hat forum]("https://www.redhat.com/archives/fedora-list/2006-October/msg02260.html") that installing the dev part of libglade-2.0 would take care of it. The gtkmod configure ran fine after that.

Thanks for your great help with this thread!

---

### Post by eclesh on 2006-12-26
The new iPod Nano doesn't work properly due to a bug in hal.  A fairly quick fix will make it work flawlessly like older iPods, and allow you to use whatever iPod tools you're used to (in my case, Banshee, which updates cover art along with the albums).

See [https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068/comments/13](https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068/comments/13)
for more information.  Those steps worked fine for me.  The only hiccup is that the patch won't apply the changelog entry properly, confusing the packaging system so it keeps telling you there is an update available.  To fix this, apply the attached patch after step 6 in the link (in the same way as given in that step: patch -p0 < changelog.patch.txt).

Good luck!

---

### Post by Charco on 2006-12-31
Thanks so much! Everything is so... beautiful now.

---

### Post by Obor on 2007-01-05
> **eclesh said:**
> The new iPod Nano doesn't work properly due to a bug in hal.  A fairly quick fix will make it work flawlessly like older iPods, and allow you to use whatever iPod tools you're used to (in my case, Banshee, which updates cover art along with the albums).

See [https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068/comments/13](https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068/comments/13)
for more information.  Those steps worked fine for me.  The only hiccup is that the patch won't apply the changelog entry properly, confusing the packaging system so it keeps telling you there is an update available.  To fix this, apply the attached patch after step 6 in the link (in the same way as given in that step: patch -p0 < changelog.patch.txt).

Good luck!

Thanks for that, exactly what I was looking for. It failed on step 8 on my mashine though. Any ideas?
```
dh_builddeb -plibhal-dev 
dpkg-deb: building package `libhal-dev' in `../libhal-dev_0.5.7.1-0ubuntu17ipod_i386.deb'.
tar: -: file name read contains nul character
dh_gencontrol -plibhal-storage-dev 
dh_md5sums -plibhal-storage-dev 
dh_builddeb -plibhal-storage-dev 
dpkg-deb: building package `libhal-storage-dev' in `../libhal-storage-dev_0.5.7.1-0ubuntu17ipod_i386.deb'.
tar: -: file name read contains nul character
 signfile hal_0.5.7.1-0ubuntu17ipod.dsc
gpg: skipped "Soren Hansen <sh@linux2go.dk>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-genchanges
dpkg-genchanges: warning: unknown information field `Xb-Python-Version' in input data in package's section of control info file
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
(WARNING: Failed to sign .dsc and .changes file)

```

---

### Post by eclesh on 2007-01-05
> **Obor said:**
> Thanks for that, exactly what I was looking for. It failed on step 8 on my mashine though. Any ideas?
```
dh_builddeb -plibhal-dev 
dpkg-deb: building package `libhal-dev' in `../libhal-dev_0.5.7.1-0ubuntu17ipod_i386.deb'.
tar: -: file name read contains nul character
dh_gencontrol -plibhal-storage-dev 
dh_md5sums -plibhal-storage-dev 
dh_builddeb -plibhal-storage-dev 
dpkg-deb: building package `libhal-storage-dev' in `../libhal-storage-dev_0.5.7.1-0ubuntu17ipod_i386.deb'.
tar: -: file name read contains nul character
 signfile hal_0.5.7.1-0ubuntu17ipod.dsc
gpg: skipped "Soren Hansen <sh@linux2go.dk>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-genchanges
dpkg-genchanges: warning: unknown information field `Xb-Python-Version' in input data in package's section of control info file
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
(WARNING: Failed to sign .dsc and .changes file)

```

These errors are normal.  Because you don't have the developer's secret key the signing process won't work.  The deb files were still made, though, and should be around in the current directory.  Proceed as normal with step 9 and everything should install properly (sudo dpkg -i *.deb).

---

### Post by Leec on 2007-01-05
Just finished all the above steps and upgraded to 99.8 and when I run gtkpod, I get the following messages on missing some symbols?  Any help on this?

lee@ubuntu:/tmp/gtkpod-0.99.8$ sudo gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_get_mountpoint
lee@ubuntu:/tmp/gtkpod-0.99.8$ sudo gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_device_set_mountpoint
lee@ubuntu:/tmp/gtkpod-0.99.8$ sudo gtkpod
lee@ubuntu:/tmp/gtkpod-0.99.8$ gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_info_get_ipod_info_table
lee@ubuntu:/tmp/gtkpod-0.99.8$

While I'm here, just one more if I can intermis problems.  When I plug the nano into the computer.  nothing is ever detected....however, I can plug a digital camera into the same USB and it is detected and works.  Anyone have any idea on what is wrong here?
Thanks
lee

---

### Post by eclesh on 2007-01-06
> **Leec said:**
> Just finished all the above steps and upgraded to 99.8 and when I run gtkpod, I get the following messages on missing some symbols?  Any help on this?

lee@ubuntu:/tmp/gtkpod-0.99.8$ sudo gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_get_mountpoint
lee@ubuntu:/tmp/gtkpod-0.99.8$ sudo gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_device_set_mountpoint
lee@ubuntu:/tmp/gtkpod-0.99.8$ sudo gtkpod
lee@ubuntu:/tmp/gtkpod-0.99.8$ gtkpod
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_info_get_ipod_info_table
lee@ubuntu:/tmp/gtkpod-0.99.8$


You probably didn't uninstall the system-installed version of libgpod first.  apt-get remove it (as stated in the original post), then compile/install libgpod from source, then recompile/install gtkpod from source.

> 
While I'm here, just one more if I can intermis problems.  When I plug the nano into the computer.  nothing is ever detected....however, I can plug a digital camera into the same USB and it is detected and works.  Anyone have any idea on what is wrong here?


This is probably due to the above-mentioned bug in hal.  If you follow the instructions a couple of posts up, you will have no need to recompile libgpod or gtkpod, or mess with your fstab.  Follow the nine steps in the link and your iPod will Just Work like it ought to.  Plug it in, it will mount itself, appear on the desktop, etc.

---

### Post by ions on 2007-01-07
Why is this problem not striking more Edgy users?  It got me because I'm lucky that way but a search on the forums and IRC shows that not all Edgy users have to apply this patch.  Why?  Are some of us using a HAL from a magic repo?  :\

---

### Post by ions on 2007-01-07
So I tried applying the patch anyway....

```
$ patch -p0 < via-raid-fix.debdiff
patching file hal-0.5.7.1/debian/changelog
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file hal-0.5.7.1/debian/changelog.rej
patching file hal-0.5.7.1/debian/patches/23-fix-via-raid-detection.patch

```

---

### Post by eclesh on 2007-01-07
ions:

As far as I could tell, the issue effects the new nano Windows-formatted iPods because they changed the way they initialize the FAT partition.  Hal recognizes them as RAID members instead of music players.  The hal patch fixes that.  Older nanos and iPods don't have that weird initialization sequence, nor do Apple-formatted music players.

As to your patch trouble, that's also expected.  The patch was written against a slightly older version of hal than is in the current repos so the changelog section of the patch fails.  The code portion of the patch applies fine so compilation works.  With that failed chunk, though, the updater will keep saying that there is an update available and downgrade your hal to the non-working version.  That's why you need to apply the changelog patch from a few posts up after applying the via-raid-fix patch.

Edit: There are also precompiled .debs available at [http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/](http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/) but I haven't used them and can't vouch for them.  It looks like they are for the older version of hal, so Edgy might still try and replace your hal with the non-working version.

---

### Post by ions on 2007-01-07
Thanks eclesh, between your post and a very helpful IRCer the ipod is behaving as it should.  Still not sure why mine isn't plug and play...

---

### Post by Obor on 2007-01-08
> **eclesh said:**
> These errors are normal.  Because you don't have the developer's secret key the signing process won't work.  The deb files were still made, though, and should be around in the current directory.  Proceed as normal with step 9 and everything should install properly (sudo dpkg -i *.deb).

Sweet. It works now, wife will be happy :D

---

### Post by morganGDFP on 2007-02-19
This HOWTO looks like the thing i've been looking for for a long time now.
i still boot into my windows partition occasionally just to update my ipod but if I can get this gtkpod up and running I can probably remove windows altogether. :)
Just have one last question before I start:

> Turns out things become a bit neater if you use checkinstall to create packages for the new libgpod and gtkpod.

Checkinstall can be installed from the repositories, and its man page explains what to do. But in short: instead of calling "make install", you issue the command "checkinstall".

If you specify the package names to be "libgpod0" and "gtkpod", it will replace the versions that come with 10.6.

Do you mean that I do not have to uninstall the previous versions of gtkpod and libgpod0?

---

### Post by morganGDFP on 2007-02-20
Don't worry, I think I realized that I still have to uninstall the previous versions of libgpod and gtkpod but that if I use checkinstall instead of make install the repositories in the synaptic package manager will be up to date as well.

I have installed everything and apart from one small thing everything works perfect..
This is probably something really simple again..
Ok here is the problem:
When I run gtkpod from the terminal it runs perfectly but if I want to add a custom application launcher to my panel it refuses to run..
Can anyone please tell me why it is behaving like that?

cheers

PS
One thing I noticed as well..

> Rhythmbox: libgpod from source install to the wrong place, do this..
sudo rm /usr/lib/libgpod-0.4.0.so.0
sudo ln -s /usr/local/lib/libgpod-0.4.0.so.0 /usr/lib/libgpod-0.4.0.so.0

I had to change the filenames slightly to get rythmbox to work, the file rythmbox is looking for was called libgpod.so.0 and the file that libgpod placed in my usr/local/lib folder is called libgpod.so.1.0.0.
So for me this worked:

sudo ln -s /usr/local/lib/libgpod.so.1.0.0 /usr/lib/libgpod.so.0

hopefully that helps someone...

---

### Post by HeyGabe on 2007-04-06
Quick question:
Is this patch part of Feisty? Because If it's going to be fixed when I upgrade, I don't want to dink around with patching my system now. 

Thanks.
G.

---

### Post by HeyGabe on 2007-04-07
Tested it myself. 
It's in Feisty.So If you don't want to hassle with this patch, upgrade to Feisty.

---

