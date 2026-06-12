---
title: "will not boot ubuntu 12.4"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by vegas89 on 2012-10-30
I am running ubuntu 12.4. When I power up my computer it will freeze at the purple screen with the ububtu logo. The dots under logo do not turn from white to red, screen is just froze, so I do a forced shut down by holding in the power button till it shuts down, I then wait a few minuets  then power back up holding the f7 key. I toggle down to the recovery mode, then I choose the repair broken packages and at that point it starts reading the cache and at the end it will say it could not resolve archive.liniux.duke.edu and also it could not resolve archive.canonical.com. then I hit enter and the desktop boots up.   Is there a code script I could do to repair this issiue or is there a way I can retrieve the information that someone could look at to help fix this problem.  I just did a unity --reset and these are the factors now in the terminal    vegas@vegas-desktop:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2600163

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:1807): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xc0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-10-30 17:21:11 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1dd5850

WARN  2012-10-30 17:21:11 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x1dd5850
WARN  2012-10-30 17:21:11 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1dd5850

WARN  2012-10-30 17:21:11 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window39846243
WARN  2012-10-30 17:21:11 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
Initializing addhelper options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing extrawm options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
ERROR 2012-10-30 17:21:11 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
OS Determining best projection for type int (size:  4 ) signed
OS Projected as a regular number
OS Determining best projection for type unsigned_int (size:  4 ) unsigned
OS Projected as a regular number
OS Determining best projection for type long (size:  8 ) signed
OS Projected as a large signed integer
OS Determining best projection for type int (size:  4 ) signed
OS Projected as a regular number
OS Determining best projection for type int (size:  4 ) signed
OS Projected as a regular number
OS Determining best projection for type off_t (size:  8 ) signed
OS Projected as a large signed integer
OS Determining best projection for type size_t (size:  8 ) unsigned
OS Projected as a large unsigned integer
OS Determining best projection for type ssize_t (size:  8 ) signed
OS Projected as a large signed integer
OS Unix Could not open libc libsystem.B.dylib
OS Unix dirent is: ctypes.StructType("dirent", [{ "padding_0": ctypes.uint8_t.array(18) }, { "d_type": ctypes.uint8_t }, { "d_name": ctypes.char.array(261) }])
OS Attempting to declare FFI  access
OS Function access declared
OS Attempting to declare FFI  chdir
OS Function chdir declared
OS Attempting to declare FFI  chmod
OS Function chmod declared
OS Attempting to declare FFI  chown
OS Function chown declared
OS Attempting to declare FFI  copyfile
OS Could not declare function copyfile Error: couldn't find function symbol in library
OS Attempting to declare FFI  dup
OS Function dup declared
OS Attempting to declare FFI  chdir
OS Function chdir declared
OS Attempting to declare FFI  fchdir
OS Function fchdir declared
OS Attempting to declare FFI  fchown
OS Function fchown declared
OS Attempting to declare FFI  fsync
OS Function fsync declared
OS Attempting to declare FFI  getcwd
OS Function getcwd declared
OS Attempting to declare FFI  getwd
OS Function getwd declared
OS Attempting to declare FFI  get_current_dir_name
OS Function get_current_dir_name declared
OS Attempting to declare FFI  getwd
OS Function getwd declared
OS Attempting to declare FFI  fdatasync
OS Function fdatasync declared
OS Attempting to declare FFI  ftruncate
OS Function ftruncate declared
OS Attempting to declare FFI  lchown
OS Function lchown declared
OS Attempting to declare FFI  link
OS Function link declared
OS Attempting to declare FFI  lseek
OS Function lseek declared
OS Attempting to declare FFI  mkdir
OS Function mkdir declared
OS Attempting to declare FFI  mkstemp
OS Function mkstemp declared
OS Attempting to declare FFI  open
OS Function open declared
OS Attempting to declare FFI  opendir
OS Function opendir declared
OS Attempting to declare FFI  pread
OS Function pread declared
OS Attempting to declare FFI  pwrite
OS Function pwrite declared
OS Attempting to declare FFI  read
OS Function read declared
OS Attempting to declare FFI  readdir
OS Function readdir declared
OS Attempting to declare FFI  rename
OS Function rename declared
OS Attempting to declare FFI  rmdir
OS Function rmdir declared
OS Attempting to declare FFI  splice
OS Function splice declared
OS Attempting to declare FFI  strerror
OS Function strerror declared
OS Attempting to declare FFI  symlink
OS Function symlink declared
OS Attempting to declare FFI  truncate
OS Function truncate declared
OS Attempting to declare FFI  unlink
OS Function unlink declared
OS Attempting to declare FFI  write
OS Function write declared
OS Attempting to declare FFI  pipe
OS Function pipe declared
NOTE: child process received `Goodbye', closing down

---

### Post by shreepads on 2012-10-31
What graphics card (and general other system specs esp networking details)

---

### Post by vegas89 on 2012-10-31
Lets try this I went to systems settings and have better information  Memory 3.8 GiB Processor Intel® Pentium(R) CPU G630 @ 2.70GHz × 2  Graphics VESA: Intel® Sandybridge/Ivybridge Graphics OS type 64-bit Disk  980.4 GB Western Digital SATA 7200 I hope this information helps you  help me8-[

---

### Post by NikTh on 2012-10-31
Hi , 
is this a fresh Ubuntu install , is from new install or upgrade from older release ? 

and when this problem occurred ? after an update or a program installation or suddenly ? 

You know , the complete freeze of the screen maybe is not a good sign. I suspect an HDD fault but nothing is for sure if we not test it. 

Can you boot from a LiveCD-USB ? 

Thanks

---

### Post by vegas89 on 2012-10-31
Thanks for the reply, Okay, I have a ubuntu 12.4 install dvd that I have used to install this version. I just did another install using the same dvd and put it side by side on this computer. The new version boots just fine, no problems. However when I toggle down to this version and go to boot, same problem with the freeze and then I go back and do the recovery as I explained previously, so I don't believe it is a hardware issue but something in the code line script that just needs to be altered , perhaps. I am trying not to have to do a complete reinstall on the other OS because I have this one just as I need it to be! If there is a code script that I can put in the terminal that will pull up any information you may need, please let me know  ](*,)

---

### Post by NikTh on 2012-11-01
So probably is not a hardware issue , but if we don't know what code you changed or what you did (generally) we cannot help to undo. 
For further debugging you can see the dmesg messages and Xorg messages. The locations are /var/log/dmesg  and /var/log/Xorg.0.log and you can gain the info with a liveCD if you mount the root partition. 
Example.

Boot from LiveCD and "Try Ubuntu" , then open a terminal and give this command
```
sudo fdisk -l
``` it will list all partitions of the drive and you will see where Ubuntu is. 
We assume now that Ubuntu is in /dev/sda2 , then you do
```
sudo mount /dev/sda2 /mnt
``` 
and gain the info like this
```
cat /mnt/var/log/dmesg > dmesg.txt
cat /mnt/var/log/Xorg.0.log > xorg.txt
```
```
gedit dmesg.txt
gedit xorg.txt
```

You can copy-paste the results in here , **but do not forget** to put the results between the brackets **[noparse]```
here
```[/noparse]** because are lot of lines. 
Eventually someone will translate the messages and tell you where is the mistake.

Thanks

---

### Post by vegas89 on 2012-11-01
Thanks Nikth, I will save this info for future reference. I believe I will just reinstall a new version of the 12.4 to this hard drive and choose to erase the entire drive along with the corrupted  version. Then I am going to install another version of the 12.4 to use as a version to try out new apps and different set ups, keeping the first one as a good working OS. I believe my original problem came about when I was trying to install Remastersys and messed up something in the synaptic package manager. AS always I am learning new things about this Linux OS system and I am sure I will see more of your post, as you seem dedicated to helping others. Once again I appreciate your help. I have gained valuable information by reading other post and perhaps in the future I will be able to offer assistance to someone else.

---

### Post by NikTh on 2012-11-02
> **vegas89 said:**
> .....in the future I will be able to offer assistance to someone else.

That's the spirit of the community 
:)

Glad you solved it , even with the re-install. 

A suggestion (for the future) would be to install VirtualBox and you can test there anything you want without corrupt your actual system. 
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

