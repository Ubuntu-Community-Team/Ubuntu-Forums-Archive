---
title: "HOWTO: Grub Menu Kernel Display Options"
date: 2008-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by drs305 on 2008-06-04
EDIT: I highly recommend using [Grub Customizer]("http://ubuntuforums.org/showthread.php?t=1664134") rather than StartUp Manager if you are using Grub 2. StartUp Manager was designed for Grub legacy and incorporated some support for Grub 2. Grub Customizer was designed after the introduction of Grub 2 and supports many more of its features and is still being actively developed.

[SIZE=2]In a hurry and just want to know how to limit the number of displayed kernels or want to know why the new kernel isn't running? Go the the red stars![/SIZE] [COLOR=Red][SIZE=4]**[/SIZE][/COLOR]

[COLOR=NAVY]**[SIZE=3]Using GRUB 1.99?[/SIZE]**[/COLOR]
Grub 1.99 radically changes how additional/older kernels are displayed. There is now a new "Submenu" feature where all but the most recent kernel (and recovery mode, if enabled) reside. This will prevent the main Grub menu from expanding as new kernels are introduced. The portions of this guide which detail how to physically remove kernels still applies, but for information about the new Submenu feature, please visit this thread:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")

[COLOR=NAVY]**[SIZE=3]*StartUp-Manager Issues with GRUB 2:*[/SIZE]**[/COLOR]
StartUp-Manager has not been updated since July 2010. Therefore, it has not kept up with advances in Grub 2, especially Grub 2 version 1.99 and later.

StartUp-Manager ver 1.9.12-1 works with GRUB 2, however some of the options available with Grub Legacy have not yet been incorporated to work with Grub 2. The Boot Options tab remains essentially unchanged. The Appearance and Advanced tabs contain fewer entries at present, and the Security tab does not exist with Grub 2 fully-installed.

Menu Resolution/Font Size. While StartUp-Manager can set the menu resolution, it does so by rewriting the /etc/grub.d/00_header script. Once changed, this file remains in it's altered form even if StartUp-Manager is uninstalled or another Grub 2 application such as Grub Customizer it used.
[LIST]
[*] If StartUp-Manager was used to set the resolution and the user wishes to set the resolution via another method or application, the 00_header file should be restored to its original form. This can be accomplished by either purging/reinstalling Grub 2 or changing set gfxmode=<some user-defined value> back to the original set gfxmode=${GRUB_GFXMODE}
[/LIST]

StartUp-Manager ver 1.9.12-1 will work with GRUB 2, however some of the options available with Grub legacy have not yet been incorporated to work with Grub 2. The *Boot Options* tab remains essentially unchanged. The *Appearance* and *Advanced* tabs contain fewer entries at present, and the *Security* tab does not exist with Grub 2 fully-installed. There are reports that a StartUp-Manager 2 is under development which will work with Grub 2. When it is released this page will be updated. 

**[COLOR=DarkRed]GRUB 2 items available for change with StartUp Manager will be annotated with a [/COLOR][COLOR=DarkGreen][SIZE=4]*[/SIZE] green asterisk[/COLOR]**.

Currently the following StartUp-Manager options work:
[LIST]
[*][COLOR=DarkGreen][SIZE=4]*[/SIZE][/COLOR] Timeout
[*][COLOR=DarkGreen][SIZE=4]*[/SIZE][/COLOR] Default OS/kernel
[*][COLOR=DarkGreen][SIZE=4]*[/SIZE][/COLOR] Misc. (Writes to the "GRUB_CMDLINE_LINUX=" line of /etc/default/grub but will not remove the same entries such as "splash" and "quiet" already entered on "GRUB_CMDLINE_LINUX_DEFAULT=")
[LIST]
[*] Show text during boot
[/LIST]
 
[*][COLOR=DarkGreen][SIZE=4]*[/SIZE][/COLOR] Display resolution - Placed on "GRUB_CMDLINE_LINUX_DEFAULT=" line of /etc/default/grub. During boot GRUB 2 will note that the "vga=" option is deprecated.
[/LIST]


[COLOR=MAROON]**[SIZE=4]*StartUp-Manager and Editing Grub Legacy's menu.lst or GRUB 2's /etc/default/grub - Intro:*[/SIZE]**[/COLOR]
With each kernel update, the grub menu is usually updated to reflect the new change.[SIZE=4][COLOR=DarkRed]*[/COLOR][/SIZE] This creates questions by new users on exactly what happened and how to change the display. By default, the old kernel versions are kept on the menu and the new kernel is added at the top. Over time, this list of kernels can grow quite long. Here are 5 methods to change the menu. The first two are the only methods I recommend unless there are extenuating circumstances. [COLOR=MAROON]Most users will only need the information in section 1 to make the desired changes to the grub menu display.[/COLOR]
[SIZE=4][COLOR=DarkRed]*[/COLOR][/SIZE] [B][COLOR=DarkRed]Run "[COLOR=Navy]sudo update-grub[/COLOR]" to ensure you are working with the most up-to-date grub information.
[/COLOR][/B]
**Before modifying your menu, it is good practice to make a backup copy.** If you intend to make multiple changes within a short time, I'd recommend assigning each backup a unique number (menu.lst.bak1, bak2, etc). To make a backup:
For Grub:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak1 
```For Grub 2:
```
sudo cp /etc/default/grub /etc/default/grub.bak1 
```[B][COLOR=Navy][SIZE=3]

1. StartUp-Manager[/SIZE][/COLOR] [/B]
The introduction of StartUp-Manager created an easy and safe method to update the grub menu list via a GUI interface. You can make a variety of changes to the appearance and function of the grub menu without ever directly editing the file. 
StartUp-Manager is accessed via [COLOR=MAROON]System > Administration > StartUp-Manager[/COLOR]. If it is not in your menu, install it via synaptic ( [COLOR=MAROON] System > Administration > Synaptic Package Manager[/COLOR]. StartUp-Manager is in the 'universe' repository. If you don't see 'startupmanager' listed in synaptic or the command line method doesn't find it, go to Synaptic's Settings > Repositories > Ubuntu Software and make sure the (universe) repository is checked. Hit the 'Reload' button to refresh the package list and then select *startupmanager* or install it simply with:

```
sudo aptitude install startupmanager 
```To start it, [COLOR=MAROON] System > Administration > StartUp-Manager[/COLOR] or in terminal type: **gksu startupmanager**

[COLOR=MAROON]***Boot Options***[/COLOR]
[LIST]
[*]**[COLOR=DarkGreen]* [/COLOR]*****Timeout***. Select how long you see the menu before the default is automatically selected and started.
[*]**[COLOR=DarkGreen]* [/COLOR]*****Default operating system***. Set the default operating system, including different kernels and any other OS if installed. Although you can select another OS or version of linux, you will be unable to set up specific boot options (such as kernel version) for them. Changing internal boot options within another operating system requires manual editing of menu.lst.
[*]***Show bootloader menu***. If not selected, no menu will be seen. The default or saved OS will be selected.
[*]**[COLOR=DarkGreen]* [/COLOR]*****Show text during boot***. This option presents some textual information to allow you to see what is happening during boot.
*If you want a clean-looking boot with no text scrolling, untick "Show text during boot" and tick "Show boot splash"*. Even cleaner, you can untick "Show bootloader menu" but this option is better left visible.
[/LIST]

[COLOR=MAROON]**[COLOR=DarkGreen]* [/COLOR]*****Appearance***[/COLOR]
Note: With Grub 2, only the *Usplash theme* option is available for change.
This tab presents many options on how the grub menu is presented, including colors, grub background image,themes. These apply only to the grub bootloader screens. Eye candy.

[COLOR=MAROON]***Security***[/COLOR]
Note: Not yet available in Grub 2.
Set passwords to prevent grub changes without authorization. Passwords can be set to require a password to change the bootloader, rescue mode and old boot options.

[COLOR=MAROON]***Advanced***[/COLOR] 
Note: Grub 2 options include only the ability to make a floppy or to change the bootloader resolution.
[LIST]
[*]***Limit the number of kernels to keep***. [COLOR=Red][SIZE=4]**[/SIZE][/COLOR] This is the option to set the number of kernels you see on the boot menu. Choosing "2" is a good compromise, as it allows you to use and see the current kernel plus have the previous kernel version immediately available via the grub menu should you have problems with the new kernel.

Here are some important points about this option:
[LIST]
[*]The grub menu is updated as soon as you close StartUp-Manager.
[*]No kernels are removed from the computer - only the displayed menu items change. No extra space is freed by *hiding* the kernel entries.
[*]You can change the number more than once, and even go from a smaller to larger number.   StartUp-Manager checks the number of installed kernels and will display that number up to the maximum number installed on the computer. If you select a number greater than that installed, it will display all those kernels currently installed and the menu will continue to grow until the number of kernels selected is met. *If you removed kernel options by manually deleting items in menu.lst you may not be able to restore them by increasing the number here.*
[/LIST]
 
[*]***Create boot option for memtest86+***. When's the last time you used this? But the option is here if you want it.
[*]***Create boot option for recovery mode***. An important option to allow you to select *Recovery mode* if you have problems with the kernel and need to perform maintenance on your kernel.
[*]***Automatically update default boot option.***. [COLOR=Red][SIZE=4]**[/SIZE][/COLOR]
[LIST]
[*]If selected, grub's setting is: "# updatedefaultentry=true"; if unticked, value is changed to "# updatedefaultentry=false"
[*]**If unchecked, new kernels *will not be used until you make changes to grub, approve the change during installation, or manually edit grub*.** To start using a new kernel, make the change in the "*Default operating system*" in the [COLOR=MAROON]***Boot Options***[/COLOR] tab.
[/LIST]
 
[*]***Create Rescue Floppy***.  Okay, so many of us don't have floppy drives any longer. If your computer does - lucky you. If your's doesn't, you can still make a rescue floppy image, install it in the grub folder, and use it for an emergency boot backup. The instructions on how to do this are found here: [GrubHowto/BootFloppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy")
[/LIST]

***[COLOR=NAVY][SIZE=3]The bottom line for StartUp-Manager - it's convenient, prevents editing errors, and is fully reversible.[/SIZE][/COLOR]***

[CENTER]----------------------------------------------------------------[/CENTER]

**[COLOR=MAROON][SIZE=4]Manually Editing /boot/grub/menu.lst (Grub Legacy only) -- If You Must ...[/SIZE][/COLOR]**
Note: Grub 2 does not use /boot/grub/menu.lst for it's options. The Grub 2 files include /boot/grub/grub.cfg, /etc/default/grub, and the configuration scripts in the /etc/grub.d/ folder. Changes should not be made to /boot/grub/grub.cfg.

*Again, make sure you have made a backup.* This is especially important if you manually edit menu.lst as there is no internal protection using this method other than to restore a backup copy previously saved on your computer. Before manually editing menu.lst, if you are having grub problems and are not seeing something you expect, such as a new kernel not being displayed, you might try running this command to see if your problem can be resolved:
```
sudo update-grub
```***Comment Symbol (#) Note:**** When editing the grub menu.lst:*
There are many comment (#) symbols in menu.lst. They can be a bit confusing in that the double comment symbols (##) are not really comments at all but mark a special section of the file. Do not uncomment  (remove the # symbols) items in this section, just change the values if necessary.

To edit /boot/grub/menu.lst, make a backup and then run the following. Change the editor if you prefer another text editor:
```
gksu **gedit** /boot/grub/menu.lst
```[B][COLOR=Navy][SIZE=3]

2. Change the 'howmany=all' line.[/SIZE][/COLOR][/B]

There is a line in menu.lst which designates how many kernels (and recovery options) to view by default. This is the same value as in the StartUp-Manager "number of kernels to keep".  The default menu.lst is:

```
# howmany=all 
```Do not remove the comment symbol - just change the value; 2 is what many users choose. 

```
# howmany=2 
```This setting will take effect on the next boot (and reflected in StartUp-Manager upon save). The kernel entries are completely removed from the menu but would be restored should you increase the 'howmany' number. It will display up to the number of kernels installed on your computer. If fewer kernels exist, new kernels will expand the menu options until the number is reached. Changes to this option will take effect on reboot or, interestingly, immediately if you open and close StartUp-Manager.

**Caution: The menu options displayed in boot are automatically created. They should not normally be edited manually. The options presented below require manual editing of menu.lst** .From my testing, it appears that StartUp-Manager cannot restore menu items manually deleted in menu.lst. Kernels are not physically removed from the computer. 

If you feel like you must edit this file manually (such as a new kernel simply doesn't show up after installation/reinstallation), the next section details how to change the menu list view by manually editing and/or deleting items near the bottom of the menu.lst file.

**Note to GRUB 2 Users:** You can edit */etc/grub.d/10_linux* to automatically display only the two most current system kernels. The extra kernels will remain on the computer but not be displayed. Instructions are in Section 1. B. of [Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602").

**[COLOR=Navy][SIZE=3]3. Comment the Menu Items You Don't Want to See.[/SIZE][/COLOR] **
Near the bottom of the file are the kernel, recovery and memtest options you see on boot. You can hide any of these items by placing a comment  symbol ( # ) at the start of the line. Any commented line will not be displayed. Comment out each line in the section. To redisplay the line, remove the comment symbol.
In the following example, **the first kernel and recovery option** will be visible; the second will not.

```

[B]
title        Ubuntu 8.04, kernel 2.6.24-18-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro splash
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro single
initrd        /boot/initrd.img-2.6.24-18-generic
[/B]

# title        Ubuntu 8.04, kernel 2.6.24-17-generic
# root        (hd1,0)
# kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro splash
# initrd        /boot/initrd.img-2.6.24-17-generic
# quiet

# title        Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
# root        (hd1,0)
# kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro single
# initrd        /boot/initrd.img-2.6.24-17-generic

```

**[COLOR=Navy][SIZE=3]4. Remove (or add) the items.[/SIZE] [/COLOR]**
You can simply delete the kernels you don't want to see on boot. If you remove them, you can restore them by retyping them or restoring your backup file. You may be able to restore deleted kernel options by changing the value in StartUp-Manager but I would not count on it.

**[COLOR=Navy][SIZE=3]Other Editable Items.[/SIZE][/COLOR]**
While you are manually editing the kernels, note this file contains entries you may edit concerning how long the menu is displayed in seconds ( timeout 3 ). You can also set which system to boot. The default is 0 . 0 is the first uncommented title. Count the number of uncommented "titles", including recovery modes and memtest86+, and subtract 1. In addition to a number, this value may also be "saved", meaning that grub will start the next time using the same system booted during the current session. This is eqivalent to the "last used" option available in StartUp-Manager.

```
timeout 10
``````
default 0
```
[COLOR=MAROON][B][SIZE=4]
Removing Older Kernels:[/SIZE][/B][/COLOR]
You can permanently delete older kernels via synaptic.
First, determine which kernel you are using. You do not want to remove this kernel. To find which kernel you are using:
```

uname -r

```Open Synaptic via System > Administration > Synaptic. Search for *linux-image*. You will see all the available kernels - those with green selection boxes are currently installed. They will look something like *linux-image-2.6.27-XX* or *linux-image-2.6.27-XX-generic*. The older kernels will have **lower** ending numbers. You can also remove the associated ***linux-headers...*** and ***linux-restricted-modules**-...* for the earlier versions. An easy way to find all these files is to type the main kernel version (2.6.XX) into the top search bar. *Many users keep at least one older kernel in case problems occur with the most recent kernel.*

When you delete a an older (or newer) kernel via synaptic the kernel is removed from the computer and more disk space is freed up. The menu.lst is updated and the deleted kernel will no longer be displayed on the menu. Make sure you are satisfied with the performance of newly-released kernels before deleting older ones. Note: The associated linux-header will not automatically be removed when the linux-image is removed. The linux-header for the specific kernel must be removed separately.

**[COLOR="DarkRed"]A Very Easy Alternate GUI Method - Ubuntu-Tweak[/COLOR]**
Another GUI third-party app which can easily remove older kernels is Ubuntu Tweak. It is independent of Grub and will work with Grub legacy and Grub 2. It performs a variety of common Ubuntu tasks, one of which is to remove older kernels. This app *removes* older kernels, unlike StartUp-Manager, which merely removes them from the menu.

To install Ubuntu-Tweak, which is not in the normal respositories, go to the Ubuntu-Tweak site, [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/"), click on the "Download" button.

To run Ubuntu-Tweak:
```

ubuntu-tweak

```
[list]
[*]Select "Package Cleaner" on the left and ""Clean Kernel" from the right panel.
[*]Press the "Unlock" button at the lower right, enter your password.
[*]Select from the displayed list the kernel images and headers you wish to remove. The kernel in use is *not* listed.
[*]Press the "Cleanup" button at the lower right to remove the selected kernel images and headers.  
[/list]
Update Grub to refresh the menu:
```

sudo update-grub

```


[COLOR=MAROON]**[SIZE=4]Summary:[/SIZE]**[/COLOR]
You can change the number of kernels displayed via the StartUp-Manager or by editing grub's menu.lst  StartUp-Manager makes the process simple, fast and more or less error-proof (did I actually say that?). Deleted kernel options can be restored via either method as long as the actual kernels remain installed on the computer. Even though I have used ubuntu only a few years, I am as big a fan of the command line as most long-time users - in this case there are just too many advantages to using StartUp-Manager.

[COLOR=MAROON]***Other Possibly Useful Grub-Related Links:***[/COLOR]
[ Recovering Ubuntu after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")
[How to restore Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")
[Cannot boot windows without external hard drive plugged in]("http://ubuntuforums.org/showthread.php?p=3995006")
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")
[Super Grub Disk]("http://www.supergrubdisk.org/")

[StartUp-Manager Wiki]("https://help.ubuntu.com/community/StartUpManager") Based on this post.

---

### Post by Seisen on 2008-06-04
You should have the mods move this the howto section of the forums, very nice howto.

---

### Post by kpkeerthi on 2008-06-04
If you want completely uninstall the kernels that you no longer need:
1. Open System -> Admin -> Synaptic
2. Search for **linux-image**
3. Select the kernels you no longer need and Mark for complete removal. Click Apply.

**Your GRUB menu will be automatically updated.**

---

### Post by drs305 on 2008-06-04
> **kpkeerthi said:**
> If you want completely uninstall the kernels that you no longer need:
1. Open System -> Admin -> Synaptic
2. Search for **linux-image**
3. Select the kernels you no longer need and Mark for complete removal. Click Apply.

**Your GRUB menu will be automatically updated.**

kpkeerthi,
when i started this it was originally titled 5 ways to update the kernel display. i got to four, couldn't remember what the fifth one was and decided to write *at least 4* ways ...  ;-)  i'll update the post to reflect this option. thanks for pointing this out!

---

### Post by kaibob on 2008-06-04
> **drs305 said:**
> <snip>You can permanently delete older kernels via synaptic.  System > Administration > Synaptic. Search for *linux-image*. You will see the older kernels - those in green are currently installed.<snip>

Thanks for the howto--it's well written and very helpful.

I did a clean install of Ubuntu Hardy, and both the installed and older linux images are shown in black text. I checked and that is how it's set up in the color tab of Synaptic preferences. I may have made this change, but I don't recall doing it. 

There used to be (and may still be) a problem when utilizing Synaptic to uninstall older versions of the linux modules. The following thread is a current example:

[http://ubuntuforums.org/showthread.php?t=817852](http://ubuntuforums.org/showthread.php?t=817852)

I don't know if this is an ongoing problem, but I thought I might mention it. One fix as shown in the thread is to create an empty directory. Someone suggested that this problem can be avoided by uninstalling the Linxu modules first.

Thanks again.

---

### Post by Biggy on 2008-06-04
> **kpkeerthi said:**
> If you want completely uninstall the kernels that you no longer need:
1. Open System -> Admin -> Synaptic
2. Search for **linux-image**
3. Select the kernels you no longer need and Mark for complete removal. Click Apply.

**Your GRUB menu will be automatically updated.**

Thank you kpkeerthi !

---

### Post by Paddy Landau on 2008-06-04
I wish I'd seen this "how to" earlier. Well written.

You may want to mention that you can install startupmanager from Synaptic Package Manager (much easier for those -- like me -- who don't like using command lines).

I have a small question. It's not important, but I am curious:

After installing Ubuntu, I installed and used startupmanager easily and successfully.

Interestingly, my Vista system doesn't see Ubuntu (it did when I experimented with WUBI). Thus, I can't change the bootup options from Windows whether with msconfig or [EasyBCD]("http://neosmart.net/dl.php?id=1").

It's not a problem, because I can do it from startupmanager in Ubuntu. I'm just curious as to why this is?

---

### Post by drs305 on 2008-06-04
> **Paddy Landau said:**
> I wish I'd seen this "how to" earlier. Well written.

You may want to mention that you can install startupmanager from Synaptic Package Manager (much easier for those -- like me -- who don't like using command lines).

I have a small question. It's not important, but I am curious:

After installing Ubuntu, I installed and used startupmanager easily and successfully.

Interestingly, my Vista system doesn't see Ubuntu (it did when I experimented with WUBI). Thus, I can't change the bootup options from Windows whether with msconfig or [EasyBCD]("http://neosmart.net/dl.php?id=1").

It's not a problem, because I can do it from startupmanager in Ubuntu. I'm just curious as to why this is?

I'll note the synaptic option for installation, thanks.

I don't have windows on my main machine. I imagine windows worked with wubi because the linux system was actually within the windows system. I don't know if you can get windows to see the boot menu where it is. It's possible your boot menu is now on the ubuntu partition and not in the MBR. You can do a search on these forums - I've seen it discussed at length but didn't pay particular attention ;-)

---

### Post by Sef on 2008-06-05
> You should have the mods move this the howto section of the forums, very nice howto.

So moved.

---

### Post by meierfra. on 2008-06-06
```
cat /boot/grub/menu.lst | grep "title" | grep -v "#\|recovery\|memtest"
sudo grub-set-default <number>
```

I suggest to  remove  "grep -v "#\|recovery\|memtest".  One needs  to count all titles, including memtest and recovery.

Also "grub-set-default" will only have an effect  if one uses "default saved"

---

### Post by drs305 on 2008-06-06
> **meierfra. said:**
> ```
cat /boot/grub/menu.lst | grep "title" | grep -v "#\|recovery\|memtest"
sudo grub-set-default <number>
```

I suggest to  remove  "grep -v "#\|recovery\|memtest".  One needs  to count all titles, including memtest and recovery.

Also "grub-set-default" will only have an effect  if one uses "default saved"


Thanks, you are correct and I'll fix the search line. I experimented with the grub-set-default and achieved mixed results. Given the vagaries of using CLI for updating this, and how few people would probably ever use it and need guidance, I've decided to just remove that section. ;-)

---

### Post by u18b on 2008-06-06
Thank you.

This is just the info I needed.

Not only did I need to trim kernel entries (and thus the safe way was good)...


but I wanted to actually edit the Grub menu because I dual boot to Vista.  And Ubuntu describes it as 
Windows Vista (Longhorn) loader

Since I have a laptop, I also have a recovery partition.  Thus I have still another Grub entry that reads the same!
Windows Vista (Longhorn) loader

So NOW, thanks to your help, my menu reads:

Windows Vista
Windows Vista RECOVERY


Thank you for this great explanation.

I'm a newbie.  And it is work like this that makes switching to Linux more bearable.
:popcorn:

---

### Post by VMC on 2008-06-08
This how-to enabled me to finally get a splash screen. I have a limited integrated video, and I keep getting that "you have passed undocumented video mode". I have never been able to get beyond 640x480 before.

Startup Manager took care of that! Wow. Now I boot up using my full 1024x768 and, I see a boot up splash screen along with the orange ribbon. The text that follows is very clear. Before they were huge and wriped around several lines.
Also it appears to boot faster.

What's nice about Startup Manager is that it takes care of backing up grub automatically. Great program.

The How-to guide is top notch!

Thanks you.

---

### Post by the_good_senator on 2008-07-29
> **u18b said:**
> Thank you.

This is just the info I needed.

Not only did I need to trim kernel entries (and thus the safe way was good)...


but I wanted to actually edit the Grub menu because I dual boot to Vista.  And Ubuntu describes it as 
Windows Vista (Longhorn) loader

This is what I came here to ask about. GRUB lists too many options on boot, and some of those entries are ambiguous. I wanted to make it error-proof in case someone else tried to boot up my machine (family, gf, whatever) and accidentally try to boot into the recovery partition.

---

### Post by drs305 on 2008-07-29
> **the_good_senator said:**
> This is what I came here to ask about. GRUB lists too many options on boot, and some of those entries are ambiguous. I wanted to make it error-proof in case someone else tried to boot up my machine (family, gf, whatever) and accidentally try to boot into the recovery partition.

Did you find the answers to your questions from the tutorial?

The number of kernels displayed is controlled by the "Limit the number of kernels displayed" in the Advanced section. You can reduce it to one or two. A better option is to remove them from the system via synaptic but SUM can at least hide them until you remove them completely.

The ability to see or hide the 'Recovery Mode' option is contained in the 'Create boot option for recovery mode'. If not selected you won't see it.

The timeout setting can be used so novice users wouldn't even see the menu should you choose to do that. If you don't select a timeout remember that if you have problems you can access the menu by hitting ESC during boot.

---

### Post by Nabanna on 2008-10-03
Thanks.....

really a very good HOW-TO....

i am new to Ubuntu(and Linux) and i always wanted to increase time-out without messing up with menu.lst, this HOW-TO helped me a lot...and showed me to use a safer method by using 'start-up manager' instead.....

---

### Post by raynedanser on 2008-10-15
> **kpkeerthi said:**
> If you want completely uninstall the kernels that you no longer need:
1. Open System -> Admin -> Synaptic
2. Search for **linux-image**
3. Select the kernels you no longer need and Mark for complete removal. Click Apply.

**Your GRUB menu will be automatically updated.**

How do you know which kernels are no longer needed, though?

---

### Post by drs305 on 2008-10-15
raynedanser, 

Run this to see which kernel you are using:
```
uname -r
```

You can safely remove any other kernel on your machine. However, most users recommend keeping one previous kernel that worked for you in case you develop problems. 

For example, if you run the command and get the result: 
2.6.24-21-generic

The previous kernel was: 2.6.24-19-generic.

Keep -19 for at least a while. Go to synaptic and look at the listings for linux-image-2.6.24-*

If you see you still have linux-image-2.6.24-18-generic and linux-image-2.6.24-16-generic installed, you could safely remove them. By removing them from your computer via synaptic, grub's menu list would be altered automatically as well if these kernels were displayed on your boot menu.

---

### Post by von Stalhein on 2009-02-13
Tahnks for the tute.

If startupmanager won't start though - what is the workaround/fix?

Mine still finds GRUB2, and I think that's what borks it, as there is no grub.cfg file - see below

```
gksu startupmanager
/home/stephen/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
/usr/share/startupmanager/gtk_frontend.py:159: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated  self.glade_xml = gtk.glade.XML(GLADE_FILE, None ,APP_NAME)
kSpinButton: setting an adjustment with non-zero page size is deprecatedSearching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: /boot/grub/splash.xpm.gz
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-10-generic
Found kernel: /boot/vmlinuz-2.6.27-8-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub2 detected
Usplash detected
Splashy not detected
File /boot/grub/grub.cfg does not exist.

```

TIA

---

### Post by drs305 on 2009-02-13
Grub2 is supposed to be supported since SUM version 1.9, according to it's creator. I haven't used Grub2 so I don't have the .cfg file either. I notice it also mentions a "*default*, which also doesn't exist in my grub folder. It appears to have found a /boot/grub/menu.lst  You could try adding a comment or two on the title line of menu.lst and rebooting to see if the added comment is displayed during boot.

If that is the case, there is always manual editing of /boot/grub/menu.lst  if startupmanager won't run. If you post your menu.lst and tell us what you want to do someone here will certainly be able to help if you aren't sure how to go about it.

---

### Post by von Stalhein on 2009-02-13
Thanks for the quick reply.

I managed to get it up by renaming a backed up copy of menu.lst to grub.cfg.

However, I don't have any options in the default operating systems box.

I was originally doing some maintenance, and was going to use it to delete some old kernels from the list - I got sidetracked trying to solve why it wouldn't work.

I can edit menu.lst manually, but it is definitely easier and safer if the startupmanager is a goer.

---

### Post by listerdl on 2009-02-15
Hi, does anyone reading this have a suggestion to remove what seems to be a duplicating process when i login to ubtunu.

Basically after the ubuntu logo with the status bar completing its length, I am then told blow by blow what is happening to the laptop and the OS?

This does seem to be an issue with the grum menu and kernel display?

---

### Post by von Stalhein on 2009-02-16
I think it's a matter of editing the "ro quiet" dialogue in the GRUB menu.lst to remove the "quiet" parameter.

Back up the file before you do this.  :)

More info [here]("http://ubuntuforums.org/showthread.php?t=511382")

---

### Post by TonyChaos on 2009-10-22
Fantastic How-To. Was just what I was looking for!

---

### Post by Nathan.Flow on 2009-11-02
> **Paddy Landau said:**
> I wish I'd seen this "how to" earlier. Well written.

You may want to mention that you can install startupmanager from Synaptic Package Manager (much easier for those -- like me -- who don't like using command lines).

I have a small question. It's not important, but I am curious:

After installing Ubuntu, I installed and used startupmanager easily and successfully.

Interestingly, my Vista system doesn't see Ubuntu (it did when I experimented with WUBI). Thus, I can't change the bootup options from Windows whether with msconfig or [EasyBCD]("http://neosmart.net/dl.php?id=1").

It's not a problem, because I can do it from startupmanager in Ubuntu. I'm just curious as to why this is?

To get windows to recognize your Linux partitions, you need to install a driver, depending on what file system you used EXT2, EXT3 or EXT4. Take a look at [HTML]http://www.fs-driver.org/[/HTML] this file only works with EXT2. I'm not sure if their has been updates to the file for EXT3, or EXT4. I remember a file like this that allowed reading/writing EXT3 don't remember the name tho.
 
Side note, doing this can cause problems, if you reboot windows because of what ever reason(BSOD). It will not safely unmount those partitions we all know what that means. It will cause increased fragmentation, at least this is what I experienced while using this method.
Good luck

---

### Post by Paddy Landau on 2009-11-02
> **Nathan.Flow said:**
> To get windows to recognize your Linux partitions, you need to install a driver ...
[Ext2Fsd]("http://www.ext2fsd.com/") supports ext2 and ext3.

As far as I know, no Windows driver exists for ext4.

---

### Post by rogue_0111 on 2010-03-10
Thanks for this. Great job.

---

### Post by cb5online on 2010-06-15
Agreed. Very helpful. Thanks!

---

### Post by Vector721 on 2011-03-19
Kudos to drs305!  Many thanks for the great tutorial!  It should become part of the howto, like Seisen said! :D

---

### Post by drs305 on 2011-03-19
Vector721,

Thanks for the kind words. Even though I still maintain this thread there is a new GUI app for Grub 2 that is very comprehensive. It's called Grub Customizer.

I wrote a guide for it as well, linked in my signature line. If StartUp-Manager isn't able to do what you want in Grub 2, Grub Customizer probably can.

---

### Post by gesaugen on 2011-04-24
I'm trying to hide bootloader menu, so I've found [this tutorial]("https://help.ubuntu.com/community/StartUpManager") that speaks about  "Start-Up" manager which should have exactly what I'm looking for, the **Show bootloader menu **option. But in my case, I don't have that option, theres only** Show boot splash** and **Show text during boot**

I'm running U10.10, freshly installed. How to fix this?

---

### Post by drs305 on 2011-04-24
Startup Manager isn't as good at working with Grub 2. You could try to hide the menu by editing the /etc/default/grub file. The instructions are in the following link. At the bottom of Section 1 there is a paragraph about hiding the menu.

[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

If that doesn't work, it's possible the 'recordfail' check isn't working. If the above doesn't work, let me know if the menu is still displaying but has a counter and eventually boots, or if there is no countdown and you always have to press ENTER to get the computer to boot.

I'm about to leave on a few weeks vacation and won't be on the forums as often as normal. I'll be checking in from time to time and will see your post - it might just take a day or two.

---

### Post by gesaugen on 2011-04-24
drs305, thanks for repy!
I've tryed to configure Grub 2 as described on that link you gave me, but it didn't work:
I've remowed # before the GRUB_HIDDEN_TIMEOUT and set the same time for both TIMEOUT sections (3 sec). Then I've saved the change and updated the menu via "sudo update-grub" but after a restart, the only change was that menu was lasting 3 seconds, but visible...

Someone mentioned before that if I have dual boot (in my case win7 and ubuntu10.10) then I can't hide the bootloader menu just with GRUB_HIDDEN_TIMEOUT, but that I would have to use somekind of a script (but which one and how to use it wasn't mentioned)

---

### Post by drs305 on 2011-04-24
> **gesaugen said:**
> 
I've remowed # before the GRUB_HIDDEN_TIMEOUT and set the same time for both TIMEOUT sections (3 sec). 

That should set a blank screen for 3 seconds, then the menu should display for 3 seconds and automatically boot.

So if you want Grub to just boot without seeing the menu, change GRUB_TIMEOUT=0 and it should boot immediately after 3 seconds of blank screen.

---

### Post by gesaugen on 2011-04-25
> **drs305 said:**
> That should set a blank screen for 3 seconds, then the menu should display for 3 seconds and automatically boot.

So if you want Grub to just boot without seeing the menu, change GRUB_TIMEOUT=0 and it should boot immediately after 3 seconds of blank screen.
I've set GRUB_TIMEOUT=0 and GRUB_HIDDEN_TIMEOUT=10 - it didn't work! The menu was visible
NOTICE: I have multiOS dual boot (win7 & ubuntu 10.10) - as I've read in your tutorials, hidden menu with multiOS system requires a bit more of adjustment...

So I've tried to add commands from [yours tutorial:]("http://ubuntuforums.org/showthread.php?t=1287602")

> **drs305 said:**
> 
[SIZE=3]**11. [COLOR=DarkRed]HIDING THE MENU ON MULTI-OS SYSTEMS[/COLOR]**[/SIZE]
By design, Grub 2 allows hiding the menu only on single-OS systems. This is established in the */etc/grub.d/30_os-prober*  file. For users with multiple OS's on their machines, hiding the menu  can be accomplished by altering the scripts. There are two ways to  accomplish the task. The first edits only one file and eliminates a  conditional; the second edits two files and adds a conditional, but is a  bit more 'elegant'.

Shown are the applicable sections. Changes are highlighted in [COLOR=Red]**bold red**[/COLOR]. The lines between the altered lines have been omitted.**Method 1.** Remove a conditional from */etc/grub.d/30_os-prober*.
For both Grub 1.97~beta (Karmic) and 1.98 (Lucid & later), the first  line to edit is the same. It appears at approximately line 25-30 of */etc/grub.d/30_os-prober* in both versions.
> [COLOR=Red]**# **[/COLOR] if [ "x${found_other_os}" = "x" ] ; then                      The second change is to place a **[COLOR=DarkRed]#[/COLOR]** symbol at the end of the conditional. There are many *if* statements, and it's important to find the correct nested *fi*. 

Lucid & later (Grub 1.98+):
     Quote:
[QUOTE]**[COLOR=DarkRed]#[/COLOR]**
  fi
}

adjust_timeout () {[/QUOTE]

result is that now menu IS hidden BUT I can't call it via SHIFT or ESC key :confused:

UPDATE EDIT:
1. I've reinstalled ubuntu because I haven't make backup files of grub.cfg and 30_os-prober files
2. I wiser now so I've made backup files :)
3. Now I've decided to use method #2 from your tutorial:
> **drs305 said:**
> 
**Method 2.** Add a conditional.
This procedure modifies both */etc/grub.d/30_os-prober* and */etc/default/grub*. Open both with:
gksu gedit /etc/default/grub /etc/grub.d/30_os-prober
Add this line to */etc/default/grub*:
> [B][COLOR=DarkRed]GRUB_FORCE_HIDDEN_MENU="true"
export GRUB_FORCE_HIDDEN_MENU[/COLOR][/B]Change this line in */etc/grub.d/30_os-prober*, approximately line 25-30, 
From this:
[QUOTE]if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; thenTo this:
                                                        > if [ "x${found_other_os}" = "x" ] || [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then                      [/QUOTE]

Also_ I've set the default OS for loading to be Ubuntu_ - and it worked: the bootloader menu wasn't showing up and I could call it by holding down left SHIFT key after BIOS load up. Also hidden loading took about 10 sec, so I can conclude that that works...
BUT!
When I've changed in the grub that the default OS to load will be Win7, then the set up broke down! - holding shift resulted with command showing "GRUB loading" but then windows started to load normaly like theres no bootmenu at all!
So as I can figure it out, the problem is in windows OS loader which doesn't respond for hidden timeout function. 
help?

---

### Post by drs305 on 2011-04-25
I'll take a look at it at the hotel this evening. The Grub 1.98 scripts have been modified quite a bit and perhaps it's affected my workaround.

If I understand your post, you now have Windows as the default but you can't interrupt the boot and display the menu using SHIFT?  If you haven't been able to get back into Ubuntu, try pressing the ESC key repeatedly during boot.

---

### Post by gesaugen on 2011-04-25
> **drs305 said:**
> If I understand your post, you now have Windows as the default but you can't interrupt the boot and display the menu using SHIFT?  If you haven't been able to get back into Ubuntu, try pressing the ESC key repeatedly during boot.
yes, that's exactly what is the problem!
ann I've tryed to press ESC key but that reboots the PC in both cases (when default os is ubuntu and also with windows)

---

### Post by drs305 on 2011-04-25
Assuming you still cannot boot Ubuntu normally, try accessing Ubuntu in one of these ways.

First, a second or two after your BIOS screen blanks (if you have one), CTRL-ALT-DEL twice to recycle the boot (or cycle the power off, although that's not generally a nice way to treat the computer). This may disrupt Grub, in which case it may start with a 'recordfail' marker the next time and display the menu. Boot into Ubuntu.

If you don't want to disrupt power during boot (understandable) boot the LiveCD and mount your Ubuntu partition. For this post, I'll assume it's sda5. 

We will put the 'keystatus' check in /etc/grub.d/40_custom so it is always incorporated into the menu regardless of what OSs Grub finds.

```

sudo mount /dev/sda[COLOR="DarkRed"]5[/COLOR] /mnt
gksu gedit /mnt/etc/default/grub /mnt/boot/grub/grub.cfg /mnt/etc/grub.d/40_custom
```

In /etc/default/grub:  
> GRUB_HIDDEN_TIMEOUT=5  # Just to give you a chance to stop the boot
GRUB_HIDDEN_TIMEOUT_QUIET=false # This is supposed to provide a countdown timer, but it's currently broken in G2. But try it anyway in case it's fixed.


In /mnt/boot/grub/grub.cfg, add this to the bottom so it's there for the next boot:
> 
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi


Copy the same thing to /mnt/etc/grub.d/40_custom. Add it below the existing lines to ensure the keystatus check is performed.

Save all the files, reboot (without the CD). If things work, "sudo update-grub". The 40_custom file should be executable by default, and after you run the update the keystatus check code should still be near the bottom of the grub.cfg file. (After updating, it will be in the 40_custom section of grub.cfg. If it isn't, check to make sure /etc/grub.d/40_custom is an executable file).

---

### Post by charliemagiera on 2011-04-26
I wanted to say many thanks to you for this wonderful tutorial.  I applied the knowledge applied therein, and my machine works a lot better now.  

Thank you again.

---

### Post by drs305 on 2011-04-26
charliemagiera,

Welcome to the Ubuntu Forums. :-)

Glad you enjoyed this thread. There is a lot of useful information throughout these forums.

Just for the record, the tips in this thread may keep the menu more manageable but shouldn't noticeably affect the actual performance of the system. But mind over matter can be just as important.

Happy Ubuntu-ing !

---

### Post by charliemagiera on 2011-04-26
Thank you for the greeting.

The truth of the matter is, my machine is an older one, and I enjoy Ubuntu very much.  I have searched the forum threads previously, and only recently realized how invaluable the information is. I'm trying to "tweak" both Ubuntu and my machine to maximize my enjoyment.

As I said previously, mine is an older machine. It has only a single core processor, so almost anything makes it seem to run faster.

---

### Post by gesaugen on 2011-04-29
> **drs305 said:**
> Save all the files, reboot (without the CD). If things work, "sudo update-grub". The 40_custom file should be executable by default, and after you run the update the keystatus check code should still be near the bottom of the grub.cfg file. (After updating, it will be in the 40_custom section of grub.cfg. If it isn't, check to make sure /etc/grub.d/40_custom is an executable file).
sorry for no feedback, I was struck by food poisoning...

here are the results:
After running a live CD, I've mounted a partition and copy everything as you described. Nothing changed / still if I press shift, it says "GRUB loading" and then continues to load into the windows
BUT there's another problem now: first time I've copy all the lines and didn't call the "sudo update-grub" command. After restart nothing happened. So I've booted again with live CD and looked just in case if the lines were there - they were. So then I've tried the  "sudo update-grub" command and I get this error: " /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)."
I've tried a numerous times and it keeps popping...

As I understand, the grub must be updated via sudo update-grub command or all the changes in grub.cfg won't be executed?

---

### Post by Paddy Landau on 2011-04-29
> **charliemagiera said:**
> ... mine is an older machine.
You may find your older machine will run faster if you use [Lubuntu]("http://lubuntu.net/"), designed for low-end machines.

---

### Post by drs305 on 2011-04-29
> **gesaugen said:**
> So I've booted again with live CD and looked just in case if the lines were there - they were. So then I've tried the  "sudo update-grub" command and I get this error: " /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)."
I've tried a numerous times and it keeps popping...

As I understand, the grub must be updated via sudo update-grub command or all the changes in grub.cfg won't be executed?

When you are running the LiveCD you can't simply run "sudo update-grub". The reason is that the command is going to try to update the active OS, which is the LiveCD. In order to update your real OS's files, you would have to 'chroot' into the Ubuntu partition. This procedure allows your current system to act upon another partitions's files. We often use it to completely remove and reinstall Grub. It's the link in my signature line, called "Chroot".

I think at this point that might be the best option for you. It will return Grub2 back to it's original, installed, condition. Once you get things working *normally* we can see what we can do about modifying it again.

Hope you are feeling better!

---

### Post by charliemagiera on 2011-04-30
I had considered a lighter weight version; yet, my setup isn't too ungodly slow.  I recently upgraded to Natty, if I can't get the bugs out of it I may look a little deeper into Lubuntu or going back to Maverick.  Thank you for the tip.

---

### Post by gesaugen on 2011-05-01
> **drs305 said:**
> I think at this point that might be the best option for you. It will return Grub2 back to it's original, installed, condition. Once you get things working *normally* we can see what we can do about modifying it again.
after a whole day of not sucseeding to recover things to normal, I've decided to reinstall ubuntu...

So now I've backuped all the files again and we can start from the begining :)

---

### Post by drs305 on 2011-05-01
> **gesaugen said:**
> So now I've backuped all the files again and we can start from the begining :)

Just let us know what you need. We are here to serve!  ;-)

---

