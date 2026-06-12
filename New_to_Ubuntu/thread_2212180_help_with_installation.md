---
title: "help with installation"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by snifer2 on 2014-03-19
im trying install sdk android but nothing when i type android i get nothing

**2.2 Download the Android SDK**
Get the Android SDK at [URL]http://dl.google.com/android/android-sdk_r21.0.1-linux.tgz
Unzip the contents to your root directory (home). Contents should be located @ /home/patcher/android-sdk-linux

Till here is fine after I cant.....
can u help me with deitails how to to next step?

Ok, now edit the .bashrc file in your root directory (home), change the PATH environment variable to: export PATH=~/android-sdk-linux/platform-tools:~/android-sdk-linux/tools:$PATH

Now apply the changes you've made to the PATH environment variable:
[LIST=1]
[*].~/.bashrc
[/LIST]

Copy the Code
2.3 Install the Android SDK

Launch the Android SDK Manager:
[LIST=1]
[*]android
[/LIST]

Copy the Code
After the installation is finished you'll see following window:

---

### Post by codingman on 2014-03-19
What guide are you following? Is it [this]("https://help.ubuntu.com/community/AndroidSDK") guide?

---

### Post by snifer2 on 2014-03-20
yes is for develoing rom for android phone

---

### Post by codingman on 2014-03-20
That guide should give you a detailed explanation, but if you are having issues, please be clear on what the matter is so we can help you.

---

### Post by snifer2 on 2014-03-20
[COLOR=#444444][FONT=Microsoft YaHei]I'm wanna practice a bit for edit rom for android over linux, I'm following a guide but i guess not very detail ...
the guide is

[/FONT][/COLOR]http://en.miui.com/thread-9630-1-1.html
[COLOR=#444444][FONT=Microsoft YaHei]


so im following the guide to porting rom ... im arrive till this point ...[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]"For the device I'm using, the output display is: [/FONT][/COLOR]

[COLOR=#444444][FONT=Microsoft YaHei]Bus 002 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]Bus 001 Device 098:ID 04e8:685e Samsung Electronics Co.,Ltd[/FONT][/COLOR]

[COLOR=#444444][FONT=Microsoft YaHei]Now copy the corresponding "04e8:685e" number (this contains the vendor id and product id). If you're not sure which line is your phone, then run the $ lsusb before connecting your device[/FONT][/COLOR]

[COLOR=#444444][FONT=Microsoft YaHei]  2. Under the directory "/etc/udev/rules.d"[/FONT][/COLOR][COLOR=#666666][FONT=Microsoft YaHei]
[LIST]
[*]mkdir 99-android.rules
[/LIST]

[color=rgb(51, 102, 153) !important]Copy the Code[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]then make the following edits: SUBSYSTEMS=”usb”, ATTRS{idVendor}=”04e8”,ATTRS{idProduct}=”685e”,[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]MODE=”0666” , OWNER=”current_user”[/FONT][/COLOR]

[COLOR=#444444][FONT=Microsoft YaHei]  3. In terminal run:[/FONT][/COLOR][COLOR=#666666][FONT=Microsoft YaHei]
[LIST]
[*]sudo restart udev
[/LIST]

[color=rgb(51, 102, 153) !important]Copy the Code[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]Then reconnect your device. [/FONT][/COLOR]

[COLOR=#444444][FONT=Microsoft YaHei]3. Sync MIUI code[/FONT][/COLOR]

[COLOR=#444444][FONT=Microsoft YaHei]Under your root directory (home)  make a new file:[/FONT][/COLOR][COLOR=#666666][FONT=Microsoft YaHei]
[LIST]
[*]mkdir patchrom
[/LIST]

[color=rgb(51, 102, 153) !important]Copy the Code[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]Install repo[/FONT][/COLOR][COLOR=#666666][FONT=Microsoft YaHei]
[LIST]
[*]mkdir ~/bin
[*]vim ~/.bashrc
[*]set PATH=~/bin:$PATH
[/LIST]

[color=rgb(51, 102, 153) !important]Copy the Code[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]Ok, switch to your patchrom directory (cd patchrom)..."[/FONT][/COLOR]

[COLOR=#444444][FONT=Microsoft YaHei]Question i got my product and vendor id[/FONT][/COLOR]

[COLOR=#444444][FONT=Microsoft YaHei]i dont understand what i must to do later...[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]mkdir? not touch file?[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]where i need to put the SUBSYSTEMS=”usb”, ATTRS{idV.....[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]after that... how install repo?? please write me details description .. im really stucked[/FONT][/COLOR]

---

### Post by mörgæs on 2014-03-20
Please stop multiposting.
Threads merged.

---

### Post by codingman on 2014-03-20
Why don't you follow this: [https://help.ubuntu.com/community/AndroidSDK](https://help.ubuntu.com/community/AndroidSDK)

---

### Post by snifer2 on 2014-03-20
[COLOR=#444444][FONT=Microsoft YaHei]I read link you posted.. thank u
but u think this i must do it? or simply open 51.android.rule?



2. Under the directory "/etc/udev/rules.d"[/FONT][/COLOR][COLOR=#666666][FONT=Microsoft YaHei]
[LIST=1]
[*]mkdir 99-android.rules
[/LIST]

[COLOR=#336699 !important]Copy the Code[/COLOR][/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]then make the following edits: SUBSYSTEMS=”usb”, ATTRS{idVendor}=”04e8”,ATTRS{idProduct}=”685e”,[/FONT][/COLOR]
[COLOR=#444444][FONT=Microsoft YaHei]MODE=”0666” , OWNER=”current_user”



[/FONT][/COLOR]

---

### Post by snifer2 on 2014-03-31
this is my make file
# The original zip file, MUST be specified by each product
local-zip-file := stockrom.zip
# The output zip file of MIUI rom, the default is porting_miui.zip if not specified
local-out-zip-file := MIUI_IOCEAN.zip
local-miui-modified-apps :=
# All apps from original ZIP, but has smali files chanded
local-modified-apps :=
# All apks from MIUI
local-miui-removed-apps :=
# All apps need to be removed from original ZIP file
local-phone-apps :=
# To include the local targets before and after zip the final ZIP file,
# and the local-targets should:
# (1) be defined after including porting.mk if using any global variable(see porting.mk)
# (2) the name should be leaded with local- to prevent any conflict with global targets
local-pre-zip := local-zip-misc
# The local targets after the zip file is generated, could include 'zip2sd' to
# deliver the zip file to phone, or to customize other actions
include $(PORT_BUILD)/porting.mk
local-zip-misc:
local-test:
 echo "an example action"



and this is what terminal give me

root@ubuntu:~/MIUI# make workspace
Makefile:22: *** missing separator.  Stop

any ideas?

---

### Post by steeldriver on 2014-03-31
Action lines in your makefile need to be indented using tabs

```

local-test:
[COLOR=#0000ff]TAB-->[/COLOR]echo "an example action"

```

---

