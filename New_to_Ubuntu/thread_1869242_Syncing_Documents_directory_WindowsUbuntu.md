---
title: "Syncing Documents directory Windows/Ubuntu"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by teacherjeff on 2011-10-25
I'm sure this is a really simple question, but I'm still having trouble figuring out a good answer.

I have Windows 7 and Oneiric installed on the same computer, dual boot.  I want my Documents folder (a few GB) to be available from both.  And I would also like to use Ubuntu One (although more as a backup service than anything else).  So here's my problem.

I could have the Ubuntu Documents directory point to the Windows Documents folder (on the NTFS Windows file system).  But apparently Ubuntu One under Linux won't sync directories on NTFS file systems.

Or I could do what I'm doing now: run Ubuntu One on both Ubuntu and Windows, using the service to sync separate document directories on the same computer.  But this is not a good solution, because Ubuntu One is sometime slow to sync (and rather moody).  And doesn't sync automatically under Windows.  So if I have to stop and reboot into the other OS do accomplish some specific task, I can't assume that everything will be in sync.

Any suggestions on what the cleanest way to do this would be?

Thanks.

---

### Post by cryptotheslow on 2011-10-25
I've never had a great deal of faith in cloudy file sync services - but that's just me :)

Personally I'd create a new ntfs partition of requisite size separate to the Windows install partition (just on the off chance the ntfs-3g driver does something screwy at some point) - with a label of something like Shared. Then mount that up in Ubuntu to /media/Shared - you could sym-link it to Documents if you like but it's just as easy to access it from the usual "Places" list in most file dialogues.

Then keep the documents to be accessed by both OS's in there.

As for backup - regularly copy the contents of that partition into a Truecrypt archive (standard file type) - then upload the entire encrypted archive file to the cloud. At least then you can be sure no-one will be peeking at your files sould the cloud decide to rain all over the place some day :D

That's just my approach. Probably not the most straightforward but works for me :)

---

### Post by mlentink on 2011-10-25
[http://www.fs-driver.org/](http://www.fs-driver.org/)
Will let you access your home directory from windows, *and* let you sync your home on U1

Edit: Works on ext3, but you can easily create one. U1 works with ext3

---

### Post by JayKay3OOO on 2011-10-25
Use dropbox as it's compatible with Linux and Windows, but only has 2GB free space & I think you have to put the files in a folder called dropbox.

Servers seem to be pretty fast though.

I built my own small home server though instead. You could use NAS (would do the same thing), but you have to remember to backup.

---

