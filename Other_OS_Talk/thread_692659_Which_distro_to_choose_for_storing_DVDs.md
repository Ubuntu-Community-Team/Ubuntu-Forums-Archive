---
title: "Which distro to choose for storing DVDs?"
date: 2008-02-10
forum: Other OS Talk
---

### Post by tr333 on 2008-02-10
I have a collection of DVDs that I would like to store on a computer so I can play them on a TV from the computer.  Which linux distro would be best for this?  I have heard about Mythbuntu and LinuxMCE, but i'm not sure if thats what i'm looking for (I could be wrong about that).

---

### Post by yabbadabbadont on 2008-02-10
Mythbuntu, or similar (other MythTV based distros), is most likely what you are looking for.  They provide functionality similar to Windows Media Center Edition.

---

### Post by tr333 on 2008-02-10
The Mythbuntu/MythTV requirements say that it needs a tv tuner card.  Do I need this for just playing back DVDs?  I was only wanting to connect via s-video from the graphics card output.

---

### Post by yabbadabbadont on 2008-02-10
In that case, you can probably get away with just about any linux distribution.

---

### Post by tr333 on 2008-02-11
In that case, what is the best method to store the dvds on the system?  I currently have them stored as VIDEO_TS folders on a portable HDD.  Is there any software available for managing a collection of DVDs?

---

### Post by yabbadabbadont on 2008-02-11
I don't have any suggestions on management software.  I probably would have stored them as ISO images, but it doesn't really matter as there are players that can handle them as they are now.  Both xine and vlc can play them back from the folders and both also support the DVD menus.

You might want to research that MythTV tuner requirement some more.  I think that is only needed if you wish to record.  I'm pretty sure that MythTV can be setup to playback collections of movie files, music, and dvd images that already exist on the disk.  As I said, you probably just need to do a little more research on the matter.

---

### Post by tr333 on 2008-02-11
Thanks for the info on this!

EDIT:  Is a DVD iso file any different to a CD iso file?  I thought I heard somewhere that iso images couldn't be larger than 4GB?  If not, then I suppose I could just grab the data with "dd"?

```
$ dd if=/dev/cdrom of=/path/to/iso/file
```

---

### Post by yabbadabbadont on 2008-02-11
I used 'ISO' meaning a DVD image.  I should have been more clear.  :)  However, I think that mkisofs can do it, when using the "-dvd-video" option.  As I don't have access to a dual layer DVD writer, I've never bothered to test it.  ;)

I think your dd command will work, but again, I haven't tried it with a DVD.  If it did work, the image would still have the CSS encryption as well as region coding and prohibited user operations (PUO).  None of these should cause trouble, although I find the PUOs annoying and strip them out when I backup a disc.

By the way, while I appreciate it, there isn't any reason to thank every response I make to your thread.  Enough is as good as a feast.  (as they say in Mary Poppins :lol:)

---

### Post by yabbadabbadont on 2008-02-11
Well, I just did a test.  dd doesn't work.  It craps out after a couple hundred megabytes.  OK, so I mount the disc as UDF and try to "cp -r".  I/O errors.  I think the disc has to be decrypted using libdvdcss while copying or it won't work.  Personally, when I backup a disc, I use DVDFabHDDecrypter under WINE.  It has never failed on me yet.  I haven't used it in a while, but I don't think that it produces an image, but a decrypted VIDEO_TS folder.  (which is what you already have I believe)  You've piqued my curiosity now.  I'm going to have to run a test and see if mkisofs can produce an ISO file that is larger than 4GB.  (but tomorrow, it's 4:30AM for me.  well past my bedtime :D)

---

### Post by tr333 on 2008-02-11
Thanks for doing the research on this.  At the moment, i'm just using MacTheRipper on an old Powerbook 12" to get the VIDEO_TS folder.

---

### Post by tr333 on 2008-02-11
It looks like MythTV can play back DVDs using the MythVideo component.  It can play DVD .iso images and also [VIDEO_TS](http://www.mythtvtalk.com/forum/archive/o_t/t_2631) folders with a small hack.

I have genisoimage installed and I think I should be able to create a DVD iso (UDF format, instead of ISO9660 for a CD) with the following command:

```
$ genisoimage -dvd-video -o /path/to/image.iso /path/to/VIDEO_TS/folder
```

---

### Post by koleoptero on 2008-02-11
I'd use just about any distribution with a media center application like elisa. If you also want to save some space on your hard drive you can compress your dvd's to movie files. Thoggen DVD ripper is a good starting point that offers only the essential choices (size or quality and cropping) with size being the only one you'll need. It is available in the ubuntu repositories (add/remove applications).

Also if you have a nice wireless mouse that can operate the computer from where you're sitting in front of the tv, you can just use VLC to playback anything (or xine, or mplayer).

---

### Post by tr333 on 2008-02-11
Thanks for the tip on the mouse.  I don't have to bother with a IR remote now :)

---

### Post by yabbadabbadont on 2008-02-12
Well, I finally got around to testing this.  I used a dual-layered DVD as the source and ripped it to my drive producing a VIDEO_TS directory with 7.7GB of files.  Since mkisofs with the -dvd-video option expects to find VIDEO_TS in a subdirectory, I ran it on the parent directory of VIDEO_TS.  It worked fine and produced a UDF ISO image file that xine had no problem playing.  (including menus and what not)  It should be noted that I used mkisofs from cdrtools and not the one provided by cdrkit.  I think cdrkit is the default on Ubuntu and simply creates a symlink between genisofs and mkisofs.

---

### Post by tr333 on 2008-02-12
[http://packages.ubuntu.com/feisty/otherosfs/mkisofs](http://packages.ubuntu.com/feisty/otherosfs/mkisofs)

It seems like genisoimage is a fork of mkisofs, which has now been moved to the multiverse repository.  The current version of genisoimage in the gutsty repositories does not provide the symlink to mkisofs.

---

