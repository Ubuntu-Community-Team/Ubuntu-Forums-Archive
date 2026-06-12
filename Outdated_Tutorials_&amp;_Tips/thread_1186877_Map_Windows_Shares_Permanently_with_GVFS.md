---
title: "Map Windows Shares Permanently with GVFS"
date: 2009-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by NTolerance on 2009-06-13
**_Concept_**

The file manager in MS Windows has a nice feature called "Map Network Drive".  This allows you to permanently assign Samba shares to a drive letter which any program can access.  It can be made persistent across reboots.  This feature is tremendous when you have a Samba server on your network that has files you need to continuously access.  

**_Applicable Systems_**

This guide will explain how to do the same using an up-to-date Ubuntu Intrepid or Jaunty.  This guide will not work on Hardy unless _[this bugfix](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)_ is backported to Hardy.  

**_Comparison to Other Methods_**

There is an _[ages-old method](http://ubuntuforums.org/showthread.php?t=288534)_ which produces a similar result and involves editing /etc/fstab.  I don't like this method for a number of reasons, such as the fact that it's difficult, it involves storing your Samba password in plain text, and it exposes a _[nasty bug](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/90795)_ that can cause your system to hang on shutdown.

**_Procedure_**

1.  Select the "Network" option from the "Places" menu.  

2.  Select the "Windows Network" icon.

3.  Select the workgroup that your share resides in.

4.  Select the PC on your network that contains the share you want to access.  You will now see an authentication prompt.  Enter the correct username and password.  IMPORTANT:  Make sure to select the radio button that is labled "Remember forever".  This will permanently save your password in the GNOME keyring.  

6.  Select the "Connect" option.  You will now see a folder for each share that is available on the selected PC.  

8.  Select the folder you want to access.  You will now see a prompt regarding the keyring.  Select the "Always Allow" option.  The share is now temporarily mounted (will not survive a reboot) and your password is permanently saved and accessible in the GNOME keyring.

9.  The share should be visible in the "Places" menu on the left of the Nautilus file manager.  Select the eject icon to the right of the share to unmount it.  

10.  Now we will test out a command which will go into a script.  Open the Terminal from the "Accessories" submenu in the "Applications" menu.  

11.  Run this command in the Terminal while filling in the appropriate information within the <> symbols.
```
gvfs-mount smb://<pcname>/<sharename>
```

Example:
```
gvfs-mount smb://desktop/sharedfolder
```

The share should now be mounted again and will appear in the "Places" menu on the left side of the Nautilus file manager.  Select the eject icon to the right of the share to unmount it. 

12.  Now we will put that command in a script to be executed during startup.  In the Terminal, run this command to create the script:
```
gedit ~/sharemount.sh
```

If you'd like to change the path or the filename of the script, feel free to do so.  

13.  Paste this into the GEdit window while filling in the appropriate information into the <> symbols.
```
#!/bin/sh
gvfs-mount smb://<pcname>/<sharename>
```

Example:
```
#!/bin/sh
gvfs-mount smb://desktop/sharedfolder
```

14.  Make the script executable by running this command in the Terminal:
```
chmod +x ~/sharemount.sh
```

15.  Now let's add the script to GNOME startup.  Choose the "Startup Applications" option from the "Preferences" submenu located in the "System" menu.  

16.  Select the "Add" option.  Type a name of your choice in the "Name" field, browse to the path of the script in the "Command" field, and optionally add a comment to the "Comment" field.  Press the "Add" button to save your settings.

17.  Now log out and log back in or restart your PC.  Check the "Places" menu and the shares should be automatically mounted.

**_Usage Notes_**

The shares are mounted using _[GVFS](http://fedoraproject.org/wiki/Features/Gvfs)_.  From the GNOME GUI, shares are accessible via the "Places" menu in Nautilus and the smb:// path in the address bar.  Command-line programs can access these shares via the ~/.gvfs path.

**_Uninstallation_**

If you'd like to remove these changes, follow the these two simple steps:

1.  Choose the "Startup Applications" option from the "Preferences" submenu located in the "System" menu.  Select the sharemount.sh script and press the "Remove" button.  

2.  Delete the script with the Terminal:
```
rm ~/sharemount.sh
```

**_Community Additions**_

Since the ~/.gvfs directory is a directory like any other, michaelzap [presented](http://ubuntuforums.org/showpost.php?p=7565902&postcount=22) the idea of using symbolic links to further improve the usefulness of all this.  In particular you can work around particular applications such as Firefox that don't display network mounts in their file open/save dialog.

---

### Post by NTolerance on 2009-06-28
Which topic title, keywords, tags, etc... do I need to get some interest in my awesome thread?

---

### Post by dmizer on 2009-06-28
> **NTolerance said:**
> Which topic title, keywords, tags, etc... do I need to get some interest in my awesome thread?

I actually didn't know this was possible. Nicely done. I'll link to it in my CIFS tutorial.

---

### Post by Jorgo on 2009-06-30
I think this method will also store your password in plain text.  Have a look in Applications -> Passwords and Encryption Keys.  In the Passwords tab, your password description should be listed.  If you look at the Properties of the key, you can show the password in plain text with a couple of clicks of the mouse!  I only discovered this a few days ago...not impressed.

---

### Post by NTolerance on 2009-06-30
> **dmizer said:**
> I actually didn't know this was possible. Nicely done. I'll link to it in my CIFS tutorial.

Thanks!

> **Jorgo said:**
> I think this method will also store your password in plain text.  Have a look in Applications -> Passwords and Encryption Keys.  In the Passwords tab, your password description should be listed.  If you look at the Properties of the key, you can show the password in plain text with a couple of clicks of the mouse!  I only discovered this a few days ago...not impressed.

The password is encrypted on the disk, but it can be displayed as text if you are properly authenticated/logged in to GNOME.  

From the [GNOME wiki](http://live.gnome.org/GnomeKeyring):
> GNOME Keyring is a place where passwords (and soon encryption keys) for a user are stored in an encrypted file. The user enters a global password when first accessed.

By comparison, the password files that the fstab methods use are stored unencrypted in plain text on the disk.

---

### Post by benrb on 2009-06-30
Thanks for that tutorial. It comes in very handy for me as I've been playing around with a D-LINK DNS-323 NAS the past couple of days.

---

### Post by sloppyc on 2009-06-30
> **NTolerance said:**
> Thanks!



The password is encrypted on the disk, but it can be displayed as text if you are properly authenticated/logged in to GNOME.  

From the [GNOME wiki](http://live.gnome.org/GnomeKeyring):


By comparison, the password files that the fstab methods use are stored unencrypted in plain text on the disk.
Using the CIFS tutorial though, one would need root access to the machine to read the .smbcredentials file even though it's plain text, no?

Cool tutorial nonetheless, I will look at playing with it; might be good for mounting shares for certain users only.

---

### Post by benrb on 2009-06-30
Quick question: should a share that is mounted this way be manually unmounted before system shutdown, or will the OS take care of that automatically?

---

### Post by dmizer on 2009-06-30
> **sloppyc said:**
> Using the CIFS tutorial though, one would need root access to the machine to read the .smbcredentials file even though it's plain text, no?

Yes, but with this method even root (or anyone in sudoers) cannot view the password. Even though cifs and /etc/fstab still has advantages, this method is certainly more secure.

---

### Post by sloppyc on 2009-06-30
Ah, I see now.

---

### Post by dmizer on 2009-07-02
> **benrb said:**
> Quick question: should a share that is mounted this way be manually unmounted before system shutdown, or will the OS take care of that automatically?

I'm interested in this as well. Please test it and report your results :)

---

### Post by drocksvold on 2009-07-04
Has anyone had any luck with NAS Drives?  I have a Maxtor NAS Drive that I have hooked up to my network.  I also have another Maxtor hard drive plugged into the NAS via USB.  I can access them very easily from Windows Vista, but I cannot see them using Jaunty...

I have followed the beginning instructions on the first post in this thread, but the "Windows Network" does not show any other items.  I cannot navigate to the drive.  Any suggestions?

Dustin

---

### Post by dmizer on 2009-07-05
> **drocksvold said:**
> Has anyone had any luck with NAS Drives?  I have a Maxtor NAS Drive that I have hooked up to my network.  I also have another Maxtor hard drive plugged into the NAS via USB.  I can access them very easily from Windows Vista, but I cannot see them using Jaunty...

I have followed the beginning instructions on the first post in this thread, but the "Windows Network" does not show any other items.  I cannot navigate to the drive.  Any suggestions?

Dustin

You may have luck by following the tutorial located in the 2nd link in my sig. Some NAS devices are very difficult, but I've been mostly successful with CIFS. If you have problems, please post in that howto, and I will be more than happy to assist you.

---

### Post by drocksvold on 2009-07-05
I was able to connect to it previously when I had Hardy installed.  I will check the link you mentioned and see if I have any better luck.  I know I have connected to that drive before, that is why it is bugging me.  Trying to remember how to do things two ways is getting difficult.

Now that I found Wine, i may be more reliant on Ubuntu, provided I can get a few key programs to work...

Dustin

---

### Post by michaelzap on 2009-07-05
Excellent! I may give this a try. It works with my two NAS drives, and I've had intermittent shutdown issues mounting them via fstab. It seems as if any GUI programs can access these shares in ~/.gvfs as well (for example, I added my shared mp3 folder as a library to Exaile).

Anyone know how to keep these shares from appearing on the desktop?

As far as encrypting your fstab credentials file, that can be done in Jaunty by placing it inside your encrypted home directory (or of course you could use full disk encryption).

---

### Post by Spenzer4Hire on 2009-07-05
You can disable the mounted shares from showing up on the desktop but it also disables the desktop shortcut for USB drives, etc.

Open a terminal and run:  ```
gconf-editor
```

In the tree on the left expand apps.  Find and expand nautilus.  Select desktop.  In the right pane uncheck "volumes_visible".

Nice writeup.  I wanted to mention that if you have joined your computer to a Windows domain this method allows you to use kerberos to mount the Windows shares.  Kerberos has always been a headache for me when using fstab or pam_mount.  This method was much easier.

I unknowingly created a duplicate writeup here:  [http://ubuntuforums.org/showthread.php?t=1204652]("http://ubuntuforums.org/showthread.php?t=1204652")

---

### Post by NTolerance on 2009-07-05
> **benrb said:**
> Quick question: should a share that is mounted this way be manually unmounted before system shutdown, or will the OS take care of that automatically?

I don't believe there's a need to manually unmount these shares.  They're mounted in the same way that shares are mounted when you manually browse to them via the "Network" menu.  GNOME appears to deal with it gracefully.

---

### Post by NTolerance on 2009-07-05
> **drocksvold said:**
> Has anyone had any luck with NAS Drives?  I have a Maxtor NAS Drive that I have hooked up to my network.  I also have another Maxtor hard drive plugged into the NAS via USB.  I can access them very easily from Windows Vista, but I cannot see them using Jaunty...

I have followed the beginning instructions on the first post in this thread, but the "Windows Network" does not show any other items.  I cannot navigate to the drive.  Any suggestions?

Dustin

If the NAS is not visible via the "Network" menu, you can try typing the path manually into the Nautilus location bar.  Use this format assuming the network name of your NAS is "NASdrive" and its share name is "shared".

```
smb://NASdrive/shared
```

If you're lucky you'll get an authentication prompt at this point.  If you're unlucky you'll get an error message or a blank Nautilus window.

---

### Post by michaelzap on 2009-07-05
Giving this method a proper try today. I've commented out my fstab mounts and my unmount hacks and I'm mounting my NAS shares via this method. So far, so good.

Auto-mounting in Startup Applications doesn't work for me on wireless because the script is run before the connection is made. I could add a sleep command to the script, but I opted to make it a manual menu entry instead. That way if I'm not at home with my shares it doesn't try to mount them.

---

### Post by NTolerance on 2009-07-05
> **michaelzap said:**
> Excellent! I may give this a try. It works with my two NAS drives, and I've had intermittent shutdown issues mounting them via fstab. It seems as if any GUI programs can access these shares in ~/.gvfs as well (for example, I added my shared mp3 folder as a library to Exaile).

Anyone know how to keep these shares from appearing on the desktop?

As far as encrypting your fstab credentials file, that can be done in Jaunty by placing it inside your encrypted home directory (or of course you could use full disk encryption).

I had considered the encrypted home directory idea, but fstab mounts are done early in the boot process long before a user logs in and decrypts their home directory, no?

---

### Post by michaelzap on 2009-07-05
> **NTolerance said:**
> I had considered the encrypted home directory idea, but fstab mounts are done early in the boot process long before a user logs in and decrypts their home directory, no?

I thought that as well, but it works for me. Before Jaunty I used full-disk encryption, so I kept my credentials file in my home directory and it was decrypted along with everything else long before login. In Jaunty I'm using an encrypted home directory, and I left my credentials file in there to see what would happen. It worked just the same as always. I was of the impression that fstab mounts happened before login, but apparently either I was wrong or that's been changed in Jaunty.

---

### Post by michaelzap on 2009-07-05
I have a lot of links to my previous fstab mounts in various applications, so I decided to ease the transition by deleting the mount point folders (mine were in /mnt) and creating symbolic links to the hidden gvfs share directories:

```
sudo ln -s ~/.gvfs/'sharename on server' /mnt/sharename
```

Of course you could do the same thing in your home directory:

```
ln -s ~/.gvfs/'mp3s on server' ~/Music/shared
```

The next thing that I really need to verify is that files that I create on these shares are accessible to other users (I had to force 777 permissions on my NAS drives in fstab before).

---

### Post by michaelzap on 2009-07-05
> **michaelzap said:**
> The next thing that I really need to verify is that files that I create on these shares are accessible to other users (I had to force 777 permissions on my NAS drives in fstab before).

I don't seem to have any trouble with permissions between Ubuntu and Vista and using different NAS user logins on each. I've tested this on a Buffalo Linkstation and an HP MediaVault so far. This was always a pita with fstab, so this seems to be yet another major advantage to gvfs.

Perhaps the next thing to test is whether that annoying gedit bug that complained so loudly when saving files on Samba shares is also resolved in gvfs (I expect that it will be).

---

### Post by michaelzap on 2009-07-05
> **michaelzap said:**
> Perhaps the next thing to test is whether that annoying gedit bug that complained so loudly when saving files on Samba shares is also resolved in gvfs (I expect that it will be).

Indeed! Gedit doesn't seem to freak out when saving files over gvfs. I had given up using gedit for any real work because this bug was so frustrating, but now I may go back to it!

---

### Post by NTolerance on 2009-07-05
> **michaelzap said:**
> I have a lot of links to my previous fstab mounts in various applications, so I decided to ease the transition by deleting the mount point folders (mine were in /mnt) and creating symbolic links to the hidden gvfs share directories:

```
sudo ln -s ~/.gvfs/'sharename on server' /mnt/sharename
```

Of course you could do the same thing in your home directory:

```
ln -s ~/.gvfs/'mp3s on server' ~/Music/shared
```

The next thing that I really need to verify is that files that I create on these shares are accessible to other users (I had to force 777 permissions on my NAS drives in fstab before).

This is a great idea.  Don't know why I didn't think of it.  In case anyone tries to use GVFS mounts with Rhythmbox you may run into a bug in Rhythmbox which prevents these mounts from being used.  Your symlink idea may fix this.

---

### Post by michaelzap on 2009-07-05
> **NTolerance said:**
> This is a great idea.  Don't know why I didn't think of it.  In case anyone tries to use GVFS mounts with Rhythmbox you may run into a bug in Rhythmbox which prevents these mounts from being used.  Your symlink idea may fix this.

It works in Exaile just fine.

I did just run into a situation that gave me some trouble, however. I tried to mount a disk image on one of my remote shares using Unetbootin, but it couldn't see my symbolic links and even more strangely the .gvfs directory was also not visible in my home directory. The same thing happens with gedit, so it's not just a Unetbootin issue. It appears that when programs run as root they don't have access to these shares.

That could be problematic at times, but there's probably a way to work around it (by mounting the share manually, I assume).

I also think it's odd that I don't experience the gedit bug now, given that these shares are still mounted via Samba. Anyone else who knows this bug want to give this a shot? I definitely still had them when I first installed Jaunty and I was mounting them using CIFS via fstab.

---

### Post by KillerKiwi on 2009-07-06
There is already a list of shares in the keyring...

```

import gnomekeyring
def list_all():

    for obj in gnomekeyring.find_network_password_sync(None,None,None,None,"smb"):

        mount = "%s://%s:%s@%s" % (obj["protocol"], obj["user"], obj["password"], obj["server"])
        print mount



if __name__ == '__main__':
    list_all()


```

---

### Post by Spenzer4Hire on 2009-07-06
Well, I am a pretty heavy user of my file shares.  I'm often reading/writing large amounts of data to and from the shares.  Already, in the past 2 days, I've had dbus-gvfs hang on me once, and I've had gvfs just drop the mount 4 - 6 times.

I'm not particularly frustrated because I've always had problems between Ubuntu and a SMB server when heavily accessing large files.  It works fine on the same computer Vista > SMB.

Of course, if anyone has any suggestions or troubleshooting steps I'd be glad to hear them.

---

### Post by michaelzap on 2009-07-06
> **Spenzer4Hire said:**
> Of course, if anyone has any suggestions or troubleshooting steps I'd be glad to hear them.

You're not copying the files over wireless, are you? I've had some issues with large files over wireless since the last kernel update. I actually haven't noticed it happen since I switched to GVFS, but that may just be due to not copying many large files sine then.

---

### Post by zzyzx1 on 2009-07-22
[quote=NTolerance;7453309]**_Concept_**

The file manager in MS Windows has a nice feature called "Map Network Drive".  This allows you to permanently assign Samba shares to a drive letter which any program can access.  It can be made persistent across reboots.  This feature is tremendous when you have a Samba server on your network that has files you need to continuously access.  

I followed this to a "T" and it didnt work... no mount... any suggestions..??

---

### Post by NTolerance on 2009-07-22
> **zzyzx1 said:**
> [quote=NTolerance;7453309]**_Concept_**

The file manager in MS Windows has a nice feature called "Map Network Drive".  This allows you to permanently assign Samba shares to a drive letter which any program can access.  It can be made persistent across reboots.  This feature is tremendous when you have a Samba server on your network that has files you need to continuously access.  

I followed this to a "T" and it didnt work... no mount... any suggestions..??

Need more info.  Please post all relevant error messages, observations, etc...

---

### Post by adonet on 2009-07-27
dear NTolerance,
I've used this way of connecting to my freecom networkdrive I can make the connection. I can read files, I can write files but I cannot replace files with another (newer) version and I cannot delete directories when these directories have files still in it. This is very annoying when using backup software like Synkron.

Do you have any idea how to fix this?

Another machine running windows XP can do the overwriting and multi deleting with no pain at all. I could of course boot into windows when syncronizing my files to the networkdrive, but there should be a nicer ubuntu way to do the job.

---

### Post by NTolerance on 2009-07-27
> **adonet said:**
> dear NTolerance,
I've used this way of connecting to my freecom networkdrive I can make the connection. I can read files, I can write files but I cannot replace files with another (newer) version and I cannot delete directories when these directories have files still in it. This is very annoying when using backup software like Synkron.

Do you have any idea how to fix this?

Another machine running windows XP can do the overwriting and multi deleting with no pain at all. I could of course boot into windows when syncronizing my files to the networkdrive, but there should be a nicer ubuntu way to do the job.

I'm not familiar with Synkron, but I will try to help if you're using another method to do the overwrites and deletes, such as Nautilus or the command line.  Which one are you getting the problem with?  What error message do you get?  

There's an option in Nautilus to add a true "delete" command to the context menu.  I usually use that to delete any files as the Trashcan seems to be problematic when dealing with non-internal drives.

---

### Post by adonet on 2009-07-29
> **NTolerance said:**
> I'm not familiar with Synkron, but I will try to help if you're using another method to do the overwrites and deletes, such as Nautilus or the command line.  Which one are you getting the problem with?  What error message do you get?  

There's an option in Nautilus to add a true "delete" command to the context menu.  I usually use that to delete any files as the Trashcan seems to be problematic when dealing with non-internal drives.

Synkron is just a program that checks two volumes and copies the files from one volume to another if files are new, changed or deleted. It simply is not allowed to overwrite a file with a newers version of it, nor is it allowed to delete a excisting file.

I get the same input / output error in nautilus and thunar or if I try to resave a file I'm working on in Open Office. I don't use commandline for these kind of actions.

In Thunar I could copy a newer version over an excisting file with the same filemane) But I couldn't make Thunar, nor Nautilus deleting a directory with a file in it. It simply says that the directory doesn't excist. (with Nautilus started from terminal, there a no extra messages visible in the terminal.)

I'm confused with this....

---

### Post by NTolerance on 2009-08-01
> **adonet said:**
> Synkron is just a program that checks two volumes and copies the files from one volume to another if files are new, changed or deleted. It simply is not allowed to overwrite a file with a newers version of it, nor is it allowed to delete a excisting file.

I get the same input / output error in nautilus and thunar or if I try to resave a file I'm working on in Open Office. I don't use commandline for these kind of actions.

In Thunar I could copy a newer version over an excisting file with the same filemane) But I couldn't make Thunar, nor Nautilus deleting a directory with a file in it. It simply says that the directory doesn't excist. (with Nautilus started from terminal, there a no extra messages visible in the terminal.)

I'm confused with this....

I'm a bit at a loss here because I don't have access to the NAS device that you use.  My network shares are served via Samba on Ubuntu and regular Windows systems.  Being that so many trouble posts in this thread deal with NAS devices, I wonder if they use Samba settings that GVFS can't understand or properly deal with.  You may or may not have control over these settings.

In spite of the fact that you don't use the command line to access this data during normal use, the command line may be required to gain more information about the nature of the errors you're getting.  Naturally, it's common to use the command line to get information that the GUI does not provide.

We need to find out if GVFS provides logging information and if so, where that information is kept.  So far I haven't been able to find out.

GVFS is still new technology compared to the old fstab method that I discussed in the original post.  We may need to punt here and use that method because GVFS isn't working out for you.

---

### Post by adonet on 2009-08-02
> **NTolerance said:**
> I'm a bit at a loss here because I don't have access to the NAS device that you use.  My network shares are served via Samba on Ubuntu and regular Windows systems.  Being that so many trouble posts in this thread deal with NAS devices, I wonder if they use Samba settings that GVFS can't understand or properly deal with.  You may or may not have control over these settings.

In spite of the fact that you don't use the command line to access this data during normal use, the command line may be required to gain more information about the nature of the errors you're getting.  Naturally, it's common to use the command line to get information that the GUI does not provide.

We need to find out if GVFS provides logging information and if so, where that information is kept.  So far I haven't been able to find out.

GVFS is still new technology compared to the old fstab method that I discussed in the original post.  We may need to punt here and use that method because GVFS isn't working out for you.


Well, thank you for your comments and help so far. By the way, I'm having the same troubles when mounting the device within fstab.

dmizer is trying to help me on that now.

---

### Post by Burky on 2009-10-02
The share folder has parenthesis, so when I run it, I get an error message. Is there a way around this?

```
gvfs-mount smb://compac/external%20(j)/
```

---

### Post by NTolerance on 2009-10-03
> **Burky said:**
> The share folder has parenthesis, so when I run it, I get an error message. Is there a way around this?

```
gvfs-mount smb://compac/external%20(j)/
```

This is a guess on my part, but try putting quotes around the share path:

```
gvfs-mount "smb://compac/external%20(j)"
```

---

### Post by Burky on 2009-10-03
Thanks a lot NTolerance, I appreciate it. It worked.

---

### Post by cjfarley on 2009-10-28
This is a life saver!  I'm trying to implement Ubuntu at our school and was having problem mapping shares.  This method will do, but I was wondering about a few specifics.  Is there anyway to use with the users current credentials (not have to ask for the keyring)? I have connected my test machine to our domain and can login as a domain user, so the current user has full rights to the shares.

If you have to stick with the keyring, what happens when the users password changes?  Will it update?

Is there anyway to apply this for all users who login on the machine?

Sorry for the on-slot of questions, but we have a short time frame to do all our feasibility testing before we roll out Ubuntu.  Thanks

---

### Post by KillerKiwi on 2009-10-28
> **cjfarley said:**
> This is a life saver!  I'm trying to implement Ubuntu at our school and was having problem mapping shares.  This method will do, but I was wondering about a few specifics.  Is there anyway to use with the users current credentials (not have to ask for the keyring)? I have connected my test machine to our domain and can login as a domain user, so the current user has full rights to the shares.

If you have to stick with the keyring, what happens when the users password changes?  Will it update?

Is there anyway to apply this for all users who login on the machine?

Sorry for the on-slot of questions, but we have a short time frame to do all our feasibility testing before we roll out Ubuntu.  Thanks

You may want to mount at the fs level 
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

---

### Post by NTolerance on 2009-10-28
> **cjfarley said:**
> This is a life saver!  I'm trying to implement Ubuntu at our school and was having problem mapping shares.  This method will do, but I was wondering about a few specifics.  Is there anyway to use with the users current credentials (not have to ask for the keyring)? I have connected my test machine to our domain and can login as a domain user, so the current user has full rights to the shares.

If you have to stick with the keyring, what happens when the users password changes?  Will it update?

Is there anyway to apply this for all users who login on the machine?

Sorry for the on-slot of questions, but we have a short time frame to do all our feasibility testing before we roll out Ubuntu.  Thanks

Thanks for your feedback!  I'm glad this method has helped with your Windows/Ubuntu network setup.  Frankly, I'm surprised there aren't more threads and guides about helping Ubuntu play nice on a Windows network.  

Anyways, I am not clear on your question about the keyring.  I will say that via the GUI, the GNOME keyring can be made to save credentials for Windows shares permanently, so that those credentials are always automatically used whenever a user has logged into their Ubuntu account. 

Regarding password changes, are you referring to the user's Ubuntu password or their Windows share password?  If the Ubuntu password changes, nothing should happen and everything should still work.  If the user's Windows share password changes, the automatic GVFS mount will fail.  In this case, simply use the GUI to browse to the share via the method outlined in my original post and Nautilus will provide a new password prompt that will allow you to use and save the new Windows share password.  

As far as applying this for all users who log into the Ubuntu system, I'm not sure.  I don't know of a way to automatically deploy GNOME keyrings across multiple users.  Hopefully someone with some hands-on Ubuntu network experience can jump in here.  

If your Windows share password never changes but the Ubuntu users are ever-changing, you may want to investigate the "fstab" method outlined in my original post.  This method is handled by the system and not by individual users, and therefore may be better suited for a multiple-user system where all users need access to the same Windows share that maintains a consistent network location and password.

---

### Post by michaelzap on 2009-10-28
Actually, it sounds as if you might want to search for OpenLDAP in these forums (LDAP is the protocol used to authenticate with a Windows server and use the credentials stored on it).

---

### Post by cjfarley on 2009-10-30
Thanks for your replies.  

I'm using likewise-open to add the computer to our domain and using active directory to authenticate users on the ubuntu machine.  So, the windows share (domain share) accepts the same Uname and Pword that they user to login with.

What I would like to have happen is that the drives are mapped based on the current users credentials (they are the same for both ubuntu and the network).  The will both change at the same time (every 30 days).  I want to make this as seemless for the user as possible.  

Does anyone know if ubuntu can import the login script from AD?  Anyway, thanks again, you have all been really helpful!

---

### Post by jeffimus on 2009-11-03
Thanks to NTolerance for the first post in this thread.  I've found it very useful.  However, I have a problem with the advice later in this thread on creating a symbolic link to the .gvfs directory.  It doesn't work as I expect

My share is mapped to "~/.gvfs/share on fileserver".  I don't like the hidden file and spaces in this path, so I would like to make a symbolic link with a more friendly path like "~/fileserver/share".  I tried following michaelzap's example in this thread to create a link using the command:

```
sudo ln -s ~/.gvfs/'share on fileserver' ~/fileserver/share
```

The command completed successfully, but when I did:

```
ls fileserver/share
```

the listing came back as:

```
[COLOR="Cyan"]**share on fileserver**[/COLOR]
```

(in light blue because it is a symbolic link, I guess). I was expecting to see the root directories in my share, not the directory name 'share on fileserver'. How did that get inserted into the path?  (Before anyone asks, there is not a directory called 'share on fileserver' in the root of my share.)

For example, if I have a directory in the root of my share called Stuff, then I want it to appear at ~/fileserver/share/Stuff and not at ~/fileserver/share/share on fileserver/Stuff'.  I'm not experienced with using symbolic links, so I have probably misunderstood how they work.  Can anyone tell me what I am doing wrong?

---

### Post by michaelzap on 2009-11-03
Did you perhaps create the folder "share" before creating the symbolic link? I ask because something similar happened to me when I did this all over again on Karmic and it took me a little while to figure out. In my case:

I have a share called "archivos" on a NAS file server called "tooga". I mounted "archivos on tooga" with GVFS as described above, and then I wanted to create the symbolic link "/mnt/tooga" to the GVFS mount point directory, just like I did in Jaunty.

However after doing this I would open up /mnt/tooga/ and there would be a directory inside of it called "archivos on tooga". If I opened that folder up all of the share's files were accessible, but I didn't understand why I suddenly had an extra directory in the path. It turns out that I had created a folder called "tooga" in mnt before I ran the symbolic link command, when I should have just ran the command without doing that and it would've created a symbolic link with that name.

So I just deleted the folder I'd created and re-ran the command and it once again worked as expected.

Maybe you did the same thing?

---

### Post by suzypeppercorn on 2009-11-03
Great guide. Thanks so much :D

---

### Post by jeffimus on 2009-11-04
> **michaelzap said:**
> Did you perhaps create the folder "share" before creating the symbolic link? ...

Yes I did, but for a good reason. Before that, I had attempted to create the link without creating the directory first, but it didn't work! I tried it again just now, to make sure. I start with an empty directory called ~/fileserver. Then I issue the command:

```
ln -s .gvfs/share\ on\ fileserver/ fileserver/share
```

which executes with no warnings or errors, and creates a symbolic link called ~/fileserver/share. However, if I try to list its contents, the directory listing just shows the name of the link with no sign of any subdirectories, like this: 

```
jeff@computer:~$ ls fileserver/share 
[COLOR="Red"]**fileserver/share**[/COLOR]
```

The red text on a black background (I can't reproduce the black background here) means an orphan link ([I looked it up]("http://ubuntuforums.org/showthread.php?t=501914")).  

If I do a long listing, the symbolic link is clearly pointing to the right place:

```
jeff@computer:~$ ls -la fileserver/share 
lrwxrwxrwx 1 jeff jeff 26 2009-11-04 20:13 [COLOR="Red"]**fileserver/share**[/COLOR] -> [COLOR="Red"]**.gvfs/share on fileserver/**[/COLOR]

```

but as it's an orphan link I can't see what's below it, i.e. the files on my share. Just to prove that my share exists, here it is:

```
jeff@computer:~$ ls .gvfs/share\ on\ fileserver/
[COLOR="LightBlue"]**Stuff**[/COLOR]  [COLOR="LightBlue"]**Jeff**[/COLOR]  [COLOR="LightBlue"]**mail**[/COLOR]  [COLOR="LightBlue"]**trashbox**[/COLOR]
```

Edit: I just learnt that you have add a slash to the end of the path to list the contents of a symbolic link that points to a directory. It still doesn't work though:

```
jeff@computer:~$ ls fileserver/share/
ls: cannot access fileserver/share/: No such file or directory
```

Thanks for your help, but I don't understand why your example works and mine doesn't. :-?

---

### Post by michaelzap on 2009-11-04
You must be trying to view the contents with different privileges than you used to mount it in GVFS. For example, if I try to view the contents of my GVFS shares using sudo, I can't even view the .gvfs directories and the symbolic links are shown as broken (e.g, using gksudo nautilus). As I understand it, this is because these shares are only available to the user that mounted them (so it's by design).

---

### Post by jeffimus on 2009-11-05
I'm fairly sure that I am using the right privileges, since the directory listings of the share and the symbolic link both show that they belong to me. I tried your example of using sudo to view the share and, as in your case, it was invisible. Anyway, I'll keep investigating. Thanks for staying with me this far!

---

### Post by michaelzap on 2009-11-05
> **jeffimus said:**
> I'm fairly sure that I am using the right privileges, since the directory listings of the share and the symbolic link both show that they belong to me. I tried your example of using sudo to view the share and, as in your case, it was invisible. Anyway, I'll keep investigating. Thanks for staying with me this far!

Do the symbolic links work using a normal Nautilus window?

---

### Post by jeffimus on 2009-11-05
> **michaelzap said:**
> Do the symbolic links work using a normal Nautilus window?

No. The icon has an X in the corner, and clicking on it produces an error message:

> The Link "share" is Broken. Move it to the Deleted Items folder?
This link cannot be used, because its target ".gvfs/share on fileserver" doesn't exist.

But its target does exist, because I can browse it at "~/.gvfs/share on fileserver" using the same Nautilus window.

---

### Post by michaelzap on 2009-11-05
You're using "share" and "fileserver" as generic names in place of your real ones, right? You don't have any funky characters in the real names, do you? I don't see any reason that your symbolic links would be broken, but perhaps if you posted the actual commands you ran and paths I might see something.

---

### Post by jeffimus on 2009-11-05
> **michaelzap said:**
> You're using "share" and "fileserver" as generic names in place of your real ones, right? You don't have any funky characters in the real names, do you? I don't see any reason that your symbolic links would be broken, but perhaps if you posted the actual commands you ran and paths I might see something.

My NAS box is actually called "fileserver" and the directory on it that I'm using is called "share". Not very imaginative, but it works.  I'm beginning to wonder if my Linux installation is just plain broken.  Maybe I'll try creating a new user account and experimenting in that. Thanks again.

---

### Post by michaelzap on 2009-11-05
> **jeffimus said:**
> My NAS box is actually called "fileserver" and the directory on it that I'm using is called "share". Not very imaginative, but it works.  I'm beginning to wonder if my Linux installation is just plain broken.  Maybe I'll try creating a new user account and experimenting in that. Thanks again.

Maybe try creating the symbolic links somewhere other than where you're trying now and try creating links to something other than the GVFS shares to see if those work as expected (and if not, you'll have more info).

And of course you need to mount your GVFS shares before the symbolic links will work. You did that, right?

---

### Post by jeffimus on 2009-11-06
> **michaelzap said:**
> Maybe try creating the symbolic links somewhere other than where you're trying now and try creating links to something other than the GVFS shares to see if those work as expected (and if not, you'll have more info).

And of course you need to mount your GVFS shares before the symbolic links will work. You did that, right?

Your suggestion to create more symlinks in other places was a good one.  I have cracked it.

In a nutshell: if you use a relative path as the target for a symlink, then it must be relative to the location of the symlink, not relative to where you are when you issue the command. Obvious really, but we both managed to overlook it.

I was in my home directory when I issued the command "ln -s .gvfs/... ~/fileserver/share".  I was expecting Linux to expand my relative path ".gvfs/..." to "~/.gvfs/..." but of course it didn't, it just dutifully created a symlink containing exactly what I typed. I failed to notice that in the "ls -la" listing. Thus, when I invoked the symlink, the OS  looked for a nonexistent directory called "~/fileserver/share/.gvfs...".  Even if I invoked the symlink from my home directory with "ls fileserver/share", it still would have been pointing to that non-existent path.  So there are two ways to create a valid symlink, both of which I have just successfully tested:

1. ln -s ~/.gvfs/share\ on\ fileserver ~/fileserver/share 
2. ln -s ../gvfs/share\ on\ fileserver ~/fileserver/share 

Version 1 is the one for sane people. Version 2 is a bit nutty but it works, and it illustrates how it is possible to use relative paths in symlinks if you really need to.

Thanks, MZ, for helping me to understand this!

---

### Post by michaelzap on 2009-11-06
> **jeffimus said:**
> Your suggestion to create more symlinks in other places was a good one.  I have cracked it.
...
Thanks, MZ, for helping me to understand this!

Glad you worked it out!

I always use absolute paths when creating symlinks (e.g., /mnt/share/, /home/zap/, etc.), so I've never noticed how relative symlinks behave either.

---

### Post by b0b138 on 2009-11-11
I bookmark mine in nautilus

---

### Post by jeffimus on 2009-11-11
> **b0b138 said:**
> I bookmark mine in nautilus

That only works if you're using Nautilus, or an application that opens files using Nautilus. There are lots of applications that use different file-chooser dialogs, which can only see files in the main filing system. Even some that use Nautilus seem to use a stripped-down version that doesn't list the bookmarks.

---

### Post by JUNiA on 2009-11-11
I can't get past step 4.  I double click on my workgroup and I can't access it, why?

> **NTolerance said:**
> **_Concept_**

The file manager in MS Windows has a nice feature called "Map Network Drive".  This allows you to permanently assign Samba shares to a drive letter which any program can access.  It can be made persistent across reboots.  This feature is tremendous when you have a Samba server on your network that has files you need to continuously access.  

**_Applicable Systems_**

This guide will explain how to do the same using an up-to-date Ubuntu Intrepid or Jaunty.  This guide will not work on Hardy unless _[this bugfix]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072")_ is backported to Hardy.  

**_Comparison to Other Methods_**

There is an _[ages-old method]("http://ubuntuforums.org/showthread.php?t=288534")_ which produces a similar result and involves editing /etc/fstab.  I don't like this method for a number of reasons, such as the fact that it's difficult, it involves storing your Samba password in plain text, and it exposes a _[nasty bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/90795")_ that can cause your system to hang on shutdown.

**_Procedure_**

1.  Select the "Network" option from the "Places" menu.  

2.  Select the "Windows Network" icon.

3.  Select the workgroup that your share resides in.

4.  Select the PC on your network that contains the share you want to access.  You will now see an authentication prompt.  Enter the correct username and password.  IMPORTANT:  Make sure to select the radio button that is labled "Remember forever".  This will permanently save your password in the GNOME keyring.  

6.  Select the "Connect" option.  You will now see a folder for each share that is available on the selected PC.  

8.  Select the folder you want to access.  You will now see a prompt regarding the keyring.  Select the "Always Allow" option.  The share is now temporarily mounted (will not survive a reboot) and your password is permanently saved and accessible in the GNOME keyring.

9.  The share should be visible in the "Places" menu on the left of the Nautilus file manager.  Select the eject icon to the right of the share to unmount it.  

10.  Now we will test out a command which will go into a script.  Open the Terminal from the "Accessories" submenu in the "Applications" menu.  

11.  Run this command in the Terminal while filling in the appropriate information within the <> symbols.
```
gvfs-mount smb://<pcname>/<sharename>
```Example:
```
gvfs-mount smb://desktop/sharedfolder
```The share should now be mounted again and will appear in the "Places" menu on the left side of the Nautilus file manager.  Select the eject icon to the right of the share to unmount it. 

12.  Now we will put that command in a script to be executed during startup.  In the Terminal, run this command to create the script:
```
gedit ~/sharemount.sh
```If you'd like to change the path or the filename of the script, feel free to do so.  

13.  Paste this into the GEdit window while filling in the appropriate information into the <> symbols.
```
#!/bin/sh
gvfs-mount smb://<pcname>/<sharename>
```Example:
```
#!/bin/sh
gvfs-mount smb://desktop/sharedfolder
```14.  Make the script executable by running this command in the Terminal:
```
chmod +x ~/sharemount.sh
```15.  Now let's add the script to GNOME startup.  Choose the "Startup Applications" option from the "Preferences" submenu located in the "System" menu.  

16.  Select the "Add" option.  Type a name of your choice in the "Name" field, browse to the path of the script in the "Command" field, and optionally add a comment to the "Comment" field.  Press the "Add" button to save your settings.

17.  Now log out and log back in or restart your PC.  Check the "Places" menu and the shares should be automatically mounted.

**_Usage Notes_**

The shares are mounted using _[GVFS]("http://fedoraproject.org/wiki/Features/Gvfs")_.  From the GNOME GUI, shares are accessible via the "Places" menu in Nautilus and the smb:// path in the address bar.  Command-line programs can access these shares via the ~/.gvfs path.

**_Uninstallation_**

If you'd like to remove these changes, follow the these two simple steps:

1.  Choose the "Startup Applications" option from the "Preferences" submenu located in the "System" menu.  Select the sharemount.sh script and press the "Remove" button.  

2.  Delete the script with the Terminal:
```
rm ~/sharemount.sh
```

---

### Post by tracyandskye on 2009-11-19
I'm kinda new to Ubuntu so I may be missing something simple.

I've been trying this with a new install of 9.10 on an XP network.  Here is what I entered:

gvfs-mount smb://bob/data%20(d)/

First I got an error regarding the ( so I got rid of the %20(d).  I then got an error that it failed to mount the windows share.  Is there a different way I should be doing this in 9.10?

---

### Post by NTolerance on 2009-11-20
I think there's a new bug going around, possibly with 9.10, that's making this process more difficult than it was in the past.  I'll update this thread when I've had a chance to do some testing.

---

### Post by michaelzap on 2009-11-20
> **NTolerance said:**
> I think there's a new bug going around, possibly with 9.10, that's making this process more difficult than it was in the past.  I'll update this thread when I've had a chance to do some testing.

I didn't have to do anything different in my fresh installation of 9.10 to make this work.

---

### Post by NTolerance on 2009-11-21
After some cursory testing it appears that the Windows share browsing feature in Nautilus was possibly broken in 9.10.  The good news is that if you know the name of the share that you want to access you can still type it into the Nautilus address bar like so:

smb://computer/sharename

Similarly, the same path should be accessible through the gvfs-mount command.  Keep in mind to use double quotes around the smb:// path if you have any spaces in the path.

---

### Post by tracyandskye on 2009-11-21
Thanks for the tip about the double quotes.  I was thinking that might cause some problem.  There seemed to be some problems consistently connecting to my Windows shares right after I installed 9.10, but after doing the first big update everything works now.  I can browse my Windows shares in Nautilus OK.  Just can't make this automount thing work.

---

### Post by NTolerance on 2009-11-21
> **tracyandskye said:**
> Thanks for the tip about the double quotes.  I was thinking that might cause some problem.  There seemed to be some problems consistently connecting to my Windows shares right after I installed 9.10, but after doing the first big update everything works now.  I can browse my Windows shares in Nautilus OK.  Just can't make this automount thing work.

Try it like this:

```
gvfs-mount "smb://bob/data (d)"
```

---

### Post by tracyandskye on 2009-11-21
OK, this is weird.  I tried it and it worked...one time.  Since then I can't get it to mount.  I don't get an error now in the terminal.  Just a > on the next line.  Still not having a problem mounting manually.

---

### Post by NTolerance on 2009-11-22
> **tracyandskye said:**
> OK, this is weird.  I tried it and it worked...one time.  Since then I can't get it to mount.  I don't get an error now in the terminal.  Just a > on the next line.  Still not having a problem mounting manually.

Paste the command you're using when you get the > prompt.

---

### Post by tracyandskye on 2009-11-22
I had some other problems with Karmic so I decided to reinstall.  So here is where I'm at.  The path to this drive in nautilus:

smb://bob/data%20(d)/

My attempts in the terminal:

voodoo@voodoo-desktop:~$ gvfs-mount “smb://bob/data (d)”
bash: syntax error near unexpected token `('
voodoo@voodoo-desktop:~$ gvfs-mount smb://bob/data
Error mounting location: Failed to mount Windows share
voodoo@voodoo-desktop:~$ gvfs-mount “smb://bob/data d”
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
voodoo@voodoo-desktop:~$ gvfs-mount “smb://bob/data (d)/”
bash: syntax error near unexpected token `('
voodoo@voodoo-desktop:~$ gvfs-mount smb://bob/data/
Error mounting location: Failed to mount Windows share
voodoo@voodoo-desktop:~$

---

### Post by NTolerance on 2009-11-22
> **tracyandskye said:**
> I had some other problems with Karmic so I decided to reinstall.  So here is where I'm at.  The path to this drive in nautilus:

smb://bob/data%20(d)/

My attempts in the terminal:

voodoo@voodoo-desktop:~$ gvfs-mount &#8220;smb://bob/data (d)&#8221;
bash: syntax error near unexpected token `('
voodoo@voodoo-desktop:~$ gvfs-mount smb://bob/data
Error mounting location: Failed to mount Windows share
voodoo@voodoo-desktop:~$ gvfs-mount &#8220;smb://bob/data d&#8221;
Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
voodoo@voodoo-desktop:~$ gvfs-mount &#8220;smb://bob/data (d)/&#8221;
bash: syntax error near unexpected token `('
voodoo@voodoo-desktop:~$ gvfs-mount smb://bob/data/
Error mounting location: Failed to mount Windows share
voodoo@voodoo-desktop:~$

Looks like you're using "backticks" or some other special characters instead of double quotes.  Try this:

```
gvfs-mount "smb://bob/data (d)"
```

Notice the vertical alignment of the quote symbols.

---

### Post by tracyandskye on 2009-11-22
That was it!  Thank you so much.  The quotes came from Open Office Writer.  I was doing copy/paste to put the strings together.  Weird to me because it's the same damn key!  Probably not that weird though if you're not a noob like I am.

---

### Post by cozmicharlie on 2010-01-15
Nice - thanks for the How-to.  Very simple and best of all it worked great!  Thanks for taking the time to write this and being so kind to share with the community.

=D>

---

### Post by Dareus on 2010-02-21
great how to!

very helpful!

---

### Post by EnlistedSquire on 2010-03-06
Hey, is anyone else having trouble getting samba shares to mount with gvfs in the latest Lucid alpha? I've reported a bug but there doesn't seem to be much interest in it.

[https://bugs.launchpad.net/bugs/530605](https://bugs.launchpad.net/bugs/530605)

---

### Post by Nixblicker on 2010-05-07
Thank you for this nice Howto,

i was experimenting with gvfs-mount for a couple of days now and am trying to mount shares via ssh on a different machine. I learned that i need to execute the following two lines before i use the actual mount command.
```
dbus-launch bash
/usr/lib/gvfs/gvfsd -r &
```
But i frequently encounter problems with the mount points in ~/.gvfs as they sometimes or better most of the times do not show up at all. If i manually test the mounts with 
```
gvfs-mount -l
```
they are listed correctly.
Does one of you have an idea how to deal with this and where the mounts get linked to if not in the above directory? 

Thx,
Nix

---

### Post by e-Claude on 2010-05-12
**Thanks** for your nice tutorial. I'm new to Ubuntu and don't know much about the shell and scripts and so on. 
You explained it so clearly that I managed to install it on my machine without any problem. I used it to ensure that the FreeNAS (running on my old 'recycled' PC) is well there at each startup !

Friendly greetings from Belgium ! Claude :)

---

### Post by Boondoklife on 2010-05-18
Hey just wanted to post up a script I put together that mounts your drives on login and it runs in the background to ensure the connection stays active. Just as with the OPs code, you need to mount it one time via nautilus and tell it to remember your password. You will need to do this for each share that is linked to your username.
Note: You can map bad users to a guest account on the server's smb.conf. This will allow you to connect to shares with guest privileges for shares that you did not provide a password for.

[Samba mounter]("http://dl.dropbox.com/u/4804818/scripts/gnome-samba-mount-startup")
[Startup Item]("http://dl.dropbox.com/u/4804818/scripts/gnome-samba-mount-startup.desktop")

I run into times where transferring many files can cause a connection drop and then I am hosed till it gets remounted. This takes care of that issue.

BEFORE YOU RUN IT!!!:
Please go into the file and change the paths that are to be mounted and get rid of unneeded entries. Lines 47-51 of the file, you can simply delete lines that you dont need or add more just follow the numbering scheme (0,1,2,3,n...). The syntax is outlined in the file.

The script requires gvfs be installed so install it via the manager or use:
```

sudo apt-get install gvfs

```NOTE: 
Please make sure you are running this as a startup application. 
If you  are having issues please change the DEBUG=0 line to DEBUG=1 and post the  output of the log file from "/tmp/gnome-samba-mount-startup.log"

To make the script available to all run
```

sudo cp ~/Downloads/gnome-samba-mount-startup /usr/bin
sudo chmod 755 /usr/bin/gnome-samba-mount-startup

```To put the startup item in place run
```

sudo cp ~/Downloads/gnome-samba-mount-startup.desktop /etc/xdg/autostart

```This assumes you downloaded the file to ~/Downloads

---

### Post by mujahied on 2010-05-19
thanks hmmm

---

### Post by cbanakis on 2010-05-30
I found a very easy workaround for automatically mounting windows shares on startup.

May not be the right way, but its easy enough.

Go to "System" - "Preferences" - "Startup Applications"

Then Click on Add

For Name, put whatever you want

Then for command, put "nautilus smb://(IP of share/share path)

For example, the shared drive on my windows server is called "my-terabytes" and my servers local ip is 192.168.1.30

So the command on mine says "nautilus smb://192.168.1.30/my-terabytes" (no quotes)

Everything works great
only downside, is every time I log in, that folder opens, but most of the time, thats where I'm going anyway

---

### Post by Boondoklife on 2010-05-30
> **cbanakis said:**
> I found a very easy workaround for automatically mounting windows shares on startup.

May not be the right way, but its easy enough.

Go to "System" - "Preferences" - "Startup Applications"

Then Click on Add

For Name, put whatever you want

Then for command, put "nautilus smb://(IP of share/share path)

For example, the shared drive on my windows server is called "my-terabytes" and my servers local ip is 192.168.1.30

So the command on mine says "nautilus smb://192.168.1.30/my-terabytes" (no quotes)

Everything works great
only downside, is every time I log in, that folder opens, but most of the time, thats where I'm going anyway

Really you should use the script I posted as if the drive become un-mapped, it will remap it for you. In addition it allows you to have just one script in your startup applications for all network mappings.

Plus you will not have the nautilus popup you are talking about.

---

### Post by Mark M. on 2010-06-29
> **NTolerance said:**
> Which topic title, keywords, tags, etc... do I need to get some interest in my awesome thread?

I signed up for an account on these forums for two reasons...  one, because I find myself coming back to this site as a source of problem-solving (I'm pretty new to Linux, being a crusty, old MS proponent)... and two, to say thank you for this thread.  It has definitely helped me get through mimicking "Map Network Drive" from Windows.

Thanks a bunch.  :)

=D>

---

### Post by justinmiller87 on 2010-07-08
This is great, except for one thing. The network share always seems to time out or just go offline for whatever reason. I keep all my media on a network drive and symbolically linked in order to access it. If the share goes down without my knowing, there goes the music playing. Is there some way to keep it from timing out or to restore itself if I come back from suspension?

---

### Post by Boondoklife on 2010-07-08
> **justinmiller87 said:**
> This is great, except for one thing. The network share always seems to time out or just go offline for whatever reason. I keep all my media on a network drive and symbolically linked in order to access it. If the share goes down without my knowing, there goes the music playing. Is there some way to keep it from timing out or to restore itself if I come back from suspension?

Go back to post #77, I put a script up that does just that. Not sure why they dont update the main page with it though.

---

### Post by justinmiller87 on 2010-07-10
> **Boondoklife said:**
> Go back to post #77, I put a script up that does just that. Not sure why they dont update the main page with it though.
Awesome. Hopefully that fixes the issue for me.

---

### Post by Boondoklife on 2010-07-10
Yea the script just polls to make sure your drives are still mapped, if they disconnect, then it remaps them back. I use it myself for a number of things, including my music collection.

In the media case, you may experience a connection drop and the audio/video will stop. However it will remap and then you can just click play again.

---

### Post by ColombianGold on 2010-07-12
Hi,

NTolerance thanks for the How-to, it seems simple and easy to follow...but I cant get it to work. Followed everything correctly but when I log in mount doesn't occur. I was wondering if my connection being wireless affects anything. When I log in, my network manager takes a couple of seconds to connect to my wireless router, maybe the script runs while its not connected....please help. I get no errors, where can I find a log with the information. Thank you.

Boondoklife, thank you too for your postings, regarding your script, do I just follow the original post procedure and use your script instead? 
Thanks for the help, these are the first scripts I use so not sure what to do.

CG

---

### Post by Boondoklife on 2010-07-12
Yea just save it as a script and put a link in the startup application to kick it off once you log in.

---

### Post by EdSp on 2010-07-26
Thanks for this very useful script Boondoklife. It works fine for me except it will only mount the first share in my list. 

SHARES[0]="server/share1"
SHARES[1]="server/share2"

...only share1 gets mounted. I've tried reversing the order - then only share2 gets mounted. I've copied the syntax exactly as written but only having a tiny amount of scripting ability I haven't been able to debug it. Any thoughts?

Thanks again and best regards.

---

### Post by Boondoklife on 2010-07-26
> **EdSp said:**
> Thanks for this very useful script Boondoklife. It works fine for me except it will only mount the first share in my list. 

SHARES[0]="server/share1"
SHARES[1]="server/share2"

...only share1 gets mounted. I've tried reversing the order - then only share2 gets mounted. I've copied the syntax exactly as written but only having a tiny amount of scripting ability I haven't been able to debug it. Any thoughts?

Thanks again and best regards.

That is very odd, could you please upload a copy of the script with your data? When you login can you mount the shares through nautilus and if so does it ask for a password? Remember, if it asks for a password you have to tell it to remember the password for this to work.

---

### Post by EdSp on 2010-07-26
There's no problem with mounting either share e.g. through nautilus, no password is needed. Whatever is assigned to SHARES[0] gets mounted, SHARES[1] doesn't play ball. The script below is saved as auto-map-shares and saved in /etc/init.d

#!/bin/bash
#Here you need to list your shares in the given format
SHARES[0]="readynas.local/audio"
SHARES[1]="readynas.local/video"

if [ -e /tmp/smbloginmounts ]; then
    exit
else
    touch /tmp/smbloginmounts
fi

#Setup the checking loop to make sure connections is always available
while [ 1 -eq 1 ]; do
sleep 30

for SHARE in ${SHARES
[*]}; do
    MOUNTEDAS="${SHARE##*/} on ${SHARE%%/*}"
    LS=`ls ~/.gvfs | grep -o "$MOUNTEDAS"`
    if [ "$LS" == '' ]; then
        gvfs-mount 'smb://'$SHARE
    fi
done
done

---

### Post by Boondoklife on 2010-07-26
Are you putting this in the statup-applications for your user? I really can not see why this would not connect both of them.

Try to run it from the terminal and see if you get any errors and let me know.

---

### Post by EdSp on 2010-07-26
The script is in /etc/init.d - its definitely working, I can unmount the one share and it automatically reappears. No errors are generated if run from the terminal and I couldn't see anything obvious in syslog.

How could I modify the script so it echos each attempt at mounting a share?

Cheers,
Ed

---

### Post by Boondoklife on 2010-07-26
Try to download this and run [this]("http://ubuntuone.com/p/Aj2/"), I updated the script to do some debug work. Change $DEBUG=0 to $DEBUG=1

then tell me the output of the log file @ /tmp/gnome-samba-mount-startup.log

---

### Post by noelnro on 2010-07-29
Thank you for the script.

The script mounts all the shares on my computer, but the loop keeps trying to mount the shares even if there are already mounted.

---

### Post by Boondoklife on 2010-07-29
> **noelnro said:**
> Thank you for the script.

The script mounts all the shares on my computer, but the loop keeps trying to mount the shares even if there are already mounted.

The script runs in a loop to check and see if the drives are still mounted, if not then it remounts them.

Please make sure you are running this as a startup application. If you are having issues please change the DEBUG=0 line to DEBUG=1 and post the output of the log file from "/tmp/gnome-samba-mount-startup.log"

---

### Post by cbstryker on 2010-07-29
Will this method also allow my windows partitions to appear along side "File System" if I go to "Tree" view mode? I've been trying to figure that out for a while.

---

### Post by Boondoklife on 2010-07-29
> **cbstryker said:**
> Will this method also allow my windows partitions to appear along side "File System" if I go to "Tree" view mode? I've been trying to figure that out for a while.

I am not sure as to exactly what you mean. If you are asking will the mounted shares show up under "Computer" then yes they will, see attached pic.

---

### Post by escoba00 on 2010-08-02
Hi I'm really a new Ubuntu user. I switch from windows and I like it. I just trying to map my Dlink 321 Nas. I can do it with Nautilus but when I log out and restart the computer I loose the mapping even thou I select "remember me for ever',  when I connect to the drive. Every time I have to repeat the same step. Can I do it automatically?

---

### Post by Boondoklife on 2010-08-03
> **escoba00 said:**
> Hi I'm really a new Ubuntu user. I switch from windows and I like it. I just trying to map my Dlink 321 Nas. I can do it with Nautilus but when I log out and restart the computer I loose the mapping even thou I select "remember me for ever',  when I connect to the drive. Every time I have to repeat the same step. Can I do it automatically?

The "remember me" is just so the password/username will be added to your keyring, it does not do the actual mounting. This script should work just fine for you as long as the NAS shares the files via samba (windows file sharing).

---

### Post by Morbius1 on 2010-08-03
> **escoba00 said:**
> Hi I'm really a new Ubuntu user. I switch from windows and I like it. I just trying to map my Dlink 321 Nas. I can do it with Nautilus but when I log out and restart the computer I loose the mapping even thou I select "remember me for ever',  when I connect to the drive. Every time I have to repeat the same step. Can I do it automatically?
This is a HowTo on the very thing you are trying to do. Go to the first page of this thread.

---

### Post by brianuk on 2010-08-05
Thank you **NTolerance** :D
I was mounting my NAS (Qnap) using a bookmark but this way is much more reliable.

I followed your instructions and created file mount_neptune.sh in my user directory.
```
gvfs-mount smb://neptune/public
ln -s /home/brian/.gvfs/"public on neptune" /home/brian/neptune

```

My problem of being able to save files from firefox and other apps into my nas, this was solved by m**ichaelzap**'s suggestion of using "**ln**" on the second line.

I would suggest adding this to the bottom of your very excellent tutorial. ;)

Thank you both again.

---

### Post by shardy on 2010-09-14
Question for the security folks:

Doesn't automounting a network filesystem like gvfs leave one open to a very close copy of the Windows DLL hijacking family of exploits? For example, if someone can create a malicious library and/or other binary using the $LD_LIBRARY_PATH or $LD_PRELOAD family of exploits, and put it in a shared directory, wouldn't everyone who automounted it be a sitting duck for a remote exploit, "drive by" style?

Reference: [http://securityetalii.es/2010/08/31/dll-hijacking-linux-windows-like/](http://securityetalii.es/2010/08/31/dll-hijacking-linux-windows-like/) (and a few years of similar discussions elsewhere on the Internet)

---

### Post by pf100 on 2010-11-02
I can't get the script because I can't log in to Ubuntu One because it sent me an invalid confirmation code. So I tried to get a new confirmation code sent and it seems not possible. I could have it sent to a different email account but I suspect the system is messed up right now and I don't want to try to get another invalid code sent to a different email. I only have so many emails. Could someone kindly pm it to me? Thanks in advance.

> **Boondoklife said:**
> Hey just wanted to post up a script I put together that mounts your drives on login and it runs in the background to ensure the connection stays active.

[LINK]("http://ubuntuone.com/p/Aj2/")

I run into times where transferring many files can cause a connection drop and then I am hosed till it gets remounted. This takes care of that issue.

NOTE: Please make sure you are running this as a startup application. If you  are having issues please change the DEBUG=0 line to DEBUG=1 and post the  output of the log file from "/tmp/gnome-samba-mount-startup.log"

---

### Post by Boondoklife on 2010-11-02
Try here [http://dl.dropbox.com/u/4804818/custom_commands/gnome-samba-mount-startup](http://dl.dropbox.com/u/4804818/custom_commands/gnome-samba-mount-startup)

---

### Post by pf100 on 2010-11-03
Boondoklife, thank you very much.

> **Boondoklife said:**
> Try here [http://dl.dropbox.com/u/4804818/custom_commands/gnome-samba-mount-startup](http://dl.dropbox.com/u/4804818/custom_commands/gnome-samba-mount-startup)

---

### Post by pwebster25 on 2010-11-14
Thanks for the great tutorial, NTolerance and other contributors.
I would like to replicate this for multiple users on a single computer. We join Ubuntu machines to an AD domain with Likewise-Open (Maverick Netbooks).  They are used in a classroom, so many kids use the same computer.  Each one needs to get to their own windows share on the server.

I'm thinking of this but I don't know how to put in the wildcard for the name of the user.

```
gvfs-mount smb://<servername>/<folder>/<%username> /home/DOMAIN/<%username>Windows-Share
```

How would I get this to replicate for each possible user?  On Windows machines it just uses a login script on the domain controller to map this drive.  I think it is possible to use "connect to server" in nautilus but these are 7th graders.  Not exactly practical to teach them to do this on each machine they end up using.

---

### Post by Hieronymus on 2010-11-15
Hi guys, 

I'm giving this a try. Works like a charm when I manually run the script after login. The issue I have at the moment is that the script is run before the wifi link is up and running. 

Is there any easy way to have the script run automatically AFTER the network is up and running?

---

### Post by michaelzap on 2010-11-15
> **Hieronymus said:**
> Hi guys, 

I'm giving this a try. Works like a charm when I manually run the script after login. The issue I have at the moment is that the script is run before the wifi link is up and running. 

Is there any easy way to have the script run automatically AFTER the network is up and running?

I actually started futzing with that the first time that I set this up on my laptop, but then I realized that I often take my laptop to other locations where these shares can't be mounted anyway. So in the end I decided to just mount them manually and I put a shortcut in my main menu. If you're sure that you want it to mount them automatically anyway, the best method that I found was just adding a 30-second pause to the script command.

---

### Post by pwebster25 on 2010-11-15
What's the best way to add a 30 second pause to your script?
I'm fairly new to scripting but am happy to learn.  I've done a couple bash scripts for server backups.

Thanks
Paul

---

### Post by michaelzap on 2010-11-15
> **pwebster25 said:**
> What's the best way to add a 30 second pause to your script?
I'm fairly new to scripting but am happy to learn.  I've done a couple bash scripts for server backups.

Thanks
Paul

I'm no bash expert, but I think that you just do 
sleep 30 && gvfs-mount...

---

### Post by Hieronymus on 2010-11-15
> **pwebster25 said:**
> What's the best way to add a 30 second pause to your script?
I'm fairly new to scripting but am happy to learn.  I've done a couple bash scripts for server backups.

Thanks
Paul

This one I do know :-)just add sleep 30 to your script, like so:

```

#!/bin/sh
sleep 30
```

---

### Post by Morbius1 on 2010-11-15
> **Hieronymus said:**
> Hi guys, 

I'm giving this a try. Works like a charm when I manually run the script after login. The issue I have at the moment is that the script is run before the wifi link is up and running. 

Is there any easy way to have the script run automatically AFTER the network is up and running?
I think that the script that Boondoklife wrote above is capable of doing that or you can just use gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by Hieronymus on 2010-11-15
> **Boondoklife said:**
> Hey just wanted to post up a script I put together that mounts your drives on login and it runs in the background to ensure the connection stays active.

[Samba mounter]("http://dl.dropbox.com/u/4804818/scripts/gnome-samba-mount-startup")
[Startup Item]("http://dl.dropbox.com/u/4804818/scripts/gnome-samba-mount-startup.desktop.desktop")

I run into times where transferring many files can cause a connection drop and then I am hosed till it gets remounted. This takes care of that issue.

NOTE: 
Please make sure you are running this as a startup application. 
If you  are having issues please change the DEBUG=0 line to DEBUG=1 and post the  output of the log file from "/tmp/gnome-samba-mount-startup.log"

Boondok, 

Could you post the script again? The provided link is dead...

Thanks in advance, 

H

---

### Post by Boondoklife on 2010-11-15
Updated the script for yas:

CHANGES:
1) Added a wait variable, if you need the script to wait for a connection or what ever just replace the 0 with a higher number. This will let the script wait on its first run for that many seconds before continuing.

2) No need to change the username. Now the script will pull the current username and use it as part of the drive mapping. This should be more effective in a campus/domain environment.

3) I also added a Link to a startup item you can use to make the drive mappings occur for all users.

Let me know how it works out for yas

[LINK TO MY MAIN POST]("http://ubuntuforums.org/showpost.php?p=9322776&postcount=77")

---

### Post by cmallam on 2010-11-30
running the script in a terminal gives

gnome-samba-mount-startup: 12: function: not found

that would be 'domount'

here's the log
Ran as: cmallam
Polling shares.
Mounting 192.168.1.119/Volume_1
Mounting 192.168.1.139/Volume_1
Mounting 192.168.1.139/Volume_2
Mounting 192.168.1.139/Volume_3
Mounting 192.168.1.139/Volume_4
Polling shares.
Mounting 192.168.1.119/Volume_1
Mounting 192.168.1.139/Volume_1
Mounting 192.168.1.139/Volume_2
Mounting 192.168.1.139/Volume_3
Mounting 192.168.1.139/Volume_4
Polling shares.

There is a file in tmp called smbloginmounts and it is a zero byte file.  Looking at the script, i am assuming that the NAS would be mounted under my home as SHARE or something like that.  Clicking on 'Computer' on the desktop opens to reveal only the local harddrives and the DVD Drive.

Do you have any ideas?

---

### Post by Boondoklife on 2010-11-30
It actually shows up as network folders in computer. Can you attach your script.

---

### Post by cmallam on 2010-11-30
i think i found the problem.  i went back to the first post in this thread, and followed thru the steps.  turns out gvfs was not installed.  once i installed that, everything works fine.

Thanks for the help!

Hmmm, this still doesn't solve my original problem, which is that when i open Geegie (GQView) to find and edit pictures, it still doesn't show any of these remote drives.  Guess i have to play with fstab again.

---

### Post by Boondoklife on 2010-11-30
> **cmallam said:**
> i think i found the problem.  i went back to the first post in this thread, and followed thru the steps.  turns out gvfs was not installed.  once i installed that, everything works fine.

Thanks for the help!

Thought I had that listed in the script, thanks for catching that. I have updated it with the requirement of gvfs.

---

