---
title: "Few errors setting up new ubuntu Dual Boot computer"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by JoppaRecordings on 2013-05-24
So i've installed Ubuntu on a second hard drive on my computer. It dual boots fine. Other than a few errors Ubuntu is working great. 

When I install anything outside of the Ubuntu software store I get errors on installation. I have tried installing Blender and Lightworks, both came up with errors which I copied down.

The other larger issue is I can't seem to get sound to work at all. I tried installing a work around to get sound when I plug in my TV via HDMI as a second monitor. That installation failed. The monitor works but the sound doesn't. I don't get sound out of the headphone jack on the computer or the HDMI TV. 

Any suggestions?

---

### Post by 2F4U on 2013-05-24
What exactly do you mean by "outside of the Ubuntu software store"? Can you post the error messages or, ideally, the complete output of what you are doing?

---

### Post by JoppaRecordings on 2013-06-09
Sorry for the late reply, 

An example is lightworks i download a .deb file. Which then opens Ubuntu software center to install. Unlike things that I click inside the software center, which install themselves without issue, this downloaded .deb file along with when I downloaded blender caused an error upon installation. Here is the error message I received.



installArchives() failed: Selecting previously unselected package freeglut3:amd64.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40WTkymkY8%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 195368 files and directories currently installed.)
Unpacking freeglut3:amd64 (from .../freeglut3_2.6.0-4ubuntu1_amd64.deb) ...
Selecting previously unselected package libportaudiocpp0:amd64.
Unpacking libportaudiocpp0:amd64 (from .../libportaudiocpp0_19+svn20111121-1build1_amd64.deb) ...
Selecting previously unselected package libtiff4:amd64.
Unpacking libtiff4:amd64 (from .../libtiff4_3.9.7-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libcg:amd64.
Unpacking libcg:amd64 (from .../libcg_3.1.0013-1_amd64.deb) ...
Selecting previously unselected package libcggl:amd64.
Unpacking libcggl:amd64 (from .../libcggl_3.1.0013-1_amd64.deb) ...
Selecting previously unselected package libgsf-1-common.
Unpacking libgsf-1-common (from .../libgsf-1-common_1.14.26-1ubuntu1_all.deb) ...
Selecting previously unselected package libgsf-1-114.
Unpacking libgsf-1-114 (from .../libgsf-1-114_1.14.26-1ubuntu1_amd64.deb) ...
Selecting previously unselected package nvidia-cg-dev:amd64.
Unpacking nvidia-cg-dev:amd64 (from .../nvidia-cg-dev_3.1.0013-1_amd64.deb) ...
Selecting previously unselected package nvidia-cg-toolkit.
Unpacking nvidia-cg-toolkit (from .../nvidia-cg-toolkit_3.1.0013-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up alsa-hda-dkms (0.201210261053~natty1) ...
Removing old alsa-hda-0.201210261053~natty1 DKMS files...

------------------------------
Deleting module version: 0.201210261053~natty1
completely from the DKMS tree.
------------------------------
Done.
Loading new alsa-hda-0.201210261053~natty1 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-21-generic
Building for architecture x86_64
Building initial module for 3.8.0-21-generic
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.8.0-21-generic (x86_64)
Consult /var/lib/dkms/alsa-hda/0.201210261053~natty1/build/make.log for more information.
dpkg: error processing alsa-hda-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up oem-audio-hda-daily-dkms (0.201305171830~precise1) ...
Removing old oem-audio-hda-daily-0.201305171830~precise1 DKMS files...

------------------------------
Deleting module version: 0.201305171830~precise1
completely from the DKMS tree.
------------------------------
Done.
Loading new oem-audio-hda-daily-0.201305171830~precise1 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-21-generic
Building for architecture x86_64
Building initial module for 3.8.0-21-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
dpkg: error processing oem-audio-hda-daily-dkms (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up freeglut3:amd64 (2.6.0-4ubuntu1) ...
Setting up libportaudiocpp0:amd64 (19+svn20111121-1build1) ...
Setting up libtiff4:amd64 (3.9.7-0ubuntu1) ...
Setting up libcg:amd64 (3.1.0013-1) ...
Setting up libcggl:amd64 (3.1.0013-1) ...
Setting up libgsf-1-common (1.14.26-1ubuntu1) ...
Setting up libgsf-1-114 (1.14.26-1ubuntu1) ...
Setting up nvidia-cg-dev:amd64 (3.1.0013-1) ...
Setting up nvidia-cg-toolkit (3.1.0013-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 alsa-hda-dkms
 oem-audio-hda-daily-dkms
Error in function: 
Setting up oem-audio-hda-daily-dkms (0.201305171830~precise1) ...
Removing old oem-audio-hda-daily-0.201305171830~precise1 DKMS files...

------------------------------
Deleting module version: 0.201305171830~precise1
completely from the DKMS tree.
------------------------------

Thanks for your help, I'm very excited to learn the ins and outs of Ubuntu.

---

### Post by JoppaRecordings on 2013-06-09
Here is another example of the installation issues I am having.
In ubuntu software center I tried to install Inkscape Vector Graphics Editor.
Installation went good til the very end I get a pop up "Package operation failed"
```

installArchives() failed: Selecting previously unselected package imagemagick-common. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 195422 files and directories currently installed.) 
Unpacking imagemagick-common (from .../imagemagick-common_8%3a6.7.7.10-5ubuntu2_all.deb) ... 
Selecting previously unselected package libgfortran3:amd64. 
Unpacking libgfortran3:amd64 (from .../libgfortran3_4.7.3-1ubuntu1_amd64.deb) ... 
Selecting previously unselected package libgtkmm-2.4-1c2a:amd64. 
Unpacking libgtkmm-2.4-1c2a:amd64 (from .../libgtkmm-2.4-1c2a_1%3a2.24.2-1ubuntu2_amd64.deb) ... 
Selecting previously unselected package liblqr-1-0:amd64. 
Unpacking liblqr-1-0:amd64 (from .../liblqr-1-0_0.4.1-2_amd64.deb) ... 
Selecting previously unselected package libmagickcore5:amd64. 
Unpacking libmagickcore5:amd64 (from .../libmagickcore5_8%3a6.7.7.10-5ubuntu2_amd64.deb) ... 
Selecting previously unselected package libmagickwand5:amd64. 
Unpacking libmagickwand5:amd64 (from .../libmagickwand5_8%3a6.7.7.10-5ubuntu2_amd64.deb) ... 
Selecting previously unselected package libmagick++5:amd64. 
Unpacking libmagick++5:amd64 (from .../libmagick++5_8%3a6.7.7.10-5ubuntu2_amd64.deb) ... 
Selecting previously unselected package libmagickcore5-extra:amd64. 
Unpacking libmagickcore5-extra:amd64 (from .../libmagickcore5-extra_8%3a6.7.7.10-5ubuntu2_amd64.deb) ... 
Selecting previously unselected package imagemagick. 
Unpacking imagemagick (from .../imagemagick_8%3a6.7.7.10-5ubuntu2_amd64.deb) ... 
Selecting previously unselected package libgsl0ldbl. 
Unpacking libgsl0ldbl (from .../libgsl0ldbl_1.15+dfsg.2-2_amd64.deb) ... 
Selecting previously unselected package libgtkspell0. 
Unpacking libgtkspell0 (from .../libgtkspell0_2.0.16-1ubuntu6_amd64.deb) ... 
Selecting previously unselected package inkscape. 
Unpacking inkscape (from .../inkscape_0.48.4-0.1ubuntu2_amd64.deb) ... 
Selecting previously unselected package libblas3. 
Unpacking libblas3 (from .../libblas3_1.2.20110419-5_amd64.deb) ... 
Selecting previously unselected package libgnomevfs2-extra:amd64. 
Unpacking libgnomevfs2-extra:amd64 (from .../libgnomevfs2-extra_1%3a2.24.4-1ubuntu5_amd64.deb) ... 
Selecting previously unselected package liblapack3. 
Unpacking liblapack3 (from .../liblapack3_3.4.2-1~exp3_amd64.deb) ... 
Selecting previously unselected package libnetpbm10. 
Unpacking libnetpbm10 (from .../libnetpbm10_2%3a10.0-15ubuntu2_amd64.deb) ... 
Selecting previously unselected package libwmf-bin. 
Unpacking libwmf-bin (from .../libwmf-bin_0.2.8.4-10.3ubuntu1_amd64.deb) ... 
Selecting previously unselected package netpbm. 
Unpacking netpbm (from .../netpbm_2%3a10.0-15ubuntu2_amd64.deb) ... 
Selecting previously unselected package perlmagick. 
Unpacking perlmagick (from .../perlmagick_8%3a6.7.7.10-5ubuntu2_amd64.deb) ... 
Selecting previously unselected package python-numpy. 
Unpacking python-numpy (from .../python-numpy_1%3a1.7.1-1ubuntu1_amd64.deb) ... 
Selecting previously unselected package python-uniconvertor. 
Unpacking python-uniconvertor (from .../python-uniconvertor_1.1.4-1ubuntu2_amd64.deb) ... 
Processing triggers for mime-support ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for man-db ... 
Setting up alsa-hda-dkms (0.201210261053~natty1) ... 
Removing old alsa-hda-0.201210261053~natty1 DKMS files... 
 
------------------------------ 
Deleting module version: 0.201210261053~natty1 
completely from the DKMS tree. 
------------------------------ 
Done. 
Loading new alsa-hda-0.201210261053~natty1 DKMS files... 
First Installation: checking all kernels... 
Building only for 3.8.0-21-generic 
Building for architecture x86_64 
Building initial module for 3.8.0-21-generic 
Traceback (most recent call last): 
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module> 
    import apport 
ImportError: No module named apport 
Error! Bad return status for module build on kernel: 3.8.0-21-generic (x86_64) 
Consult /var/lib/dkms/alsa-hda/0.201210261053~natty1/build/make.log for more information. 
dpkg: error processing alsa-hda-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 10 
No apport report written because MaxReports is reached already
Setting up oem-audio-hda-daily-dkms (0.201305171830~precise1) ... 
Removing old oem-audio-hda-daily-0.201305171830~precise1 DKMS files... 
 
------------------------------ 
Deleting module version: 0.201305171830~precise1 
completely from the DKMS tree. 
------------------------------ 
Done. 
Loading new oem-audio-hda-daily-0.201305171830~precise1 DKMS files... 
First Installation: checking all kernels... 
Building only for 3.8.0-21-generic 
Building for architecture x86_64 
Building initial module for 3.8.0-21-generic 
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which 
does not match this kernel/arch.  This indicates that it should not be built. 
dpkg: error processing oem-audio-hda-daily-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 9 
No apport report written because MaxReports is reached already
Setting up imagemagick-common (8:6.7.7.10-5ubuntu2) ... 
Setting up libgfortran3:amd64 (4.7.3-1ubuntu1) ... 
Setting up libgtkmm-2.4-1c2a:amd64 (1:2.24.2-1ubuntu2) ... 
Setting up liblqr-1-0:amd64 (0.4.1-2) ... 
Setting up libmagickcore5:amd64 (8:6.7.7.10-5ubuntu2) ... 
Setting up libmagickwand5:amd64 (8:6.7.7.10-5ubuntu2) ... 
Setting up libmagick++5:amd64 (8:6.7.7.10-5ubuntu2) ... 
Setting up libmagickcore5-extra:amd64 (8:6.7.7.10-5ubuntu2) ... 
Setting up imagemagick (8:6.7.7.10-5ubuntu2) ... 
update-alternatives: using /usr/bin/compare.im6 to provide /usr/bin/compare (compare) in auto mode 
update-alternatives: using /usr/bin/animate.im6 to provide /usr/bin/animate (animate) in auto mode 
update-alternatives: using /usr/bin/convert.im6 to provide /usr/bin/convert (convert) in auto mode 
update-alternatives: using /usr/bin/composite.im6 to provide /usr/bin/composite (composite) in auto mode 
update-alternatives: using /usr/bin/conjure.im6 to provide /usr/bin/conjure (conjure) in auto mode 
update-alternatives: using /usr/bin/import.im6 to provide /usr/bin/import (import) in auto mode 
update-alternatives: using /usr/bin/identify.im6 to provide /usr/bin/identify (identify) in auto mode 
update-alternatives: using /usr/bin/stream.im6 to provide /usr/bin/stream (stream) in auto mode 
update-alternatives: using /usr/bin/display.im6 to provide /usr/bin/display (display) in auto mode 
update-alternatives: using /usr/bin/montage.im6 to provide /usr/bin/montage (montage) in auto mode 
update-alternatives: using /usr/bin/mogrify.im6 to provide /usr/bin/mogrify (mogrify) in auto mode 
Setting up libgsl0ldbl (1.15+dfsg.2-2) ... 
Setting up libgtkspell0 (2.0.16-1ubuntu6) ... 
Setting up inkscape (0.48.4-0.1ubuntu2) ... 
Setting up libblas3 (1.2.20110419-5) ... 
update-alternatives: using /usr/lib/libblas/libblas.so.3 to provide /usr/lib/libblas.so.3 (libblas.so.3) in auto mode 
Setting up libgnomevfs2-extra:amd64 (1:2.24.4-1ubuntu5) ... 
Setting up liblapack3 (3.4.2-1~exp3) ... 
update-alternatives: using /usr/lib/lapack/liblapack.so.3 to provide /usr/lib/liblapack.so.3 (liblapack.so.3) in auto mode 
Setting up libnetpbm10 (2:10.0-15ubuntu2) ... 
Setting up libwmf-bin (0.2.8.4-10.3ubuntu1) ... 
Setting up netpbm (2:10.0-15ubuntu2) ... 
Setting up perlmagick (8:6.7.7.10-5ubuntu2) ... 
Setting up python-numpy (1:1.7.1-1ubuntu1) ... 
Setting up python-uniconvertor (1.1.4-1ubuntu2) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 alsa-hda-dkms 
 oem-audio-hda-daily-dkms 
Error in function:  
Setting up oem-audio-hda-daily-dkms (0.201305171830~precise1) ... 
Removing old oem-audio-hda-daily-0.201305171830~precise1 DKMS files... 
 
------------------------------ 
Deleting module version: 0.201305171830~precise1 
completely from the DKMS tree. 
------------------------------ 
Done. 
Loading new oem-audio-hda-daily-0.201305171830~precise1 DKMS files... 
First Installation: checking all kernels... 
Building only for 3.8.0-21-generic 
Building for architecture x86_64 
Building initial module for 3.8.0-21-generic 
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which 
does not match this kernel/arch.  This indicates that it should not be built. 
dpkg: error processing oem-audio-hda-daily-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 9 
Setting up alsa-hda-dkms (0.201210261053~natty1) ... 
Removing old alsa-hda-0.201210261053~natty1 DKMS files... 
 
------------------------------ 
Deleting module version: 0.201210261053~natty1 
completely from the DKMS tree. 
------------------------------ 
Done. 
Loading new alsa-hda-0.201210261053~natty1 DKMS files... 
First Installation: checking all kernels... 
Building only for 3.8.0-21-generic 
Building for architecture x86_64 
Building initial module for 3.8.0-21-generic 
Traceback (most recent call last): 
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module> 
    import apport 
ImportError: No module named apport 
Error! Bad return status for module build on kernel: 3.8.0-21-generic (x86_64) 
Consult /var/lib/dkms/alsa-hda/0.201210261053~natty1/build/make.log for more information. 
dpkg: error processing alsa-hda-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 10
```


Then I get another popup saying "Sorry, Ubuntu 13.04 has experienced an internal error."
When I click details i see "problem type: crash"


The Program Inkscape still comes up on my toolbar and is fully usable as far as I can tell. This same thing happened when I installed Blender. But Lightworks didn't work at all.

---

### Post by mastablasta on 2013-06-09
which version of Ubutnu are you using (32bit or 64 bit?). Which version of programms you downloaded (32 bit or 64 bit)?

as for the sound what GPU do you have and what sound chip do you have?

what does alsamixer (run in terminal) say? are all powerbars showing?

---

### Post by JoppaRecordings on 2013-06-09
which version of Ubutnu are you using (32bit or 64 bit?). Which version of programms you downloaded (32 bit or 64 bit)?
I have installed the 64 bit version of ubuntu. In the example of Inkscape which error out, there is only a 32 bit version available, but most with 64bit linux installs have had success running the program fully.

as for the sound what GPU do you have and what sound chip do you have?
I have a 1gb Radeon Sapphire HD 4670 GPU
Sound is just using my build in sound from the motherboard. Integrated Realtec ALC888S Audio
The front headphone jack works, I have gotten it to work going into the audio settings of "System Settings" but I have an HDTV I use as a 2nd monitor which I like to send my sound through on windows 7. It is connected via HDMI. I tried installing a fix for it, but my inexperience in linux i think botched it.

what does alsamixer (run in terminal) say? are all powerbars showing? 		
No the first 4 to the left are running.  Underneath are labeled "Master" "Headphone" "PCM" "Front"  
Greyed our are "Front Mi" "Front Mi" "Surround" "center"
When I unplug my headphones 
"Surround" and "Center" then become activated and full bars.

If I goto F6: Select Sound Card, and Choose HDA ATI HDMI then I am able to select HDMI but it doesn't appear to be working. 
"Chip: ATI R6XX HDMI" 
 "Item: S/PDIF [off]" 

Is there a way to flip this switch to enable sound?

---

