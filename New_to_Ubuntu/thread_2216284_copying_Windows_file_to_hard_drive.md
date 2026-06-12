---
title: "copying Windows file to hard drive"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by David_Webb on 2014-04-11
I installed Ubuntu yesterday, and it is the only operating system on my computer. I've also put Wine on it so that a few programmes that require Windows can be run, and there is a particular programme that I'll use it for. I've tried running that programme from an external usb hard drive - and it works. Using Wine, Ubuntu can run that programme. But I've run into difficulty with the simple task of copying files. I want to copy that exe file from the external hard drive to my computer running Ubuntu, yet whatever I do it won't let me copy the file. I can select it and copy it, but then I can't paste it in anywhere. I make a directory for my windows files using mkdir but I can't actually put any files in it. What am I doing wrong?

---

### Post by SeijiSensei on 2014-04-11
Ordinary users can only write files to their home directories and /tmp.  To write a file anywhere else requires "root" privileges using [sudo]("https://help.ubuntu.com/community/RootSudo").

Wine is designed with these limitations in mind.  There is a "hidden" directory called .wine in your home directory.  Your entire wine configuration is stored there.  You'll see a "drive_c" directory and the emulated registry files..  Hidden files and directories have names that begin with a dot and do not appear in regular directory listings.  In most file managers like Nautilus and Dolphin holding down Alt and hitting the period with toggle the display of hidden files.  At the command prompt, you can list hidden files with the command "ls -a".

Most Windows programs these days need to be run from an installer.  If that's the case for this program, and the setup program resides on the external drive, you should be able to double-click the setup program to install it.  Wine will start up and the installer will write to that "drive_c" directory.

---

### Post by David_Webb on 2014-04-11
Thanks for that. This exe does not require an installer. I just have to copy the entire directory across. To enable root sudo, I type [COLOR=#333333][FONT=UbuntuMono]sudo -i[/FONT][/COLOR] into terminal, right? But what is the terminal command to copy something from the external drive?

---

### Post by David_Webb on 2014-04-11
By the way, I decided, "in for a penny, in for a pound", and so I just wiped over the whole of Windows 8 - no dual-booting here. It took me hours to work out how to disable Secure Boot and UEFI and after all that, I decided I wanted out of Windows for good, but I'm still finding my way round Ubuntu!

---

### Post by SeijiSensei on 2014-04-11
Why don't you just copy it to your home directory?  You don't need sudo to do that.

From the command prompt you can use cp or rsync.  To copy a whole directory
to your home directory use 
```
cp -a /path/to/the/directory ~
```
The tilde ("~") represents /home/username.  The "-a" ("archive") switch preserves ownerships and symbolic links and "recurses" through any subdirectories. From a terminal prompt type "man cp" for more details.

Most command-line programs have an associated "manual page" that you can read by typing "man program_name".

---

### Post by coldraven on 2014-04-11
As mentioned above you could just use the file manager "Nautilus" to copy the files to you home folder.
If you do want to learn the command line way here is a tip  :)
If you use Nautilus to navigate to your external drive you will see the path on the top of the screen as clickable trail of "breadcrumbs". (I think that is the correct term)
If you then press Ctrl+L it changes to an absolute path that you can copy and paste into a terminal.
Use Ctrl+C to copy from Nautilus and then Ctrl+Shift+V to paste into the terminal screen.
Enjoy!

---

### Post by David_Webb on 2014-04-11
Thanks both of you for good advice. I'm excited now to be using Ubuntu!

---

