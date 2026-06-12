---
title: "initNG Nvidia Tutorial (Alot useful for non Nvidia card users)"
date: 2006-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Demon012 on 2006-06-07
Introduction

initNG is a next generation init replacement and is designed to run the startup scripts of your computer as soon as their dependencies are met. It does all this in parallel so makes a huge difference in startup times (especially if used with hyperthreading or a multiprocessor machine etc).

**_Acknowledgements_**

Ok first let me thank Jimmy Wennlund, DEac-, Trigger and qupada for creating such a great replacement for sysinit and then thank bunkacid who I met in the #initng irc channel for putting up with all my questions and for being so much help =).

**_Preperations_**

Ok in this tutorial we are going to be using the latest version of initNG and initNG-ifiles from the subversion repository. This will require us to build it from source so first we will need build-essentials which can be attained by this command.

> sudo apt-get install build-essential

And to configure it we will need cmake

> sudo apt-get install cmake

And ofcourse subversion to get the source in the first place =)

> sudo apt-get install subversion

**_Getting the source's from the subversion repo's_**

Ok now we have the things required to configure and make initNG we need to get the sourcecode.

First we will make a directory to download the source to in your home directory. 

> mkdir ~/build

then change into that directory

> cd ~/build

Now we can get initng's source via this command

> svn co [https://svn.initng.org/initng/trunk](https://svn.initng.org/initng/trunk) initng

When you press enter it will ask you if you wish to accept the certificate. You can either press 't' to temporarily accept or 'p' to permanently accept the certificate.

Now we will get initng-ifiles

> svn co [https://svn.initng.org/initng-ifiles/trunk](https://svn.initng.org/initng-ifiles/trunk) initng-ifiles

It will ask you about the cert (unless you pressed 'p' last time. Just press 't' or 'p'.

**_Configuring, Building and Installing initNG_**

Ok now we have the sources first make sure you are in the same directory as when you ran the svn commands and then do.

> cd initng

Then.

> ./build.sh

This should then (hopefully) configure, build and install initNG.

Now we need to install initNG-ifiles so first we need to

> cd ..

To return to the directory we downloaded the subversion sources too.

Then

> cd initng-ifiles

Then we need to run cmake to configure the ifiles (no build script for this).

> cmake . (make sure you include the '.' or else it will not know where the source files are).

then you need to make the ifiles

> make

then install them

> sudo make install

Now we have almost finished. The next step it to get initNG to configure the startup scripts which can be done by using.

> sudo gen_system_runlevel -all /etc/initng/

This will then create 2 files in the /etc/initng folder 1 called default.runlevel and 1 called system.virtual.

Now we need to change some files to make gdm and the nvidia driver work correctly.

There are 2 ways of doing this but I am going to show you what in my opinion is the best way (to get your hands dirty).

First we need to change to the /etc/initng folder

> cd /etc/initng

Now we will get gdm to run on startup by editing default.runlevel in vi

> sudo vi default.runlevel

Now in we need to add a new line at the end of this file. To do this press 'i' on the keyboard to go into insert mode. Then use your arrow keys on your keyboard to navigate to the end of the last line in the file and press enter. It should have then created a new line. Then you need to add.

> daemon/gdm

and if you are running a nvidia card also add

> daemon/nvidia-glx

Now press ':w' and then press enter (that is semicolon then press w) to save the file then we need to quit using ':q' (semicolon then q).

Now we need to edit system.virtual file

> sudo vi system.virtual

and append a new line containing

> system/modules/depmod

Then save the file and quit as you did with the last file.

Now the final stage is to edit your /boot/grub/menu.lst

> sudo vi /boot/grub/menu.lst

You need to scroll to the bottom and look for something similar to this:

> title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

You need to create your own version just bloew the top block but with some small ammendments.

The first ammendment you need to make is on the title line. All you need to do on this like is append (initNG) to the end of it to identify it as using initNG (this is just the text you see in grub and in no way makes initNG work so you can skip this if you wish).

The next step is adding "init=/sbin/initng" to the end of the kernel line which will tell the kernel to use initNG to load everything.

E.G

> kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash init=/sbin/initng

Now you need to save the file.

You can then reboot your PC and then select the (initNG) entry in grub and with a little luck initNG should load your PC/Laptop up in record time =).

Enjoy,

Demon012

P.S If you get stuck on the bootloader configuration here is where I learn't how to do this stuff minus the nvidia stuff [http://www.initng.org/wiki/Installation](http://www.initng.org/wiki/Installation).

---

### Post by Demon012 on 2006-06-08
Please post comments and suggestions this is my first how to I have written for the Ubuntu community.

Thanks,

Demon012

P.S This post is anything but finished I have alot more to add to it

---

### Post by jakeee on 2006-06-08
I saw no need to add nvidia-glx to the default because it failed to start but CoD still worked well. The problem might be that I don't use nvidia-glx package. Somehow my internet started working perfectly. So thanks.

Btw. I bet some of you need to use cupsd so do this:

```
sudo ng-update add daemon/cupsd default
```

---

### Post by Demon012 on 2006-06-08
Thanks for the comment jake. The cupsd bit is one of the things I am going to add later on (doing a assignment for college atm).

**Also to get HP Printers you have to run 2 more other commands besides**

> sudo ng-update add daemon/cupsd default

which are

> 
sudo ng-update add daemon/hpiod default
sudo ng-update add daemon/hpssd default

[B]
To get CPU scaling to work again you need to do this[/B]

> 
sudo ng-update add system/speedstep
sudo ng-update add daemon/powernowd


---

### Post by tlaloczint on 2006-06-08
well I got this out

tlaloc@tlaloc-desktop:~/build/initng$ ./build.sh
**** Creating the build directory ****
**** Configuring project ****
-- Check for working C compiler: gcc
-- Check for working C compiler: gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Looking for include files HAVE_COREDUMPER_H
-- Looking for include files HAVE_COREDUMPER_H - not found.
-- Looking for WriteCoreDump in coredumper
-- Looking for WriteCoreDump in coredumper - not found
-- Configuring done
-- Generating done
-- Build files have been written to: /home/tlaloc/build/initng/build
Configuration successful.
**** Compiling project ****
Scanning dependencies of target initng
Building C object src/CMakeFiles/initng.dir/initng_active_db.o
Building C object src/CMakeFiles/initng.dir/initng_active_state.o
Building C object src/CMakeFiles/initng.dir/initng_common.o
Building C object src/CMakeFiles/initng.dir/initng_control_command.o
Building C object src/CMakeFiles/initng.dir/initng_depend.o
Building C object src/CMakeFiles/initng.dir/initng_error.o
Building C object src/CMakeFiles/initng.dir/initng_execute.o
Building C object src/CMakeFiles/initng.dir/initng_env_variable.o
Building C object src/CMakeFiles/initng.dir/initng_fd.o
Building C object src/CMakeFiles/initng.dir/initng_fork.o
Building C object src/CMakeFiles/initng.dir/initng_handler.o
Building C object src/CMakeFiles/initng.dir/initng_interrupt.o
Building C object src/CMakeFiles/initng.dir/initng_kill_handler.o
Building C object src/CMakeFiles/initng.dir/initng_load_module.o
Building C object src/CMakeFiles/initng.dir/initng_main.o
Building C object src/CMakeFiles/initng.dir/initng_open_read_close.o
Building C object src/CMakeFiles/initng.dir/initng_plugin_callers.o
Building C object src/CMakeFiles/initng.dir/initng_plugin_hook.o
Building C object src/CMakeFiles/initng.dir/initng_process_db.o
Building C object src/CMakeFiles/initng.dir/initng_service_data_types.o
Building C object src/CMakeFiles/initng.dir/initng_service_types.o
Building C object src/CMakeFiles/initng.dir/initng_service_cache.o
/home/tlaloc/build/initng/src/initng_service_cache.c: In function &#8216;initng_servic e_cache_register&#8217;:
/home/tlaloc/build/initng/src/initng_service_cache.c:64: error: &#8216;s_global&#8217; has n o member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c: In function &#8216;initng_servic e_cache_find_by_exact_name&#8217;:
/home/tlaloc/build/initng/src/initng_service_cache.c:155: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:155: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c: In function &#8216;initng_servic e_cache_find_by_name&#8217;:
/home/tlaloc/build/initng/src/initng_service_cache.c:188: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:188: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c: In function &#8216;initng_servic e_cache_find_in_name&#8217;:
/home/tlaloc/build/initng/src/initng_service_cache.c:227: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:227: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c: In function &#8216;initng_servic e_cache_clear_father_pointer_from&#8217;:
/home/tlaloc/build/initng/src/initng_service_cache.c:249: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:249: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
cc1: warnings being treated as errors
/home/tlaloc/build/initng/src/initng_service_cache.c: In function &#8216;initng_servic e_cache_free&#8217;:
/home/tlaloc/build/initng/src/initng_service_cache.c:276: warning: implicit decl aration of function &#8216;initng_active_db_change_service_h&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:276: warning: nested extern  declaration of &#8216;initng_active_db_change_service_h&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c: In function &#8216;initng_servic e_cache_free_all&#8217;:
/home/tlaloc/build/initng/src/initng_service_cache.c:308: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:308: warning: left-hand ope rand of comma expression has no effect
/home/tlaloc/build/initng/src/initng_service_cache.c:308: warning: value compute d is not used
/home/tlaloc/build/initng/src/initng_service_cache.c:308: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:314: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:314: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:314: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:314: error: &#8216;s_global&#8217; has no member named &#8216;service_cache&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c: In function &#8216;initng_servic e_cache_find_father&#8217;:
/home/tlaloc/build/initng/src/initng_service_cache.c:332: warning: implicit decl aration of function &#8216;initng_common_parse_service&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:332: warning: nested extern  declaration of &#8216;initng_common_parse_service&#8217;
/home/tlaloc/build/initng/src/initng_service_cache.c:332: warning: assignment ma kes pointer from integer without a cast
make[2]: *** [src/CMakeFiles/initng.dir/initng_service_cache.o] Error 1
make[1]: *** [src/CMakeFiles/initng.dir/all] Error 2
make: *** [all] Error 2
tlaloc@tlaloc-desktop:~/build/initng$

any ideas?

---

### Post by glennric on 2006-06-08
I get the same errors that tlaloczint gets.

---

### Post by Sandlst on 2006-06-09
[QUOTE=glennric]I get the same errors that tlaloczint gets.[/QUOTE]
Same problem here: I just did a fresh install, used automatix as well as installed ndiswrapper.  This really looks cool though, can't wait to get it working.

---

### Post by mp3guy on 2006-06-18
Yep, same error.

---

