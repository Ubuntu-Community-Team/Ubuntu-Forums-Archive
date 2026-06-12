---
title: "HOWTO: Splashy (replacement for usplash, as good (or better) than bootsplash!)"
date: 2006-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxnewbie946 on 2006-07-15
[B]Splashy ([http://splashy.alioth.debian.org/wiki/doku.php]("http://splashy.alioth.debian.org/wiki/doku.php")) is a next generation boot splashing system for Linux systems. Unlike other splashig systems, it needs no patches to the kernel and it’s installed like a normal package. Make your boot process eye-candy with Splashy!
[/B]
**Some of Splashy’s most noticable features include:**


[LIST]
[*]Require zero kernel patches/full functionality in user-space

[*]Boot/halt/reboot/runlevel-switch support

[*]Progressbar support (with optional border)

[*]Verbose mode (with F2/ESC keys)

[*]Configuration file in XML

[*]Cope with any video-mode resolution/size

[*]Cope with 8, 16, and 24 bit framebuffers

[*]Alpha channel (transparency) support

[*]Video mode detection

[*]Initramfs support

[*]TrueType2 fonts support

[*]Lots of image/animation file formats supported: jpg, png, gif, mpg, swf

[*]Low dependencies and code in C to best perform

[*]Full LSB support

[*]Multiple themes support

[*]Really easy to create new themes

[*]X detection on exit

[*]Smooth progressbar movement

[*]Animations support

[*]Fade in/out effects

[*]Totally configurable
[/LIST]

Splashy is easier to install than bootsplash because **[COLOR="Red"]you don't have to patch the kernel[/COLOR]**! It gives the same resolution as bootsplash and is themeable! Try it!


[B]
To Install Splashy:[/B]

[LIST=1]
[*][COLOR="Blue"]Edit /etc/apt/sources.list and add[/COLOR]

```

## Debian Sarge (stable) users: 
deb [http://splashy.alioth.debian.org/debian](http://splashy.alioth.debian.org/debian) stable main

## Debian Etch/Sid (testing/unstable) users: 
deb [http://splashy.alioth.debian.org/debian](http://splashy.alioth.debian.org/debian) unstable main
```

[*][COLOR="Blue"]Now run:[/COLOR]

```
apt-get update
apt-get install splashy splashy-themes
```

[*][COLOR="Blue"]When that is done, do this:[/COLOR]
```

sudo kate /boot/grub/menu.lst
```
[COLOR="Blue"]
and at the line in bold below (keep in mind your kernel AND hda# may be different so make sure you use the right one or your system will be screwed)[/COLOR]

> title Ubuntu, Kernel 2.6.17
root (hd0,9)
**kernel /boot/<YOUR KERNEL HERE> root=/dev/hda<YOUR HD # HERE> ro quiet splash**
initrd /boot/initrd.img-2.6.17
savedefault
boot

[COLOR="Blue"]replace with this:[/COLOR]
> 
kernel /boot/<YOUR KERNEL HERE> ro root=/dev/hda<YOUR HD # HERE> vga=792

[COLOR="Blue"]Now, whenever the system is updated, Splashy will be updated along with it.[/COLOR]
[/LIST]


[B]
Installing and setting themes through splashy_config[/B]

[LIST=1]
[*][COLOR="Blue"]Once you have downloaded the theme tarball, run the following command:[/COLOR]

```
splashy_config -i <path_to_tarball_w/o_brackets>
```
[COLOR="Red"]You must run that command as root super-user.[/COLOR]


[*][COLOR="Blue"]To set the theme, do the following:[/COLOR]
```
splashy_config -s <NAME OF THEME W/O BRACKETS>
```
[COLOR="Red"]You must run that command as root super-user.[/COLOR]
[/LIST]

**[COLOR="Red"]For more info visit [http://splashy.alioth.debian.org/wiki/doku.php]("http://splashy.alioth.debian.org/wiki/doku.php")[/COLOR]**

---

### Post by linuxnewbie946 on 2006-07-17
Updated!

---

### Post by Don_DiZzLe on 2006-07-17
This one is also pretty tight!

[http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper](http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper)

---

### Post by linuxnewbie946 on 2006-07-17
> **Don_DiZzLe said:**
> This one is also pretty tight!

[http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper](http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper)

I saw that one, but you can't theme it without rebuilding the source code.

---

### Post by Peturrr on 2006-07-17
Works great!

Somebody should definately organise a splashy theme contest !

---

### Post by linuxnewbie946 on 2006-07-17
You can find some themes at kde-look.org

---

### Post by linuxnewbie946 on 2006-07-17
Updated! Added setting themes section.

---

### Post by linuxnewbie946 on 2006-07-18
Updated

---

### Post by ss0007 on 2006-07-18
Hey , whn i run , i get this error ,

$sudo dpkg -i splashy_0.1.8-0-39_i386.deb
dpkg: considering removing usplash in favour of splashy ...
dpkg: no, cannot remove usplash (--auto-deconfigure will help):
 ubuntu-desktop depends on usplash
  usplash is to be removed.
dpkg: regarding splashy_0.1.8-0-39_i386.deb containing splashy:
 splashy conflicts with usplash
  usplash (version 0.2-4) is installed.
dpkg: error processing splashy_0.1.8-0-39_i386.deb (--install):
 conflicting packages - not installing splashy
Errors were encountered while processing:
 splashy_0.1.8-0-39_i386.deb

pls help ..

---

### Post by linuxnewbie946 on 2006-07-18
> **ss0007 said:**
> Hey , whn i run , i get this error ,

$sudo dpkg -i splashy_0.1.8-0-39_i386.deb
dpkg: considering removing usplash in favour of splashy ...
dpkg: no, cannot remove usplash (--auto-deconfigure will help):
 ubuntu-desktop depends on usplash
  usplash is to be removed.
dpkg: regarding splashy_0.1.8-0-39_i386.deb containing splashy:
 splashy conflicts with usplash
  usplash (version 0.2-4) is installed.
dpkg: error processing splashy_0.1.8-0-39_i386.deb (--install):
 conflicting packages - not installing splashy
Errors were encountered while processing:
 splashy_0.1.8-0-39_i386.deb

pls help ..

Splashy is for Ubuntu Dapper. Do you use Dapper or an older version?

---

### Post by linuxnewbie946 on 2006-07-18
> **ss0007 said:**
> Hey , whn i run , i get this error ,

$sudo dpkg -i splashy_0.1.8-0-39_i386.deb
dpkg: considering removing usplash in favour of splashy ...
dpkg: no, cannot remove usplash (--auto-deconfigure will help):
 ubuntu-desktop depends on usplash
  usplash is to be removed.
dpkg: regarding splashy_0.1.8-0-39_i386.deb containing splashy:
 splashy conflicts with usplash
  usplash (version 0.2-4) is installed.
dpkg: error processing splashy_0.1.8-0-39_i386.deb (--install):
 conflicting packages - not installing splashy
Errors were encountered while processing:
 splashy_0.1.8-0-39_i386.deb

pls help ..

I think I see the problem. You are using dpkg to install it when you should use apt-get. Refer to the installation instructions above and tell me if it works or not.

---

### Post by linuxnewbie946 on 2006-07-18
Updated!! I found a major error in the installation instructions.

---

### Post by ss0007 on 2006-07-19
ya , ur right i used dpkg instead of apt-get.
the reason i used is , last night i got an error whn i added the repo u 've suggested. The apt-get reported me an error code of -1 when fetching packages.tag.gz 

So i went to debian site and downloaded, .deb file and tried to install . And that's wht i have posted.

can u pls check again , if the server is working  ?

TIA

---

### Post by linuxnewbie946 on 2006-07-19
> **ss0007 said:**
> ya , ur right i used dpkg instead of apt-get.
the reason i used is , last night i got an error whn i added the repo u 've suggested. The apt-get reported me an error code of -1 when fetching packages.tag.gz 

So i went to debian site and downloaded, .deb file and tried to install . And that's wht i have posted.

can u pls check again , if the server is working  ?

TIA

It is working, I sent you a private message on what to do next.

---

### Post by scenestar on 2006-07-19
splashy is horrible. You really just use fbsplash.

---

### Post by ss0007 on 2006-07-19
Here's wht happened whn i tried to do

$sudo apt-get update

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) stable Release.gpg
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:7 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release [2147B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) stable Release
Ign [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) stable/main Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Get:9 [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) stable/main Packages [845B]
92% [9 Packages gzip 0] [8 Release 27126/30.9kB 87%] [6 Release 27360/30.9kB 88
gzip: stdin: not in gzip format
Err [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) stable/main Packages
  Sub-process gzip returned an error code (1)
Get:10 [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages [12.6kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [39.4kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4275B]
Get:14 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [191B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [6951B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Get:16 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [2147B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [43.0kB]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:20 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages [12.6kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Fetched 206kB in 13s (15.6kB/s)
Failed to fetch [http://splashy.alioth.debian.org/debian/dists/stable/main/binary-i386/Packages.gz](http://splashy.alioth.debian.org/debian/dists/stable/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done

now , wht to do .. pls help ...

---

### Post by linuxnewbie946 on 2006-07-19
Remove everything in your /etc/apt/sources.list and replace it with this:

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free                                              
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Debian Sarge (stable) users: 
deb [http://splashy.alioth.debian.org/debian](http://splashy.alioth.debian.org/debian) stable main

## Debian Etch/Sid (testing/unstable) users: 
deb [http://splashy.alioth.debian.org/debian](http://splashy.alioth.debian.org/debian) unstable main

---

### Post by hanzomon4 on 2006-07-19
Can't get splashy to work. I followed the guide but I just get a black screen at boot.
I followed the howto for compiling the 2.6.17 kernel(just in case thet makes a diffrence)
I ran splashy test and got this output ```
 DirectFBError [DirectFBCreate (&video->dfb)]: Initialization error
```
Any ideas

---

### Post by linuxnewbie946 on 2006-07-19
I have no idea. I'll google and see what I can find.

---

### Post by pwaller on 2006-07-19
> **hanzomon4 said:**
> Can't get splashy to work. I followed the guide but I just get a black screen at boot.
I followed the howto for compiling the 2.6.17 kernel(just in case thet makes a diffrence)
I ran splashy test and got this output ```
 DirectFBError [DirectFBCreate (&video->dfb)]: Initialization error
```
Any ideas

exactly the same scenario here.

---

### Post by SickIcarus on 2006-07-20
Failed for me too - I get "Splashy server failed to load" and I get a ton of text for my boot.
Using kernel 2.6.15 still if that matters

---

### Post by snowpalmer on 2006-07-20
> **scenestar said:**
> splashy is horrible. You really just use fbsplash.

Care to explain why?

---

### Post by linuxnewbie946 on 2006-07-20
> **snowpalmer said:**
> Care to explain why?

I really don't think it's any better. Like bootsplash, you have to recompile the kernel to get fbsplash to work.

---

### Post by aeto on 2006-07-20
my menu.lst has about 5 or 6 times of the following

> title Ubuntu, Kernel 2.6.17
root (hd0,9)
kernel /boot/<YOUR KERNEL HERE> root=/dev/hda<YOUR HD # HERE) ro quiet splash
initrd /boot/initrd.img-2.6.17
savedefault
boot

so which do i edit? all of em? or just the first 1? or any 1?

---

### Post by linuxnewbie946 on 2006-07-20
> **aeto said:**
> my menu.lst has about 5 or 6 times of the following



so which do i edit? all of em? or just the first 1? or any 1?

Go to the line that says # defoptions=, replace it with this:

# defoptions=vga=792

Then run
```
update-grub
```

---

### Post by Slicedbread on 2006-07-20
I keep getting xml parser errors everytime I run splashy_config, and even when booting up in relation to splashy. 

```
** (process:5958): CRITICAL **: xml_parser_text_handler: assertion `text_len > 0 ' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

```

---

### Post by linuxnewbie946 on 2006-07-20
> **Slicedbread said:**
> I keep getting xml parser errors everytime I run splashy_config, and even when booting up in relation to splashy. 

```
** (process:5958): CRITICAL **: xml_parser_text_handler: assertion `text_len > 0 ' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

** (splashy_config:5958): CRITICAL **: _xml_parser_compare_element: assertion `_ node->got_text == TRUE' failed

```

do you see the splashy boot screen?

---

### Post by linuxnewbie946 on 2006-07-20
I get these messages too, but I still see the splash screen.......

---

### Post by linuxnewbie946 on 2006-07-20
> **SickIcarus said:**
> Failed for me too - I get "Splashy server failed to load" and I get a ton of text for my boot.
Using kernel 2.6.15 still if that matters

It sounds like you didn't install Splashy correctly.

---

### Post by Slicedbread on 2006-07-20
All I get is a blank screen.  When I try to set the theme to ubuntusplashy:


```
root@Laptop:/home/jeff# splashy_config -s ubuntusplashy

** (process:4931): CRITICAL **: xml_parser_text_handler: assertion `text_len > 0' failed

** (splashy_config:4931): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed
>Set theme as: ubuntusplashy
** (splashy_config:4931): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed

** (splashy_config:4931): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed

** (splashy_config:4931): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed
          [ DONE ]
root@Laptop:/home/jeff#


```

This is my grub boot:
title		Ubuntu, kernel 2.6.17.6
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17.6 ro root=/dev/hda2 vga=792
initrd		/boot/initrd.img-2.6.17.6
savedefault
boot

---

### Post by linuxnewbie946 on 2006-07-20
Try this:
kernel /boot/vmlinuz-2.6.17.6 ro root=/dev/hda2 vga=792 quiet splash

---

### Post by Slicedbread on 2006-07-20
That doesnt do anything.

---

### Post by linuxnewbie946 on 2006-07-20
```
sudo apt-get install --reinstall splashy splashy-themes
```

---

### Post by Slicedbread on 2006-07-20
It works on the normal kernel, but the one I compiled from your guide doesnt work. It also gave me an error when I was trying to compile the ati kernel module so its a kernel compilation error even though everything went through without a hitch.

---

### Post by linuxnewbie946 on 2006-07-20
That's very strange. I use the kernel that I have posted in my guide and it works great. I wonder why it doesn't work for you? Here is my /boot/grub/menu.lst:
> title		Kubuntu, kernel 2.6.17.6
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.17.6 root=/dev/hda10 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.17.6
savedefault
boot


---

### Post by Slicedbread on 2006-07-20
When I was trying to compile the ati kernel module it gave me missing file errors like makefile.cpu, makelib and others; even though they were extracted safely they were never copied to kernel headers directory. After I copied all the files its still would not let me build the module but luckily that ati installer script worked. 

In short my kernel didnt compile right for an unknown reason (its done this more than once) and it is effect my ability to install anything.

---

### Post by linuxnewbie946 on 2006-07-20
I have another guide on that same kernel for fakeroot. It's in my signature below.  vvvvvv

---

### Post by Slicedbread on 2006-07-20
Still no errors, but splashy doesnt work either. Splashy technically starts but doesnt do anything. If I leave the vga argument out it shows that splashy started and the screen flashes but continues on with text output. If I use vga=791 or vga=792 I get a blank screen. It still works with the default ubuntu kernel though.

---

### Post by linuxnewbie946 on 2006-07-20
> **Slicedbread said:**
> Still no errors, but splashy doesnt work either. Splashy technically starts but doesnt do anything. If I leave the vga argument out it shows that splashy started and the screen flashes but continues on with text output. If I use vga=791 or vga=792 I get a blank screen. It still works with the default ubuntu kernel though.

I think I know why it works with the old kernel and not the new one. The old kernel has defaults which have framebuffer support and the new kernel does not.

---

### Post by Slicedbread on 2006-07-20
Any idea how to fix? Or maybe a way to integrate usplash or fbsplash into the kernel?

Edit: I am compiling with ```
Device Drivers &#8594; Graphics support &#8594; VESA VGA graphics support
``` enabled.

From [http://splashy.alioth.debian.org/wiki/doku.php?id=faq]("http://splashy.alioth.debian.org/wiki/doku.php?id=faq")
and [http://splashy.alioth.debian.org/wiki/doku.php?id=faq#how_can_i_use_another_fb_driver_other_than_vesa_or_my_bios_doesn_t_support_vesafb]("http://splashy.alioth.debian.org/wiki/doku.php?id=faq#how_can_i_use_another_fb_driver_other_than_vesa_or_my_bios_doesn_t_support_vesafb")

EDIT 2: Enabling that option does work.

---

### Post by linuxnewbie946 on 2006-07-20
Glad it finally worked.

---

### Post by fatsheep on 2006-07-20
Ok I opened up the sources.list file and add pasted in the repositories but when I do apt-get update it gives me this:

> fatsheep@fatsheep:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory


Help please? 

appreciate it,

-sheep

---

### Post by Slicedbread on 2006-07-20
```

sudo apt-get update
sudo apt-get install splashy splashy-themes
sudo gedit /boot/grub/menu.lst

```

```

sudo splashy_config --info #displays installed themes#
sudo splashy_config -s /name of theme/

```

---

### Post by fatsheep on 2006-07-20
> **fatsheep@fatsheep:~$ sudo apt-get update**
Password:
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
  404 Not Found
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:7 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [5161B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release [30.9kB]
Get:9 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages [355B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages [38.0kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources [9552B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages [4101B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources [974B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages [6939B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources [902B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages [2055B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources [521B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [43.0kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [25.0kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [9381B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources [2224B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [14B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [14B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Err [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) stable Release.gpg
  Temporary failure resolving 'splashy.alioth.debian.org'
Err [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) unstable Release.gpg
  Temporary failure resolving 'splashy.alioth.debian.org'
Fetched 231kB in 2m40s (1441B/s)
Failed to fetch [http://splashy.alioth.debian.org/debian/dists/stable/Release.gpg](http://splashy.alioth.debian.org/debian/dists/stable/Release.gpg)   Temporary failure resolving 'splashy.alioth.debian.org'
Failed to fetch [http://splashy.alioth.debian.org/debian/dists/unstable/Release.g](http://splashy.alioth.debian.org/debian/dists/unstable/Release.g) pg  Temporary failure resolving 'splashy.alioth.debian.org'
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd) 64/Packages.gz  404 Not Found
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used  instead.
**fatsheep@fatsheep:~$ sudo apt-get install splashy-themes**
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package splashy-themes


Is the server down?

---

### Post by aeto on 2006-07-21
> **linuxnewbie946 said:**
> Go to the line that says # defoptions=, replace it with this:

# defoptions=vga=792

Then run
```
update-grub
```

now it takes 30 secs longer to boot into Ubuntu. And theres no splash bootscreen, just the console. Ok let me ask again.

In Step 3 im told to edit the menu.lst with the given line. But this is what i have in my menu.lst after i edited the # defoptions:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=792

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro vga=792
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro vga=792
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/hda1 ro vga=792
initrd		/boot/initrd.img-2.6.15-25-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-25-686
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro vga=792
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro vga=792
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro vga=792
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

so it looks ok..but there is no bootscreen. and its taking a much longer time to boot. Plus i got some sort of video mode error, but i just chose continue. any idea whats goin wrong?

---

### Post by linuxnewbie946 on 2006-07-21
No idea...... try splashy's faq: [http://splashy.alioth.debian.org/wiki/doku.php](http://splashy.alioth.debian.org/wiki/doku.php)

---

### Post by aeto on 2006-07-22
hmm..i get a message during boot:

You have passed an undefined video mode. To select a mode, press <Return>. To continue, press <Space>.

So i chose to select a new video mode..its all like 80x60 80x40 etc. I selected 80x60. Then it went through the long booting phase without any splash but near the end, it says "loading splashy". Then nothing happens..it just loads straight to Ubuntu.

The FAQ or the documentation there isnt helping )=

---

### Post by Don_DiZzLe on 2006-07-22
I also get the ****ing XML error messages during bootup and when trying to set themes with splashy_configure

This is my menu.lst:

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/sda1 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

And indeed the FAQ is no good at all.

---

### Post by aeto on 2006-07-22
but you get the splash bootscreen dont u? btw how come most of u got just 1 paragraph in ur menu.lst? mine as u can see above has multiples of the same para..is that normal?

---

### Post by bulldog on 2006-07-22
Every time when you get a new kernel or when you compile one by yourself,you get a new entry in your grub menu.lst.
When there is an error in your new kernel you can always choose to go back to  an older one which should work fine.
You can uninstall the kernels you don't use or put a # in front of each line you don't want to use in your menu.lst.
When you out commented them [#] you should not see them when you boot however they are still in your menu.lst.

---

### Post by Don_DiZzLe on 2006-07-22
I dont get any splashscreen whatsoever, I only get a verbose list of everyting thats starting up but no splashyscreen.

---

### Post by drgonzo88 on 2006-07-23
I'm having problems too. 
After following all the steps, selecting the theme, checking it was selected. and setting the VGA in grub.  I rebooted, then at boot-up all I could see was a black screen till X starts up.
I noticed when I changed my VGA back to normal so I could see the boot-up splashy has some "Critical errors", complaining about XML issues.


Dr.G

---

### Post by BKK on 2006-07-23
Yes I have just uninstalled splashy. It doesnt work properly.

I got a screen with a blue background and a penguin, then nothing happend for  a long time so I rebooted. I fixed the menu.lst and rebooted and it was hanging as splashy was trying to connect to something! I unplugged the network cable rebooted and deleted splashy packages...Booo splashy

---

### Post by Don_DiZzLe on 2006-07-23
Indeed crappy Splasy. Im gonna uninstall this and stick with the maybe not so goodlooking yet reliable usplash. What is the correct setting for the menu.lst for usplash?

---

### Post by aeto on 2006-07-24
> **bulldog said:**
> Every time when you get a new kernel or when you compile one by yourself,you get a new entry in your grub menu.lst.
When there is an error in your new kernel you can always choose to go back to  an older one which should work fine.
You can uninstall the kernels you don't use or put a # in front of each line you don't want to use in your menu.lst.
When you out commented them [#] you should not see them when you boot however they are still in your menu.lst.
thanks!

I think splashy would work only for some. Then again, it wouldnt b nice to call it crappy :neutral: Tho that somehow rhymes :lol: Btw just try installing usplash..it should remove splashy & then just revert ur menu.lst. i hope that would get it done..

---

### Post by Don_DiZzLe on 2006-07-24
What is the correct setting for the menu.lst for usplash then?

Does the weird XML error have something to do with the fact that I use XML desktop-optimizations mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=189192&highlight=improve+performance](http://ubuntuforums.org/showthread.php?t=189192&highlight=improve+performance)
?

---

### Post by RavenOfOdin on 2006-07-24
I'm using Debian Sarge on my backup comp. . .Let's see if this installs well. 

(EDIT: Does anyone know if a Splashy package is available for PPC? >.<)

---

### Post by drgonzo88 on 2006-07-25
```
What is the correct setting for the menu.lst for usplash then?
 
 Does the weird XML error have something to do with the fact that I use XML desktop-optimizations mentioned in this thread:
 http://ubuntuforums.org/showthread.p...+performa nce
```


No, I don't use XML desktop-optimizations and I'm getting the same problem.

---

### Post by denisesballs on 2006-07-31
I wanted to let everyone know Splashy has some big bugs. The most prominent being that you randomly get switched to tty1 (non graphical terminal). Irt's being worked on, amd you can see the progress here - [http://www.nanofreesoft.org/index.php?name=PNphpBB2&file=viewtopic&p=47](http://www.nanofreesoft.org/index.php?name=PNphpBB2&file=viewtopic&p=47)

I would suggest not using it until it's fixed, unless you wanna hit ctrl-alt-f7 everytime you reboot.

---

### Post by citizenr on 2006-08-05
rasz@rasz-desktop:/usr/src$ sudo apt-get install splashy splashy-themes
Reading package lists... Done
Building dependency tree... Done
Package splashy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package splashy has no installation candidate

---

### Post by Jucato on 2006-08-11
Is there something wrong with the repositories? No matter how much I update, it doesn't seem to show splashy...

---

### Post by thomasf on 2006-08-13
> **Fenyx said:**
> Is there something wrong with the repositories? No matter how much I update, it doesn't seem to show splashy...

Definitly something is wrong with the repo. I can't install Splashy.

```
tomek@ubuntu:~$ sudo apt-get install splashy splashy-themes
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package splashy
```

To be sure, I cleaned up /var/lib/apt/lists and ran apt-get update. This is the part of output which concerns Splashy:
```

Ign http://splashy.alioth.debian.org stable Release.gpg
Ign http://splashy.alioth.debian.org unstable Release.gpg
Get: 9 http://splashy.alioth.debian.org stable Release [3951B]
Get: 10 http://splashy.alioth.debian.org unstable Release [6817B]

Ign http://splashy.alioth.debian.org stable/main Packages
Ign http://splashy.alioth.debian.org unstable/main Packages

Get: 27 http://splashy.alioth.debian.org stable/main Packages [845B]
Get: 28 http://splashy.alioth.debian.org unstable/main Packages [20B]
```

---

### Post by XPuntu on 2006-08-13
The how to has this line:
kernel /boot/<YOUR KERNEL HERE> ro root=/dev/hda<YOUR HD # HERE> vga=792

And your post #35 has this line:
kernel /boot/vmlinuz-2.6.17.6 root=/dev/hda10 ro quiet splash vga=792

the ro is in a different place. What's right?

---

### Post by idn on 2006-08-13
Does anyone have the debs available for splashy? The repositories are aso down for me

---

### Post by Jucato on 2006-08-14
The repositories, are up. You can visit them directly in a web browser. But for some reason, we can't get packages from it...

---

### Post by idn on 2006-08-14
Is it possible for someone to post the debs for this? I will email the authors of splashy and let them know its down.

Edit: They can be found hre :) [http://alioth.debian.org/project/showfiles.php?group_id=30657](http://alioth.debian.org/project/showfiles.php?group_id=30657)

Although it would be good to install them via apt because then they will be automatically updated

---

### Post by voltagex on 2006-08-15
I wish there was a standard for splash screens... I definately like splashy but there's now so so many different ways to have a splash screen.

---

### Post by delfick on 2006-08-16
> **idn said:**
> Is it possible for someone to post the debs for this? I will email the authors of splashy and let them know its down.

Edit: They can be found hre :) [http://alioth.debian.org/project/showfiles.php?group_id=30657](http://alioth.debian.org/project/showfiles.php?group_id=30657)

Although it would be good to install them via apt because then they will be automatically updated

i followed that link and opened the .deb file (usuing ubuntu dapper here) and the package installer thing says 

> Error: Conflicts with the installed package 'usplash'

is it alright to uninstall usplash first...? will this screw things over for me?

aslo if it won't be automatically be updated....how is it manually updated?

thnx

---

### Post by spoiled on 2006-08-16
It should not be any problem to uninstall usplash and ubuntu-desktop. I've done it without problem. Although I havent managed to get splashy work yet but that is another story I think hehe... 

Here is what I've read on the Ubuntu site somewhere;
> 
Open up a terminal, and enter this to remove uSplash: (This will also remove the 'ubuntu-desktop' package, that's okay.)

sudo apt-get --purge remove usplash 

Then recreate the Linux image:

sudo dpkg-reconfigure linux-image-`uname -r` 

uSplash should now be properly removed.

Hope this helps..

---

### Post by Jucato on 2006-08-16
argh! I was able to download and install splashy but I got XML errors when trying to set a theme. Then when I boot, I get error messages that scroll too fast for me to read, and splashy won't work. Although I do get a screen that says that it failed to load (or something like that). And the splashy for shutting down/restarting works perfectly...

Any other thing I should be aware of? I'm using the kernel provided in the repositories (2.6.15-26-k7). I hope I wouldn't need to recompile the kernel, coz that would make splashy no different than the other alternatives... :(

---

### Post by delfick on 2006-08-16
> **spoiled said:**
> It should not be any problem to uninstall usplash and ubuntu-desktop. I've done it without problem. Although I havent managed to get splashy work yet but that is another story I think hehe... 

Here is what I've read on the Ubuntu site somewhere;


Hope this helps..

thnx for that :D

i got it to sorta work :D

basicaly when i choose linux to boot....it has the old text style (just text going down the screen (which is now small...though i like that better so all is good :p)
then it says something about a xml_parser error or something (is there a log file or something i can copy and paste into here ? )
then it comes up with the pretty bootscreen (btw where can i get other bootscreens (beside kde-look.org ?)) 

then after a little bit the whole screen except for the progress bar goes black.... then it loads into GDM and all is good from then....

 shutdown works perfectly :D

thnx

---

### Post by spoiled on 2006-08-17
Good for you :)  You got further than I hehe

I'm not sure about splashy logs but you could try to see what dmesg has to say about it.
> dmesg | more

I've installed the 2.6.17 kernel (from another HowTo on this forum) and it turns out now that Vesa graphics needs to be enabled in the kernel which I did not have :(  So I need to recompile the kernel before I can move on...

Also, I've read that BootUp logo needs to be enabled in the kernel. If you had usplash working before that option should be enabled I guess but you may wanna check to make sure?

Have you tried using other themes?
When I choose ubuntusplashy
> splashy_config -s ubuntusplashy
I get no errors but choosing the default theme I get lots of .xml errors for example.

Btw, you can see all available themes with
> splashy_config --info

Other than this it seems like splashy is a bit buggy ;)

---

### Post by delfick on 2006-08-17
is there a way to copy and paste the whole dmesg thing in one go?

also i'm already using ubuntusplashy though i want better looking ones that aren't so linux orientated (not that there is anything wrong with that but that's beside the point)


btw... my linux kernel version is vmlinuz-2.6.15-26-386 just so u know

---

### Post by GregaS on 2006-08-17
I have the same problem as delfick. When computer boots up there is just text but when I shut it down, I can see that fancy image. BTW i'm getting errors like theme.xml not found. What's that all about?

---

### Post by spoiled on 2006-08-18
I've managed to get it going now :)

Both startup and shutdown image is working.. Although Verbose mode by pressing F2 seems to do nothing?.. I'm running v1.8.1 .

The problem for me was not having VESA enabled (Device Drivers &#8594; Graphics support &#8594; VESA VGA graphics support) in the kernel.

You can check if you do by doing this:
> grep CONFIG_FB_VESA /boot/config-$(uname -r)

Btw, what do you have in your /boot/grub/menu.lst file? Have you added vga=792 or vga=791 to it?

---

### Post by GregaS on 2006-08-18
> grep CONFIG_FB_VESA /boot/config-$(uname -r)

Shows me this:

> CONFIG_FB_VESA=m

This is my /boot/grub/menu.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Kubuntu
root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hdd1 ro quiet splash
kernel		/boot/vmlinuz-2.6.15-26-686 ro root=/dev/hdd1 vga=792
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Kubuntu (varni zagon)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

title		Kubuntu memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by spoiled on 2006-08-18
I'm not sure if it makes a difference or not but instead of:
> title Kubuntu
root (hd1,0)
#kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/hdd1 ro quiet splash
kernel /boot/vmlinuz-2.6.15-26-686 ro root=/dev/hdd1 vga=792
initrd /boot/initrd.img-2.6.15-26-686
savedefault
boot

I have it like this (using your settings);
> title Kubuntu
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/hdd1 ro quiet splash vga=792
initrd /boot/initrd.img-2.6.15-26-686
savedefault
boot

I know it says using only vga=792 in the HowTo on the first page, but I've seen others menu.lst and also my own that looks like the last one..

Hope this helps!

---

### Post by delfick on 2006-08-18
inserting quiet splash got rid of most of the writing before the screen :D but it still goes black (except for the loading bar which remains) towards the end of the boot process.....

i have gone into tty1 after getting to the GDM login screen and then wrote down the few lines that appear before the screen appears...here they are.....(can someone tell me where a log file or something of this is so in future i don't have to write down what it says ? thnx)

> [17179572.232000] PCI: cannot allocate resource region 3 of device 0000:01:00.0
* Reading files needed to boot...
**(process :2101) : CRITICAL **: xml_parser_text_handler: assertion 'text_len > 0' failed
**(splashy_config : 2101): CRITICAL **: _xml_parser_compare_element: assertion '_node -> got_text == TRUE' failed
** (process : 2103): CRITICAL **: xml_parser_text_handler: assertion 'text_len > 0' failed
** (splashy_config :2103): CRITCAL **: _xml_parser_compare_element: assertion '_node -> got_text == TRUE' failed

here is my /boot/grub/menu.lst (important part anyway)
> title		Ubuntu Dapper, kernel 2.6.15-26-386
root		(hd0,7)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda8 ro quiet splash
kernel 		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda8 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.15-26-386
boot

I have:
GPU : Nvidia Geforce 6600GT
CPU : AMD Athlong 64 3200+
RAM : 1 gig of it (don't know what type)
and i use the "ubuntusplashy" theme for splashy
tell me if u need more info...

looking forward to someone telling me how to fix these issues :D

thnx

also....when i use splashy_config --info  i get this
```
iambob@bob-linux:~$ splashy_config --info

** (process:8058): CRITICAL **: xml_parser_text_handler: assertion `text_len > 0' failed
>Theme currently used:

** (splashy_config:8058): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed
                      ubuntusplashy

** (splashy_config:8058): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed
                      version 1.0

** (splashy_config:8058): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed
                         Ubuntu Splashy theme

** (splashy_config:8058): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed
                      URLs (null)

** (splashy_config:8058): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed
                      by Sebastian Sariego B. >segfault@kde.cl<
>Installed themes:

** (splashy_config:8058): CRITICAL **: _xml_parser_compare_element: assertion `_node->got_text == TRUE' failed
                      ubuntusplashy
                      default
                      debian3
                      debian4
                      debiansplashy
                      kubuntusplashy
                      crux

```

---

### Post by spoiled on 2006-08-18
I have the same type of error messages when running "splashy_config --info". Not sure what that means but for me it seems to work.

Have you tried the FAQ on the splashy homepage?

I've no idea what those error messages that you see before the login screen are.. Sorry.

Your menu.lst entries look just like mine.

---

### Post by GregaS on 2006-08-18
This is what i get from "splashy_config --info"

> (process:8167): GLib-CRITICAL **: g_ascii_strncasecmp: assertion `s1 != NULL' failed

(process:8167): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed

(process:8167): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed
Splashy ERROR: Setting XML file to <</theme.xml>> failed. XML File not found
>Theme currently used:
                      (null)
                      version (null)
                         (null)
                      URLs (null)
                      by (null)
>Installed themes:

(splashy_config:8167): GLib-CRITICAL **: g_dir_open: assertion `path != NULL' failed

(splashy_config:8167): GLib-CRITICAL **: g_dir_read_name: assertion `dir != NULL' failed

(splashy_config:8167): GLib-CRITICAL **: g_dir_close: assertion `dir != NULL' failed

---

### Post by delfick on 2006-08-18
> **spoiled said:**
> I have the same type of error messages when running "splashy_config --info". Not sure what that means but for me it seems to work.

Have you tried the FAQ on the splashy homepage?

I've no idea what those error messages that you see before the login screen are.. Sorry.

Your menu.lst entries look just like mine.

just tried the faq and the tips and tricks section and got nothing :'(

---

### Post by Robor on 2006-08-18
I edited my /etc/apt/sources.list to include the repos and did an 'apt-get upgrade' but here's all I get:

robor007@Home-T42-Ubuntu:~$ sudo apt-get install splashy splashy-themes
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package splashy

Any ideas?

---

### Post by edthefox on 2006-08-18
:-s I get the same error! is it broken?!
```
eddie@zorro:~$ sudo apt-get install splashy splashy-themes
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package splashy

```

---

### Post by GregaS on 2006-08-18
repos are not working. Download .deb from their site and install them manually.

---

### Post by meander on 2006-08-18
> **ss0007 said:**
> Hey , whn i run , i get this error ,

$sudo dpkg -i splashy_0.1.8-0-39_i386.deb
dpkg: considering removing usplash in favour of splashy ...
dpkg: no, cannot remove usplash (--auto-deconfigure will help):
 ubuntu-desktop depends on usplash
  usplash is to be removed.
dpkg: regarding splashy_0.1.8-0-39_i386.deb containing splashy:
 splashy conflicts with usplash
  usplash (version 0.2-4) is installed.
dpkg: error processing splashy_0.1.8-0-39_i386.deb (--install):
 conflicting packages - not installing splashy
Errors were encountered while processing:
 splashy_0.1.8-0-39_i386.deb

pls help ..
i am getting the same thing.

---

### Post by GregaS on 2006-08-18
You have to remove usplash. Just look at page 7.

---

### Post by spoiled on 2006-08-21
GregaS:

Have you managed to get it to work?

I noticed you have error messages when its suppose to list your themes. That, mine does not have. On some selected themes I've got a few lines of xml errors just before but then it lists my themes fine.

Read somewhere it could help with a re-install.
Let me know if you still have problem and I'll see if I can find that info for you.

---

### Post by GregaS on 2006-08-21
I haven't managed to get it work. It says something about Glib error or something. By the way if I try this:

> sudo splashy_config -s kubuntusplashy/

I get the same errors as when computer is booting:

> (process:8965): GLib-CRITICAL **: g_ascii_strncasecmp: assertion `s1 != NULL' failed

(process:8965): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed

(process:8965): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed
Splashy ERROR: Setting XML file to <</theme.xml>> failed. XML File not found
>Set theme as: kubuntusplashy/          [ FAIL ]

I don't know if I do this right. I was in directory */etc/splashy/themes* and there are these folders:

> crux  debian3  debian4  debiansplashy  default  kubuntusplashy  KubuntuSpringSplashy  ubuntusplashy

PS: Those GLib-CRITICAL erros are only erros when booting.

---

### Post by spoiled on 2006-08-22
hm... I never include the trailing slash if that might have something to do with it. I just write, from any PWD, like this;
> sudo splashy_config -s ubuntusplashy

---

### Post by GregaS on 2006-08-22
Nope. It doesn't help.

---

### Post by GregaS on 2006-08-22
Any other suggestions?

---

### Post by mejy on 2006-08-25
> **GregaS said:**
> Any other suggestions?

I have my console at 1440x900 - is it possible to use splashy at this widescreen resolution and are then any themes for it?

---

### Post by ciscosurfer on 2006-08-26
Seems to me, as some others have pointed out already, that Splashy is indeed quite buggy and most certainly does require kernel changes (not to mention removing usplash, etc.).  I'd stay away from it right now until all the kinks are worked out.

It would be nice if the original poster would update his/her post to reflect the possible problems that may arise, i.e., "WARNING: SPLASHY IS EXPERIMENTAL.  USE OF SAID PROGRAM DESERVES CAUTION AND IS TO BE DONE AT YOUR OWN RISK.  YOU'VE BEEN WARNED."

It's also important to note that while Ubuntu is Debian-based, not all Debian programs work smoothly on Ubuntu, and this, coupled with the fact that a newer kernel is suggested/recommended, should be noted caveats for users to know/pay attention to.

---

### Post by Jucato on 2006-08-26
I would generally agree with you except in one thing: Splashy itself is not buggy. The problem, it seems, is that the Ubuntu kernels is not set up in a way that would make Splashy work. It is set up for USplash. Splashy is not really the problem. It's being used in MEPIS, and I don't see any problems.

---

### Post by ciscosurfer on 2006-08-27
> **Fenyx said:**
> I would generally agree with you except in one thing: Splashy itself is not buggy. The problem, it seems, is that the Ubuntu kernels is not set up in a way that would make Splashy work. It is set up for USplash. Splashy is not really the problem. It's being used in MEPIS, and I don't see any problems.
Ok.  But considering most people don't use the absolute latest, bleeding-edge kernel, using Splashy might be difficult.  Hence, a kernel upgrade is in fact necessary (from what I've read) and that in itself contradicts one of Splashy's selling points of no kernel manipulations.  Glad to hear that it works on Mepis, but this is all about Ubuntu ;)

---

### Post by Jucato on 2006-08-27
Yeah, I was pretty much disappointed that Splashy doesn't work on the current kernel. I also forgot what kernel version MEPIS 6 uses. It loses one of its strongest selling points, as you have mentioned.

Anyway, by the time Edgy comes out, the clamor for Splashy might die down a bit. I think USplash is going to get a bit better. Don't quote me on that one, though...

---

### Post by spoiled on 2006-08-30
> **mejy said:**
> I have my console at 1440x900 - is it possible to use splashy at this widescreen resolution and are then any themes for it?

This is the table from the Vesafb mini-HOWTO

```

Colours   640x480 800x600 1024x768 1280x1024 1600x1200
--------+---------------------------------------------
256     |   769     771      773      775       796
32,768  |   784     787      790      793       797
65,536  |   785     788      791      794       798
16.8M   |   786     789      792      795       799

```

hope this helps

---

### Post by spoiled on 2006-08-30
> **ciscosurfer said:**
> Seems to me, as some others have pointed out already, that Splashy is indeed quite buggy and most certainly does require kernel changes (not to mention removing usplash, etc.).  I'd stay away from it right now until all the kinks are worked out.

It would be nice if the original poster would update his/her post to reflect the possible problems that may arise, i.e., "WARNING: SPLASHY IS EXPERIMENTAL.  USE OF SAID PROGRAM DESERVES CAUTION AND IS TO BE DONE AT YOUR OWN RISK.  YOU'VE BEEN WARNED."


Yes, it seems like there are a few bugs still to be fixed.
For those that doubt, please read about the latest splashy developer meeting held some weeks ago.

> [http://splashy.alioth.debian.org/wiki/doku.php?id=news](http://splashy.alioth.debian.org/wiki/doku.php?id=news)

I have it working though, but after some trouble. And even now I can not get verbose mode to work as it should, shows no output until late in the bootprocess (possibly due to that nasty initramfs bug?).
I'm using kernel 2.6.17 built from the HowTo here in this forum. If you plan to follow that guide please dont forget to enable VESA VGA graphics support in the kernel or splashy won't work.

UPDATE: Just read in the splashy forum that version 0.2.x of splashy is suppose to be released within a week or two! :-D

Great news indeed!

---

### Post by lozenge on 2006-09-08
```
james@monkey:~$ sudo apt-get install splashy
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package splashy
```

This is after updating with the new repositories.

---

### Post by flargen on 2006-09-09
The repos in the howto do not work. However, there are the newest packages on the project page:
[http://alioth.debian.org/project/showfiles.php?group_id=30657]("http://alioth.debian.org/project/showfiles.php?group_id=30657")

---

### Post by xnn on 2006-11-05
This is strange. Doesn't work for me (Ubuntu Dapper).

```
xenon@xenon:~/Desktop$ sudo apt-get install splashy splashy-themes
Reading package lists... Done
Building dependency tree... Done
Package splashy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package splashy has no installation candidate
```

But **apt-cache search splashy** doesn't return anything...

---

### Post by aniskasa on 2006-11-08
Tried the apt-get, didn't work. Downloaded the files, and:

```
dpkg -i splashy*.deb splashy-themes*.deb
```

resulted:

```
dpkg: considering removing usplash in favour of splashy ...
dpkg: no, cannot remove usplash (--auto-deconfigure will help):
 kubuntu-desktop depends on usplash
  usplash is to be removed.
dpkg: regarding splashy_0.1.8-0sarge40_i386.deb containing splashy:
 splashy conflicts with usplash
  usplash (version 0.2-4) is installed.
dpkg: error processing splashy_0.1.8-0sarge40_i386.deb (--install):
 conflicting packages - not installing splashy
(Reading database ... 99984 files and directories currently installed.)
Preparing to replace splashy-themes 0.1.8-0sarge40 (using splashy-themes_0.1.8-0sarge40_all.deb) ...
Unpacking replacement splashy-themes ...
Preparing to replace splashy-themes 0.1.8-0sarge40 (using splashy-themes_0.1.8-0sarge40_all.deb) ...
Unpacking replacement splashy-themes ...
More than one copy of package splashy-themes has been unpacked
 in this run !  Only configuring it once.
dpkg: dependency problems prevent configuration of splashy-themes:
 splashy-themes depends on splashy; however:
  Package splashy is not installed.
dpkg: error processing splashy-themes (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy_0.1.8-0sarge40_i386.deb
 splashy-themes
```

What to do to get it work?

---

### Post by linuxnewbie946 on 2006-11-08
To tell you the truth, I am not sure if Splashy is usable anymore. It may even be obselete. I personally have quit using Splashy for this very reason. Once a version comes out for Kubuntu Edgy, I will try again. But until then, I can wait.

---

### Post by ashrack on 2006-11-10
> **aniskasa said:**
> Tried the apt-get, didn't work. Downloaded the files, and:

```
dpkg -i splashy*.deb splashy-themes*.deb
```

resulted:

```
dpkg: considering removing usplash in favour of splashy ...
dpkg: no, cannot remove usplash (--auto-deconfigure will help):
 kubuntu-desktop depends on usplash
  usplash is to be removed.
dpkg: regarding splashy_0.1.8-0sarge40_i386.deb containing splashy:
 splashy conflicts with usplash
  usplash (version 0.2-4) is installed.
dpkg: error processing splashy_0.1.8-0sarge40_i386.deb (--install):
 conflicting packages - not installing splashy
(Reading database ... 99984 files and directories currently installed.)
Preparing to replace splashy-themes 0.1.8-0sarge40 (using splashy-themes_0.1.8-0sarge40_all.deb) ...
Unpacking replacement splashy-themes ...
Preparing to replace splashy-themes 0.1.8-0sarge40 (using splashy-themes_0.1.8-0sarge40_all.deb) ...
Unpacking replacement splashy-themes ...
More than one copy of package splashy-themes has been unpacked
 in this run !  Only configuring it once.
dpkg: dependency problems prevent configuration of splashy-themes:
 splashy-themes depends on splashy; however:
  Package splashy is not installed.
dpkg: error processing splashy-themes (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy_0.1.8-0sarge40_i386.deb
 splashy-themes
```

What to do to get it work?

well manually uninstall usplash!
just do 
```
aptitude purge usplash
```
And if it says that KUBUNTU-DESKTOP must also be uninstall the uninstall it! KUBUNTU-DEKSToP is nothing but a meta package! And by removing it absolutely nothing harm will come to U!

---

### Post by aniskasa on 2006-11-15
Yeah, Ok. Thanks :) Got it installed just fine.

---

### Post by darkcommon on 2006-11-22
Hi, how I can install Splashy in Ubuntu Dapper 6.06 LTS if its  possible...](*,) ](*,) :confused: :confused: ](*,)

---

### Post by airflow on 2007-09-01
> **mejy said:**
> I have my console at 1440x900 - is it possible to use splashy at this widescreen resolution and are then any themes for it?

Yeah, that would interest me, too... Are there any widescreen-resolutions available to use for splashy/usplash? According to the VESA-codetable, it's not.

greez,
airflow

---

### Post by runesvend on 2008-01-26
I get the following error when running *sudo apt-get update* in a terminal after updating my sources.list file:

> 
rune@rune:~$ sudo apt-get update
[...]
Err [http://splashy.alioth.debian.org](http://splashy.alioth.debian.org) stable/main Packages
  403 Forbidden
[...]
Failed to fetch [http://splashy.alioth.debian.org/debian/dists/stable/main/binary-i386/Packages.gz](http://splashy.alioth.debian.org/debian/dists/stable/main/binary-i386/Packages.gz)  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


This is what I put in my sources.list file:

> ## Debian Sarge (stable) users: 
deb [http://splashy.alioth.debian.org/debian](http://splashy.alioth.debian.org/debian) stable main

## Debian Etch/Sid (testing/unstable) users: 
#deb [http://splashy.alioth.debian.org/debian](http://splashy.alioth.debian.org/debian) unstable main

None of the other entries in my *sources.list* file give me a "forbidden" response when running *apt-get update*.

Any ideas?

---

### Post by tripmix on 2008-08-30
Is there anyway to get splashy to display a background image on all consoles (F1-F6) like bootsplash could? I miss the bootsplash patch. Any one figure out how to do that with splashy or usplash or even a way to get 2.6.24 bootsplash patch to work with 2.6.26 kernel please let me know.

---

### Post by dk_sn1p3r on 2009-03-10
I tried using Splashy today but it did end in nothing but failure.  I've tried pulling from the bleeding edge of off alioth and I've tried pulling off the Ubuntu 8.10 reposotory and both of them are very buggy indeed.  When just testing out Splashy themes (The Default Ones) I'll end up with a boot screen stuck on the face of my desktop. I'd have to reboot when testing them in the start up manager just to get my screen back.  I'd much rather just recompile a few good looking Usplash themes to how I want them to work or make my own and compile it then use something this buggy.  For that matter maybe even using gfxboot from suse instead of Splashy.  I would be nice to not have to spend time recompiling some Usplash themes and taking the time to get the source or even remake a few of them but I'd rather have it work stable and not crash constantly.

---

### Post by Ampersand. on 2009-04-09
I second that opinion, this just doesnt work well enough to make it worth being able to use a gui. it is a nice idea to make a basic splash screen with no progress bar but once you try to get complicated its gets upset and dies

---

### Post by Intrepid Ibex on 2009-08-12
I prefer fbsplash on my arch, because it has nice fadein and fadeout effects.

---

