---
title: "Wubi/Ubuntu messing up"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by forcerecon808 on 2008-09-01
About three or four days ago I downloaded ubuntu through wubi on my vista, but, just yesterday, I got really frustrated and uninstalled wubi through add/remove programs on the vista control panel. I did that in anger(I get stupid when I'm pissed) and now I want ubuntu back. I downloaded it again through wubi, again, and everything worked fine. When I rebooted and went to ubuntu to finish the installation, when it got to 50% this popped up:

"Device /dev/sdf has a logical sector size of 2048. Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL."

"OK" was the only option, so I pressed it. It stayed at 50%, and there was no way to cancel or shutdown so I manually shutdown(I pressed the power button). Then I tried to uninstall it again and this time(it didn't say this the first time I uninstalled it) it had a check box for whether or not I wanted to:

"Back up downloaded files (CD ISO file).
Backup location: C:\ubuntu-backup"

I don't know what any of this means or what I'm supposed to do and I'm hoping you do. Please help!

---

### Post by ctswhole on 2008-09-02
I wouldn't bother backing up anything from your install attempts.  It doesn't look like you ever got your machine to boot into Ubuntu so there's nothing worth saving.

From my limited experience with Wubi (the program by itself), I have seen it to act a little different than the Ubuntu LiveCD w/Wubi.  I would suggest downloading the actual livecd, burn it to a disc, and pop it into your drive with Windows already running.  You should be able to do a Wubi install that way with no errors (hopefully!)

---

### Post by forcerecon808 on 2008-09-02
> **ctswhole said:**
> I wouldn't bother backing up anything from your install attempts.  It doesn't look like you ever got your machine to boot into Ubuntu so there's nothing worth saving.

From my limited experience with Wubi (the program by itself), I have seen it to act a little different than the Ubuntu LiveCD w/Wubi.  I would suggest downloading the actual livecd, burn it to a disc, and pop it into your drive with Windows already running.  You should be able to do a Wubi install that way with no errors (hopefully!)

I had ubuntu running fine until I uninstalled it.

---

### Post by ctswhole on 2008-09-02
> **forcerecon808 said:**
> I had ubuntu running fine until I uninstalled it.

My mistake....I musta skimmed right over that part :oops:

As for the backup, then, it's up to you.  I have never saved a backup from the times I uninstalled the Ubuntu wubi thing in Vista, so I'm not certain how that would work out.

---

### Post by fidamehran on 2008-09-02
> **ctswhole said:**
> I wouldn't bother backing up anything from your install attempts.  It doesn't look like you ever got your machine to boot into Ubuntu so there's nothing worth saving.

From my limited experience with Wubi (the program by itself), I have seen it to act a little different than the Ubuntu LiveCD w/Wubi.  I would suggest downloading the actual livecd, burn it to a disc, and pop it into your drive with Windows already running.  You should be able to do a Wubi install that way with no errors (hopefully!)

There should not be any problem with Wubi downloading the image. I guess, you can still burn the image that Wubi downloaded and make a Live CD. All Wubi does is create a virtual partition within a Windows partition to install the Ubuntu. It also works as a means for mounting the CD image as a CD and installing the OS.

But still, it might be a good idea to have a real CD at hand.

> **forcerecon808 said:**
> I had ubuntu running fine until I uninstalled it.

Did you uninstall Wubi or Ubuntu?

You said earlier, you uninstalled Wubi. Anyway, from the knowledge of Windows that I have, I think, you can do the following:

1. Use one of the free Add/Remove applications for Windows to check whether Ubuntu or Wubi was properly uninstalled. If not, use the uninstaller program to remove it/them properly.

2. If there is no trace of Ubuntu/Wubi from the Add/Remove Program, then check if the "X:" drive that you installed Ubuntu in, still has the X:\Ubuntu" folder. If so, Shift-delete it.

3. Also delete wubibldr.... type named blah blah files from the drive you installed Ubuntu and from your C: drive (Drive that Windows is installed in).
However, to see these files you may need to uncheck "Hide Protected Operating System Files" and check "Show Hidden Files and Folders" from Tools-->Folder Options--> View menu.

4. If you have done things so far, then go to registry Editor (Start--> Run; type "regedit", press Enter.). Then Search for any and all entries by the names "Ubuntu", "Wubi", "Canonical" "Hardy" etc. And delete those entries. Alternatively you can also use a freeware named CCleaner to check your registry for obsolete entries and delete them.

5. Then use the burned CD or "ISO image through Wubi" to install Ubuntu once again.

6. If it all works, press the Thanks medal icon below my post at the right.
:popcorn:

---

### Post by forcerecon808 on 2008-09-02
> **fidamehran said:**
> 2. If there is no trace of Ubuntu/Wubi from the Add/Remove Program, then check if the "X:" drive that you installed Ubuntu in, still has the X:\Ubuntu" folder. If so, Shift-delete it.:popcorn:

How do I do that?

---

### Post by fidamehran on 2008-09-02
> **forcerecon808 said:**
> How do I do that?

Say, you installed Ubuntu in Drive "D:" when you installe dit for the first time. Then it was installed in a folder "D:\Ubuntu". If you still have that, you can delete it permanently. Shift-Delete means, Press Shift and Delete buttons together:)

We are planning here to clean all and every traces of Ubuntu from your Windows installation before going for a re-installation.

---

### Post by forcerecon808 on 2008-09-02
> **fidamehran said:**
> Say, you installed Ubuntu in Drive "D:" when you installe dit for the first time. Then it was installed in a folder "D:\Ubuntu". If you still have that, you can delete it permanently. Shift-Delete means, Press Shift and Delete buttons together:)

We are planning here to clean all and every traces of Ubuntu from your Windows installation before going for a re-installation.

I know, but how do I go to the C drive(that's where I installed it)? I'm computer retarded in case you haven't noticed.

---

### Post by fidamehran on 2008-09-02
> **forcerecon808 said:**
> I know, but how do I go to the C drive(that's where I installed it)? I'm computer retarded in case you haven't noticed.

Come on, don't get so upset. You still have your Windows installation intact, right? Meaning, you can still use your Windows, right?

---

### Post by fidamehran on 2008-09-02
So, in Windows, you have to go to My Computer an double click C: to get into it. Then see if the files I mentioned or their kind are in there...

---

### Post by forcerecon808 on 2008-09-02
> **fidamehran said:**
> Come on, don't get so upset. You still have your Windows installation intact, right? Meaning, you can still use your Windows, right?

Yeah, but I like ubuntu a lot more. Where do I go to delete wubi from my C drive?

<edit> Oops. Didn't read you next post.

---

### Post by forcerecon808 on 2008-09-02
> **fidamehran said:**
> 
3. Also delete wubibldr.... type named blah blah files from the drive you installed Ubuntu and from your C: drive (Drive that Windows is installed in).
However, to see these files you may need to uncheck "Hide Protected Operating System Files" and check "Show Hidden Files and Folders" from Tools-->Folder Options--> View menu.
:popcorn:

How do I get to tools?

---

### Post by fidamehran on 2008-09-02
> **forcerecon808 said:**
> How do I get to tools?

Are you using Vista? Okay, then its a bit different.

I use Windows XP, that's why I instructed according to XP. I got this in Microsoft's website on Folder Options changing in Vista. See if it helps.

"Using Folder Options in Control Panel, you can change the way your files and folders function, as well as how the content in your folders is displayed.

Open Folder Options by clicking the Start button , clicking Control Panel, clicking Appearance and Personalization, and then clicking Folder Options."

There you should be able to find the options to show the hidden files and the options to show hidden operating system files. Although the so-called high security warnings may be clicked OK to proceed.

---

### Post by fidamehran on 2008-09-02
Go to this link to see the page. It might have something more:
[Link]("http://windowshelp.microsoft.com/Windows/en-US/help/3a3bfe59-5268-4fb3-81c5-7972c28939cd1033.mspx#section_2")

---

### Post by fidamehran on 2008-09-02
I saw something else in another forum.

"Click Tools in the menu bar and click on Folder Options. If you cannot see the menu bar, you have to press the Alt key on the keyboard and the menu bar should be visible."

"Well there is a few ways to do this. (From what I&#8217;ve seen most Vista systems do not have the menu bar visible by default, which was a real pain at first but now its a cinch.) First you could use the method described above. Second you could click on the organize button (top left) to access the &#8220;folder options&#8221; from the drop-down menu (along with layout options right above &#8220;folder options&#8221;, which gives you the option to enable the menu bar manually along with a couple extra navigation helpers. Last, which is the most painful.. You could go to the control panel, under classic view, and pick folder options from there. Enjoy!"

---

### Post by fidamehran on 2008-09-02
The best one on Folder options I found is the following one. Please check it out.
["http://www.vista4beginners.com/Folder-Options"]("http://www.vista4beginners.com/Folder-Options")

---

### Post by forcerecon808 on 2008-09-02
> **fidamehran said:**
> Are you using Vista? Okay, then its a bit different.

I use Windows XP, that's why I instructed according to XP. I got this in Microsoft's website on Folder Options changing in Vista. See if it helps.

"Using Folder Options in Control Panel, you can change the way your files and folders function, as well as how the content in your folders is displayed.

Open Folder Options by clicking the Start button , clicking Control Panel, clicking Appearance and Personalization, and then clicking Folder Options."

There you should be able to find the options to show the hidden files and the options to show hidden operating system files. Although the so-called high security warnings may be clicked OK to proceed.

There was nothing but an empty ubuntu backup file, which I deleted.

---

### Post by fidamehran on 2008-09-02
Ok, good, now do the regedit thing.

   1. Click on the Vista Start Orb
   2. Click in the Start Search Dialog Box
   3. Type regedit
   4. Press enter (or double click Program: regedit)

Note 1: Unlike other Vista executables, if you type just the first few letters, 'reg' or 'reged', Vista does not auto-complete the name of the program, you have to type the full name - regedit.

Note 2: Another clue that amateurs are not supposed to open the registry, is that the special editor, Regedit, does not appear on any Vista menu.

Note 3: The actual executable is called regedit, but for backwards compatibility with NT 4.0, it also responds to the name of regedt32.

Then search the strings with names, 'Wubi", "Ubuntu", etc. And delete them.

Now all entries and histories of Ubuntu will be cleared. That is when you can go for a re-installation of Ubuntu.

---

### Post by forcerecon808 on 2008-09-02
> **fidamehran said:**
> Then search the strings with names, 'Wubi", "Ubuntu", etc. And delete them.

Now all entries and histories of Ubuntu will be cleared. That is when you can go for a re-installation of Ubuntu.

There are three "Windows based UBuntu Installer" files. Should I delete them? Were they there before I installed wubi?

---

### Post by fidamehran on 2008-09-02
> **forcerecon808 said:**
> There are three "Windows based UBuntu Installer" files. Should I delete them? Were they there before I installed wubi?

They are not supposed to be there before you installed Wubi, as Windows did not know you were going to install Ubuntu.

So delete them.

Of course, if it is the main Wubi exe file, you can keep it.

---

### Post by forcerecon808 on 2008-09-02
Ok, I searched wubi, ubuntu, and hardy and deleted everything that came up. Any other searches I should do before I reinstall wubi?

---

### Post by fidamehran on 2008-09-02
I guess not. You can install Ubuntu now. My personal preference is not to install it in Windows system drive (the one where Windows in installed, usually C: drive). You can use Wubi to install it.

Now if you already did run Ubuntu properly before, then you can use the same installer. Otherwise, I prefer you download a fresh installer through Wubi and install it, or download a CD image from Ubuntu.com and burn it on CD.

Best of Luck.

---

### Post by forcerecon808 on 2008-09-02
I'm installing it right now. I'll let you know if it works this time.

---

### Post by forcerecon808 on 2008-09-02
It didn't work. This time when I clicked reboot it froze while logging off. I let it sit for like 30 mins hoping it would somehow start working again, but it didn't so I held the power button to manually shut it down. When I turned the computer back on, I booted ubuntu, but instead of installing, it went to a black terminal-like screen that said busybox v1.1.3(i think) and it said a whole lot of other stuff, too. Should I uninstall and try it again or do you know what to do?

---

### Post by fidamehran on 2008-09-02
Check the following thread:

"[http://ubuntuforums.org/showthread.php?t=854618]("http://ubuntuforums.org/showthread.php?t=854618")"
or
"[http://ubuntuforums.org/showthread.php?t=904077]("http://ubuntuforums.org/showthread.php?t=904077")"
and/or
"[http://ubuntuforums.org/showthread.php?t=906161]("http://ubuntuforums.org/showthread.php?t=906161")"

As I said before, your installer CD or image might be corrupted. I think you'd better download a fresh copy or order a CD through "shipit.ubuntu.com".

Best way to download a non-corrupt CD image is to download through torrent.

After downloading you should also check the integrity of the download through "md5checksum". This is a parameter to check whether your download is ok.

---

### Post by fidamehran on 2008-09-02
Please don't lose hope already. Keep at it.

---

