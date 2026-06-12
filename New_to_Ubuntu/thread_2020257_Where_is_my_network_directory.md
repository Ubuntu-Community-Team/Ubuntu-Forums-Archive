---
title: "Where is my network directory?"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by paul1945 on 2012-07-08
Managed to setup Ubuntu on a Windows network (with some help) and I can see and access all the shares from the folders "network" --> "browse net" on my desktop. I can also copy and move files across the network by dragging these from another folder or from Krusader. My Ubuntu machine is also visible and accessible on my Windows machine, from where I can do the same. But I cannot seem to find the folder in Ubuntu that gives me access to the network shares from the terminal. And as I want to automate copying files from Ubuntu to my NAS for backup purposes, as I am already doing on my Windows machine, this is a pain.
Has anyone any suggestions that may help?
Thanks, Paul.

---

### Post by kimda on 2012-07-08
Does your nas support rsync? I would setup a rsync script with cron to automatically sync files between ubuntu and your nas. This is how I backup my machines. 

Another way to backup your system is by using Ubuntu's gui backup system dejadup. It can backup system via smb/ftp/ssh etc.. You can even backup to Ubuntu one.

---

### Post by paul1945 on 2012-07-08
I have a business program that runs under Dosbox, when it is used it updates the associated database files. I want to copy these automatically after any changes to a dedicated directory on my NAS. The easiest would be to copy these files individually, as my other machines are Windows machines and confusion would reign if the Windows machines updated the files from their end. This is the system I have used for a long time on the Windows machines; it checks each time I start the program for updated files on the NAS and updates these before running the program. The easiest would be if I could see my shared NAS directory as a Linux directory, or be able to treat it as such with a command, so I can map it to a drive in Dosbox. But I do not have any idea as to how to do this in (Ubuntu) Linux.

---

### Post by Morbius1 on 2012-07-08
It's not clear to me if you are using Kubuntu or Ubuntu since you bring up Krusader. If you are using Ubuntu when you go to Nautilus > Browse Network and select a share it mounts it to a hidden folder in your home directory:

/home/your-user-name/.gvfs/share-name on server-name

---

### Post by kimda on 2012-07-08
I would either make a nfs share or samba share. If your nas supports this (nfs).

You can mount the nas directly for example on a folder in your home drive. Then each time when you startup your machine and the nas is running it will be mounted automatically. 

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
Only follow client section if nas has nfs capabilities. 


Mounting via samba automatically on startup. 
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Hope this helps.

---

### Post by Paqman on 2012-07-08
+1 to kimda's suggestions. To answer one of the OP's specific questions: most people mount their network shares to a folder in /mnt, but you can choose anywhere you like really. Using gvfs through Nautilus and then try to access that share through the terminal is a bit ungainly, it's cleaner to mount it through /etc/fstab at boot time.

---

### Post by Morbius1 on 2012-07-08
And just for completeness sake, if the .gvfs mountpoint is not an issue and you wish to automount to that location at boot I would recommend Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by paul1945 on 2012-07-09
Thanks for all that, it is appreciated. I must say I am a bit nervous to get into the "guts" of Ubuntu as is recommended in the "mount windows shares permanently" post, as I am a total novice to everything Linux. I downloaded Gigolo, and that enabled me to set up the shares in /home/paul/.gvfs but Dosbox spat the dummy on my attempts to mount the remote share, as "share-name on server-name" contains spaces. Yet I can mount /home/paul/.gvfs and get into the share from dos without problems by doing a cd\share-~1
I guess that's a bug in Dosbox. But it is workable.
The only problem is that the share has to be called up each boot by launching gigolo and that is a bit of a pain. I cannot see any way to auto-launch gigolo on startup, so I presume there is no way to mount my share on startup apart from the potentially cumbersome and dangerous process (for someone still wet behind the ears) described in the above post? I don't think I have the skill to recover from a system lockup.

---

### Post by Paqman on 2012-07-09
Editing fstab needn't be dangerous if you take some sensible precautions:
[LIST=1]
[*]Make a copy of it before editing anything. That way you can restore it if you need.
[*]After editing it and before rebooting run this command:
[/LIST]
```
sudo mount -a
```
This will notify you of any errors in fstab, so you can fix them or restore your backed up copy before risking a reboot.

Both of these (back up before and check after) are good practice for working on any system file.

---

### Post by Morbius1 on 2012-07-09
> The only problem is that the share has to be called up each boot by  launching gigolo and that is a bit of a pain. I cannot see any way to  auto-launch gigolo on startup, Then I did a bad job in my HowTo.

If you went through the preference changes on Gigolo, created the bookmark, and selected Auto-Connect you should have something that looks like the first screen shot below.

To have Gigolo start on login you go to that Dash thingy and type: startup > then select **Startup Applications** > Add and fill in the boxes as indicated in the second screen shot below.

Then logout and login and it should mount to .gvfs. It won't place a mount icon on the desktop as I said in the howto for the latest gnome/unity because that feature was removed.

[COLOR=Blue]*Note: It also helps to create a bookmark to the .gvfs folder in Nautilus so a given application can find it easier. Just run the following command:*
```
nautilus $HOME/.gvfs
```Then bookmark it: Bookmarks > Add Bookmark

[I]It will show up in all the Open and Save dialogs in your applications and can be renamed.

[/I]  

[/COLOR]

---

### Post by paul1945 on 2012-07-09
Hello Morbius1, thanks for that very precise explanation. Interestingly, you seem to use the IP addresses, while I used the individual computers share name. Both work fine, although your method appears to be a tiny bit quicker. Anyhow, I did as instructed and Gigolo comes up nicely on startup. It tries to connect, but of course it beats the wifi connection and comes up with an error. Clicking the error report box away seems to make little difference as it still connects automatically about one minute later. What Gigolo could do with is a one to two minute delay facility for the automatic startup of wifi connections. 
Nevertheless I am pretty happy so far with the progress made, and am grateful for your assistance.:p

---

### Post by Morbius1 on 2012-07-09
> Clicking the error report box away seems to make little difference as it  still connects automatically about one minute later. What Gigolo could  do with is a one to two minute delay facility for the automatic startup  of wifi connections. You need to get a nice cup of tea and spend some "quality time" with Gigolo :). 

It does the very thing you want it to do. By default it will probe the network for these automounted shares every 60 seconds - something you can adjust ( Screenshot 1). And  you can turn off the error messages (Sreenshot 2):

---

### Post by Paqman on 2012-07-09
> **paul1945 said:**
> What Gigolo could do with is a one to two minute delay facility for the automatic startup of wifi connections. 


You could do that by launching it with the command:
```
sleep 60 && gigolo
```
..instead of just:
```
gigolo
```

---

### Post by Morbius1 on 2012-07-09
When you login, Gigolo attempts to mount the remote share immediately. The "Bookmark Auto-Connect Interval" default of 60 seconds is for any reason. Network not up, NAS not turned on yet, NAS doesn't exist becasue you are no longer home, solar flares, etc ...

---

### Post by paul1945 on 2012-07-16
Hello Morbius1, again thanks for that very concise and easy to understand information. 
As the blending of a program's toolbar with that of the Ubuntu desktop still throws me a bit, I failed to look at Gigolo's toolbar; hence my dilemma. 
Anyhow, this approach works really well; you are right, Gigolo is a magic little program.
As Paqman shows, Linux provides considerably more control to the user than Windows, something that went with the loss of the old Dos prompt. Linux is sort of Dos on steroids. Hence I think I will need to do some study..............

---

