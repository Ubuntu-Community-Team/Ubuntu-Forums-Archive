---
title: "alpha2 still no fglrx"
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-07-09
the heading says it all something to do with jockey I filed a bug

---

### Post by Harry33 on 2011-07-09
> **rbrick49 said:**
> the heading says it all something to do with jockey I filed a bug

If it is a jockey based issue (which I doubt), you can try to install fglrx with Synaptic.

---

### Post by P-I H on 2011-07-09
I haven't been able to install fglrx for some time. Tried with Additional Drivers, synaptic and also with the methode described in cchtml.com without success.
Tried today with synaptic and got this result

```
Selecting previously deselected package patch.
(Reading database ... 123573 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-2_amd64.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-5ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.16-1_amd64.deb) ...
Selecting previously deselected package libc6-i386.
Unpacking libc6-i386 (from .../libc6-i386_2.13-9ubuntu1_amd64.deb) ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.1-2ubuntu2_amd64.deb) ...
Selecting previously deselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.861-0ubuntu2_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.861-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-2) ...
Setting up dkms (2.1.1.2-5ubuntu1) ...
Setting up fakeroot (1.16-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libc6-i386 (2.13-9ubuntu1) ...
Setting up lib32gcc1 (1:4.6.1-2ubuntu2) ...
Setting up fglrx (2:8.861-0ubuntu2) ...
update-alternatives: renaming x86_64-linux-gnu_xorg_extra_modules slave link from /usr/lib/x86_64-linux-gnu/xorg/extra-modules to /usr/lib/xorg/extra-modules.
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/x86_64-linux-gnu_fglrx_dri: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up fglrx (2:8.861-0ubuntu2) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/x86_64-linux-gnu_fglrx_dri: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
```
Thre are some bug reports related to this, 807078, 807204, 807346,  807347.
However, on the same hardware, fglrx works fine in an Oneiric installation upgraded from Natty.

---

### Post by rbrick49 on 2011-07-09
> **Harry33 said:**
> If it is a jockey based issue (which I doubt), you can try to install fglrx with Synaptic.
harry33 i am only saying what my eror report says it says something to do with jockey and dependencies
regards Ron

---

### Post by ranch hand on 2011-07-09
I am running 3.0.0 with my Debian G2 install and fglrx is working fine.  There is some OSS replacement for fglrx-glx that seems to work well so all I needed to do was install the (Debian) package "fglrx-driver", I don't remember what the Ubuntu package is so I do not know if that is an option.

---

### Post by ratcheer on 2011-07-10
I tried to install fglrx with jockey and got the failure as well. So, I tried to use Software Center. It says the driver is installed. My system doesn't seem to know about it, though.

Tim

---

### Post by rbrick49 on 2011-07-10
> **ranch hand said:**
> I am running 3.0.0 with my Debian G2 install and fglrx is working fine.  There is some OSS replacement for fglrx-glx that seems to work well so all I needed to do was install the (Debian) package "fglrx-driver", I don't remember what the Ubuntu package is so I do not know if that is an option.
thanks for the tip ranch it didnt work though it just refuses to install a lot of updates mesa and the likes but still no when I uninstall from recovery I get a black screen on reboot maybe alberto will make a fix
thanks mate regards Ron

---

### Post by rbrick49 on 2011-07-10
I had to download codecs to watch a web cast,gstreamer codecs fglrx installed after I did that

---

### Post by P-I H on 2011-07-11
fglrx also installed OK on my system today.
I used Synaptic to install gstreamer0.10-ffmpeg, after rbrick49's advice about codec, and then fglrx.
However I have changed motherboard and there have been some updates since I tried last time.
Anyhow, good to have fglrx back in use.

---

### Post by rbrick49 on 2011-07-11
> **P-I H said:**
> fglrx also installed OK on my system today.
I used Synaptic to install gstreamer0.10-ffmpeg, after rbrick49's advice about codec, and then fglrx.
However I have changed motherboard and there have been some updates since I tried last time.
Anyhow, good to have fglrx back in use. glad you got it working mate 
cheers ronnie
by the way I did same on kubuntu 11.10 it is beautiful kubuntu has improved greatly

---

### Post by ikt on 2011-07-13
> **rbrick49 said:**
> the heading says it all something to do with jockey I filed a bug

which bug did you file?

I have the same issue.

> Setting up fglrx (2:8.861-0ubuntu2) ...
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
A package failed to install.  Trying to recover:
Setting up fglrx (2:8.861-0ubuntu2) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/x86_64-linux-gnu_fglrx_dri: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle



---

### Post by rbrick49 on 2011-07-14
I fixed the problem by accident I loaded gstreamer plugins and fglrx auto installed but it has something to do with a file not loading someone sent me an email about it but cant find the email to tell you I will go and find it for you

---

### Post by rbrick49 on 2011-07-14
> **rbrick49 said:**
> I fixed the problem by accident I loaded gstreamer plugins and fglrx auto installed but it has something to do with a file not loading someone sent me an email about it but cant find the email to tell you I will go and find it for you
heres the fix
sudo mkdir /usr/lib/dri"

---

### Post by somesayinice on 2011-07-17
> **rbrick49 said:**
> heres the fix
sudo mkdir /usr/lib/dri"

Thank you soo soo much.  :D

---

### Post by justborn on 2011-07-20
```


installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:

	LANGUAGE = (unset),

	LC_ALL = (unset),

	LANG = "en_IN.ISO8859-1"

    are supported and installed on your system.

perl: warning: Falling back to the standard locale ("C").

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...

perl: warning: Setting locale failed.

perl: warning: Please check that your locale settings:

	LANGUAGE = (unset),

	LC_ALL = (unset),

	LANG = "en_IN.ISO8859-1"

    are supported and installed on your system.

perl: warning: Falling back to the standard locale ("C").

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...

perl: warning: Setting locale failed.

perl: warning: Please check that your locale settings:

	LANGUAGE = (unset),

	LC_ALL = (unset),

	LANG = "en_IN.ISO8859-1"

    are supported and installed on your system.

perl: warning: Falling back to the standard locale ("C").

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...

(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 151479 files and directories currently installed.)

Preparing to replace update-manager-core 1:0.152.4 (using .../update-manager-core_1%%3a0.152.5_i386.deb) ...

Unpacking replacement update-manager-core ...

Preparing to replace update-manager 1:0.152.4 (using .../update-manager_1%%3a0.152.5_all.deb) ...

Unpacking replacement update-manager ...

Preparing to replace cpp 4:4.6.1-2ubuntu2 (using .../cpp_4%%3a4.6.1-2ubuntu3_i386.deb) ...

Unpacking replacement cpp ...

Preparing to replace gcc 4:4.6.1-2ubuntu2 (using .../gcc_4%%3a4.6.1-2ubuntu3_i386.deb) ...

Removing old gcc doc directory.

Unpacking replacement gcc ...

Preparing to replace gnome-orca 3.1.3-0ubuntu1 (using .../gnome-orca_3.1.3-0ubuntu2_all.deb) ...

Unpacking replacement gnome-orca ...

Selecting previously deselected package xdiagnose.

Unpacking xdiagnose (from .../archives/xdiagnose_0.8_all.deb) ...

Preparing to replace x11-common 1:7.6+7ubuntu3 (using .../x11-common_1%%3a7.6+7ubuntu4_all.deb) ...

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

Unpacking replacement x11-common ...

Preparing to replace xserver-xorg-video-all 1:7.6+7ubuntu3 (using .../xserver-xorg-video-all_1%%3a7.6+7ubuntu4_i386.deb) ...

Unpacking replacement xserver-xorg-video-all ...

Preparing to replace xserver-xorg-input-all 1:7.6+7ubuntu3 (using .../xserver-xorg-input-all_1%%3a7.6+7ubuntu4_i386.deb) ...

Unpacking replacement xserver-xorg-input-all ...

Preparing to replace xserver-xorg 1:7.6+7ubuntu3 (using .../xserver-xorg_1%%3a7.6+7ubuntu4_i386.deb) ...

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

Unpacking replacement xserver-xorg ...

Preparing to replace xorg 1:7.6+7ubuntu3 (using .../xorg_1%%3a7.6+7ubuntu4_i386.deb) ...

Unpacking replacement xorg ...

Processing triggers for man-db ...

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

Processing triggers for hicolor-icon-theme ...

Processing triggers for libglib2.0-0 ...

Processing triggers for gconf2 ...

Processing triggers for desktop-file-utils ...

Processing triggers for gnome-menus ...

Processing triggers for bamfdaemon ...

Rebuilding /usr/share/applications/bamf.index...

Processing triggers for ureadahead ...

ureadahead will be reprofiled on next reboot

Setting up fglrx (2:8.861-0ubuntu2) ...

update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.

update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/i386-linux-gnu_fglrx_dri: No such file or directory

dpkg: error processing fglrx (--configure):

 subprocess installed post-installation script returned error exit status 2

No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of fglrx-amdcccle:

 fglrx-amdcccle depends on fglrx; however:

  Package fglrx is not configured yet.

dpkg: error processing fglrx-amdcccle (--configure):

 dependency problems - leaving unconfigured

No apport report written because MaxReports is reached already
Setting up update-manager-core (1:0.152.5) ...

Setting up update-manager (1:0.152.5) ...

Setting up cpp (4:4.6.1-2ubuntu3) ...

Setting up gcc (4:4.6.1-2ubuntu3) ...

Setting up gnome-orca (3.1.3-0ubuntu2) ...

Setting up xdiagnose (0.8) ...

Setting up x11-common (1:7.6+7ubuntu4) ...

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

Setting up xserver-xorg-video-all (1:7.6+7ubuntu4) ...

Setting up xserver-xorg-input-all (1:7.6+7ubuntu4) ...

Setting up xserver-xorg (1:7.6+7ubuntu4) ...

locale: Cannot set LC_CTYPE to default locale: No such file or directory

locale: Cannot set LC_MESSAGES to default locale: No such file or directory

locale: Cannot set LC_ALL to default locale: No such file or directory

Setting up xorg (1:7.6+7ubuntu4) ...

Errors were encountered while processing:

 fglrx

 fglrx-amdcccle

Error in function: 

Setting up fglrx (2:8.861-0ubuntu2) ...

update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.

update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/i386-linux-gnu_fglrx_dri: No such file or directory

dpkg: error processing fglrx (--configure):

 subprocess installed post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of fglrx-amdcccle:

 fglrx-amdcccle depends on fglrx; however:

  Package fglrx is not configured yet.

dpkg: error processing fglrx-amdcccle (--configure):

 dependency problems - leaving unconfigured


```

i've trouble installing it on alpha 2.Can someone temme what's wrong with it?

---

### Post by justborn on 2011-07-20
> **somesayinice said:**
> Thank you soo soo much.  :D

hey,did it work?

---

