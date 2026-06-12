---
title: "fglrx tracking (updated with every breakage!)"
date: 2011-06-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2011-06-02
Another release, another opportunity for breakage.

**** Latest news ****

fglrx 8.872 / Catalyst 11.7 has been pushed to the repos.

* Useful information *

Looks like the radeon kernel driver is kicking in and conflicting with  fglrx. You will most likely need to add radeon.nomodeset=1 to your GRUB boot line if you get nothing but a blank (suspend/off) screen when X loads.

$ sudo nano /etc/default/grub

GRUB_CMDLINE_LINX_DEFAULT="quiet splash radeon.nomodeset=1"

CTRL-O
CTRL-X

$ sudo update-grub

If you get an error like "update-alternatives: error: alternative link /usr/bin/aticonfig is already managed by x86_64-linux-gnu_gl_conf" then this can be fixed by running

```
sudo apt-get purge fglrx*
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
sudo dpkg -i fglrx*.deb
sudo update-alternatives --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf 100 --slave /usr/lib/x86_64-linux-gnu/xorg/extra-modules x86_64-linux-gnu_xorg_extra_modules /usr/lib/fglrx/xorg/modules/
sudo ldconfig
```[Credit]("http://ubuntuforums.org/showpost.php?p=11121586&postcount=42") and nice work to TrueJournals for this. :)

**** Current status ****

11.7/8.872: **Working. Installation is trivial**.

**** How? ****

**11.7:**
Install fglrx from the repo, e.g.
```
$ sudo apt-get install fglrx
```
**Old 11.7:**
1) Download [11.7]("http://www2.ati.com/drivers/linux/ati-driver-installer-11-7-x86.x86_64.run") from [AMD]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx").
2) Build debs
3) Install

No need for huge detail (including TrueJournals' direct rendering [fixes]("http://ubuntuforums.org/showpost.php?p=11120083&postcount=38")):

$ cd ~/download/ati/11.7
$ sudo ./ati-driver-installer-11-7-x86.x86_64.run --buildpkg
$ sudo apt-get purge fglrx*
$ sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
$ sudo dpkg -i fglrx*.deb
$ sudo update-alternatives --install  /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf  /usr/lib/fglrx/ld.so.conf 100 --slave  /usr/lib/x86_64-linux-gnu/xorg/extra-modules  x86_64-linux-gnu_xorg_extra_modules /usr/lib/fglrx/xorg/modules/
$ sudo update-alternatives --config x86_64-linux-gnu_gl_conf 

Pick fglrx. ;)

$ sudo ldconfig

Replace x86_64 with i386 if you are 32-bit.
[B]
Historical 11.6 for reference:[/B]
Builds with manual patching:

**In summary:**
1) Download and extract [11.6]("http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run") from [AMD]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx").
2) Apply the patch attached to this post (it's taken from the repo 8.850 fglrx .deb, credit Alberto Milone)
3) Apply makefile patch (credit Vi0L0 at Arch)
4) Build packages
5) Install

**Details:**
1) Once downloaded:
$ sh ./ati-driver-installer-11-6-x86.x86_64.run --extract [name of directory e.g. ~/temp/ati]

This will extract the files so we can patch and build manually.

2) Download the fglrx 8.850 .deb, extract and apply the patch (or use the attached file at your own risk).

$ cd [extract-dir]/common/lib/modules/fglrx/build_mod
$ patch -i replace-global-lock-with-a-driver-specific-mutex.patch

3) Download the Arch aur catalyst.tar.gz "Tarball" from [here]("http://aur.archlinux.org/packages.php?ID=29111") and patch [extract-dir]/common/lib/modules/fglrx/build_mod/2.6.x/makefile using makefile_compat.patch (also attached). It's a one line addition and prevents a blank screen when GDM loads.

4) In the folder you extracted the files (let's call it ~/temp/ati/) run:
$ sudo ./ati-installer.sh 8.861 --buildpkg Ubuntu/oneiric

This will place packages in the parent directory (e.g. ~/temp/). sudo is needed to so we can find execstack (which lives in /usr/bin/sbin/)

5) In ~/temp/ (or wherever you put the files):
$ sudo dpkg -i *.deb

If you haven't already got an xorg.conf you will need to run:
$ sudo aticonfig --initial
and reboot.

SEO: ati fglrx 8.872 catalyst 11.7 xserver xorg-server oneiric kernel 3 3.0 3.0.0

---

### Post by P-I H on 2011-06-15
Installation of fglrx in the 3.0.0 kernel, by use of Additional Drivers worked after today's updates.

---

### Post by jfernyhough on 2011-06-15
I like to see the repo version updated just as AMD release a new version. :D

11.6 is available: [http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run)

--edit
Op updated for Catalyst 11.6 / fglrx 8.861

---

### Post by alphacrucis2 on 2011-06-15
> **jfernyhough said:**
> I like to see the repo version updated just as AMD release a new version. :D

11.6 is available: [http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run)

--edit
Op updated for Catalyst 11.6 / fglrx 8.861

Does 11.6 have useful improvements/bug fixes? Just wondering if it is worth bothering with it or wait for a later edition.

---

### Post by jfernyhough on 2011-06-16
There don't appear to be any major changes with 11.6, just "minor bug fixes" from what I've found with my searches.

gnome-shell isn't fixed so there's not a lot of point upgrading from the repo version of 8.850 unless you've really got to have the latest versions. ;)

---

### Post by jfernyhough on 2011-06-23
Alberto Milone has just pushed 8.861 to oneiric. Either wait for it to hit your mirrors or grab it from under the Builds section here: [https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.861-0ubuntu1](https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.861-0ubuntu1)

---

### Post by Harry33 on 2011-06-23
> **jfernyhough said:**
> Alberto Milone has just pushed 8.861 to oneiric. Either wait for it to hit your mirrors or grab it from under the Builds section here: [https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.861-0ubuntu1](https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.861-0ubuntu1)

That version has the multiarch support.
So now it also supports the newest mesa (7.10.3).
But you still cannot use that the current 7.10.3 mesa from Oneiric repos,
because that build has been set to break proprietary drivers.
You have to wait for a new build before the installation.

See here:
> libgl1-mesa-glx 7.10.3-0ubuntu3
Breaks:
fglrx
nvidia-173
nvidia-current

---

### Post by linuxman94 on 2011-06-23
Anyone else notice that fglrx trys to remove half the system (including unity) when installing?

---

### Post by sparker256 on 2011-06-23
> **linuxman94 said:**
> Anyone else notice that fglrx trys to remove half the system (including unity) when installing?
I had to downgrade mesa to (7.10.2-0ubuntu2) so that the new Nvidia Current would not do the same thing.

Bill

---

### Post by P-I H on 2011-06-24
> **linuxman94 said:**
> Anyone else notice that fglrx trys to remove half the system (including unity) when installing?

Yes, happened for me when I used Additional Drivers to install 8.861. Looked rather strange. Installed a daily build afterwards.

---

### Post by jfernyhough on 2011-06-24
I'd forgotten about mesa - I added the x-edgers PPA to get my patched 11.6 to install. Updated the first post with alternative mesa sources.

---

### Post by jfernyhough on 2011-06-24
Alberto has pushed a new version of the mesa libs that should be compatible with repo fglrx and nvidia-current:

[https://launchpad.net/ubuntu/oneiric/+source/mesa/7.10.3-0ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/mesa/7.10.3-0ubuntu4)

---

### Post by P-I H on 2011-06-24
The installation of fglrx fails.
I have checked in synaptic. The fglrx version is 2:8.861-0ubuntu1 and the mesa version is 7.10.3-0ubuntu4.
The system is an updated daily build from 24/6 with the Main Server repository.

This is the last part of jockey.log.
```
2011-06-24 17:14:08,944 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-06-24 17:14:16,123 DEBUG: Installing package: fglrx
2011-06-24 17:14:16,553 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.000000
2011-06-24 17:14:16,554 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.000000
2011-06-24 17:14:16,605 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.000000
2011-06-24 17:14:16,675 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.000000
2011-06-24 17:14:16,767 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.000000
2011-06-24 17:14:17,058 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.175160
2011-06-24 17:14:17,058 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.175160
2011-06-24 17:14:17,059 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.175160
2011-06-24 17:14:17,143 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.331124
2011-06-24 17:14:17,143 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.331124
2011-06-24 17:14:17,144 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.331124
2011-06-24 17:14:17,232 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.568220
2011-06-24 17:14:17,232 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 0.569224
2011-06-24 17:14:17,733 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 1.879572
2011-06-24 17:14:18,234 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 3.167923
2011-06-24 17:14:18,735 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 4.478271
2011-06-24 17:14:19,236 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 5.829468
2011-06-24 17:14:19,737 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 7.186951
2011-06-24 17:14:20,235 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 8.567479
2011-06-24 17:14:20,235 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 8.568907
2011-06-24 17:14:20,283 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 8.684772
2011-06-24 17:14:20,283 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 8.684772
2011-06-24 17:14:20,284 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 8.684772
2011-06-24 17:14:20,785 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 10.185013
2011-06-24 17:14:21,286 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 11.743603
2011-06-24 17:14:21,787 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 13.380752
2011-06-24 17:14:22,288 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 15.171875
2011-06-24 17:14:22,789 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 17.120113
2011-06-24 17:14:23,290 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 18.179075
2011-06-24 17:14:23,791 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 18.273345
2011-06-24 17:14:24,292 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 18.421034
2011-06-24 17:14:24,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 18.609573
2011-06-24 17:14:25,293 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 18.857816
2011-06-24 17:14:25,794 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 19.118629
2011-06-24 17:14:26,295 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 19.407722
2011-06-24 17:14:26,796 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 19.731381
2011-06-24 17:14:27,297 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 20.130456
2011-06-24 17:14:27,798 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 20.768347
2011-06-24 17:14:28,299 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 21.601062
2011-06-24 17:14:28,800 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 22.553185
2011-06-24 17:14:29,301 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 23.948375
2011-06-24 17:14:29,802 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 25.541531
2011-06-24 17:14:30,302 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 27.420638
2011-06-24 17:14:30,803 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 29.161484
2011-06-24 17:14:31,304 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 30.877191
2011-06-24 17:14:31,805 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 32.640032
2011-06-24 17:14:32,306 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 34.531709
2011-06-24 17:14:32,807 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 36.492517
2011-06-24 17:14:33,308 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 38.494175
2011-06-24 17:14:33,809 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 40.502117
2011-06-24 17:14:34,310 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 42.327805
2011-06-24 17:14:34,811 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 44.027800
2011-06-24 17:14:35,312 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 45.790642
2011-06-24 17:14:35,812 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 47.663465
2011-06-24 17:14:36,313 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 49.608561
2011-06-24 17:14:36,814 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 51.603934
2011-06-24 17:14:37,315 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 53.608734
2011-06-24 17:14:37,816 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 55.054202
2011-06-24 17:14:38,317 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 57.222403
2011-06-24 17:14:38,818 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 58.969533
2011-06-24 17:14:39,319 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 60.814074
2011-06-24 17:14:39,820 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 62.734032
2011-06-24 17:14:40,321 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 64.719978
2011-06-24 17:14:40,822 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 66.724779
2011-06-24 17:14:41,323 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 68.465624
2011-06-24 17:14:41,823 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 69.559151
2011-06-24 17:14:42,324 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 70.812937
2011-06-24 17:14:42,825 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 72.095004
2011-06-24 17:14:43,326 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 73.417920
2011-06-24 17:14:43,827 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 74.712556
2011-06-24 17:14:44,328 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 76.032331
2011-06-24 17:14:44,829 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 77.320682
2011-06-24 17:14:45,330 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 78.665595
2011-06-24 17:14:45,831 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 79.963373
2011-06-24 17:14:46,332 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 81.339710
2011-06-24 17:14:46,832 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 82.731757
2011-06-24 17:14:47,333 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 84.155228
2011-06-24 17:14:47,834 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 85.628976
2011-06-24 17:14:48,335 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 87.187567
2011-06-24 17:14:48,516 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 87.776611
2011-06-24 17:14:48,516 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 87.777651
2011-06-24 17:14:49,017 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 89.458792
2011-06-24 17:14:49,518 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 91.303334
2011-06-24 17:14:50,019 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 93.239003
2011-06-24 17:14:50,520 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 94.791309
2011-06-24 17:14:51,021 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 95.837702
2011-06-24 17:14:51,522 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 97.072634
2011-06-24 17:14:52,022 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 98.351558
2011-06-24 17:14:52,523 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 99.655621
2011-06-24 17:14:52,659 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4716L> 100.000000
2011-06-24 17:14:54,427 DEBUG: install progress dpkg-exec 0.000000
2011-06-24 17:14:55,834 DEBUG: install progress patch 0.000000
2011-06-24 17:14:55,934 DEBUG: install progress patch 2.857140
2011-06-24 17:14:57,282 DEBUG: install progress patch 5.714290
2011-06-24 17:14:57,314 DEBUG: install progress patch 8.571430
2011-06-24 17:14:57,849 DEBUG: install progress dkms 8.571430
2011-06-24 17:14:57,850 DEBUG: install progress dkms 11.428600
2011-06-24 17:14:58,953 DEBUG: install progress dkms 14.285700
2011-06-24 17:14:58,993 DEBUG: install progress dkms 17.142900
2011-06-24 17:14:59,475 DEBUG: install progress fakeroot 17.142900
2011-06-24 17:14:59,575 DEBUG: install progress fakeroot 20.000000
2011-06-24 17:15:00,491 DEBUG: install progress fakeroot 22.857100
2011-06-24 17:15:00,813 DEBUG: install progress fakeroot 25.714300
2011-06-24 17:15:01,368 DEBUG: install progress libc6-i386 25.714300
2011-06-24 17:15:01,368 DEBUG: install progress libc6-i386 28.571400
2011-06-24 17:15:02,478 DEBUG: install progress libc6-i386 31.428600
2011-06-24 17:15:02,519 DEBUG: install progress libc6-i386 34.285700
2011-06-24 17:15:03,182 DEBUG: install progress lib32gcc1 34.285700
2011-06-24 17:15:03,283 DEBUG: install progress lib32gcc1 37.142900
2011-06-24 17:15:03,489 DEBUG: install progress lib32gcc1 40.000000
2011-06-24 17:15:03,824 DEBUG: install progress lib32gcc1 42.857100
2011-06-24 17:15:04,634 DEBUG: install progress fglrx 42.857100
2011-06-24 17:15:04,635 DEBUG: install progress fglrx 45.714300
2011-06-24 17:15:08,578 DEBUG: install progress fglrx 48.571400
2011-06-24 17:15:08,619 DEBUG: install progress fglrx 51.428600
2011-06-24 17:15:09,228 DEBUG: install progress fglrx-amdcccle 51.428600
2011-06-24 17:15:09,329 DEBUG: install progress fglrx-amdcccle 54.285700
2011-06-24 17:15:10,089 DEBUG: install progress fglrx-amdcccle 57.142900
2011-06-24 17:15:10,121 DEBUG: install progress fglrx-amdcccle 60.000000
2011-06-24 17:15:10,159 DEBUG: install progress man-db 60.000000
2011-06-24 17:15:14,318 DEBUG: install progress ureadahead 60.000000
2011-06-24 17:15:15,223 DEBUG: install progress dpkg-exec 60.000000
2011-06-24 17:15:15,269 DEBUG: install progress patch 60.000000
2011-06-24 17:15:15,473 DEBUG: install progress patch 62.857100
2011-06-24 17:15:15,507 DEBUG: install progress patch 65.714300
2011-06-24 17:15:15,626 DEBUG: install progress dkms 65.714300
2011-06-24 17:15:17,833 DEBUG: install progress dkms 68.571400
2011-06-24 17:15:18,093 DEBUG: install progress dkms 71.428600
2011-06-24 17:15:18,124 DEBUG: install progress fakeroot 71.428600
2011-06-24 17:15:18,158 DEBUG: install progress fakeroot 74.285700
2011-06-24 17:15:18,409 DEBUG: install progress fakeroot 77.142900
2011-06-24 17:15:18,604 DEBUG: install progress libc6-i386 77.142900
2011-06-24 17:15:18,828 DEBUG: install progress libc6-i386 80.000000
2011-06-24 17:15:19,310 DEBUG: install progress libc6-i386 82.857100
2011-06-24 17:15:19,567 DEBUG: install progress lib32gcc1 82.857100
2011-06-24 17:15:19,609 DEBUG: install progress lib32gcc1 85.714300
2011-06-24 17:15:19,991 DEBUG: install progress lib32gcc1 88.571400
2011-06-24 17:15:20,090 DEBUG: install progress fglrx 88.571400
2011-06-24 17:15:20,854 DEBUG: install progress fglrx 91.428600
2011-06-24 17:15:21,625 DEBUG: install progress libc-bin 91.428600
2011-06-24 17:15:38,463 DEBUG: Shutting down

```

---

### Post by jfernyhough on 2011-06-24
Have you tried installing via synaptic or apt-get?

---

### Post by P-I H on 2011-06-24
Yes, but this is not working either, but I haven't tried it as the first alternative.
This is the terminal print out.

```
p-i@pi-MS-7125-oneiric-test:~$ sudo apt-get install fglrx
[sudo] password for p-i: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/42.1 MB of archives.
After this operation, 129 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package fglrx.
(Reading database ... 130700 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.861-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.861-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.861-0ubuntu1) ...
update-alternatives: renaming x86_64-linux-gnu_xorg_extra_modules slave link from /usr/lib/x86_64-linux-gnu/xorg/extra-modules to /usr/lib/xorg/extra-modules.
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/x86_64-linux-gnu_fglrx_dri: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)
p-i@pi-MS-7125-oneiric-test:~$
```

---

### Post by jfernyhough on 2011-06-24
Ah, looks like the mesa packages don't quite work yet. I had to use the x-edgers versions (again).

---

### Post by tista on 2011-06-25
Hi guys. ;)

I have my PPA for Thinkpad X120e yeah fglrx and radeon:
[https://launchpad.net/~tista/+archive/x120e]("https://launchpad.net/~tista/+archive/x120e")

then this PPA has the latest Mesa from oibaf's patched against Gallium3D. these would be better than X-edgers.
today I'm playing with OO on radeon driver instead of fglrx.
my fglrx had improved 8.861 latest.

so may I fork it for OO? my patch could be OK on 3.0 kernel.

cheers.

---

### Post by P-I H on 2011-06-25
It installed OK with the ppa from xorg-edgers.

I used **sudo apt-get install fglrx** to install.

---

### Post by jfernyhough on 2011-06-27
New fglrx and nvidia-current have been pushed which fix the installation script error.

---

### Post by jfernyhough on 2011-07-26
Interesting... somewhere during the last week or so the radeon kernel module is kicking in, meaning I have a lovely graphical boot screen but then a corrupted GDM/LightDM.

Booting via recovery, then resume, then login, then sudo service lightdm start got everything working again.

Then I remembered about radeon.nomodeset=1.

$ sudo nano /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.nomodeset=1"

ctrl-o, ctrl-x

$ sudo update-grub

Working again.

---

### Post by MadCow108 on 2011-07-26
I have this problem with a current oneiric:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/816290](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/816290)
does someone know a solution?
changing the grub line does not help :/

---

### Post by jfernyhough on 2011-07-27
11.7 is out. Downloading now. As of posting the release notes are 404.

> **MadCow108 said:**
> I have this problem with a current oneiric:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/816290](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/816290)
does someone know a solution?
changing the grub line does not help :/That sounds more like regression with Compiz/Mesa as fglrx was working fine before. I get the same thing if I try to use Unity (none of the interface appears, just black bars). I normally use GNOME classic, though, so I'm not sure when this first started.

---

### Post by jfernyhough on 2011-07-27
Holy moly. It built a package, it installed, and DMKS build the module, all without any errors.

Well, except for a "update-alternatives: error: alternative link /usr/bin/aticonfig is already managed by x86_64-linux-gnu_gl_conf." which was fixed by a 

$ sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf

Rebooting.

--edit
It all works. Amazing.

---

### Post by el_koraco on 2011-07-27
Does it work with Gnome Shell?

---

### Post by jfernyhough on 2011-07-27
I'll try; just been updating the first post. :)

--edit

Nope. Same as before - rainbow activities bar, very slow window movement. It also died first time I tried it so had to drop to a console and run with $ DISPLAY=:0 gnome-shell --replace

(which is also a useful trick if e.g. Compiz dies and leaves you unable to click on type into windows)

---

### Post by el_koraco on 2011-07-27
I'll try it on my Fedora install.

Edit: lawl, coming to you from a horrible version of the Gnome fallback mode!

---

### Post by cariboo on 2011-07-27
> **el_koraco said:**
> I'll try it on my Fedora install.

Edit: lawl, coming to you from a horrible version of the Gnome fallback mode!

What's so horrible about it?

---

### Post by P-I H on 2011-07-28
I have not been able to use fglrx for some weeks.
When installed with Jockey, there is an error message about broken packages and the Jockey log ends with, "2011-07-27 18:24:13,279 DEBUG: Installing package: fglrx:i386
2011-07-27 18:24:22,401 DEBUG: Shutting down", on a 64-bit system.
Installation with Synaptic works OK, but fglrx is not working. I have problems similar to thoose described by Madcow108 and jefernyhough.
This is with the daily build from 27/7.
The graphic card is Radeon 5450.

---

### Post by el_koraco on 2011-07-28
> **cariboo907 said:**
> What's so horrible about it?

Not the fallback mode itself, but it's fscked up beyond recognition. I'm getting screen artifacts left and right, the mouse is lagging, and it takes like 10 seconds for a menu to pop up.

---

### Post by miracle2k on 2011-08-03
I upgraded from the fglrx included with Ubuntu to Catalyst 11.7 (in the hopes that it would fix things like these: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/763352](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/763352) - Compiz is basically unusable for me with Natty and an ATI card).

I'm a bit confused though, because under "Information", the Catalyst Control Center still says "8.84.6" under "Driver Packaging Version", which it already said before (to be precise, it shows: 8.84.6-110324a-116088C-ATI). However, "Catalyst Version" does say "11.7".

So something did get installed, but maybe not properly? For people running 11.7, can you confirm that your "Driver Packaging Version" says something different than mine?

---

### Post by jfernyhough on 2011-08-03
If I remember correctly the version number is set when fglrx is first installed and then never updated again - I think there was a bug report to AMD but it's a minor thing.

---

### Post by TrueJournals on 2011-08-03
Hmmm... seems I have some trouble using Unity with fglrx.  Downloaded 11.7, made packages and installed, but Unity is falling back to Unity 2D.  /usr/lib/nux/unity_support_test tells me that only "GL vertex buffer object" is missing.  Unity works fine with the built-in open-source drivers, but the open source driver chokes on any game I throw at it (and I need my minecraft fix :p )  I tried adding radeon.nomodeset=0 to the boot line, but it gives the same result.  The driver seems to be working fine other than that.  This is an ATI Mobility Radeon HD 3650.  Unity has worked fine with fglrx in 11.04.

Is this a known issue?  Is there some workaround? Any ideas?

[edit]Hmmm... downgraded to the fglrx in repos and it "worked!"  But I ran into [Bug #819144](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144), which made the system unusable.  I tried to reinstall the new version over the current one, but dpkg gave a couple errors.  Then tried just purging everything, and now I'm left with a system in which X doesn't work properly O.o  I think some alternatives got screwed up somewhere... I'll have to play around with it more tomorrow.

---

### Post by ratcheer on 2011-08-04
@TrueJournals, thanks for the link to the bug. I have added an "affects me too" to the bug.

Tim

---

### Post by tista on 2011-08-04
Hi guys. ;)

I've uploaded fglrx-8,872 to my PPA:
[https://launchpad.net/~tista/+archive/x120e]("https://launchpad.net/~tista/+archive/x120e")

and I've experienced such similar issues on 3D desktop environments... :sad:
so I wanna know whether the results you guys run glxinfo?
mine is here:
```
name of display: :0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6300 series Graphics
OpenGL version string: 1.4 (2.1 (4.1.10907 Compatibility Profile Context))
OpenGL extensions:
.....
```

yeah it seems direct renderings are dead on latest 8.872 with Radeon HD6300 (thinkpad X120e).
but I run fglrx as side by side with radeon dirver and mesa 7.12-git development states, so I couldn't confirm it really caused fglrx's problems...

cheers.

---

### Post by TrueJournals on 2011-08-04
I ran into the same problem with my Radeon HD Mobility 3650.  Part of the reason I chose to downgrade to the driver in the repo.  Turning the debug flag on, it seemed like it was looking for a software rasterizer, and not the fglrx driver. Strange :/

---

### Post by tista on 2011-08-04
> **TrueJournals said:**
> I ran into the same problem with my Radeon HD Mobility 3650.  Part of the reason I chose to downgrade to the driver in the repo.  Turning the debug flag on, it seemed like it was looking for a software rasterizer, and not the fglrx driver. Strange :/

Hi TrueJournals. ;)

OK...but our problems are a bit differences between you and i.
1. mine is now accepted proper libGL.so provided from fglrx 8.872.
2. yours seems to fail to load such libGL.so from /usr/lib/...

if so, you might have to re-make alternatives via gl_conf. mine is quite more bad thing... because drm seems to fail to initialize within system booting... yeah it caused kernel module...

cheers.

**P.S**
I've found the mistakes in my pakcages and fixed about dkms, then re-made symlink /usr/lib/libGL.so and libGL.so.1. finally I could confirm the bug post of TrueJournals. yeah randomly black areas appeared... :sad:
thanks for your bug report TrueJournals!! :)

---

### Post by rajeev1204 on 2011-08-04
Ok so iam all ready with a brand new alpha 3 with ubuntu radeon driver. if i install fglrx from the repo all should be good?


thanks

rajeev

---

### Post by TrueJournals on 2011-08-05
> **tista said:**
> Hi TrueJournals. ;)

OK...but our problems are a bit differences between you and i.
1. mine is now accepted proper libGL.so provided from fglrx 8.872.
2. yours seems to fail to load such libGL.so from /usr/lib/...

if so, you might have to re-make alternatives via gl_conf. mine is quite more bad thing... because drm seems to fail to initialize within system booting... yeah it caused kernel module...

cheers.

**P.S**
I've found the mistakes in my pakcages and fixed about dkms, then re-made symlink /usr/lib/libGL.so and libGL.so.1. finally I could confirm the bug post of TrueJournals. yeah randomly black areas appeared... :sad:
thanks for your bug report TrueJournals!! :)

After playing around with it a bunch, I finally got back to working radeon drivers!  Yay!  For any reference, I think this did it:
```
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
```
Honestly, I think only libgl1-mesa-glx would have sufficed, but I ran both and it worked :D

As much as I would like to take credit for that bug report, I can't :P MadCow linked to a dupe of it on the top of Page 3, and it looks like someone else might have filed it.  Regardless, I'm anxiously awaiting a fix so I can use the proprietary driver again...

Although, I never did get 11.7 working... Time to break my OS again ;)

[edit]Ah, looks like there's a small packaging problem with 11.7.  This line:
```
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
```
Should be updating a platform-specific alternative.  Since I'm running 64-bit, I'll try adding that alternate as:
```
sudo update-alternatives --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf 100 --slave /usr/lib/x86_64-linux-gnu/xorg/extra-modules x86_64-linux-gnu_xorg_extra_modules /usr/lib/fglrx/xorg/modules/
```
I'll post back with results...

[edit2] Nope :/
```
bobby@rgraese-oneric:~$ LIBGL_DEBUG=verbose glxinfo | grep direct
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed (/usr/lib32/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrastg_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrastg_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrastg_dri.so failed (/usr/lib/fglrx/dri/swrastg_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/tls/swrastg_dri.so
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/swrastg_dri.so
libGL error: dlopen /usr/lib32/fglrx/dri/swrastg_dri.so failed (/usr/lib32/fglrx/dri/swrastg_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrastg_dri.so
libGL error: reverting to indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

Can anyone explain to me what's going on here? I've gotta be missing something simple...

[edit3] Ah-ha!  I just needed to run sudo ldconfig!
So, current issue with fglrx packaging in 11.7 is that it creates gl_conf as an alternative, instead of arch-specific gl_conf.  This means that when ldconfig is run, it's looking for both the fglrx GL libraries, as well as the mesa ones.  The solution is to add fglrx to the alternatives list for the arch-specific gl_conf with my line above, change to this alternative, then run ldconfig.

Of course, the black box bug is still present, but this means that 11.7 does *work*!

I apologize for any typos... I'm typing this as a giant black box covers most of my screen :(

---

### Post by P-I H on 2011-08-05
I have a fresh and fully updated Alpha3 (amd64) installation with Unity.
To install fglrx by Additional Drivers does not work. I think Jockey tries to install fglrxi386 instead of fglrx.
Fglrx installs OK with Synaptic, but it is not working.
The Desktop is just a black field. The Launcher and the upper panel is not visible.
However the applets in the upper panel are working. It is possible to start System Settings. It is also possible to start applications from the Launcher, but you have to guess the position. 
Much as described in the bug report Bug #819144.

---

### Post by jfernyhough on 2011-08-05
I've updated the op with your fix. Nice work!

---

### Post by ratcheer on 2011-08-05
Here is what I got when I attempted the revised instructions in Post #1. What do I need to do?

```
sudo dpkg -i *.deb
(Reading database ... 176450 files and directories currently installed.)
Preparing to replace fglrx 2:8.861-0ubuntu4 (using fglrx_8.872-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx ...
dpkg: warning: unable to delete old directory '/usr/lib/dri': Directory not empty
Preparing to replace fglrx-amdcccle 2:8.861-0ubuntu4 (using fglrx-amdcccle_8.872-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.872-0ubuntu1_amd64.deb) ...
Setting up fglrx (2:8.872-0ubuntu1) ...
update-alternatives: error: alternative link /usr/bin/aticonfig is already managed by x86_64-linux-gnu_gl_conf.
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
tim@tim-oneiric:~/ATIDriver11.7$ sudo update-alternatives --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf 100 --slave /usr/lib/x86_64-linux-gnu/xorg/extra-modules x86_64-linux-gnu_xorg_extra_modules /usr/lib/fglrx/xorg/modules/
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
```

Thanks,
Tim

---

### Post by TrueJournals on 2011-08-05
Wow! That's not good.  Did you try installing 11.7 over the installation from the repository?  Try the following commands to fix it:
```
sudo apt-get purge fglrx*
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
sudo dpkg -i fglrx*.deb
sudo update-alternatives --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf 100 --slave /usr/lib/x86_64-linux-gnu/xorg/extra-modules x86_64-linux-gnu_xorg_extra_modules /usr/lib/fglrx/xorg/modules/
sudo ldconfig
```

This series of commands should purge your current fglrx, reactivate the mesa drivers, then reinstall the fglrx drivers (hopefully correctly this time)!

You might have to:
```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```
and make sure fglrx is selected.  You should do this before the ldconfig line above.

Hope this helps!

---

### Post by ratcheer on 2011-08-05
Thanks. Yes, before I tried installing 11.7 I had the standard repository 11.6 driver.

Thanks for the tips. I will go try them, now. If they don't work, I guess it is time for a fresh install, anyway. :(

Tim

---

### Post by ratcheer on 2011-08-05
Uh oh! I seem to have lost access to my entire machine, even my "production" Natty instance.
 
When I reboot, I can make a selection from the grub2 menu. If I choose Natty, it boots to the login screen, at which point I have lost contact with the PC. I cannot do anything on the login screen. The mouse pointer will not even move. I cannot get to a console with Ctrl-Alt-F1.
 
If I choose Recovery option for either Natty or Oneiric, it brings up the recovery selection screen, at which point I cannot do anything with the keyboard. Every minute or so, it writes a line of garbage characters to the screen.
 
This is very bad. The last thing I can think to try is to boot to a live CD and chroot to either installation. But, I have no idea what I would do when I got there.
 
How could messing up the video driver on Oneiric screw up my Natty installation?
 
Tim

---

### Post by jfernyhough on 2011-08-05
> 
update-alternatives: error: alternative link /usr/bin/aticonfig is already managed by x86_64-linux-gnu_gl_conf.
It looks like

sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf

is the crucial part to fix that particular error - I managed to delete it from the first post (it's back there now).

> How could messing up the video driver on Oneiric screw up my Natty installation?It can't - or at least shouldn't. The only thing connecting the two is GRUB - I wonder if the initramfs needs to be rebuilt. If I remember correctly someone said that it's not rebuilt (or perhaps just the driver modules updated?) for fglrx/nvidia driver installations.

If this is the case, you'll need to run:

$ sudo update-initramfs -u -k all

Are you booting with radeon.nomodeset=1 ?

---

### Post by ratcheer on 2011-08-05
Was that a response to my post #44 about losing all access to my machine?
 
Tim

---

### Post by jfernyhough on 2011-08-05
The second half was (or at least supposed to be). :)

---

### Post by ratcheer on 2011-08-05
Thank you. I will try to do that via chroot from a live cd.
 
I have not overtly put anything in my grub config, so I don't know about radeon.nomodeset=1
 
Tim

---

### Post by jfernyhough on 2011-08-05
OK, try that first. When GRUB selection shows when you first boot, press e to edit, move down to the line with "quiet splash" and add radeon.modeset=1 to the end. Press ctrl-x to boot.

---

### Post by ratcheer on 2011-08-05
I booted a live cd and chrooted to Oneiric. I ran the update-initramfs command and it rebuilt initramfs for 3.0.0.7, 3.0.0.6, and 3.0.0.5.
 
I rebooted and did the e and added radeon.modeset=1 for Natty. It still boots up to the GUI login prompt and the mouse and keyboard are dead.
 
I did the same thing for Oneiric. It boots to a screen with a fairly large X mouse pointer in the middle. The mouse will not move it and nothing can be typed.
 
I tried to do the recovery mode boot of Natty and it still goes to the recovery menu screen and then does not respond to the keyboard.
 
How I regret trying to update my Catalyst driver. :(
 
Tim

---

### Post by ratcheer on 2011-08-05
I am going to do a fresh install of Oneiric. If that works, I hope I will be able to use it to fix whatever is wrong with Natty. I have too much going on in Natty to lose it.
 
Tim

---

### Post by ratcheer on 2011-08-05
I have fresh installed Oneiric. I got Natty back, after a fashion. I am opening a new thread about all the problems I am having.

[http://ubuntuforums.org/showthread.php?t=1819114](http://ubuntuforums.org/showthread.php?t=1819114)

Thanks for your help,
Tim

---

### Post by kiddykoff on 2011-08-06
I'm having a problem when i run this command.
```

$ sudo update-alternatives --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf 100 --slave /usr/lib/x86_64-linux-gnu/xorg/extra-modules x86_64-linux-gnu_xorg_extra_modules /usr/lib/fglrx/xorg/modules/
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/x86_64-linux-gnu/xorg/extra-modules.dpkg-tmp a symlink to /etc/alternatives/x86_64-linux-gnu_xorg_extra_modules: No such file or directory
```
So since this file is missing what do i do now?

---

### Post by TrueJournals on 2011-08-06
Are you running 64-bit Ubuntu?  You might be fine as is, but I can't be certain.  I guessed on the --slave part based on mesa, so I'm not entirely sure it's necessary.  Well... breaking your OS is expected, right? :D

---

### Post by kiddykoff on 2011-08-06
Yes, i'm using 64 bit. I'm trying this command as well and getting this result.

```
$ sudo update-alternatives --config x86_64-linux-gnu_gl_conf 
update-alternatives: error: no alternatives for x86_64-linux-gnu_gl_conf.
```
and when i run sudo ldconfig there is no options to choose fglrx

I'll restart and see what happens. Is there a command to see if they installed correctly? I think fglrx_info is used for this but i may be wrong.

---

### Post by TrueJournals on 2011-08-06
If that's showing that there are no alternatives for x86_64-linux-gnu_gl_conf, then you should be alright, as fglrx installs an alternative for gl_conf which will take over and should work.  sudo ldconfig just updates the library configuration, it doesn't give any output.

Good luck!  Let us know what happens!

---

### Post by kiddykoff on 2011-08-07
so i've done fglrxinfo and got this

$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  140 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
 
I've tried changing the grub file with, GRUB_CMDLINE_LINX_DEFAULT="quiet splash radeon.nomodeset=1"

I'm also not able to play some of the games i've played. They return errors just the same as fgl_glxgears and flgrxinfo.

I've tried the other instructions,

sudo apt-get purge fglrx*
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
sudo dpkg -i fglrx*.deb
sudo update-alternatives --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf 100 --slave /usr/lib/x86_64-linux-gnu/xorg/extra-modules x86_64-linux-gnu_xorg_extra_modules /usr/lib/fglrx/xorg/modules/
sudo ldconfig

and this has not helped either.

I've just noticed this is an oneric ocelot thread and i'm using natty. I'm not an expert at these things, so i figure if i do apt-get purge fglrx and update alternatives --remove-all that i'll be able to get my unity back.

---

### Post by TrueJournals on 2011-08-07
> **kiddykoff said:**
> I've just noticed this is an oneric ocelot thread and i'm using natty. I'm not an expert at these things, so i figure if i do apt-get purge fglrx and update alternatives --remove-all that i'll be able to get my unity back.

I'm not sure, then :/  I don't know if Natty organizes the alternatives the same way Oneiric does, and I don't have a Natty install handy to test out.

You might need the apt-get --reinstall line in what you want to try, too.  That will recreate the alternatives you just removed ;)

---

### Post by kiddykoff on 2011-08-07
Yeah, I realized that too. I used the commands

sudo apt-get purge fglrx*
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
sudo ldconfg

update-alternatives didn't do anything, so it was unnecessary. Thanks for the help.

---

### Post by tista on 2011-08-08
Hi guys.

today I've created this patch for arch-dependent alternatives:
[http://paste.ubuntu.com/660922/]("http://paste.ubuntu.com/660922/")

and my PPA had finished to build for both oneiric and natty:
[https://launchpad.net/~tista/+archive/x120e]("https://launchpad.net/~tista/+archive/x120e")

so if you guys wanna give it a try, use my PPA as testing branch!! ;) and I'm happy if you send me the detailed reports...

cheers.

---

### Post by rbrick49 on 2011-08-08
hi folks 
just put  the latest oneiric on the computer fglrx just doesnt work ,I have a 6950 card all I get in unity is a black screen that flashes

---

### Post by ratcheer on 2011-08-08
> **rbrick49 said:**
> hi folks 
just put  the latest oneiric on the computer fglrx just doesnt work ,I have a 6950 card all I get in unity is a black screen that flashes

Try Unity 2D. I have mostly been unable to get Unity to work, either. Just works for a day here and a day there.

Tim

---

### Post by TrueJournals on 2011-08-08
> **rbrick49 said:**
> hi folks 
just put  the latest oneiric on the computer fglrx just doesnt work ,I have a 6950 card all I get in unity is a black screen that flashes

Yup... that's the current state of things :/ Use Unity 2D as ratcheer suggested.  Also, can you add a "me too" to [Bug #819144](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144)?  It's already high priority, but having more reports couldn't hurt :)

---

### Post by rbrick49 on 2011-08-08
> **TrueJournals said:**
> Yup... that's the current state of things :/ Use Unity 2D as ratcheer suggested.  Also, can you add a "me too" to [Bug #819144](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144)?  It's already high priority, but having more reports couldn't hurt :)

I put a me to

---

### Post by rbrick49 on 2011-08-08
Hi guys I tried from amd page to install 11.7 I did it per the instructions from here [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Create_.deb_packages](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Create_.deb_packages). and it is working for me but it downloaded a lot of dependencies but is working ok
regards ron

---

### Post by tista on 2011-08-09
> **rbrick49 said:**
> Hi guys I tried from amd page to install 11.7 I did it per the instructions from here [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Create_.deb_packages](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Create_.deb_packages). and it is working for me but it downloaded a lot of dependencies but is working ok
regards ron

@Ron

you mean Unity works on oneiric?!

---

### Post by rbrick49 on 2011-08-09
> **tista said:**
> @Ron

you mean Unity works on oneiric?!yes tista unity is working but gnome shell is not working all i get from gnome shell is nautilus bar on top of screen I purged gnome shell and reinstalled but still only nautilus but unity seems fine on oneiric with that 11.7 driver fgl_glxgears work really fast I forget what the frame rate was will check I am on natty at the moment by the way my graphics card is a 6950
regards Ron
by the way oneiric is a fresh install from 2 days ago and now its running on 3.0.0.8 kernel

---

### Post by rbrick49 on 2011-08-09
@tista
heres the frame rate tista
7111 frames in 5.0 seconds = 1422.200 FPS
6766 frames in 5.0 seconds = 1353.200 FPS
7105 frames in 5.0 seconds = 1421.000 FPS
6882 frames in 5.0 seconds = 1376.400 FPS
7043 frames in 5.0 seconds = 1408.600 FPS
6887 frames in 5.0 seconds = 1377.400 FPS

---

### Post by tista on 2011-08-09
> **rbrick49 said:**
> @tista
heres the frame rate tista
7111 frames in 5.0 seconds = 1422.200 FPS
6766 frames in 5.0 seconds = 1353.200 FPS
7105 frames in 5.0 seconds = 1421.000 FPS
6882 frames in 5.0 seconds = 1376.400 FPS
7043 frames in 5.0 seconds = 1408.600 FPS
6887 frames in 5.0 seconds = 1377.400 FPS

Ahh.. OK.

this means you had changed the "wait for vsync" off via ccsm or catalyst GUI, right? I'm not so interested in such scores of glxgears, but looks nice. ;)

does anybody tried disabling vsync there?

cheers.

---

### Post by rbrick49 on 2011-08-09
> **tista said:**
> Ahh.. OK.

this means you had changed the "wait for vsync" off via ccsm or catalyst GUI, right? I'm not so interested in such scores of glxgears, but looks nice. ;)

does anybody tried disabling vsync there?

cheers.the only thing I did in ccsm was tick the ubuntu unity plugin box

---

### Post by rbrick49 on 2011-08-10
today fglrx stopped working unity back to flashing screen I have no idea why

---

### Post by rbrick49 on 2011-08-10
I just bit the bullet and did a reinstall of fglrx from amd and it is working again with unity I will see how many hours it lasts for this time

---

### Post by tista on 2011-08-10
Hi guys. ;)

today I've polished 3 scripts in the package on my PPA:
[https://launchpad.net/~tista/+archive/x120e]("https://launchpad.net/~tista/+archive/x120e")

1. fglrx.preinst:
[http://paste.ubuntu.com/662577/]("http://paste.ubuntu.com/662577/")

2. fglrx.postinst:
[http://paste.ubuntu.com/662576/]("http://paste.ubuntu.com/662576/")

3. fglrx.prerm:
[http://paste.ubuntu.com/662578/]("http://paste.ubuntu.com/662578/")

and then I'm running this revision on my Thinkpad X120e (Zacate, Radeon HD6310) now... so stand-alone compiz works well but unity 4.6.0-0ubuntu2 is damned still... :sad:
(see attached shot with "Shift Switcher" on stand-alone compiz)

but "/usr/lib/nux/unity_support_test -p" said here:
```
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6300 series Graphics
OpenGL version string:  4.1.10907 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```
Yep, it seems good? but actually unity didn't work anymore!!

cheers.

---

### Post by rbrick49 on 2011-08-10
@tista
ron@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series 
OpenGL version string:  1.4 (2.1 (4.1.10907 Compatibility Profile Context))

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
ron@ubuntu:~$ 
regards ron

---

### Post by tista on 2011-08-10
> **rbrick49 said:**
> @tista
ron@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series 
OpenGL version string:  1.4 (2.1 (4.1.10907 Compatibility Profile Context))

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
ron@ubuntu:~$ 
regards ron

Hi Ron,

OMG... it seems too bad.
is it really you were running unity on this instead of unity-2d?! if so, let us know your some logs:
* output of glxinfo
* /var/log/Xorg.0.log
* $HOME/.xsession-errors

I gonna concern that your openGL ver. string seemed strange...  yeah looks like open-sourced SGI/SGX.

best regards.

---

### Post by TrueJournals on 2011-08-10
Ron, that's exactly the output you get if fglrx isn't installed correctly ;)  Did you run the update-alternatives line and then sudo ldconfig?  If not, Xorg is trying to use fglrx, but OpenGL can't find fglrx libraries and is using software libraries.  Overall, you're not actually getting accelerated 3D.

---

### Post by tista on 2011-08-10
@TrueJournals

I'm happy you could fix the python scripts. ;)
yeah we might have to do some patchworks as well for the scripts written in python...
"switchlibGL" is here:
[http://paste.ubuntu.com/662746/]("http://paste.ubuntu.com/662746/")

see the line 129, yep this still saw unused gl_conf, but I couldn't speak python. :sad: 

cheers.

---

### Post by TrueJournals on 2011-08-10
@tista
[edit] [http://paste.ubuntu.com/662782/](http://paste.ubuntu.com/662782/) should be a good modified version.  Only two lines need changing ;) (I added an import up top!)  Tested with a query on amd64.  It should work fine on i386, but I don't have an install handy to test.  Haven't poked around in the package at all, is there anything else that needs fixing...?

---

### Post by rbrick49 on 2011-08-10
@ Truejournals heres the output from update alternatives
ron@ubuntu:~$ sudo update-alternatives --config x86_64-linux-gnu_gl_conf 
[sudo] password for ron: 
There is only one alternative in link group x86_64-linux-gnu_gl_conf: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Nothing to configure.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.

---

### Post by TrueJournals on 2011-08-10
Ron,
Can you add tista's PPA and try upgrading your fglrx packages to his versions?  His scripts should be able to fix your system... hopefully!

---

### Post by rbrick49 on 2011-08-10
> **TrueJournals said:**
> Ron,
Can you add tista's PPA and try upgrading your fglrx packages to his versions?  His scripts should be able to fix your system... hopefully!
ok will I use fglrx from the repos I am just doing a fresh install
regards Ron

---

### Post by tista on 2011-08-10
> **TrueJournals said:**
> @tista
[edit] [http://paste.ubuntu.com/662782/](http://paste.ubuntu.com/662782/) should be a good modified version.  Only two lines need changing ;) (I added an import up top!)  Tested with a query on amd64.  It should work fine on i386, but I don't have an install handy to test.  Haven't poked around in the package at all, is there anything else that needs fixing...?

Nice and thanks TrueJournals!! :P

I hope this script was the last one that we should fix in wrong path/alternatives... oh god... just now I've found another "switchlibglx" in python, but its cody was very similar to previous one, so I forked your method and applied to this one!!

finally I would include your edits into my PPA ASAP!

thanks a lot again... :P

tista

**EDIT**
Just now the latest revision had landed!!
yeah I've applied the edits by TrueJournals:
1. switchlibGL:
[http://paste.ubuntu.com/663041/]("http://paste.ubuntu.com/663041/")
2. switchlibglx:
[http://paste.ubuntu.com/663043/]("http://paste.ubuntu.com/663043/")

I hope there's nothing to be loaded older "gl_conf" in an alternative...
and now I have a question. if someone had gl_conf in alternatives, fglrx must purge such gl_conf before installations? if so, I would add this workaround. or that would be better to apply dpkg-divert?

cheers.

---

### Post by rbrick49 on 2011-08-10
@tista Hi I just did a fresh install of oneiric and added your ppa fglrx wont install heres the output
Setting up fglrx (2:8.872~oneiric5) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/fglrx_dri: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1

---

### Post by tista on 2011-08-10
@Ron

> ```
update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/fglrx_dri: No such file or directory
```

I don't know why package extractions seems to be failed...:sad:
.dpkg-tmp files comes from extractions. OK... anyway you should redo the install. but if you had broken downloaded file, first you should run apt-get clean and then re-run apt-get install fglrx fglrx-amdcccle, right?

ciao.

---

### Post by rbrick49 on 2011-08-11
Hi tista I had a bad install trying again it is probably not a good time to do this as we are getting a really heavy rain storm wish me luck
ron

---

### Post by tista on 2011-08-11
> **rbrick49 said:**
> Hi tista I had a bad install trying again it is probably not a good time to do this as we are getting a really heavy rain storm wish me luck
ron

@Ron 

Oh what a pity... :sad:
umm... you did all update others before installing fglrx? if you run "gksu update-manager -d", it says something upgradable stuff?

tista

---

### Post by rbrick49 on 2011-08-11
> **tista said:**
> @Ron 

Oh what a pity... :sad:
umm... you did all update others before installing fglrx? if you run "gksu update-manager -d", it says something upgradable stuff?

tistayes thats what happened tista it wasnt fully upgraded and caused fglrx to be corrupt this time I have the same problem installer is crashing so I have to add what is missing,it is not downloading all the files.this time I know whats wrong will get back to you soon 
regards ron

---

### Post by jfernyhough on 2011-08-11
Alberto has just pushed 8.872:

[https://launchpad.net/ubuntu/oneiric/+source/fglrx-installer/2:8.872-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/fglrx-installer/2:8.872-0ubuntu1)

> fglrx-installer (2:8.872-0ubuntu1) oneiric; urgency=low

  * New upstream release 8.872 (11-7).
  * debian/rules:
    - Further improvements on files generation from templates.
    - Make sure to ship an empty ld.so.conf for the other arch for
      PXpress.
  * debian/[fglrx.postinst.in]("http://fglrx.postinst.in/"):
    - Make amdconfig point at aticonfig.
  * debian/control, debian/README:
    - Replace "ATI" with "AMD".
  * debian/control:
    - Add conflicts/replaces to deal with fglrx-updates.
    - Add fglrx-amdcccle to Replaces in fglrx.
  * debian/[fglrx.install.in]("http://fglrx.install.in/"):
    - Make sure to always install PXpress scripts in /usr/lib/fglrx
      (LP: #815322).
  * debian/[fglrx-amdcccle.install.in]("http://fglrx-amdcccle.install.in/"):
    - Do not install the PXpress scripts in amdcccle.
  * debian/pxpress/switchlib{glx|GL):
    - Fix issue when setting the alternative for the other arch.
  * Disable replace-global-lock-with-a-driver-specific-mutex.patch.

Date: Thu, 11 Aug 2011 18:06:51 +0200
Changed-By: Alberto Milone <[EMAIL="alberto.milone@canonical.com"]alberto.milone@canonical.com[/EMAIL]>
Maintainer: Ubuntu Core Developers <[EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]ubuntu-devel-discuss@lists.ubuntu.com[/EMAIL]>
[https://launchpad.net/ubuntu/oneiric/+source/fglrx-installer/2:8.872-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/fglrx-installer/2:8.872-0ubuntu1)



---

### Post by TrueJournals on 2011-08-11
Hooray!  I'm going to assume that a repacking of the same driver won't fix the black box issue.  Also, I noticed AMD has released an OpenGL 4.2 preview driver at [http://support.amd.com/us/kbarticles/Pages/AMDCatalystOpenGL42BetaLinux.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalystOpenGL42BetaLinux.aspx) .  Anyone care to try it out? ;)

---

### Post by P-I H on 2011-08-11
The installation by use of Additional Drivers worked fine, but Unity 3D shows the black fields. It is however possible to logout and login with Unity 2D, that works OK.
For me that's the same status as if fglrx is installed with Synaptic or Catalyst 1.7 is installed according to jfernyhough's instruction.

Steam works and it is at least possible to play Torchlight.
With the open driver it is not possible to login to Steam.

---

### Post by tista on 2011-08-11
> **TrueJournals said:**
> Hooray!  I'm going to assume that a repacking of the same driver won't fix the black box issue.  Also, I noticed AMD has released an OpenGL 4.2 preview driver at [http://support.amd.com/us/kbarticles/Pages/AMDCatalystOpenGL42BetaLinux.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalystOpenGL42BetaLinux.aspx) .  Anyone care to try it out? ;)

Hi TrueJournals. ;)

Yeah just now I'm uploading 8.880 to my PPA!!
but I've never tried official 8.872, so I might have to replace the debian directory in source pakcage soon...

cheers.

**EDIT**
Now fglrx-installer 8.880~oneiric1 had landed on my PPA!!
see attached shot shows some basic capabilities...

unfortunately 8.880 seems almost same as 8.872 in these stuff:
* Gnome-Shell
* Unity

so the development team looks like ugly monkey train, you know?!

**EDIT #2**
now we could see the new package named "fglrx-updates" in the main repository!!
what's that?

the contributer didn't point anything out in descriptions and/or changelog... :sad: fglrx is a binary crap package, so ubuntu contributers couldn't fix any issues causing sources, isn't it? if not, they first must contact to AMD developers before releasing any complicated packages....

---

### Post by jfernyhough on 2011-08-18
Official Catalyst 11.8 has been released: [http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run)

It may be some time before I check these as I'm now running Debian Sid+Experimental on my laptops and they've already got 11.8 in the repo. :) (along with a fully-working GNOME3 fallback mode)

Looking at Arch there are no extra patches needed so the previous manual process for 11.7 should work fine.

---

### Post by TrueJournals on 2011-08-18
Actually, looks like they've fixed the packaging scripts in 11.8!  Building debs and installing should work fine... Testing now!

[edit]Well, install went fine, but still experiencing the black box bug in Unity.... :(

---

### Post by tista on 2011-08-18
Hi guys.

OK... so may I have to sync to upstream catalyst-11.8 with my PPA?
which the driver's version it had? if almost same as 8.880 had been employed, I suppose I didn't have to update my own PPA...

@JF

Thanks for every info you posted!! ;)
well... how the stand-alone compiz works on 11.8?
and I think we might have to report and file all our experiences to AMD devs on somewhere like official support forum. or if ubuntu contributer already had done it, I'm happy...

@TrueJournals

Oh sad... :sad:
the devs still didn't fix the unity issues, right?

cheers.

---

### Post by TrueJournals on 2011-08-18
The version on this driver is 8.881.  The driver installer now creates good packages for Oneiric, so you don't have to worry about modifying its scripts.

And nope... looks like the Unity issue is still there.  Waiting for a fix for that...

---

### Post by rajeev1204 on 2011-08-19
The new 11.8 has the mouse freeze bug fixed.Any idea when this will make it to the official repository?

---

### Post by P-I H on 2011-08-19
I used the method in cchtml.com to install fglrx in an Ubuntu Natty installation and it works at least for the Gnome and Ubuntu 2D logins. I just replaced natty with oneiric in the command **sudo sh ./ati-driver-installer-11-8-x86.x86_64.run --buildpkg Ubuntu/natty**
The mouse freeze bug is fixed.
There are however still some problems
- icons in the top panel are not shown correctly
- the Nautilus menu is shown faintly under Activities also in the upper panel.
- the curser is not as nice as in the open driver.
- Steam is not working in Gnome, as there are a lot of screen corruptions. However it works in Ubuntu 2D, but there are som screen corruptions.

---

### Post by masuch on 2011-08-24
Hi,

I have installed catalyst 11.8 couple of days ago on kernel 3.0.3 but I do not have rendering.


LIBGL_DEBUG=verbose glxinfo |grep rendering

libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed (/usr/lib32/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: reverting to indirect rendering
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed (/usr/lib32/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: reverting to indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


update-alternatives --get-selections | grep gl_conf

gl_conf                        auto     /usr/lib/fglrx/ld.so.conf
x86_64-linux-gnu_egl_conf      auto     /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
x86_64-linux-gnu_gl_conf       auto     /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf


glxinfo |grep OpenGL

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series  
OpenGL version string: 1.4 (2.1 (4.1.11005 Compatibility Profile Context))
OpenGL extensions:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series  
OpenGL version string: 1.4 (2.1 (4.1.11005 Compatibility Profile Context))
OpenGL extensions:


Please any help how to get rendering?

---

### Post by jfernyhough on 2011-08-24
Alberto Milone has just pushed 8.881 towards the repos.

> fglrx-installer (2:8.881-0ubuntu1) oneiric; urgency=low

  * New upstream release 8.881 (11-8).
  * debian/rules:
    - Make sure to use LICENSE instead of ATI_LICENSE, as it
      has been renamed by AMD.
    - Add a hack for pbuild which would otherwise fail to call
      execstack when trying to build.
    - Rename the grub_fb_blacklist link, so that it has a name
      shared with all the other proprietary drivers.

Date: Wed, 24 Aug 2011 12:08:49 +0200
Changed-By: Alberto Milone <[EMAIL="alberto.milone@canonical.com"]alberto.milone@canonical.com[/EMAIL]>
[https://launchpad.net/ubuntu/oneiric/+source/fglrx-installer/2:8.881-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/fglrx-installer/2:8.881-0ubuntu1)

---

### Post by masuch on 2011-08-24
Hi,
I have installed:

xvba from:
[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/?C=N;O=A](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/?C=N;O=A)

and this ppa:dtl131/catalysthacks:
[https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.881-0ubuntu1/+build/2741982](https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.881-0ubuntu1/+build/2741982)

and fglrx from:
[https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.881-0ubuntu1/+build/2741982](https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.881-0ubuntu1/+build/2741982)


and the following are the results:

$ glxinfo |grep OpenGL
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series  
OpenGL version string: 4.1.11005 Compatibility Profile Context
OpenGL shading language version string: 4.10
OpenGL extensions:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series  
OpenGL version string: 4.1.11005 Compatibility Profile Context
OpenGL shading language version string: 4.10
OpenGL extensions:

$ glxinfo |grep rendering
direct rendering: Yes
direct rendering: Yes


$ glxgears
30037 frames in 5.0 seconds = 6007.250 FPS
37841 frames in 5.0 seconds = 7568.194 FPS
39265 frames in 5.0 seconds = 7852.999 FPS
40186 frames in 5.0 seconds = 8037.150 FPS
40522 frames in 5.0 seconds = 8104.379 FPS


Thanks a lot for this catalysthack , rendering works

What I do not understand is:
I had before ~ 12.000,- fps with catalyst 11.8 downloaded from AMD web site.

There is big performance degradation according to glxgears.
Is there any explanation for it ?

Thanks for any clue.
M.

---

### Post by budluva04 on 2011-08-24
ok i've installed the newest fglrx package from the repos...
```

billybigrigger@victor:~$ sudo apt-cache policy fglrx
fglrx:
  Installed: 2:8.881-0ubuntu1
  Candidate: 2:8.881-0ubuntu1

```

and have booted this fine, but i had to manually edit my grub line, since grub won't show 3.0.0-9...only -7, so i manually edited the grub line, changed 3.0.0-7 to -9, and added "nomodeset" to the boot line and hit f10 to boot, all is well...seem's to be working fine here...only compiz borked today, so i'm stuck using Ubuntu 2D from the lightdm login.

Logging into "Ubuntu" gtkperf shows an 8.8 second test, glxgears is over 1000fps ~ 5s, compared to 300fps ~ 5s in "Ubuntu 2D"

glxinfo reports direct rendering is enabled...so as far as i can tell, the new 881 driver is working correctly here...

---

### Post by masuch on 2011-08-25
I did not have such luck. When I switched to natty kernel 3.0.0-9.12 - and run glxinfo - does not work with usual error messages.

---

### Post by ratcheer on 2011-08-25
In the bug report (819144), some people seem to be saying they are getting fglrx and Unity working in Oneiric. But, it certainly is not working for me. Does anyone here actually have them working together in Oneiric?

Tim

---

### Post by ratcheer on 2011-08-25
> **ratcheer said:**
> In the bug report (819144), some people seem to be saying they are getting fglrx and Unity working in Oneiric. But, it certainly is not working for me. Does anyone here actually have them working together in Oneiric?

Tim

Hmmm. I just received about 94 updates and installed them. Many Unity updates were included. Now, Unity (3D) seems to be working on my system.

I wonder how long it will continue working?

Tim

---

### Post by tista on 2011-08-25
Hi guys. ;)

I've seen a lot of happy reports fglrx could run on unity-3D perfectly...

But one thing...
We have to track the reasons down why suddenly unity-3D had wiped fglrx away. the bug report #819144 page seems to still be un-updated to "fix committed" or "fix-released".  and where did the success come from? unity core, nux, compiz, etc...?

nux changelog said:
> nux (1.4.0-0ubuntu2) oneiric; urgency=low

  * Backport upstream revision to fix the opening effect of the unity dash

 -- Sebastien Bacher <seb128@ubuntu.com>  Thu, 25 Aug 2011 18:53:09 +0200

and unity said:
> unity (4.10.0-0ubuntu1) oneiric; urgency=low

  * New upstream release:
    - unity task switcher (alt-tab, alt-down) shows empty spaces for iconified 
      windows in window detail mode (lp: #828348)
    - compiz crashed with SIGSEGV in 
      unity::DeviceLauncherIcon::OnStopDriveReady() (lp: #824093)
    - Dash performance issues with 'Active Blur' enabled (lp: #824890)
    - compiz crashed with SIGABRT in raise() when setting background 
      to full color (lp: #829049)
    - Dragging from dash to launcher still doesn't work (lp: #824833)
    - .desktops dragged on to unity launcher will not be added to 
       com.canonical.Unity.Launcher favorites unless moved in the launcher
       (lp: #830536)
    - application's menu shown when the cursor is a little left 
      to window controls (lp: #820293)
    - Ubuntu Start launcher item should always start the dash with 
      the Home screen (lp: #825034)
    - search spinner does not stop hence nothing can be launched with 
      the Return key (lp: #824836)
  * debian/control: updated nux requirement
  * debian/rules: updated shlibs

 -- Sebastien Bacher <seb128@ubuntu.com>  Thu, 25 Aug 2011 15:40:18 +0200

Our bug report didn't show up... :sad: the mystery!

---

### Post by rajeev1204 on 2011-08-26
Working decent here on my system with fglrx from the repos.But the same old problem of Firefox not being happy and freezing with the fgrlx driver.Also, i have some horizontal bands on my screen from applications recently closed .Like the program left some of its mark on the screen.

---

### Post by P-I H on 2011-08-26
Fglrx now works on my system with Ubuntu, Ubuntu 2D or Gnome login.
There are however some corruptions in the upper panel in Gnome.
Installation went OK with Synaptic, but installation with Additional Drivers or the method described in cchtml.com are not working.

---

### Post by rapiertg on 2011-08-26
> **P-I H said:**
> 
There are however some corruptions in the upper panel in Gnome.


This is fixed upstream, and should be included in next driver version:
[http://ati.cchtml.com/show_bug.cgi?id=99](http://ati.cchtml.com/show_bug.cgi?id=99)

---

### Post by budluva04 on 2011-08-26
does this look right? i thought sys-info should report radeon driver NOT vesa, everything else checks out ok aswell, 8.8s in gtkperk and glxgears shows good results....is this a bug in system-info?

---

### Post by rbrick49 on 2011-08-26
> **budluva04 said:**
> does this look right? i thought sys-info should report radeon driver NOT vesa, everything else checks out ok aswell, 8.8s in gtkperk and glxgears shows good results....is this a bug in system-info?
this is what it should be saying I think the last part as in mine identifies my card type as for the vesa part fglrx is definetly working here

---

### Post by tista on 2011-08-27
> **rapiertg said:**
> This is fixed upstream, and should be included in next driver version:
[http://ati.cchtml.com/show_bug.cgi?id=99](http://ati.cchtml.com/show_bug.cgi?id=99)

Long time no see rapiertg! ;)

and thanks for your info...

---

### Post by rapiertg on 2011-08-27
Hello, Tista.

Yeah, been a while ;).

Im still monitoring our beloved poulsbo status, just dont write much.

As of fglrx this bug was crucial for me as I love new shell, and because of that it was almost unusable. So i investigated a bit and found that bug.

Last issue that left for me is that java games ( especially based on lwjgl engine ) crashes on 32bit systems with fglrx. But this can wait as i dont play too much lately.

---

### Post by masuch on 2011-09-02
Hi,

I have got into problem on my btrfs partition with ubuntu 11.04. I have tried to install catalyst 11.8 in chroot mode because after starting I have got only magenta screen and freeze.

So I created this script to run it in chroot:

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-nouveau
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon

rm -R /usr/lib/fglrx
rm -R /usr/lib32/fglrx

sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg   # create xorg.conf
sudo apt-get install dh-modaliases fglrx-modaliases

sudo dpkg -i fglrx*.deb
sudo aticonfig --initial -f --adapter=all  # dual core create xorg.conf
sudo aticonfig --initial=check		#test if glrx section is there


but unfortunately it did not help, because it is trying to recompile wrong kernel. (Probably because the 'uname' command in chroot does not work properly). See attached results.

Is it possible installation of *.deb files for catalyst 11.8 to force for specific version of kernel (like input parameter) ?

If the problem is somewhere else so please any kind of help I really much appreciate.

Thank you very much for help to linux newbee.

---

### Post by ratcheer on 2011-09-02
masuch, instead of installing under chroot, why don't you log in to the recovery mode from grub2, then select to log in as root with network access. Then you should be able to install things in a more normal fashion.

Tim

---

### Post by sumski on 2011-09-03
> **masuch said:**
> 

Is it possible installation of *.deb files for catalyst 11.8 to force for specific version of kernel (like input parameter) ?

If the problem is somewhere else so please any kind of help I really much appreciate.

Thank you very much for help to linux newbee.

Yes:

sudo dkms build -m *fglrx* -v *version* -k *version*
sudo dkms install -m *fglrx* -v *version* -k version

example:
sudo dkms build -m fglrx -v 8.881 -k 3.0.0-9-generic
sudo dkms install -m fglrx -v 8.881 -k 3.0.0-9-generic

---

### Post by masuch on 2011-09-03
> **ratcheer said:**
> masuch, instead of installing under chroot, why don't you log in to the recovery mode from grub2, then select to log in as root with network access. Then you should be able to install things in a more normal fashion.

Tim

Hi,
Thanks, but unfortunately recovery mode is not working in about 70 percent of cases according to my experience which I have been went through within the last couple of months to playing with ubuntu 11.04 and catalyst from 11.4 to 11.8 versions.

---

### Post by masuch on 2011-09-03
> **sumski said:**
> Yes:

sudo dkms build -m *fglrx* -v *version* -k *version*
sudo dkms install -m *fglrx* -v *version* -k version

example:
sudo dkms build -m fglrx -v 8.881 -k 3.0.0-9-generic
sudo dkms install -m fglrx -v 8.881 -k 3.0.0-9-generic

Thanks a lot :-)

---

### Post by sonicb00m on 2011-09-21
Have a problem with the 11.8 drivers. They install OK but I am presented with only the desktop background when logging in.

---

