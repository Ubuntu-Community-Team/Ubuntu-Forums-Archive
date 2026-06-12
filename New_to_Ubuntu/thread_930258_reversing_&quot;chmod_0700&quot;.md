---
title: "reversing &quot;chmod 0700&quot;"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by rockerphil on 2008-09-25
ok, it's pretty self explanitory. i ran this command:

```
sudo chmod 0700 /home/phil
```

in order to tighten up the security for my home folder, but it's causing some permissions issues, namely because i keep all my downloaded music on my second HDD, and it won't let me move ANY files from my home folder to my second HDD. it gives me an error message saying somthing about "unable to preserve ownership" any help would be appreciated, much thanx in advance,

Phil

---

### Post by iaculallad on 2008-09-25
On the "unable to preserve ownership" issue, had you tried using **cp -p** or **scp -p**?

---

### Post by rockerphil on 2008-09-25
> **iaculallad said:**
> On the "unable to preserve ownership" issue, had you tried using **cp -p** or **scp -p**?

sorry, but i'm not quite sure what you mean. i do consider myself decently proficiant with the terminal, but permissinos and the like are one thing i'm still learning, so could you please clarifiy what you mean by "**cp -p** or **scp -p**"?

---

### Post by iaculallad on 2008-09-25
I mean, had you tried using the cp command to transfer files from your /home directory to your second drive. Only this time using the switch -p to preserve your ownership.

```
cp -p /home/some_folders /second_drive
```

Or in any case, using scp (secure copy) with the same switch -p.

---

### Post by rockerphil on 2008-09-25
ok, i just tried both, and this is what i get:

```
phil@phil:~/FrostWire/Saved$ sudo cp -p ~/FrostWire/Saved/ICP\ -\ Echo\ Side.mp3 /home/phil/Media/My\ Music
[sudo] password for phil:
cp: failed to preserve ownership for `/home/phil/Media/My Music/ICP - Echo Side.mp3': Operation not permitted
phil@phil:~/FrostWire/Saved$ sudo scp -p ~/FrostWire/Saved/ICP\ -\ Echo\ Side.mp3 /home/phil/Media/My\ Music
cp: failed to preserve ownership for `/home/phil/Media/My Music/ICP - Echo Side.mp3': Operation not permitted
phil@phil:~/FrostWire/Saved$ 
```

edit: i had the same problem when running my file browser (rox) as user root, i even tried and failed while logged in as user root.
edit2: also if it means anything my entire second HDD is a FAT32 partition

---

### Post by iaculallad on 2008-09-25
Your destination drive, is it formated as NTFS or FAT32? This filesystem could not handle Linux file system permission thus giving you that error.

---

### Post by cousinit2 on 2009-09-28
> **iaculallad said:**
> Your destination drive, is it formated as NTFS or FAT32? This filesystem could not handle Linux file system permission thus giving you that error.

Quite right; try setting permissions on /home/phil/Media directly to allow access by everyone:
```
sudo chmod 7777 /home/phil/Media
```

You can also run this command on /home/phil, transfer the files, and then reset to 0700 if you like.

NTFS and FAT32 really do not like Linux permissions bits; usually this is not an issue because NTFS-3g should remove/modify Linux permissions accordingly.

---

