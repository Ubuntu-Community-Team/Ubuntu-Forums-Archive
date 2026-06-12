---
title: "Problem mounting windows partitions"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by vvozar on 2013-01-05
Hello Ubuntu community,

I am new to Linux, just installed Ubuntu 12.04 a week ago. But today I was "playing" with Storage device manager (GUI app), and made some mess. Before installing Ubuntu I have partitioned my hard disk like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229616&stc=1&d=1357390586[/IMG]

What I wanted to do is to set Ubuntu to mount windows partitions when booting. So I downloaded Storage device manager, and following some tutorial about mounting  (at first) tried to mount "/sda2" partition with name "windows". When I clicked Mount button (and Apply) in Storage device manager, nothing happened. Then I tried one more time, but I think now I entered name "windows c" (not sure). After that have restarted Ubuntu and got message saying :"An error occurred while mounting /media/windows. Press S to skip mounting or M for manual recovery.".
Wanting to repair these errors I have opened Storage device manager again, and still it didn't recognize /sda2 as mounted partition. So I repeated mounting process again for /sda2 and also /sda3 but now I didn't change the name (left default).

I know mounting settings are written in /etc/fstab file, which looks like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=229620&stc=1&d=1357392192[/IMG]

In "/media" folder I have now four empty folders: "sda2", "sda3", "windows" and "windows c". In Nautilus file manager, under Devices category are 125GB File system, and 52Gb File system, and if I click on any of those, I am getting message "Unable to mount 125 (or 52) GB Filesystem". And also when starting Ubuntu, that message i previously mentioned is showing.

Now, I can't access my data on ntfs partitions, and getting this message on startup.

From articles about mounting partitions in Linux, I thought that if I want from Linux  to edit and save (not only read) some files that are on "ntfs" partitions, first need to mount those partitions. (correct me if i'm wrong please). Obviously I did mount "sda2" and "sda3", but I thought that now I will get folders with same names containing everything they had in Windows OS. (and I got empty folders).

How could I reset settings about mounting partitions, so i dont get this message on startup and so i could use data (folder and files) I have on my "/sda3" (windows D:), and "/sda2" (some folders on windows C: like are Desktop, My documents...)?

Apologize for too long posting.
Thanks in advance.

---

### Post by vanadium on 2013-01-05
I already see at least one mistake in your /etc/fstab: the tool you used (Storage device manager) apparently does not handle the spaces correctly.

* Open your /etc/fstab file in an editor as root user. To do that, open a terminal and type "gksudo gedit /etc/fstab" then enter. You will need to provide your user password.

* The editor appears with the contents of your /etc/fstab. Look for the line starting with /dev/sda2. After /media/windows, remove the "  C". Save the file and exit the editor.

* Now create the proper mountpoint (if it is not yet there) and delete the one you won't use (if it is there). In the terminal, type
```

sudo mkdir /media/windows
sudo rmdir /media/windows\ C

```
You need to provide your user password again when running the first command. If it tows an error message stating that the directory already exists, then all is fine. If the second command throws the error that the directory did not exist, then that's also fine.

* Now see whether your changes were OK, and whether you can mount /dev/sda2: in the terminal, give the command:
```

sudo mount -a

```
There should not be any output on the screen. If there is, post the message here. If there isn't, you should see the contents of your Windows partition in /media/windows.

---

### Post by Impavidus on 2013-01-05
I don't use any GUI for mounting windows partition, but it's quite easy by editing /etc/fstab.

You've got two windows partitions, /dev/sda2 and /dev/sda3 (apart from the boot partition). In your present configuration the mountpoints /media/windows, /media/sda2 and /media/sda3 are configured for them, but they are not mounted. They will be mounted there automatically when you give a command to mount them.

Before you modify your fstab make a backup of the old version, so you can restore things when you do something wrong. Open a terminal and type```
sudo cp /etc/fstab /etc/fstab.backup
```(It will ask for your password. When you type it nothing will appear on the screen.)
Next start modifying your fstab
```

gksudo gedit /etc/fstab

```Put in that file lines like these (after the ones refering to linux file systems):
```

#This will mount /dev/sda2 on /media/sda2
/dev/sda2 /media/sda2 ntfs auto,rw 0 0
#You can substitute any other mountpoint, but don't put a space in it.
#It will give errors. Escape with \040.
#The following line will mount /dev/sda3 on /media/windows d
/dev/sda3 /media/windows\040d ntfs auto,rw 0 0

```You can remove the old lines refering to the ntfs partitions. Save the file and close gedit. Make sure all directories exist. You can use```
man fstab
man mount
``` to get descriptions of the fstab format and the available options (fourth column). In the manual page for mount you'll have to scroll down to about line 500.

From now on the windows partitions should get mounted automatically when booting.

---

### Post by Morbius1 on 2013-01-05
***[COLOR=Blue]If I might make a suggestion[/COLOR]***: No more screenshots please unless someone asks for it. It makes it very hard for someone to give you specific recommendations since we have to transcribe it and will most likely make a mistake somewhere as I have probably done.

If you want to post how your fstab ( or any file ) looks run the cat command followed by the path of the file name and post the output: 
```
cat /etc/fstab
```[COLOR=Blue]**Anywho**[/COLOR], As far as I can tell these are your ntfs statements:
> /dev/sda2 /media/windows C ntfs nls=iso8859-1,users,umask=000,user 0 0
/dev/sda2 /media/sda2 ntfs nls=iso8859-1,users,noauto,umask=000,user 0 0
/dev/sda3 /media/sda3 ntfs nls=iso8859-1,users,noauto,umask=000,user 0 0There's 4 things wrong with it:

(1) The "windows C" thing that *[COLOR=Blue]vanadium[/COLOR]* pointed out above.
(2) The use of /dev/sdxy instead of UUID or LABEL
(3) The use of users and user as options when not using the noauto option.
(4) Multiple references to the same partition with different mount points ( sda2 ) and different options.

*** I would replace the 3 lines with these 2 lines. I am assuming you used *[COLOR=Blue]vanadiums[/COLOR]*'s suggestion of creating a new mountpoint for sda2:
```
UUID=some-long-number-1 /media/windows ntfs defaults,uid=1000,umask=000,nls=utf8,windows_names 0 0
UUID=some-long-number-2 /media/sda3 ntfs defaults,uid=1000,umask=000,nls=utf8,windows_names 0 0
```*** To find the correct values for some-long-number-1 and 2 run the following command:
```
sudo blkid -c /dev/null
```*** If you currently have any of these partitions mounted unmount them.

*** Then run the following command to test for errors and mount them again:
```
sudo mount -a
```[COLOR=Blue]**NOTE**[/COLOR]: Do not use Storage Device Manager to do this since it has no idea what a UUID or LABEL is. You will have to edit the fstab file directly as root:
```
gksu gedit /etc/fstab
```
[COLOR=Blue]**NOTE2**[/COLOR]: I'm not a keen believer in mounting the partition that the Windows OS lives in as read / write. It it was my system I would mount it read only. You can do that with the new ntfs statement for /media/windows by changing umask=000 to umask=222.

---

### Post by vvozar on 2013-01-06
Thank You all for your recommendations and help,
I think I understand now how mounting works and how is* fstab* file organized.

As [COLOR=Blue]*vanadium*[/COLOR] have noticed right away, *Storage Device Manager* doesn't handle the spaces correctly.
Following your suggestions I did next (first deleted everything and then configured again - proper way):

*  deleted all three lines in *fstab* about mounting */dev/sda2* and* /dev/sda3*
*  removed all directories in */media* folder - "old" mounting points (sda2, sda3, windows and windows C)
*  created two folders named *windows-C *and* windows-D* in *Home* folder ("new" mounting points)
*  mounted */dev/sda2 *and */dev/sda3* partitions to these folders:
      *fstab* mounting sda's part:
> UUID-of-/dev/sda2 /home/username/windows-C ntfs auto,ro 0 0
UUID-of-/dev/sda3 /home/username/windows-D ntfs auto,rw 0 0[COLOR=Blue]*Morbius1*[/COLOR] recommended that partition on which one Windows is installed should be configured as read-only - reasonable. Although I didn't use attributes he suggested (*umask=000 to umask=222*), i just put *ro* option for windows C, and *rw* option for windows D partition (together with *auto* option).

Now I can access all data right away from *Home* folder (similar to My Computer in Windows).

Few more questions:
1. What do *uid=1000,umask=000,nls=utf8,windows_names* options in *fstab* exactly represent? (as [COLOR=Blue]*Morbius*[/COLOR] suggested)
2. Should I mount CD-ROM (and maybe anything else) also this way?
3. Now, when Ubuntu loads, all partitions mounts correctly. I can access my windows (C and D) partitions from mounted points (in Home folder) or clicking on hard disk icons in Laucher. Is there a way to remove these partition icons from Launcher?

Thanks

---

### Post by TheFu on 2013-01-06
fdisk shouldn't be used on modern HDDs.
Use **parted **or **gparted** instead. These tools handle 4K sector HDDs AND 512b properly, automatically.

**Spaces should be avoided** in any labels, directories, file names on UNIX systems. Yes, they can work, but there will always issues when you don't afford any time. Spaces cause issues for some scripts too, if the script writer is lazy ... like I am.  Learn it, accept it, know it.

Seems like all the mounting things are being addressed by others. Good luck.

---

### Post by vvozar on 2013-01-06
I did use Gparted.

---

### Post by Morbius1 on 2013-01-06
> 1. What do uid=1000,umask=000,nls=utf8,windows_names options in fstab exactly represent? (as Morbius suggested)
I will explain these options in reference to what you have now:
> UUID-of-/dev/sda3 /home/username/windows-D ntfs auto,rw 0 0 ** **[COLOR=Blue]defaults[/COLOR]** Contains auto and rw

** [COLOR=Blue]**uid=1000**[/COLOR] Transfers ownership from root to you.

*I do that so you don't get errors when you try to send something to the trash and to make it simpler to create a samba share using nautilus.*

** **[COLOR=Blue]umask=000[/COLOR]** is actually in the defaults for both statements.

[I]Unlike a linux filesystem ( ext4 ) ntfs partitions have no Linux ownership and permissions bits. So Linux has come up with a way to create a "view" of the partition that makes it appear as though it does ( fuse ). The default "view" created has all permissions = 777 ( rwxrwxrwx ). 

"umask" represents the permissions that you want to remove. So if I want to make it read only I would subtract a 2 ( 7 - 2 = 5 ). Having a umask = 000 removes nothing - that's why I like to state it explicitly.[/I]

** [COLOR=Blue]**windows_names**[/COLOR]

*This prevents you from creating or adding a file to an ntfs partition that has a name that contains characters that WIndows cannot interpret. If this were a solitary ntfs partition in an all Linux box it's not needed. If you dual boot then without windows_names the file will be lost when you boot back into Windows.*

---

### Post by TheFu on 2013-01-06
> **vvozar said:**
> Few more questions:
1. What do *uid=1000,umask=000,nls=utf8,windows_names* options in *fstab* exactly represent? (as [COLOR=Blue]*Morbius*[/COLOR] suggested)

At this point, 15 yrs ago someone would type a 4 character response and nothing else.

**RTFM.**

We don't do that anymore, at least we try NOT to do it, but is is still apropos.  RTFM defined: [https://en.wikipedia.org/wiki/RTFM](https://en.wikipedia.org/wiki/RTFM)

This is a suggestion to ***read the manual*** which is already installed on your system. Why?
* No matter how helpful we are in the forums or google search results, YOUR system has manual pages which cover the exact software versions loaded on YOUR machine. 
* Sometimes the normal version and what is on your box are different.
* Sometimes we forget to write  important details in our responses.  A missing switch can wipe out a complete OS.
* Man pages have **KNOWN ISSUES** section that we might assume you already know. This can be bad.
* Man pages have a **SEE ALSO** section.
* Reading the man page for a command usually has some option that you were not aware of previously.  Heck, every time I read the man page for **mount** or** ssh**, I still learn something new. These are two of the most important man pages.
* Give a man a fish and he eats for a day, teach a man to fish ....

So, you are convinced to read the manual, right?  How do you do that?
Lots of ways:
* Drop to a terminal, $ **man {command}**
** so you would type **man mount** in this case.
* What if you don't know the name of the command?
** the "man" system has a search feature called **apropos**
** $ **apropos ntfs** will return all the man pages with "ntfs" in them. Cool?
** $ **man -k ntfs**  is the same as apropos

If you need more help on using the manuals, $ **man man** is just awesome! I'm serious. **man** has lots of subtle information built-into the pages. If you don't at least skim the man page for man, then you'll be missing 80% of that subtle information.

Of course, google is also your friend, so knowing how to ask google a good question is a great skill to have too.

I should point out that the man page for ntfs mounting has lots of known issues and tips to map Windows users to UNIX users. Good stuff.

---

### Post by Morbius1 on 2013-01-06
Missed a question:
> Is there a way to remove these partition icons from Launcher?Is that what the daffy vertical task bar thingy is on the left side of the desktop in Unity ( can you tell I'm a Xubuntu user :p )?

Back in the Golden Age of Linux if you create mount points in /home/your-user-name or /media a mount icon was created on the desktop. No doubt the Launcher in Unity does that now. 

Back then to prevent this from happening you created a mount point anywhere else - /mnt was popular since it sort of made sense. So try moving your mount point to /mnt/Windows-C for example and the icon should go away.

***Note***: To make it easier to find in nautilus you can go to /mnt/Windows-C and Bookmark it so it ends up on the left side panel of nautilus.

---

### Post by Morbius1 on 2013-01-06
And this one:
>  2. Should I mount CD-ROM (and maybe anything else) also this way?No. The system handles this automatically. All external devices are mounted in /media automatically. There is a difference depending on what version of Ubuntu you are using:

From the Eisenhower administration to 12.04 it mounted it to: /media/LABEL

In 12.10 it mounts it to /media/your-user-name/LABEL

[I][COLOR=Blue]As an interesting side[/COLOR] note to the way 12.10 does this and in keeping with my "Golden Age of Linux" remark take a look at the permissions of /media/your-user-name:
> ls -dl /media/morbius
drwxr-x---+ 2 root root 4096 Jan  6 12:18 /media/morbiusThat doesn't look right does it? Only root will get past that directory so how the heck will morbius get past it. Well, funny story. See that "+" at the end of the permissions? That indicates Access Control Lists are being used. So what are the real permissions of this folder:
> 
getfacl /media/morbius
getfacl: Removing leading '/' from absolute path names
# file: media/morbius
# owner: root
# group: root
user::rwx
user:morbius:r-x
group::---
mask::r-x
other::---
Only morbius ( and root ) will get past the folder to see the things auto-mounted there.

They've taken something simple and made it complex. But "the more they overthink the plumbing, the easier it is to stop up the drain" so it has it own set of bug reports.[/I]

---

### Post by vvozar on 2013-01-07
[COLOR=Blue]Morbius1[/COLOR], your suggestions are really helping me a lot.
I remounted win-partitions to */mnt *folder, and those storage icons in Launcher have dissapearred (I have also bookmarked mount points in File manager).

And [COLOR=Blue]Morbius1[/COLOR], thank you for your descriptive answers regarding "folder permissions", I will study that, especially now after[COLOR=Blue] TheFu[/COLOR]'s last reply, I think I know just exact place where to look for informations. 

"[COLOR=Blue]TheFu[/COLOR] has (definitely) taught me how to fish, and showed me where are all the fishes hiding ;)."

Marking thread as SOLVED.
Thank You all for help, for your patience and time. 
Good luck.

---

