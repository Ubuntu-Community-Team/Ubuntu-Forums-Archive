---
title: "Needing help with BASH script yet again."
date: 2007-09-24
forum: Programming Talk
---

### Post by brennydoogles on 2007-09-24
ok, so I am writing a bash script that will need to be run by a friend from far away, so i need to have the script working correctly on a computer that I can't test it on, and it needs to work there the first time. Here is the deal: There are some files on his old computer that he needs, but he will only have one chance to get them before the HD is formatted. The computer is not able to be booted into windows (it's current OS), and he can't remember if he used the default username of "OWNER" or if he made it his first name, or first and last name. So what I need to do is write a script that will chack to see if a directory exists (such as Documents and Settings/owner/My Pictures) and copy that to a folder on the desktop, or if possible have it autodetect his USB hd and copy directly to it (which would be the best option.). The way I have it planned right now is to have bash check to see if all of the files he needs are in existence under each username (possibly by checking if the username exists, and if it does checking for My Pictures and stuff afterwards), and if they exist just do a cp to the correct place. Because i don't know if the HD will be a /dev/hda1 or a /dev/sda1 I will also need to autodetect that. Anyone feel able to help??


P.S.-- The only files he wants are the contents of My Pictures and his saved Firefox/IE settings. Any help would be greatly appreciated.

---

### Post by mssever on 2007-09-24
Detecting all those things would probably take more time to write than they're worth. The easiest thing would be to talk him through the process on the phone. I've done that several times. Another option would be to have him install openssh-server and give you his IP address, then you can SSH into his machine and copy the files directly.

---

### Post by brennydoogles on 2007-09-24
> **mssever said:**
> Detecting all those things would probably take more time to write than they're worth. The easiest thing would be to talk him through the process on the phone. I've done that several times. Another option would be to have him install openssh-server and give you his IP address, then you can SSH into his machine and copy the files directly.

well, i am unfamiliar with the use of SSH. Does it need to be installed on both the local and remote machines?? Another thing is that I cannot guarantee that he will have a working internet connection during the process, and his cellphone does not work where the computer is located (he is giving it to his younger siblings, hence rescuing data and formatting the drive). Basically his only hope as a poor non-computer-savvy-type is for me to  create a DEB, let him install it, and have it do everything for him (except for possibly moving one folder to his USB drive). Any takers??

---

### Post by mssever on 2007-09-24
SSH is pretty simple to use if you know the command line. But if there's no Internet connection...

To find out which partition is the Windows partition, you could simply try to mount the various options. For example (I haven't tested this): ```
for i in /dev/{h,s}da1; do
    mount -t ntfs -o defaults,ro $i /mnt
    status=$?
    [ $status -eq 0 ] && break
done
```
You'll probably want a bit more error checking. Also, this code assumes the NTFS filesystem.

Once you get the proper partition mounted, you can cd to /mnt/Documents\ and\ Settings and use a for loop to loop through all the subdirectories hunting for what you want. If you simply put the files in a directory on the desktop and let your friend manually copy them, you'll save yourself some effort.

---

### Post by nanotube on 2007-09-24
if your friend is so computer illiterate that he's unable to locate a folder, and drag it over to another drive, then can you rely in him to double-click the .deb, and then to open a terminal and to run the bash script? :)

if his cellphone doesn't work, call the landline, or let him borrow a cellphone that does work in that area - from, e.g., the people he's giving the comp to :)

seems that the script is 1 - would take too much time to write/test to make it foolproof and 2 - would still be more likely to screw things up or at least fail to do the backup than doing things by hand, given so many unknowns about the location of the files and disks...

---

### Post by ukripper on 2007-09-24
Easiest way..just ask him to use knoppix Cd or get hold of it or  download it.. it will detect ntfs partion and mount it ..from there he can transfer anything on ntfs partition to USB save you hassle of bash scripting it to USB.

[http://en.wikipedia.org/wiki/Knoppix](http://en.wikipedia.org/wiki/Knoppix)

---

### Post by brennydoogles on 2007-09-24
> **nanotube said:**
> if your friend is so computer illiterate that he's unable to locate a folder, and drag it over to another drive, then can you rely in him to double-click the .deb, and then to open a terminal and to run the bash script? :)

if his cellphone doesn't work, call the landline, or let him borrow a cellphone that does work in that area - from, e.g., the people he's giving the comp to :)

seems that the script is 1 - would take too much time to write/test to make it foolproof and 2 - would still be more likely to screw things up or at least fail to do the backup than doing things by hand, given so many unknowns about the location of the files and disks...

I am not worried about his ability to drag and drop files, I am more worried about him knowing enough about the operating system to find all of the files he is trying to find in a timely manner. I am trying hard to make sure that this goes smoothly, because some of the photos on that computer are photos that are very important to my wife and I. As for writing the script, if I can find a way to have an if statement check if a directory exists and perform an action if it does, I can walk him through the rest through an email/prior phone call.

---

### Post by Compyx on 2007-09-24
Since your friend is using Windows, how do you propose he runs a bash-script?

I think your friend would be better off just removing the old hard drive and putting a new one in.

---

### Post by mssever on 2007-09-24
> **brennydoogles said:**
> As for writing the script, if I can find a way to have an if statement check if a directory exists and perform an action if it does, I can walk him through the rest through an email/prior phone call.
You can find all kinds of possibilities for if statements from man test. For example, ```
if [ -d "some_directory" ]; then
    #the directory exists; do something
fi
```
But you might find a loop easier. At any rate, if you can possibly arrange to talk him through the process on the phone, you'll have a lot less trouble, and you won't need the script.

---

### Post by brennydoogles on 2007-09-24
> **Compyx said:**
> Since your friend is using Windows, how do you propose he runs a bash-script?

I think your friend would be better off just removing the old hard drive and putting a new one in.

By booting into an Ubuntu live cd and running the script from terminal.

> You can find all kinds of possibilities for if statements from man test. For example,
```

if [ -d "some_directory" ]; then
    #the directory exists; do something
fi

```
But you might find a loop easier. At any rate, if you can possibly arrange to talk him through the process on the phone, you'll have a lot less trouble, and you won't need the script.

Ok, although it will be dirty, I think I can make a script that will be functional enough from this. Thanks!

---

### Post by brennydoogles on 2007-09-25
Ok, I have a theoretical script setup now, with just a few pieces missing (which I'm hoping you all will be able to help me with), and I would like to see if anyone can pick out any glaring mistakes I've made. Here is a super-commented up version so far:

```
#!/bin/bash
##############################################################################################################################################################
##############################################################		Variable Declaration		######################################################
##############################################################################################################################################################

safemk () {
if [ ! -d $1 ]; 
  then mkdir -p $1; 
  chmod +rw $1; 
fi
}
#This will create a folder on the desktop for all of the rescued data to go into
TARGET=/home/$USER/Desktop/photos
#Here is where Firefox information is stored, with a variable to be named for the username, and which device (sda1 or hda1) we need to be browsing
MPATH=$DEVC/Documents\ and\ Settings/$NAME/Application\ Data/Mozilla/Firefox/Profiles
#Same thing, but My Pictures
PPATH=$DEVC/Documents\ and\ Settings/$NAME/My\ Documents/My\ Pictures
#Check to see if the Directory in question exists. If it does, Copy it to $TARGET
safecp () {
if [ -d $1 ];
  then cp -r $1 $TARGET/
fi
}

act () {
  safecp $MPATH
  safecp $PPATH
}
##############################################################################################################################################################
########################################################	Scripted Action		######################################################################
##############################################################################################################################################################

safemk $TARGET

#Attempt to mount windows partition, but doesn't the live cd automatically detect and mount all installed Disks??
for i in /dev/{h,s}da1; do
    mount -t ntfs -o defaults,ro $i /mnt
    status=$?
    [ $status -eq 0 ] && break
done

#Now it would be possible to use the let function name the output of {fdisk -l piped to grep to find out which drive we need} to $DEVC, but I'm not sure how to implement that. Any Ideas??


#Now, by systematically changing the value of $NAME to every possible username (should be two or three at most), and running the act function, we should be able to have a relatively good chance at covering all of our bases. Is there anything I have missed??
```

Any help would be greatly appreciated!!

---

### Post by mssever on 2007-09-25
```
#!/bin/bash
##############################################################################################################################################################
##############################################################        Variable Declaration        ######################################################
##############################################################################################################################################################

[COLOR=Red]#This function is unnecessary. Just use mkdir -p.[/COLOR]
[COLOR=Red]#[/COLOR]safemk () {
[COLOR=Red] #[/COLOR]if [ ! -d $1 ]; 
[COLOR=Red]#[/COLOR]  then mkdir -p $1; 
[COLOR=Red]#[/COLOR]  chmod +rw $1; 
[COLOR=Red] #[/COLOR]fi
[COLOR=Red] #[/COLOR]}
#This will create a folder on the desktop for all of the rescued data to go into
[COLOR=Red]#[/COLOR]TARGET=/home/$USER/Desktop/photos
[COLOR=Red]TARGET="$HOME/Desktop/photos"[/COLOR]
#Here is where Firefox information is stored, with a variable to be named for the username, and which device (sda1 or hda1) we need to be browsing
[COLOR=Red]# You don't need $DEVC. Just mount (or symlink) to a
# known location.
[/COLOR]MPATH=[COLOR=Red]/mnt[/COLOR]/Documents\ and\ Settings/$NAME/Application\ Data/Mozilla/Firefox/Profiles
#Same thing, but My Pictures
PPATH=[COLOR=Red]/mnt[/COLOR]/Documents\ and\ Settings/$NAME/My\ Documents/My\ Pictures
#Check to see if the Directory in question exists. If it does, Copy it to $TARGET
safecp () {
if [ -d $1 ];
  then cp -r $1 $TARGET/
fi
}

act () {
  safecp $MPATH
  safecp $PPATH
}
##############################################################################################################################################################
########################################################    Scripted Action        ######################################################################
##############################################################################################################################################################

safemk $TARGET

#Attempt to mount windows partition, but doesn't the live cd automatically detect and mount all installed Disks??
[COLOR=Red]# If I remember correctly, it doesn't automount NTFS
#partitions. But I might be wrong. You'll need to
#account for that in your script.[/COLOR]
for i in /dev/{h,s}da1; do
    mount -t ntfs -o defaults,ro $i /mnt
    status=$?
    [ $status -eq 0 ] && break
done

#Now it would be possible to use the let function name the output of {fdisk -l piped to grep to find out which drive we need} to $DEVC, but I'm not sure how to implement that. Any Ideas??
[COLOR=Red]#Just either: mount the partition to a known location
#(such as /mnt) or symlink it to the proper place. The
#loop above will take care of that for you[/COLOR]


#Now, by systematically changing the value of $NAME to every possible username (should be two or three at most), and running the act function, we should be able to have a relatively good chance at covering all of our bases. Is there anything I have missed??
[COLOR=Red]#How can you determine every possible username?
#Just loop through all the directories under Docs and
#Settings and you'll have what you need.[/COLOR]
```
EDIT: By the way, $MPATH and $PPATH are incorrect, because $NAME isn't defined before the are. But it would be a lot easier to forego the absolute path anyway and just copy from your loop using relative paths.

---

### Post by nanotube on 2007-09-25
note also that on a livecd, the /home/Desktop is in the virtual ram disk. so if you try to copy gigs and gigs of files from some disk to $HOME/Desktop/somedir you are going to run out of space (unless that old computer you refer to has gigs and gigs of ram to store it in.

so if you have more files than you have ram, you'll have to copy directly to a usb disk, not to the livecd desktop. 

note also that even if they can fit, unless you move them off the desktop to some more permanent disk, they will disappear on the next reboot - that's the nature of the livecd for you. :)

---

### Post by brennydoogles on 2007-09-25
> **nanotube said:**
> note also that on a livecd, the /home/Desktop is in the virtual ram disk. so if you try to copy gigs and gigs of files from some disk to $HOME/Desktop/somedir you are going to run out of space (unless that old computer you refer to has gigs and gigs of ram to store it in.

so if you have more files than you have ram, you'll have to copy directly to a usb disk, not to the livecd desktop. 

note also that even if they can fit, unless you move them off the desktop to some more permanent disk, they will disappear on the next reboot - that's the nature of the livecd for you. :)

The plan is indeed to copy all of the files to an external HD before the reboot, but because I don't know where the drive will automount, I am not sure how to automate the copy. If there is only one internal drive, will an external drive default to h/sdb1?? If so, I could script for the files to be copied directly to it (assuming it is FAT32 or mounted with ntfs-3g)

to mssever-- Thank you for all of the pointers, I will move the variables for the paths down to after naming the $NAME variable. Because we only need very specific data, it would be a waste of time and space to copy more than that. As for how we will determine every possible username, the computer belongs to a friend of mine, so we have it narrowed down to a few, he just can't remember which he used (e.g. his full name, his first name, or the windows default "owner"). I will play around a bit more, and see if I can't get something else working out. Thanks for all of the help!!!!

---

### Post by mssever on 2007-09-25
> **brennydoogles said:**
> The plan is indeed to copy all of the files to an external HD before the reboot, but because I don't know where the drive will automount, I am not sure how to automate the copy. If there is only one internal drive, will an external drive default to h/sdb1?? If so, I could script for the files to be copied directly to it (assuming it is FAT32 or mounted with ntfs-3g)It isn't possible to predict the name reliably. {h,s}db1 is likely, but you need more info. One way to accomplish this would be to make a list of the directories in /media, then prompt the user to insert the drive and press a key. After waiting several seconds, make another list of the directories in /media. The new one is the flash drive.

Nanotube raised another important point. Suppose you copy the files to the desktop, then something happens--such as a power outage--before they can be copied to the flash drive. Those files would be lost permanently.

> As for how we will determine every possible username, the computer belongs to a friend of mine, so we have it narrowed down to a few, he just can't remember which he used (e.g. his full name, his first name, or the windows default "owner").My point was that you don't need to know all the possible users. You might be able to do something like this: ```
for i in "/mnt/Documents and Settings"/*; do
  for j in "$i/My Documents/My Pictures/"*; do
    cp -ir "$j" /media/USB_Drive/pictures
  done
done
```You can do something similar for Firefox, but I don't remember where Windows keeps the Firefox profile. I used the -i flag of cp so that files won't get accidentally overwritten.

---

### Post by brennydoogles on 2007-09-25
> **mssever said:**
> It isn't possible to predict the name reliably. {h,s}db1 is likely, but you need more info. One way to accomplish this would be to make a list of the directories in /media, then prompt the user to insert the drive and press a key. After waiting several seconds, make another list of the directories in /media. The new one is the flash drive.

Nanotube raised another important point. Suppose you copy the files to the desktop, then something happens--such as a power outage--before they can be copied to the flash drive. Those files would be lost permanently.

My point was that you don't need to know all the possible users. You might be able to do something like this: ```
for i in "/mnt/Documents and Settings"/*; do
  for j in "$i/My Documents/My Pictures/"*; do
    cp -ir "$j" /media/USB_Drive/pictures
  done
done
```You can do something similar for Firefox, but I don't remember where Windows keeps the Firefox profile. I used the -i flag of cp so that files won't get accidentally overwritten.

I see the point about the power outage possibly losing the files. Copying directly to the drive would be twice as fast, as well as safer, so I am all about it. As for the interactive flag on the cp, wouldn't he then have to hit y+enter for every file to be copied? Is there a way to have it only prompt in the case of overwrite? Also, I believe that the for loops may be a viable solution, but we should make a few adjustments first such as
```
for i in "/mnt/Documents and Settings"/*; do
  for j in "$i/My Documents/My Pictures/"*; do
    [COLOR="Red"] safemk /media/USB_Drive/$i[/COLOR]
    cp -ir "$j" /media/USB_Drive/pictures
  done
done
```

So that multiple users (such as the All Users folder and the possible Administrator folder) do not cause the folders to be overwritten for each new user. Thanks a million for the help!!

---

### Post by mssever on 2007-09-25
> **brennydoogles said:**
> As for the interactive flag on the cp, wouldn't he then have to hit y+enter for every file to be copied? Is there a way to have it only prompt in the case of overwrite?cp -i only prompts in case of an overwrite.

Good catch below. One further change (note the double quotes around the variables; You need them if there's any possibility that the value could contain a space):
```
for i in "/mnt/Documents and Settings"/*; do
  [COLOR=Red]user="$(basename "$i")"[/COLOR]
  [COLOR=Red][COLOR=Black]safemk /media/USB_Drive/[/COLOR]"$user"[/COLOR]/pictures
  for j in "$i/My Documents/My Pictures/"*; do
     cp -ir "$j" /media/USB_Drive/[COLOR=Red]"$user"[/COLOR]/pictures
  done
done
```

---

### Post by brennydoogles on 2007-09-26
> **mssever said:**
> cp -i only prompts in case of an overwrite.

Good catch below. One further change (note the double quotes around the variables; You need them if there's any possibility that the value could contain a space):
```
for i in "/mnt/Documents and Settings"/*; do
  [COLOR=Red]user="$(basename "$i")"[/COLOR]
  [COLOR=Red][COLOR=Black]safemk /media/USB_Drive/[/COLOR]"$user"[/COLOR]/pictures
  for j in "$i/My Documents/My Pictures/"*; do
     cp -ir "$j" /media/USB_Drive/[COLOR=Red]"$user"[/COLOR]/pictures
  done
done
```

ok. This seems like the most logical and failsafe way to do this so far. The path to the data we need from firefox is this:  \Documents and Settings\"$user"\Application Data\Mozilla\Firefox\Profiles  more or less. Inside the profiles folder are directories for any other existing users, which contain the all important bookmarks and settings. When i return from class later I will try to implement this code and post back. Thanks!

---

### Post by mssever on 2007-09-26
This code is still too complicated. Let's simplify it:
```

for i in "/mnt/Documents and Settings"/*; do
  user="$(basename "$i")"
  drive="/media/USB_Drive/$user"
  mkdir -p "$drive/firefox_profiles"
  cp -ir "$i/My Documents/My Pictures" "$drive/pictures"
  cp -ir "$i/Application Data/Mozilla/Firefox/Profiles"/* "$drive/firefox_profiles"
  done
done
```A reminder: when you get the script finished, be absolutely sure to boot up a couple of Windows computers from a live CD yourself and run the script on them to verify that it actually works.

---

### Post by brennydoogles on 2007-09-26
> **mssever said:**
> This code is still too complicated. Let's simplify it:
```

for i in "/mnt/Documents and Settings"/*; do
  user="$(basename "$i")"
  drive="/media/USB_Drive/$user"
  mkdir -p "$drive/firefox_profiles"
  cp -ir "$i/My Documents/My Pictures" "$drive/pictures"
  cp -ir "$i/Application Data/Mozilla/Firefox/Profiles"/* "$drive/firefox_profiles"
  done
done
```A reminder: when you get the script finished, be absolutely sure to boot up a couple of Windows computers from a live CD yourself and run the script on them to verify that it actually works.

That was the plan, but I only have one windows computer to test it on. Would anyone else be willing to test it once it is complete?

---

### Post by brennydoogles on 2007-09-26
Ok, here is what we have now, including the simple change of making the Firefox settings folder hidden (because while he is in Linux he does not want to screw up his previous settings). Everything seems to be in order. For ease of use I am going to make a basic debian installer, so that the script can be run easily by typing savepictures in terminal. Here is the code:

```
#!/bin/bash
#Rescue Photos and settings from Windows
safemk () {
if [ ! -d $1 ]; 
  then mkdir -p $1; 
  chmod +rw $1; 
fi
}

sudo aptitude install ntfs-3g

for i in /dev/{h,s}da1; do
    mount -t ntfs -o defaults,ro $i /mnt
    status=$?
    [ $status -eq 0 ] && break
done

for i in /dev/{h,s}db1; do
    mount -t ntfs-3g -o defaults,ro $i /media/USB_Drive
    status=$?
    [ $status -eq 0 ] && break
done

for i in "/mnt/Documents and Settings"/*; do
  user="$(basename "$i")"
  drive="/media/USB_Drive/$user"
  safemk "$drive/.firefox_profiles"
  cp -ir "$i/My Documents/My Pictures" "$drive/pictures"
  cp -ir "$i/Application Data/Mozilla/Firefox/Profiles"/* "$drive/.firefox_profiles"
  done
done

exit 0
```

Any objections??

---

### Post by mssever on 2007-09-27
> **brennydoogles said:**
> For ease of use I am going to make a basic debian installer, so that the script can be run easily by typing savepictures in terminal.Making a deb is more trouble than it's worth. Why not just execute the script directly? Or, make a .desktop file that will run it. You can find sample .desktop files in /usr/share/applications and pre-installed icons in /usr/share/icons/human. Just copy a .desktop file and modify it. Be sure to tell it to run in a terminal. With a .desktop file, your friend won't even need to open a terminal.

```
#!/bin/bash
#Rescue Photos and settings from Windows
[COLOR=Red]#safemk is unnecessary. First, mkdir -p will create
#any directories that are needed. It's perfectly OK to
#call mkdir -p even if the target directory already
#exists. Also, the chmod call doesn't accomplish
#anything. Ubuntu's default umask for directories is
#022, which creates proper directory permissions of
#755. You don't need to manually set some--but not
#all--of those same permissions. Furthermore, your
#friend's flash drive, which is the only place this gets
#called, is almost certainly either FAT32 or NTFS.
#Setting permissions on either of those filesystems has
#no effect.
#
#If you decide to keep this function anyway, surround
#your "$1" variables with double quotes. That way,
#they're safe even if their value happens to contain a
#space.
[/COLOR][COLOR=Red]#[/COLOR]safemk () {
[COLOR=Red]#[/COLOR]if [ ! -d $1 ]; 
[COLOR=Red]#[/COLOR]  then mkdir -p $1; 
[COLOR=Red]#[/COLOR]  chmod +rw $1; 
[COLOR=Red]#[/COLOR]fi
[COLOR=Red]#[/COLOR]}

[COLOR=Red]#This won't work unless your friend has Internet
#access. Otherwise, you'll need a flash drive formatted
#as FAT32. You only need ntfs-3g for the flash drive;
#the standard ntfs that the mount command below
#uses supports read-only access, which is all you need
#for the Windows partition.[/COLOR]
sudo aptitude install ntfs-3g
[COLOR=Red]################################[/COLOR]

for i in /dev/{h,s}d[COLOR=Red]{[/COLOR]a[COLOR=Red],b}[/COLOR]1; do
    [COLOR=Red]#Let's discard mount's error messages so we don't worry
    #your friend.[/COLOR]
    mount -t ntfs -o defaults,ro $i /mnt[COLOR=Red] 2>/dev/null[/COLOR]
    status=$?
    [ $status -eq 0 ] && break
done

[COLOR=Red]#Error checking: make sure that we mounted something
if (mount | grep -v '/mnt' >/dev/null); then
    echo "I couldn't find your Windows partition." 2>&1
    echo "I'm giving up without accomplishing anything." 2>&1
    read -n 1 -p "Press any key to exit: "
    exit 1
fi
[/COLOR]
[COLOR=Red]# Running this loop twice might produce error messages
#[/COLOR]for i in /dev/{h,s}db1; do
[COLOR=Red]#[/COLOR]    mount -t ntfs-3g -o defaults,ro $i /media/USB_Drive
[COLOR=Red]#[/COLOR]    status=$?
[COLOR=Red]#[/COLOR]    [ $status -eq 0 ] && break
[COLOR=Red]#[/COLOR]done

for i in "/mnt/Documents and Settings"/*; do
  user="$(basename "$i")"
  drive="/media/USB_Drive/$user"
  [COLOR=Red]#[/COLOR]safemk "$drive/.firefox_profiles"
  [COLOR=Red]mkdir -p "$drive/.firefox_profiles"[/COLOR]
  cp -ir "$i/My Documents/My Pictures" "$drive/pictures"
  cp -ir "$i/Application Data/Mozilla/Firefox/Profiles"/* "$drive/.firefox_profiles"
  done
done

[COLOR=Red]#Notify the user that we're finished. Also, in case we're
#running via a .desktop file, we'll wait for a keypress before
#exiting so the terminal window doesn't disappear suddenly.
echo "Finished copying files."
read -n 1 -p "Press any key to exit: "
[/COLOR]
[COLOR=Red]# The exit 0 is optional. It's the default way to exit.[/COLOR]
exit 0
```

---

