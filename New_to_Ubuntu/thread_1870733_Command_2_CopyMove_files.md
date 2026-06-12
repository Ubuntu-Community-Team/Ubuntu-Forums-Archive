---
title: "Command 2 Copy/Move files???"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by Ex-windows on 2011-10-27
Hi folks, can any one direct me to any post relating to how I can SAFELY move my files, photos and music to an external hard drive.  Many of the photos are irreplaceable. I would also like to make a complete copy (iso image?)b4 and in addition 2 moving. Any help would be greatly appreciated. I have 1 folder in my home directory called " 1 Main Folder". I hope to just Move/copy This folder.

Thanx in advance

---

### Post by westie457 on 2011-10-27
Hi, Clonezilla should be able to that for you. Also copy and paste works. And if it should go horribly wrong there is 'photorec', part of testdisk, to recover them from your internal drive to the usb drive.

Hope this helps.

---

### Post by Vaphell on 2011-10-27
photos are irreplaceable and you have them in only 1 copy? Apparently they are not as irreplaceable as you say they are ;-) Ever heard of disk failure?

move is simply copy+delete on success, but if for whatever reason changes made to destination storage were not saved permanently (eg. data buffered, not yet physically written + loss of power) data would be lost in the void.
Simplest way would be to copy and remove only after confirming that everything works. I wouldn't even delete, more copies = safer data.

There are also tools like rsync which are much more robust.
[http://en.wikipedia.org/wiki/Rsync](http://en.wikipedia.org/wiki/Rsync)

---

### Post by decoherence on 2011-10-27
The command to copy a folder full of files is

cp -R myfolder /path/to/destination/myfolder

To move a folder it is

mv myfolder /path/to/destination/myfolder

However you could also just drag and drop the folder on to your backup drive. That's perfectly safe.

As to what Vaphell said, typing 'sync' in the terminal after doing the copy will immediately write the data to the disk. Then again, by the time you open a terminal and type 'sync' it has probably been written anyway.

rsync is mostly useful when you want to synchronize one folder with another. It will detect the changes between them and only copy the things that have changed. There's no real benefit to using it the first time but after that, it is a godsend. Especially for moving things over a network.

---

### Post by enkay009 on 2011-10-27
You don't need to generate an ISO.

However you should know that backups aren't perfect and can fail. If you've got something really important you want to keep, make redundant backups (i.e. back it up on more than one hard drive).

---

### Post by Ex-windows on 2011-10-27
Hi and Thanx,   
2 westie457, I will try the clonezilla asap. copy and paste does not seems keep the integrity of all the files and thier names.
2 Vaphell, I guess I should have mentioned that I do have copies lol (many) on a terabyte external drive and have all the files on our other netbooks and 1 desktop.  I was using Archive Manager and The problem seems to be that the "copies" get corrupted and sometimes have missing files. We have aprx 14,000 personal pix and apx. 2500 music tracks and then regular files.
 You mentioned rsync I recently downloaded Grsync. Is this a reliable progrm?? I do love the speed. TY 

:KS

---

### Post by decoherence on 2011-10-27
> **Ex-windows said:**
> Hi and Thanx,   
2 westie457, I will try the clonezilla asap. copy and paste does not seems keep the integrity of all the files and thier names.


whatwhatwhat? If that's the case, it's a serious problem and a bug, or whatever media you're copying to has problems, or it has some strange, ancient filesystem like FAT16.

File integrity between two hard drives should never be a concern. If the system is not able to properly copy the files, it should give you an I/O related error.

---

### Post by Ex-windows on 2011-10-27
Wow where did everbody come from so quickly
I need to learn to type faster :KS
Thank you as well decoherence n enkay009. In the name of redundancy I shall do them all lol. And as vaphell mentioned "disk failure" is what I am getting worried about thus my desire to move and maybe start keeping ALL the original files etc on the terabyte and putting the "copies " on our comps.
Thank all of you

---

### Post by Ex-windows on 2011-10-27
> **decoherence said:**
> whatwhatwhat? If that's the case, it's a serious problem and a bug, or whatever media you're copying to has problems, or it has some strange, ancient filesystem like FAT16.

File integrity between two hard drives should never be a concern. If the system is not able to properly copy the files, it should give you an I/O related error.
Yes I believe it may be somewhat ancient and a bit overwieght lmao. I have to recheck as at one time I reformatted it to ext3 and for some reason I felt a need to go back (dont quite remember why.)

Also what happened to the Thank you button???  And how do I mark as solved. Wow I have been gone a while lol

---

### Post by donkyhotay on 2011-10-27
> **Vaphell said:**
> photos are irreplaceable and you have them in only 1 copy? Apparently they are not as irreplaceable as you say they are ;-) Ever heard of disk failure?

move is simply copy+delete on success, but if for whatever reason changes made to destination storage were not saved permanently (eg. data buffered, not yet physically written + loss of power) data would be lost in the void.
Simplest way would be to copy and remove only after confirming that everything works. I wouldn't even delete, more copies = safer data.


+1 This is your answer, just copy/paste onto a drive rather then move. This way you have extra copies. Given enough time a computer *will* fail and without extra copies you will lose all your data when that happens.

---

