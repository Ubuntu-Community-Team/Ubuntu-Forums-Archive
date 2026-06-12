---
title: "Just installed server. Restart and I have a GUI?"
date: 2021-06-09
forum: New to Ubuntu
---

### Post by tomtheappraiser on 2021-06-09
I am new to Linux, but read online that it's pretty easy to setup a media server with an old laptop. I followed the guide and installed Ubuntu 20.04.2 LTS on an old laptop along with Plex Server. The instructional showed how to set it so that closing the laptop cover doesn't shut the server down.  I figured out how to mount an external drive and was feeling pretty confident. Last night, however, when I was updating the Plex server I noticed that it said I needed to restart. So I issued the command reboot from SSH. It shut down but didn't reboot. So I opened  the laptop and manually restarted. It went to the UEFI settings where I found that the 1st boot option was still to the USB, so I raised the OS to #1 spot.
When it finally restarted it went to a GUI log in screen. When I typed in my password it brought me into a desktop environment.  When I went to my other laptop and checked on Plex, it was running fine, so I just left it as it was. However, after about 5 minutes it goes into sleep mode and the Plex server shuts down.
I think I MIGHT have accidentally installed a GUI when I was trying to mount my external drive. Many of the instructionals said you have to install Gnome Disks first which I kept trying to do from shell.  I figured it just didn't work so I went on until I figured out how to mount the external drive the right way (without Gnome Disks).  
Can someone help me put it back to just being a server again that I can close the top on and let it run?
As you can probably tell, I am a newbie and would appreciate any help especially if it was ELI 5'd.

---

### Post by grahammechanical on 2021-06-09
Start from the beginning and install all over again. We do not know which tutorial you followed. 

In Linux there is such a thing as "dependencies." These are libraries that an application depends upon to run. So, when we install an application/program if those dependencies are not already installed the installation process will install them. Otherwise the application will be broken.

When we install Ubuntu Desktop we get the Disks application as a default application. It is part of the Gnome Desktop Environment. By installing Gnome Disks you also authorised the installation of everything that Gnome Disks depends upon. That is the Gnome Desktop Environment and the Gnome Shell.

If you want to use Ubuntu 20.04 Server as the basis for this media server then you will need to learn how to do things using Linux commands. Sorry. It is tough, I know.

Regards

---

### Post by ActionParsnip on 2021-06-10
Can you please give a link to "the guide"

---

### Post by tomtheappraiser on 2021-06-10
Here is the guide I used to set it up originally. [https://www.youtube.com/watch?v=lXcfKTNObOo](https://www.youtube.com/watch?v=lXcfKTNObOo)
As for when I installed Gnome Disks, I don't know which one I used because I was looking through a ton of How-Tos trying to figure out how to mount an external drive in Ubuntu server.

---

### Post by ActionParsnip on 2021-06-10
If you install gnome disks then it will install the entirety of the Gnome DE as a dependency.

---

### Post by TheFu on 2021-06-10
Be careful following random guides on the internet.  Often times, they are created and posted by non-experts. Could be someone with 1 day more knowledge than you have.

"Disks" is not the way to mount storage for Plex.  I've been running plex server for years and used xbmc before that. You'll want to mount storage through the /etc/fstab file.  Also, you'll want the external disk NOT to use NTFS as the file system. Go for ext4 if you don't know a linux file system that you need. It is the default and a reasonable choice.  I have 32+TB using ext4 on my plex server.  I might choose ZFS if I were setting it up again, but that isn't for people new to Linux - perhaps not even for people with intermediate Linux skills.  Why not NTFS?  With Plex, you'll want to have both security and support for multiple userids having access to modify the files, while not leaving them open to the world.  You'll probably want 0770 directory permissions and 0660 file permissions for all the media files - photos, music, videos.  Also, different userids will need to be put into a single group to make file management easier from both a remote system over sftp or locally if you connect over ssh.

And be certain to split up your media into different directories, including top level directories for each. Do not mix movies and TV and home videos, for example.  Each show/movie needs to be in a dedicated directory - TV shows probably should be split into season subdirectories too.

Lastly, don't allow any spaces for punctuation characters in the filenames. This is a general recommendation, since writing little scripts to process hundreds of files with 1 command are easier to create when the default delimiter, a space, isn't part of file names.  At this stage, you probably don't script, but when you do, you'll thank me.  I use "_" characters and all media center programs I've used, about 10 of them, handle that just fine.

---

### Post by tomtheappraiser on 2021-06-16
OK, I reinstalled Ubuntu Server and mounted the external drive (sdb4) because it was previously formatted in windows.  Now, I have just purchased a new 2tb drive and am trying to mount that. I was going to open up a new ticket, but since you have experience with plex, I thought maybe you could kind of guide me on what to do.
I have all of my TV shows, Music, and Movies backed up on a WD 2tb My passport. 
So, should I just start clean and wipe the 1tb drive (which was the original windows formatted drive I was asking about in this post) and start over?
Like I said, I have everything backed up for right now, so I could set it up in the correct way. I would just need some step by step help to do it.

Thanks

---

### Post by TheFu on 2021-06-16
Format with ext4.
Mount using the fstab.
Make the top level directory owned by your userid.  
Add your userid to the plex group.
Change the group on the mounted directory to be plex. Set the setgid on the directory so all subdirectories are forced to be in the "plex" group.
Change the permissions so the user and group members have write access.  You want 770 permissions on this directory - as stated above. If you don't understand what that means or the other stuff above - LEARN. After trying to learn, ask, but use specific questions with exact examples.
**Sudo is needed for everything above this line.**

**Sudo is **NOT** needed for everything below this line.**  
Create TV, Movies, Music, Photos, and Home_Video sub directories.
Put your content into the correct sub-directories.  A new folder will be needed for each movie, each TV series. How you organize Music and Photos is up to you.  I use Genre/Artist/Album/ for Music and YYYY/MM/dd-Event/ for photos.
Whatever you do, don't allow more than 500 files in a single directory. That's asking for corruption and data loss.

Here's 1 disk in my media:
```
$ ll /d/D1/
total 152
drwxrwx---   11 thefu thefu  4096 Jan 30 11:15 ./
drwxr-x---   10 root  root   4096 Jan 19 19:00 ../
drwx------    2 root  root  16384 Feb 16  2014 lost+found/
drwxrws--- 1286 thefu plex  61440 May  6 18:08 M/
drwxrws---   17 thefu plex   4096 Jun  1 17:51 R/
drwxrws---   99 thefu plex   4096 May 26 09:58 T/
drwxrws---    4 thefu plex   4096 Aug 23  2017 V/
drwxrwx---    5 thefu plex   4096 Mar 27  2014 Photos/
drwxrwx---    6 thefu plex   4096 May 10 12:56 ebooks/
```

Note the permissions for the different directories.
The Photos and ebooks aren't really managed by Plex. I use Calibre for ebooks and a custom perl photo web-app for photos.

Here's what the mount looks like for this single partition (I use LVM, so it isn't really a partition, but that's close enough for here):
```
$ df -Th  /d/D1
Filesystem                     Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-lv_media ext4  3.5T  3.5T   17G 100% /d/D1

```

When you make backups, 50% is the data and 50% are the permissions, ACLs, xattrs, owner and group membership.  You'll likely want to change your backup method to ensure all those are included.

All the subdirectories need similar group permissions - group write and group setgid, as shown above. Mess that up and things will become painful.

---

