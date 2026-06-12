---
title: "[SOLVED] can't log into ubuntu"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by brucegriffin on 2008-08-04
I downloaded the 8.04.1 ubuntu to disk and am able to get to the ubuntu log in page but when I type my user name in and password it just goes to a blank orange page and then back to type in user name. If I click on options then it lets me select session and if I use failsafe gnome session then it logs me in failsafe gnome mode. I am able to get here using that session but why can't I log into ubuntu from the start. I am new to ubuntu so TYVM for any help you can provide me with.

---

### Post by limasierra on 2008-08-04
You can try log in as root and create another account.

---

### Post by leomelo on 2008-08-04
Check the graphic chard,its driver and its configuration in /etc/X11/xorg,conf

---

### Post by brucegriffin on 2008-08-04
I'm new to this can you elaborate on how to log into the root to create a new account, thanks again.

---

### Post by brucegriffin on 2008-08-04
I'm new to this can you tell me what I need to do to check the graphics card, thanks again.

---

### Post by limasierra on 2008-08-04
Log in using failsafe gnome mode. If you're an administrator type "gksu users-admin" on terminal. Add a user, for example "brucegriffin". Now, check if the user you created has a home directory: type "nautilus /home" on terminal and see if that folder contains another one with exactly the same name as the user you created. Try to log in as that user and if it didn't do the trick post again otherwise add [Solved] at the beginning of this post.

---

### Post by limasierra on 2008-08-04
Another one to you to try.
Log in on your account and type "sudo apt-get update". You must have an internet connection.

---

### Post by brucegriffin on 2008-08-04
I typed in gksuusers-admin it tells me bad command and just goes to next cursor still have same problem ty. Also wanted to let you know, I'm not sure if I am an administrator or not. I am the only one that uses this computer is there something in ubuntu I need to do to make me an administrator. Also, wanted to let you know I typed in nautilus /home and only see one there "bruce" and I do have an internet connection.

---

### Post by brucegriffin on 2008-08-04
I typed in sudo apt-get update in terminal and it did seem to do some updating but when I shut down and logged back in, I still had to do it in fail safe mode still would'nt let me log directly into ubuntu. Also, to let you know I do have an internet connection.

---

### Post by cariboo on 2008-08-04
When entering user names and passwords in Linux they are case sensitive. If you don't enter them exactly the way you entered them during installation you will be rejected. If this still doesn't work, boot up in recovery mode, at the menu drop to root shell and at the prompt type:

```
useradd -m <username> -p <password>
```

Where <username> is your username and <password> is your password.

This command will also add a new home directory for the user you just created.

Jim

---

### Post by brucegriffin on 2008-08-04
jim, as i said earlier here I am new but I typed in as you said and it said bruce already exists should I type in at the prompt a new user name and password creating a new one and then try to log in to ubuntu.

---

### Post by brucegriffin on 2008-08-04
Still have not resolved this issue any help would be appreciated. tyvm!

---

### Post by limasierra on 2008-08-05
Another: log in your account and run this command on terminal, without the quotes: "sudo dpkg-reconfigure xserver-xorg".
You will be asked several question, and you must read the texts with attention to answer them.
Tip: to navigate trough the buttons you can use tab or your mouse's middle button.

---

### Post by brucegriffin on 2008-08-05
I did as you suggested and had no problem following the prompts but it did not solve the problem. When I type in my name and password to log into ubuntu it seems to accept it and goes to another orange page then goes black back to orange and then prompts me again for a user name. I use options and use gnome failsafe mode and then put in my name and password and I get in. TYVM for all your help, looking forward to solving this issue.

---

### Post by cariboo on 2008-08-05
Did you try a new user?

JIm

---

### Post by brucegriffin on 2008-08-05
Jim, I'm not sure how to get into recovery mode. I did try using failsafe gnome and failsafe terminal mode and in gnome failsafe mode at terminal, I typed in useradd -m username password and hit enter key, I also did the same in failsafe terminal and restarted but neither way did it accept a new user name and password which I had given it. In failsafe terminal mode after typing in as you said and hitting enter key it then brings up a bunch of codes, I'm not sure if I need to type in any of the codes for it to take. I did type in nautilus /home at terminal and it only has the one user bruce. Not sure what I am doing wrong to create a new user. I appreciate all your help TYVM.

---

### Post by limasierra on 2008-08-05
To get into recovery mode you must restart and select the recovery mode option when menu grub starts.

---

### Post by howlingmadhowie on 2008-08-05
your main user obviously exists. if the password was wrong, if login window would have told you that immediately.

i don't think you need recovery mode. this sounds like a problem starting gnome. the question is, why does gnome only start in recovery mode? which version of ubuntu did you install?

the configuration of the graphical user interface for each user is in their directory in /home. they are all hidden files, so you won't see them in nautilus (the file viewer) unless you switch "show hidden files" on. to get gnome to reinitialize these files (which is probably worth a shot), delete all the files which start with a '.' when you activate "show hidden files" in nautilus. that may help.

so summing up:
log in to the failsafe gnome.
click at the top on "places"=>"my home folder" (or whatever it is in english)
click on "view"=>"show hidden files"
select and delete all files and folders which start with a "."
log-out and try to log-in in standard mode.

---

### Post by brucegriffin on 2008-08-05
Jim, I was able to get in recovery mode and dropped down to root and when I did I typed in useradd -m username password and when I clicked enter alot of commands came up and was not sure how to use them so I exited and came back on. The new user I typed in is there, in nautilus /home but it doesn't have the folders bruce does, seems like it is incomplete.    Under that name and password it won't let me come in at all, says problem with user name or password not even in failsafe mode. TY again for your help.

---

### Post by brucegriffin on 2008-08-05
Howling, I did as you suggested deleting all items with a '.' they all deleted except it would not allow me to delete .gvfs I restarted and still had to come in gnome failsafe mode. I went back in and viewed my folder all "." were recreated. TYVM for your help.

---

### Post by howlingmadhowie on 2008-08-07
a bit of a long shot, but can you paste the contents of /var/log/Xorg.0.log

---

### Post by brucegriffin on 2008-08-07
I tried typing /var/log/Xorg.0.log in terminal and at the root it tells me both places permission denied. I assume the 0 between Xorg.0.log is the number zero. I don't know if this is the answer but I am the only one on this computer and would have thought I would be the administrator. Is there some step I missed when installing Ubuntu. Thank You very much for the help.

---

### Post by howlingmadhowie on 2008-08-08
> **brucegriffin said:**
> I tried typing /var/log/Xorg.0.log in terminal and at the root it tells me both places permission denied. I assume the 0 between Xorg.0.log is the number zero. I don't know if this is the answer but I am the only one on this computer and would have thought I would be the administrator. Is there some step I missed when installing Ubuntu. Thank You very much for the help.

probably best to start gnome in failsafe mode and navigate to /var/log using the file browser.

(btw, /var/log/Xorg.0.log is the name of the file. to see the file in the terminal you have to open it using the right program, like:

cat /var/log/Xorg.0.log

or probably better for you:

gedit /var/log/Xorg.0.log

you get the permission denied message because the file isn't a program but a standard text document and the first word in a shell command is (usually) the name of a program so the shell is trying to start it as a program and being told by the file system that /var/log/Xorg.0.log can't be executed)

---

### Post by brucegriffin on 2008-08-08
I don't see any EE errors but do see some ww's which I will post here, hope it helps. It wouldn't let me post the whole log here, said I had to many images, so I am posting a little before each ww and a little after. Thanks for all your help.(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 21
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x1fff1c00 is: 0x1fff1c00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x21ff2000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff1c00 0x1fff1c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0x21ff2000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen biles/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "UseFBDev" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 262 x 196
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg" Everything else seems to be II, ==, **

---

### Post by brucegriffin on 2008-08-08
I don't see any EE errors but do see some ww's which I will post here, hope it helps. It wouldn't let me post the whole log here, said I had to many images, so I am posting a little before each ww and a little after. Thanks for all your help.(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 21
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x1fff1c00 is: 0x1fff1c00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x21ff2000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff1c00 0x1fff1c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0x21ff2000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen biles/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "UseFBDev" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 262 x 196
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg" Everything else seems to be II, ==, **

---

### Post by dim333 on 2008-08-08
are you sure y typed in the right username and password? Try to create a new user.:)

---

### Post by howlingmadhowie on 2008-08-09
i don't like this line at all. is your screen really this big?


(II) RADEON(0): Setting screen physical size to 262 x 196

---

### Post by brucegriffin on 2008-08-09
My screen resolution says 1024 x 768, I also redownloaded ubuntu from another location, I still can only log in using the failsafe mode. The hard drive I am downloading to, used to have windows xp pro on it, It is a 60 gb hard drive and I have 512 mb of ram installed. I did drive scrub it before downloading ubuntu to it. In xp pro it was a ntfs partition, I assumed drive scrubbing it and then downloading ubuntu to it, ubuntu would download whatever partition it required. Where in here can I check what type of partition it is using now ntfs, fat? Thanks for everyones help.

---

### Post by howlingmadhowie on 2008-08-09
to find out your partition types, try:

sudo fdisk -l

however, that won't be the problem. i wonder why it isn't working. gdm starts fine and then gnome refuses to start. the first thing i think of is an applet problem. 

the annoying thing about your problem is that something is going wrong right at the last stage. if the partitions were wrong you'd never have got this far.

hang on, i've just had an idea.

the failsafe surface doesn't use compositing (compiz and effects), while standard gnome does.  so the question is, how can you tell standard gnome to use metacity as a window manager and not compiz...

let me see what i can find...

------------------------------------

okay, i've found something. 
in
$HOME/.gconf/desktop/gnome/applications/window_manager/%gconf.xml try changing compiz to metacity

---

### Post by brucegriffin on 2008-08-09
I am new here and if I have to install compiz or metacity I know I haven't. I did type in just what you suggested at terminal and it says permission denied. I restarted and then hit esc to take me to where I can type in at the root and when I typed in there as you suggested here is the result:
checking for xgl: xuinfo: unable to open display not present
xset: unable to open display ''''
xset q doesn't reveal the location of the log file
using fallback /var/log/Xorg.0.log
detected pci id for vga: 01:05.0 0300: 1002:5954 (prog-if 00 [vga controller])
checking for texture_from_pixmap: not present
trying again with index rendering:
checking texture_from_pixmap: not present
aborting and using fallback /usr/bin/metacity
windows manager error: unable to open x display
also when I type in metacity the result is:
unable to open x display
Thanks again for the time you are spending to help me with this problem.

---

### Post by howlingmadhowie on 2008-08-10
what exactly did you type in the terminal?

i would suggest starting gnome in failsafe mode and then opening the file browser, navigating to 
.gconf/desktop/gnome/applications/window_manager/%gconf.xml 
(you will have to show hidden files to see .gconf) and then editing the file in a text editor (right click and open with-> text editor). then in this file change the word 'compiz' to 'metacity' (don't worry, it should already be installed) and then save the file and log out. then try to log back in but not using failsafe.

---

### Post by brucegriffin on 2008-08-10
Solved: First of all to answer your question as to what I had typed in terminal before $HOME/.gconf/desktop/gnome/applications/window_manager/%gconf.xml the result was 
bash: /home/bruce/.gconf/desktop/gnome/applications/window_manager/%gconf.xml:
permission denied

You finally solved my dilemma with your last suggestion which I can't Thank You enough for. I was beginning to think that maybe I needed to ask to be sent a disk believing the download wasn't working. Thanks again for your persistence in staying with me on this issue. I am going to type in here just how I did what you last suggested and it worked.
I first signed in on the failsafe terminal mode.
Once there I clicked on the places tab at the top and then the home folder, once there I clicked on the view tab and clicked on show hidden files.
There I opened the .gconf there I opened the desktop folder, then opened the gnome folder, then I opened the applications folder, then I opened the window_manager folder, then I right clicked the %gconf.xml and I clicked on open with text editor which opened it and there were two lines which had compiz in them, I changed both to metacity and then saved it, backed out of everything and restarted and have since ben able to sign directly in. I am sure there is alot more here I need to understand and will try to find the answers in the how to use ubuntu but when I can't find the answer I will come back to the forums and just to thank you once again Howlingmadhowie for your persistence in helping me through this.

---

### Post by brucegriffin on 2008-08-13
Solved

---

### Post by nickgaydos on 2008-08-13
> **brucegriffin said:**
> Solved
That's a good thing :-)

---

