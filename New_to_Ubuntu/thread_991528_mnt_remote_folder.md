---
title: "mnt remote folder?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-23
Hi Gang

I think my brain died!
I was told to use /mnt instead of /media for pointing to a remote folder.

OK, I can't mount the folderB itself because it is inside of an already mounted folderA.  So, I mounted the primary folderA, it appears ON my desktop as Mounted.

Now for the problem.

When I try to copy files to the folder in it, it's almost successful EXCEPT, rather than being copied to the remote folder as expected, they are copied to my own /computer/mnt/folderA/folderB on the originating hard drive.

Both computers are Ubuntu machines!

I'm using (after Mounting FolderA)

```
rsync -av -delete /home/ /mnt/FolderA/FolderB/
```

My question is, how does /mnt/FolderA KNOW it's on another computer?
I'm obviously missing something and their is NO man mnt to study.

TTUL
Gary

---

### Post by Ahadiel on 2008-11-23
How are you mounting /mnt/FolderA, or did you just create the folder with mkdir?

---

### Post by Kellemora on 2008-11-23
I just made the Folder within the EXISTING /mnt folder

I used Places Network to Mount the Folder so it would be mounted in order to run rsync.

I do the same thing with a Hard Drive that I mount through fstab and it works OK.

I've obviously forgot something important that I didn't write down.

TTUL
Gary

---

### Post by ciscosurfer on 2008-11-23
I might suggest looking into **sshfs** as an alternative.

---

### Post by Kellemora on 2008-11-23
Hi CS

I can copy the file over by hand, using copy/paste, but on almost all .odt files I get an error "invalid argument".

Interestingly enough, the full path works for copy/paste, but not from terminal using cp or rsync, meaning adding smb://192.etc. as the direction.

Oh Well, I'll figure it out again, did once before, just didn't write it down right, hi hi........

What I'm trying to do is back up my /home directory from ComputerA to a Backup Folder on ComputerB drive partition sdb6.

Now, to rsync to drive sdb1 on this computer, I must mount it first.
So, logically, to copy a file to another hard drive elsewhere, I need to mount it first also, which makes sense.  BUT by mounting it FIRST, that should make it LOCAL to this machine the way Linux works!  In other words, it's ALREADY MOUNTED so I shouldn't have to go looking for it elsewhere than right here!

How to make it show as mounted in /mnt, that I haven't figured out yet.
On local drives I use /media and just add the sdb1 folder and THERE IT IS!

TTUL
Gary


TTUL
Gary

---

### Post by ciscosurfer on 2008-11-23
If sshfs is not your cup of tea, I would suggest looking into [unison]("http://www.cis.upenn.edu/%7Ebcpierce/unison/").  Unison is a well-respected tool that could solve some of these problems for you.

---

### Post by Kellemora on 2008-11-24
Hi CS

It reads like it might be something very useful!

However, compiling from source code is something I have not yet had my hand in learning how to do.

Right now I'm going back to Linux 101 to see WHY it said that any MOUNTED device or folder was the same as it being on your own system (local).

I have the folder I want to copy to MOUNTED yet it cannot be found anywhere except on my desktop in the GUI, can't find it in any of the Trees.

Seems like I still have a LOT to learn!

TTUL
Gary

---

### Post by ciscosurfer on 2008-11-24
Unison is in the repositories so you don't have to compile it from source.  Open Synaptic and search on unison.

---

### Post by go_beep_yourself on 2008-11-24
NFS would do what you want.

---

### Post by go_beep_yourself on 2008-11-24
If you are transfering large amounts of data on a trusted network then you dont need ssh. The encryption slows down file transfers.

---

### Post by Dr Small on 2008-11-24
> **go_beep_yourself said:**
> If you are transfering large amounts of data on a trusted network then you dont need ssh. The encryption slows down file transfers.
Really? I have never noticed this.

---

### Post by Kellemora on 2008-11-24
Hi CS

I installed Unison from Synaptic!

Did a SEARCH to try and find it, no such file or folder found?????

Where is it HIDING?

TTUL
Gary

---

### Post by AgentZ86 on 2008-11-24
I'm not Linux expert, but it sounds like you still have to share the remote folder or setup your workgroup name to be the same, then you have to call on the computer in which your want to mount the remote folder such as /computer1/media I don't know the exact commands and as I've said I'm not an expert, for example I have a share on another computer, which I mount thru Smb4K which is a sharing client of sort.

The mounting point is something like /home/user1/smb4k/AUCTION/myshare

But you see the user1, and the AUCTION seems to be my name of the server computer, so probably in your case it will be something like /mnt/username/FolderA or something like that.
Or perhaps /mnt/username/computer2/FolderA or something

At least from what little I know

---

### Post by Kellemora on 2008-11-24
HI SC

I finally found it hiding in /usr/share/app-install/desktop/unison

When I clicked on it, it said I needed unison-gtk, so I went back to Synaptic and loaded that part.

THEN when I clicked on it, I got the necessary screens for source and distination, however, I'm still in the exact SAME boat I was with Rsync!

It cannot find the hard drive or the folderA or the folderB on the other machine!

FolderB IS mounted on my desktop, I can unmount it and remount it with no problem!

I can copy and paste the files I want to back up to it manually and it gives the path to the folder as plain as can be.
Except, from a terminal it can't find it and instead copies the file right back to the same hard drive I'm trying to backyup from.

So far, the ONLY way I have been able to back up my system is to Remove the Cover, Unmount and Remove Drive 2, install a second Drive 2, Mount the second Drive 2, run Rsync to Sync the backup.  Unmount it, Remove it, reinstall the original drive, mount it and reinstall the cover.

THERE HAS GOT TO BE AN EASIER WAY to copy files to a hard drive on another computer!

Networking is functioning just fine as far as file sharing!  Mounting folders, etc.

But NO PATH to the shared folder has worked for Rsync or any other program I have tried.  
So obviously I'm missing something important!

I've placed physical hard drives in /media that are on THIS computer.
Was told to use /mnt for external drives, removable drives and hard drives located on other machines.

But /mnt is just a FOLDER and the FolderA and FolderB are just folders, so INSTEAD of my file being copied over to Computer2, it stays right here on Computer1 in the /mnt/FolderA/FolderB/ folder.

It's driving me NUTtier than I already am, hi hi........

TTUL
Gary

---

### Post by go_beep_yourself on 2008-11-25
> **Dr Small said:**
> Really? I have never noticed this.

Depends, are you transferring the files over a LAN or internet? It seems to slow down file transfers over LAN for me.

---

### Post by Kellemora on 2008-11-25
Well, I hate to say this but Unison is buggier than bugs on a bumper!

If you enter a path it can't find, it comes up with Fatal Error.
That parts OK, but you cannot remove the entry, there is NO Delete and NO Edit to remove or change the faulty entry.  I now have 7 in the list that cannot be removed or changed.

The path IS CORRECT, I even have the folder bookmarked so I can just click the bookmark to mount it.

Still driving me nut!

TTUL
Gary

---

### Post by go_beep_yourself on 2008-11-27
What's Unison?

---

### Post by Kellemora on 2008-12-01
Hi GBY

It's a file syncronization tool found in the repositories that needs to be deleted since it don't work properly and is loaded with bugs.

How it got 4 stars is beyond me!

It does work to copy files to different areas of the same hard drive, or to a mounted drive connected to the computer it's running on.  But it too cannot find MOUNTED hard drives across a LAN and if it tries, it leaves a trail of Fatal Errors that cannot be removed or edited.

It's programs like this one that sends folks back to Mickey$oft!!!!!

TTUL
Gary

---

