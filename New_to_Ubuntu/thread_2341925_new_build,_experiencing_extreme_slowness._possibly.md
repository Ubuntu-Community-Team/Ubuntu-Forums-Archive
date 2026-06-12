---
title: "new build, experiencing extreme slowness. possibly due to drivers?"
date: 2016-11-02
forum: New to Ubuntu
---

### Post by ember0077 on 2016-11-02
HI,

We just built our first pc and it worked when we turned it on !!!!!  (there are some problems)

Problems:
incredibly slow, mouse, typing anything - it's slow
vga not coming through on new monitor
wifi signal not detected (ethernet is working)
Videos are unwatchable as the image stutters and slows the system down considerably, sound however works fine
could this be a driver issue?

We are using Ubuntu studio Xenial Xerus 16.04.1 LTS
specs:
Intel Core i5-6500 3.2GHz Quad-Core Processor
ASrock H110M-DGS MicroATX LGA1151 Motherboard
Rosewill Line-M MicroATX Mini Tower Case
Corsair Vengeance LPX 16GB (2 x 8GB) DDR4-2133 Memory
XFX XTR 550W 80+ Gold Certified Fully-Modular ATX Power Supply
Asus VE247H 23.6" Monitor
Patriot Torch LE 240GB 2.5” Solid state drive
Hitachi Ultrastar 7K3000 2TB 3.5” 7200RPM Internal hard drive
Saphire Raedeon RX 480 4GB NITRO+4G Video card

---

### Post by oldrocker99 on 2016-11-02
Welcome to the forums!

You **might** have better results by installing the ATI **fglrx** driver. The included radeon driver (which you're using) are very good, but the fglrx drivers are faster. 

You might also not be using the ATI card at all, but the Intel graphics, although the Intel drivers are very good.

---

### Post by ember0077 on 2016-11-02
i'm completely new to linux and computing,how does one install drivers? is it as simple as downloading and running them?

---

### Post by oldfred on 2016-11-02
I do not know AMD, its drivers are in-between state. The proprietary fglrx is not supported in 16.04. But with your new hardware you probably need 16.04 for everything else. 
They used to create the proprietary drivers, but have changed to just the open source drivers. But the open source drivers do not fully support all versions, yet. New open source driver just came out and I think it only can be installed from AMD, not yet in Ubuntu repository.

 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).  

      
 [URL="http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04"]http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04
[/URL]
 AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)
[http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075) 

      
 Ubuntu 16.04 How-To Install/Uninstall AMD Radeon&#8482; Software AMDGPU-PRO Driver
[https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx) 
    [URL="http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04"]
[/URL]

---

### Post by Geoffrey_Arndt on 2016-11-02
EDIT:  Looks like oldfred has already posted what I was thinking you can try . . the last link should do it.

---

### Post by ember0077 on 2016-11-02
Great resources oldfred
We're trying to fix the most obvious problem first - which is the AMD driver and we're following your link for AMD driver:

Ubuntu 16.04 How-To Install/Uninstall AMD Radeon™ Software AMDGPU-PRO Driver
[https://support.amd.com/en-us/kb-art...O-Install.aspx]("https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx")

however the install command amdgpu-pro-driver/amdgpu-pro-install  isn't working ??? (command line is from AMD guide)

tony@EntertainmentMagic:~/Downloads$ ls
amdgpu-pro-16.40-348864  amdgpu-pro-16.40-348864.tar.xz
tony@EntertainmentMagic:~/Downloads$ amdgpu-pro-driver/amdgpu-pro-install
bash: amdgpu-pro-driver/amdgpu-pro-install: No such file or directory

---

### Post by oldfred on 2016-11-02
I know nothing about the AMD driver.
Did you extract the tarbel? So you have the install files. Or did extraction go into a sub-directly of Downloads, which then you have to cd into?

I have an older nVidia card I use on my Haswell desktop and only use the Intel driver on my Skylake system which also is a i5-6500. 
With an SSD the Skylake just worked and is very fast. 
Somehow though my typing speed has not improved so overall system is only a bit faster. :)

---

### Post by Geoffrey_Arndt on 2016-11-02
Will check script on a club members PC having amd/ati graphics . . advising if any we see any issues to pass along.

---

### Post by ember0077 on 2016-11-03
THe system can't even keep up with 2 finger typing !

THis is probly some stupid noob error but whether i'm in the directory with the command amdgpu-pro-install or the directory above - that command isn't even recognised - yet is listed  --very confused

tony@EntertainmentMagic:~/Downloads/amdgpu-pro-16.40-348864$ ls a*
amdgpu-pro_16.40-348864_amd64.deb    
 amdgpu-pro-install
amdgpu-pro_16.40-348864_i386.deb      
amdgpu-pro-lib32_16.40-348864_amd64.deb
amdgpu-pro-dkms_16.40-348864_all.deb
tony@EntertainmentMagic:~/Downloads/amdgpu-pro-16.40-348864$ amdgpu-pro-driver/amdgpu-pro-install
bash: amdgpu-pro-driver/amdgpu-pro-install: No such file or directory
tony@EntertainmentMagic:~/Downloads/amdgpu-pro-16.40-348864$ amdgpu-pro-install
amdgpu-pro-install: command not found

why is the command not found when it is listed ??

---

### Post by Geoffrey_Arndt on 2016-11-03
Did you try running the script using sudo?

---

### Post by ember0077 on 2016-11-07
yup - sudo command makes no difference

I don't get how it can list it then not find it ???

---

### Post by oldfred on 2016-11-07
Run this so we can see what you are seeing:

If at /home
cd Downloads
ls -l amd*

---

### Post by ember0077 on 2016-11-08
Hope this sheds some light, we remain firmy puzzled.
tony@EntertainmentMagic:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
tony@EntertainmentMagic:~$ cd Downloads
```
tony@EntertainmentMagic:~/Downloads$ ls -l amd*
-rw-rw-r-- 1 tony tony 109272628 Nov  2 16:54 amdgpu-pro-16.40-348864.tar.xz


amdgpu-pro-16.40-348864:
total 106840
-rw-r--r-- 1 tony tony     1308 Oct 25 06:02 amdgpu-pro_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony     1310 Oct 25 04:38 amdgpu-pro_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony  2647078 Oct 25 04:49 amdgpu-pro-dkms_16.40-348864_all.deb
-rwxr-xr-x 1 tony tony     3232 Oct 25 02:00 amdgpu-pro-install
-rw-r--r-- 1 tony tony     1282 Oct 25 06:03 amdgpu-pro-lib32_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony   148346 Oct 25 05:58 clinfo-amdgpu-pro_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony   159872 Oct 25 04:30 clinfo-amdgpu-pro_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony    62810 Oct 25 06:02 gst-omx-amdgpu-pro_1.0.0.1-348864_amd64.deb
-rw-r--r-- 1 tony tony    63384 Oct 25 04:38 gst-omx-amdgpu-pro_1.0.0.1-348864_i386.deb
-rw-r--r-- 1 tony tony    28944 Oct 25 04:51 libdrm2-amdgpu-pro_2.4.66-348864_amd64.deb
-rw-r--r-- 1 tony tony    31856 Oct 25 02:27 libdrm2-amdgpu-pro_2.4.66-348864_i386.deb
-rw-r--r-- 1 tony tony    20002 Oct 25 04:51 libdrm-amdgpu-pro-amdgpu1_2.4.66-348864_amd64.deb
-rw-r--r-- 1 tony tony    24566 Oct 25 02:27 libdrm-amdgpu-pro-amdgpu1_2.4.66-348864_i386.deb
-rw-r--r-- 1 tony tony   139804 Oct 25 04:51 libdrm-amdgpu-pro-dev_2.4.66-348864_amd64.deb
-rw-r--r-- 1 tony tony   149172 Oct 25 02:27 libdrm-amdgpu-pro-dev_2.4.66-348864_i386.deb
-rw-r--r-- 1 tony tony    21396 Oct 25 04:51 libdrm-amdgpu-pro-radeon1_2.4.66-348864_amd64.deb
-rw-r--r-- 1 tony tony    23036 Oct 25 02:27 libdrm-amdgpu-pro-radeon1_2.4.66-348864_i386.deb
-rw-r--r-- 1 tony tony    57338 Oct 25 04:51 libdrm-amdgpu-pro-utils_2.4.66-348864_amd64.deb
-rw-r--r-- 1 tony tony    58324 Oct 25 02:27 libdrm-amdgpu-pro-utils_2.4.66-348864_i386.deb
-rw-r--r-- 1 tony tony     4932 Oct 25 05:34 libegl1-amdgpu-pro_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony     4344 Oct 25 03:56 libegl1-amdgpu-pro_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony    73462 Oct 25 04:51 libgbm1-amdgpu-pro_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony    80970 Oct 25 02:28 libgbm1-amdgpu-pro_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony     3068 Oct 25 04:51 libgbm1-amdgpu-pro-base_16.40-348864_all.deb
-rw-r--r-- 1 tony tony     5620 Oct 25 04:51 libgbm1-amdgpu-pro-dev_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony     5598 Oct 25 02:28 libgbm1-amdgpu-pro-dev_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony    15114 Oct 25 05:59 libgl1-amdgpu-pro-appprofiles_16.40-348864_all.deb
-rw-r--r-- 1 tony tony  8423748 Oct 25 05:34 libgl1-amdgpu-pro-dri_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony  8072802 Oct 25 03:56 libgl1-amdgpu-pro-dri_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony    68166 Oct 25 05:34 libgl1-amdgpu-pro-ext_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony    57918 Oct 25 03:56 libgl1-amdgpu-pro-ext_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony   124716 Oct 25 05:34 libgl1-amdgpu-pro-glx_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony   115954 Oct 25 03:56 libgl1-amdgpu-pro-glx_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony     5710 Oct 25 05:17 libglamor-amdgpu-pro-dev_1.18.3-348864_amd64.deb
-rw-r--r-- 1 tony tony     5668 Oct 25 03:16 libglamor-amdgpu-pro-dev_1.18.3-348864_i386.deb
-rw-r--r-- 1 tony tony    15022 Oct 25 05:34 libgles2-amdgpu-pro_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony    10180 Oct 25 03:56 libgles2-amdgpu-pro_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony     8992 Oct 25 05:58 libopencl1-amdgpu-pro_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony     9772 Oct 25 04:30 libopencl1-amdgpu-pro_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony 11003192 Oct 25 05:21 libvdpau-amdgpu-pro_11.2.2-348864_amd64.deb
-rw-r--r-- 1 tony tony 12255946 Oct 25 03:26 libvdpau-amdgpu-pro_11.2.2-348864_i386.deb
-rw-r--r-- 1 tony tony  5492606 Oct 25 05:21 mesa-amdgpu-pro-omx-drivers_11.2.2-348864_amd64.deb
-rw-r--r-- 1 tony tony  6121968 Oct 25 03:26 mesa-amdgpu-pro-omx-drivers_11.2.2-348864_i386.deb
-rw-r--r-- 1 tony tony 23932992 Oct 25 05:58 opencl-amdgpu-pro-icd_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony 24400610 Oct 25 04:31 opencl-amdgpu-pro-icd_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony    41534 Oct 25 06:04 Packages
-rw-r--r-- 1 tony tony      814 Oct 25 06:04 Release
-rw-r--r-- 1 tony tony  2489370 Oct 25 06:01 vulkan-amdgpu-pro_16.40-348864_amd64.deb
-rw-r--r-- 1 tony tony  2439270 Oct 25 04:34 vulkan-amdgpu-pro_16.40-348864_i386.deb
-rw-r--r-- 1 tony tony    51764 Oct 25 06:01 xserver-xorg-video-amdgpu-pro_1.1.99-348864_amd64.deb
-rw-r--r-- 1 tony tony    56244 Oct 25 04:35 xserver-xorg-video-amdgpu-pro_1.1.99-348864_i386.deb
-rw-r--r-- 1 tony tony    84028 Oct 25 05:17 xserver-xorg-video-glamoregl-amdgpu-pro_1.18.3-348864_amd64.deb
-rw-r--r-- 1 tony tony    85622 Oct 25 03:16 xserver-xorg-video-glamoregl-amdgpu-pro_1.18.3-348864_i386.deb
-rw-r--r-- 1 tony tony    34158 Oct 25 05:17 xserver-xorg-video-modesetting-amdgpu-pro_1.18.3-348864_amd64.deb
-rw-r--r-- 1 tony tony    37970 Oct 25 03:16 xserver-xorg-video-modesetting-amdgpu-pro_1.18.3-348864_i386.deb
```

---

### Post by oldfred on 2016-11-08
I think the way that shows it is you only have the one tar file and then it shows everything in it.
You have to extract all those files into a folder, then you can run the install file.

If you right click on the  .tar.gz file does it not offer extract as one option?
The you should have the install file & all the .debs to use.
You probably have to choose whether 32 bit or 64 bit as it looks like it has sets of files for both.

---

