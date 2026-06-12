---
title: "Deleted sbin and bin symlinks, now system wont start, how do i replace them?"
date: 2024-02-16
forum: New to Ubuntu
---

### Post by aloneandconfused on 2024-02-16
I accidentally deleted sbin and bin symlinks in the root directory '/' when using the rm command for something else, then when i rebooted it stalls on the kubuntu load page. I have used a live usb to access the drive, then go into terminal to use the "sudo ls -s /usr/bin /bin" command, except this doesnt work, i have to use the long mount label string, so its like [FONT=monospace][COLOR=#000000]sudo ls -s [/COLOR][/FONT][COLOR=#000000][FONT=monospace]/media/mycomputer/4b3b112a-3659-4fe5-b398-ad87e6589ef4/usr[/FONT][/COLOR][FONT=monospace][COLOR=#000000]/bin /media/mycomputer/4b3b112a-3659-4fe5-b398-ad87e6589ef4/bin[/COLOR]
[/FONT]
This created the symlinks in the root folder, but it still doesnt boot, i think because of the long mount strings i had to use to create them but im not an expert at this so i dont know. I have also tried installing kubuntu on another drive and copying the symlink files over but even when i use 'sudo cp -r' to copy the files onto my transfer usb it will only create a 0b file. 

Is there another way to get the symlink back?

---

### Post by aloneandconfused on 2024-02-16
Figured it out, instead of having to create the symlinks from inside the live cd on the root of the drive, or attempt and fail at copying them over from another copy of kubuntu, i opened terminal from inside the live cd, and did 

cd ..
cd .. (until i got to the "/" directory where bin and sbin symlinks are)
sudo cp -r /bin /directpathtodrive-125-61-18-k1261-2616 (look at properties of the mounted drive to get this exact info)
sudo cp -r /sbin /directpathtodrive-125-61-18-k1261-2616

and it copied over the symlinks from the live cd distro into the root of the broken drive. Now it boots. I hate linux what a stupid OS. One simple command and you are facing a nightmare, windows never has this problem unless you are really trying hard to delete something.

---

### Post by Bashing-om on 2024-02-16
aloneandconfused; Well ??
> 
Is there another way to get the symlink back?


Show us what there is now to work with.
Identify the target and mount it from the liveUSB.
like so:
Boot the liveUSB to a terminal; there in terminal run:
```

sudo fdisk -lu ## to identify the target on the install
sudo mkdir /mnt/looksee
sudo mount /dev/sda2 /mnt/looksee ## adjust sda2 if needed to the actual target in your use case
ls -al /mnt/looksee//

```

copy/paste this output back onto the liveUSB - (or someplace even safer)

back out of the mount:
```

sudo umount /mnt/looksee

```

Now while still in the LiveUSB post the ls -al result back to this thread - Please between code tags to retain formatting:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]see here what we can do
[/INDENT]

---

