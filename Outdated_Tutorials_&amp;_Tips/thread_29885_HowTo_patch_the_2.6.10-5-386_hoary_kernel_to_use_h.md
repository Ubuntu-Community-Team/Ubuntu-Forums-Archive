---
title: "HowTo patch the 2.6.10-5-386 hoary kernel to use hp scanjet 5100c with ppscsi"
date: 2005-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by crito on 2005-04-26
[B]HowTo patch the 2.6.10-5-686 hoary kernel to use hp scanjet 5100c with ppscsi and epst.
[/B]

1) get the kernel sources from the repositorys:

 [FONT=Courier New]# apt-get install linux-source-2.6.10
[/FONT]
2) Get the ppscsi sources
 
 [FONT=Courier New]# apt-get install ppscsi-source[/FONT]

3) get the patches

 [FONT=Courier New]# cd /usr/src/
 # wget [http://penguin-breeder.org/kernel/download/linux-ppscsi-2.6.x.patch.gz](http://penguin-breeder.org/kernel/download/linux-ppscsi-2.6.x.patch.gz)
 # wget [http://penguin-breeder.org/kernel/download/linux-ppscsi-2.6.x.patch.gz.md5](http://penguin-breeder.org/kernel/download/linux-ppscsi-2.6.x.patch.gz.md5)
 # md5sum -cv linux-ppscsi-2.6.x.patch.gz.md5
 # gunzip linux-ppscsi-2.6.x.patch.gz[/FONT]

4) edit drivers/parport/share.c to avoid some stupid errors from modprobe
   i had to do this manually, because otherwise i got errormessages when i wanted to modprobe the ppscsi module.

in line 1007 you add:
 
 [FONT=Courier New]EXPORT_SYMBOL(parport_get_port);[/FONT]

5) patch the kernel

 [FONT=Courier New]# patch -p1 --dry-run < ../linux-ppscsi-2.6.x.patch[/FONT]

6) copy the config and compile the kernel

 [FONT=Courier New]# cp /boot/config-2.6.10-5-386 .config
 # make modules
 # make modules_install[/FONT]

7) compile the new ppscsi modules

 [FONT=Courier New]# cd ..
 # tar -xjvf ppscsi-source.tar.bz2
 # cd modules/ppscsi/
 # make[/FONT]
 
8) copy the new modules you need (for a hp scanjet 5100c its ppscsi and epst) to /lib/modules/

 [FONT=Courier New]# cp ppscsi.ko /lib/modules/2.6.10-5-386/kernel/drivers/parport/
 # cp epst.ko /lib/modules/2.6.10-5-386/kernel/drivers/parport/
 # modprobe scsi_mod
 # modprobe sg
 # modprobe parport
 # modprobe parport_pc
 # modprobe ppscsi
 # modprobe epst[/FONT]

9) now use xsane scanning programm to use your kernel
   edit /etc/modules to load modules at startup

---

### Post by etitor on 2005-05-28
Thank you for the hint.

Now it remains unclear for me whether all of this patching refers to a 386 or to a 686 kernel. I am using the 686 kernel and wouldn't mess with it unless I am pretty sure that this procedure doesn't apply only to 386 kernels.

---

### Post by pdk001 on 2005-05-28
thanks for tip
i'll try this on epson 5100 stylus

---

### Post by teolemon on 2005-12-25
I'm currently on Ubuntu Dapper (i also tried on Breezy)
I've installed kernel-patch-ppscsi-2.6 and ppscsi-source (the only things available in the reps)
Does the fact that source is included in kernel patch mean that i don't have to patch the kernel?

---

### Post by Garyu on 2006-03-06
I have a fresh Breezy 5.10 install and want to make my HP ScanJet 2100 work, so I followed this howto, but there are a few mistakes that needs to be corrected... Also, at the make modules I get an error:

[QUOTE=crito][B]HowTo patch the 2.6.10-5-686 hoary kernel to use hp scanjet 5100c with ppscsi and epst.
[/B]

1) get the kernel sources from the repositorys:

 [FONT=Courier New]# apt-get install linux-source-2.6.10
[/FONT]
[/QUOTE]
My source is linux-source-2.6.12, maybe it would be better to use **apt-get install linux-source-'uname -r'** in the howto? Also, this only downloads the source in a compressed file, so it needs to be unpacked before anything works.

[QUOTE=crito]4) edit drivers/parport/share.c to avoid some stupid errors from modprobe
[/QUOTE]
This should read "linux-source-'uname -r'/drivers/parport/share.c" or something like that, since this directory is located in the source directory, not "/usr/src/" which is the current directory in the terminal.

[QUOTE=crito]5) patch the kernel

 [FONT=Courier New]# patch -p1 --dry-run < ../linux-ppscsi-2.6.x.patch[/FONT]
[/QUOTE]
Again, the version doesn't match. Also, the ppscsi.patch-file contains a reference to a "linux-2.6.2" directory which isn't there. Substituting this with "linux" worked for me, but I guess a link could be made with the "ln" command as well. Also, it says "../linux-ppscsi-" and so on, but the "../" should be removed.

Since I have a parallell port scanner (but this patch still applies) I also had to skip the first two files of the patch (press enter four times) and then the rest would complete nicely. This should be pointed out to new users IMO.

[QUOTE=crito]6) copy the config and compile the kernel

 [FONT=Courier New]# cp /boot/config-2.6.10-5-386 .config
 # make modules
 # make modules_install[/FONT]
[/QUOTE]
This is as far as I get. "make modules" gives me the answer that no rule exists to make modules. How do I fix this so I can continue on to the next step?

Another note: all of the above requires either sudo in the beginning of each line or "sudo su" before executing all of the commands as they are in this howto... That too should be pointed out...

So, when or if someone can help me with the "make modules" I will get back to you on if this works or not. :)

---

### Post by miguelanxo on 2006-03-22
Ok, after seing this thread, I managed to patch my current kernel (2.6.11) and make the scanner work. I did have to adapt the patch cause I got a patch reject and after fixing it, the following messages after inserting ppscsi:

unknown symbol scsi_sleep
unknown symbol parport_get_port

which I corrected changing scsi_sleep calls for ssleep (and msleep in one case). If anyone interested in getting the patch, just mail me.

Ah, just for the record, I wasn't able to make the scanner work in Windows 2000 nor Windows XP, but after patching the kernel, it does work wonderful with xsane.

---

### Post by miguelanxo on 2006-03-22
Well, after seeing the url of the patch, I must admit I used the one in ubuntu (apt-get install ppscsi-patch-2.6.whatever), which had the scsi_sleep references. The one in the post above looks like can be aplied to 2.6.11 directly (even if I haven't tried).

P.S. If after compiling and inserting the modules (with no errors) xsane doesn't find the scanner, try to run it as root. If it finds the scanner when running as root, you'll have to check the permissions in /dev/sg0 (maybe /dev/lp0).

chmod a+rw /dev/sg0
chmod a+rw /dev/lp0

should do the trick, even if not a secure solution. :P

---

### Post by rolf_lindberg on 2006-04-16
this howto is a bit messy. I figured most things out anyway, but I get the same error as above "unknown symbol partport_get_port"

isn't there an easier and safer way to do this than to patch the kernel? :-?

---

### Post by miguelanxo on 2006-04-17
Well, maybe (maybe) if you followed the instructions in the ubuntu forum (the previous ones, not my instructions), you would have done this...

[...]

4) edit drivers/parport/share.c to avoid some stupid errors from modprobe
i had to do this manually, because otherwise i got errormessages when i wanted to modprobe the ppscsi module.

in line 1007 you add:

EXPORT_SYMBOL(parport_get_port);

[...]

Well, maybe not the line 1007 in your version of the kernel, you just have to add it near the bunch of export symbols (mine, after inserting that line reads now as...)

[...]

EXPORT_SYMBOL(parport_claim);
EXPORT_SYMBOL(parport_claim_or_block);
EXPORT_SYMBOL(parport_release);
EXPORT_SYMBOL(parport_register_port);
EXPORT_SYMBOL(parport_announce_port);
EXPORT_SYMBOL(parport_remove_port);
EXPORT_SYMBOL(parport_register_driver);
EXPORT_SYMBOL(parport_unregister_driver);
EXPORT_SYMBOL(parport_register_device);
EXPORT_SYMBOL(parport_unregister_device);
EXPORT_SYMBOL(parport_get_port);                       <--- Inserted by me
EXPORT_SYMBOL(parport_put_port);
EXPORT_SYMBOL(parport_find_number);
EXPORT_SYMBOL(parport_find_base);

[...]

Then recompile the kernel, and it should work. If you keep on getting that error, check twice that you're using the most recent recompiled version of the kernel and the modules.

---

### Post by minisori on 2006-05-16
I have tested this on dapper and seem alot more easier and clean. Instead of patch the kernel you just build a module for your actual kernel.

sudo apt-get install linux-headers-`uname -r` module-assistant

sudo module-assistant prepare
sudo module-assistant get ppscsi
sudo module-assistant unpack ppscsi
sudo module-assistant build ppscsi
sudo module-assistant install ppscsi

And all done, now you only have to do "sudo modprobe epst" before run xsane, sane or gimp plugin or anything :P

If i find how to auto the last step i will edit this post.

This should be valid too for any printer wich uses paraller port and has its own scsi interface, i guess.

NOTE: be sure before run "module-assistant get ppscis" that there is no any package manager runing.
(all the sources will be installed in /usr/src)

---

### Post by rolf_lindberg on 2006-07-23
neat! this module-assistant thing is so much more easy to do than the above. BUT, I still get an error.

After doing the above I run "sudo modprobe epst" and get a bunch of errors from both ppscsi and epst. I assume epst is giving me errors since ppscsi didn't load (unknown symbol ppsc_make_map and so on). The ppscsi error is only one, and it has been mentioned here before: 

ppscsi: "unknown symbol parport_get_port" 

How do I resolve this?

---

### Post by rolf_lindberg on 2006-07-31
> **minisori said:**
> I have tested this on dapper and seem alot more easier and clean. Instead of patch the kernel you just build a module for your actual kernel.

sudo apt-get install linux-headers-`uname -r` module-assistant

sudo module-assistant prepare
sudo module-assistant get ppscsi
sudo module-assistant unpack ppscsi
sudo module-assistant build ppscsi
sudo module-assistant install ppscsi

And all done, now you only have to do "sudo modprobe epst" before run xsane, sane or gimp plugin or anything :P

If i find how to auto the last step i will edit this post.

This should be valid too for any printer wich uses paraller port and has its own scsi interface, i guess.

NOTE: be sure before run "module-assistant get ppscis" that there is no any package manager runing.
(all the sources will be installed in /usr/src)

Thanks a lot! This worked like a charm! Finally!!! :D

---

### Post by DW5 on 2006-10-26
I am trying to get this to run in edgy.  I have a Scanjet 5100C and I'm trying to get it to work with my HP nx9010.

When I run 

```
sudo module-assistant build ppscsi
```

I get the following in the module assistant log file:

```
...
dh_clean -k                                                                
dh_installdirs -pppscsi-drivers-2.6.17-10-386
lib/modules/2.6.17-10-386/ppscsi  
make KERNEL_DIR=/lib/modules/2.6.17-10-386/build                           
make[2]: Entering directory `/usr/src/modules/ppscsi'                      
make modules -C /lib/modules/2.6.17-10-386/build                           
SUBDIRS=/usr/src/modules/ppscsi                               
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'         
CC [M]  /usr/src/modules/ppscsi/ppscsi.o         
CC [M]  /usr/src/modules/ppscsi/onscsi.o          
In file included from /usr/src/modules/ppscsi/onscsi.c:13:                 
/usr/src/modules/ppscsi/ppscsi.h:325: error: expected ‘)’ before string constant
/usr/src/modules/ppscsi/ppscsi.h:326: error: expected ‘)’ before string constant  
usr/src/modules/ppscsi/ppscsi.h:327: error: expected ‘)’ before string constant
/usr/src/modules/ppscsi/ppscsi.h:328: error: expected ‘)’ before string constant
/usr/src/modules/ppscsi/ppscsi.h:329: error: expected ‘)’ before string constant
make[4]: *** [/usr/src/modules/ppscsi/onscsi.o] Error 1
make[3]: *** [_module_/usr/src/modules/ppscsi] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ppscsi' 
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ppscsi'
make: *** [kdist_build] Error 2 
^Y

```

Any ideas on how to proceed. I'd like to get this scanner going. 

DW

---

### Post by Garyu on 2006-10-26
@DW5:

This is a long shot, and you probably don't want to do it, but you might try installing Dapper, making the scanner work (since it does work in Dapper) and then dist-upgrade to Edgy... A lot of work though. :rolleyes: 

I have never even seen Edgy Eft installed, so I can't say anything about how it works there, but if you really want the scanner to work, maybe you should just settle for Dapper until Edgy is a bit more developed... It is a beta release after all.

---

### Post by sputnik on 2006-11-06
I tried this on dapper and it worked fine.  I have since upgraded to edgy and it stopped working.  I tried running it again on Edgy, still no joy and identical messages to those above.

It appears to have been noticed in Debian [http://permalink.gmane.org/gmane.linux.debian.devel.bugs.general/129090](http://permalink.gmane.org/gmane.linux.debian.devel.bugs.general/129090) back in August.

It has been reported as an Ubuntu issue

[https://launchpad.net/distros/ubuntu/+source/ppscsi/+bug/69023](https://launchpad.net/distros/ubuntu/+source/ppscsi/+bug/69023)

Is it a module_parm problem (since those are the lines with the offending problems)?  
MODULE_PARM(host0,"1-8i");
MODULE_PARM(host1,"1-8i");
MODULE_PARM(host2,"1-8i");
MODULE_PARM(host3,"1-8i");
MODULE_PARM(verbose,"i");


Does it affect other modules? Is it anything to do with deprecation of module_parm for module_param that I have read elsewhere?

---

### Post by gciarami on 2006-12-05
I've decided to switch to Ubuntu and I'm in the process of getting everything migrated over from my XP machine.  So far, I've figured out the dual monitors, wireless card.. even got sound working.. but having trouble with my old Microtek ScanMaker v310.

I followed the steps listed using the module-assistant and came across an error when building.

 &#9474; /usr/src/modules/ppscsi/ppscsi.h:325: error: expected ‘)’ before string 
 &#9474; constant                                                                

After doing some research, I discovered that MODULE_PARM is deprecated and found the code to fix it (listed in the bug).  I wanted to keep using module-assistant, so I performed the following annoying tasks.

cd /usr/src
bunzip2 ppscsi.bz2
tar xvf ppscsi.tar
cd modules/ppscsi

EDIT ppscsi.h... 
starting at line 325, replace the following lines in /usr/src/modules/ppscsi/ppscsi.h

-MODULE_PARM(host0,"1-8i");
-MODULE_PARM(host1,"1-8i");
-MODULE_PARM(host2,"1-8i");
-MODULE_PARM(host3,"1-8i");
-MODULE_PARM(verbose,"i");

+module_param_array(host0, int, NULL, 0);
+module_param_array(host1, int, NULL, 0);
+module_param_array(host2, int, NULL, 0);
+module_param_array(host3, int, NULL, 0);
+module_param(verbose, int, 0);

DONE EDIT

tar cvf ppscsi.tar modules
bzip2 ppscsi.tar

now repeat the module-assistant steps, starting with the "unpack" line.

I now have ppscsi installed and was able to pull up XSANE image scanner.  Although now I have to figure out why I'm getting I/O errors.. but at least I heard the scanner do something and am headed in the right direction!

Thanks for all your help.

---

### Post by gciarami on 2006-12-06
The above was for Edgy.

Also, turns out my scanner would start to scan, then just power off, unless I specify a low resolution (50~75 for color/gray scans, 175 or so for line art)

---

### Post by Garyu on 2007-02-25
> **minisori said:**
> I have tested this on dapper and seem alot more easier and clean. Instead of patch the kernel you just build a module for your actual kernel.

sudo apt-get install linux-headers-`uname -r` module-assistant

sudo module-assistant prepare
sudo module-assistant get ppscsi
sudo module-assistant unpack ppscsi
sudo module-assistant build ppscsi
sudo module-assistant install ppscsi

And all done, now you only have to do "sudo modprobe epst" before run xsane, sane or gimp plugin or anything :P

If i find how to auto the last step i will edit this post.

This should be valid too for any printer wich uses paraller port and has its own scsi interface, i guess.

NOTE: be sure before run "module-assistant get ppscis" that there is no any package manager runing.
(all the sources will be installed in /usr/src)

Well, the title of this thread should be changed, because this procedure works excellent with Dapper at least. But what about auto-loading the "sudo modprobe epst" on boot?

---

### Post by hyperq on 2007-03-07
> **Garyu said:**
> Well, the title of this thread should be changed, because this procedure works excellent with Dapper at least. But what about auto-loading the "sudo modprobe epst" on boot?

How about appending "epst" as a new line at the end of the file /etc/modules ?  Will this work?

---

### Post by hyperq on 2007-03-07
> **hyperq said:**
> How about appending "epst" as a new line at the end of the file /etc/modules ?  Will this work?

Yup, I tested it, and it works.

---

### Post by bguebert on 2007-04-12
I tried this in Feisty and it could build the module, here is the log:

[HTML]<code>dh_clean
rm -f *.o *.ko
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ppscsi'
dh_clean
rm -f *.o *.ko
for templ in /usr/src/modules/ppscsi/debian/ppscsi-drivers-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.20-14-386/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.20-14-386/g ;s/#KVERS#/2.6.20-14-386/g ; s/_KVERS_/2.6.20-14-386/g ; s/##KDREV##/2.6.20-14.22/g ; s/#KDREV#/2.6.20-14.22/g ; s/_KDREV_/2.6.20-14.22/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs -pppscsi-drivers-2.6.20-14-386 lib/modules/2.6.20-14-386/ppscsi
make KERNEL_DIR=/lib/modules/2.6.20-14-386/build
make[2]: Entering directory `/usr/src/modules/ppscsi'
make modules -C /lib/modules/2.6.20-14-386/build SUBDIRS=/usr/src/modules/ppscsi
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-14-386'
  CC [M]  /usr/src/modules/ppscsi/ppscsi.o
In file included from /usr/src/modules/ppscsi/ppscsi.c:55:
/usr/src/modules/ppscsi/ppscsi.h:16:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/ppscsi/ppscsi.h:22,
                 from /usr/src/modules/ppscsi/ppscsi.c:55:
/usr/src/modules/ppscsi/scsi.h:23:31: error: scsi/scsi_request.h: No such file or directory
In file included from /usr/src/modules/ppscsi/ppscsi.h:22,
                 from /usr/src/modules/ppscsi/ppscsi.c:55:
/usr/src/modules/ppscsi/scsi.h:56: warning: ‘struct scsi_request’ declared inside parameter list
/usr/src/modules/ppscsi/scsi.h:56: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/modules/ppscsi/ppscsi.c:1147:39: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/usr/src/modules/ppscsi/ppscsi.c: In function ‘ppsc_detect’:
/usr/src/modules/ppscsi/ppscsi.c:1147: error: ‘INIT_WORK’ undeclared (first use in this function)
/usr/src/modules/ppscsi/ppscsi.c:1147: error: (Each undeclared identifier is reported only once
/usr/src/modules/ppscsi/ppscsi.c:1147: error: for each function it appears in.)
make[4]: *** [/usr/src/modules/ppscsi/ppscsi.o] Error 1
make[3]: *** [_module_/usr/src/modules/ppscsi] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-14-386'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ppscsi'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ppscsi'
make: *** [kdist_build] Error 2</code>[/HTML]

I guess I'll wait and try again after it is officially released, but maybe someoe can point out something I am screwing up.  Thanks.

---

### Post by Calabresi on 2008-08-19
Greet,

I received the same error as above, can some one help please, G Ubuntu Hardy

Used this sequency, exactly as it is:

> sudo apt-get install linux-headers-`uname -r` module-assistant
sudo module-assistant prepare
sudo module-assistant get ppscsi
sudo module-assistant unpack ppscsi
sudo module-assistant build ppscsi
sudo module-assistant install ppscsi

Thanks,

---

### Post by sputnik on 2008-08-31
Try this thread [here]("http://ubuntuforums.org/showthread.php?t=782242") ([http://ubuntuforums.org/showthread.php?t=782242](http://ubuntuforums.org/showthread.php?t=782242)) which covers some of this topic.  It seems there are some further updates/patches to the code required.

---

### Post by Calabresi on 2008-08-31
Thanks, will follow and search for a sollution

---

