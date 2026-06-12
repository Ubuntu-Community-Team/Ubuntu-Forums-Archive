---
title: "Permissions problem"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by GeordieJedi on 2008-10-30
Hi, all. Hope your all doing well, on download day.

Quick question if thats ok.

I recently fixed my friends laptop (by removing windows XP and installing Ubuntu!

However, Whenever I add media (via the dvd drive) and copy the data across to the hd.
 It becomes locked. and I can only view the data.

Eg: I put some photos on a cd. transfered them to the HD. Now I can view
 the photo's but I cant delete/move them.

What am I doing wrong? How do I stop this from happening in the future?


(My friend isn't a computer geek, and just uses it like a tool. So I want to
 make this as easy as I can for him).

Thanks in advance for any help.

---

### Post by Sarmacid on 2008-10-30
Check what permissions do the files have. Get on a console, navigate to where the files are and run
```
ls -l
```

---

### Post by GeordieJedi on 2008-10-30
Hi sarmacid. Here is the output you asked for.

dr-xr-xr-x 2 adrian adrian 4096 2008-10-26 21:52

Am I right in thinking that adrian is the sole owner, (as there's no mention of root?)

---

### Post by CatKiller on 2008-10-30
Files on DVDs and CDs are obviously read-only, and the files you've copied have inherited this characteristic.

I don't know of a way to automatically update the files to make them writeable, but it's easy enough (especially if you've still got them highlighted from the copy) to select all of them and right-click to get to the Properties dialogue, click on the Permissions tab and put a tick in the Write box for the Owner.

You can still delete files that are Read-Only.

---

### Post by Coreigh on 2008-10-30
If you are copying the files as the user (only 1 user right?) the you should have access to the files. Are the files locked as in can not open them or are they read only but you can open them? They are by default read only on the CD/DVD and I have seen that setting stay after being copied on to a hard drive.

If you issued the copy command with sudo (sudo cp /cdrom/files /home/myfolder/files) or worse with sudo su, then the permissions might be tweaked. If there is no sharing concern reset the permissions with chmod

terminal >> cd to file location and enter

sudo chmod 777 ./*

BE CAREFUL. make sure you are in the folder where the files are. you do not want to go changing permissions accross the whole hard drive!

---

### Post by GeordieJedi on 2008-10-30
Hi Catkiller. What you say makes a lot of sense.

But (with the photos I put onto cd. - That was actually done in Win XP,
and IIRC I dont think I've ever had a problem transferring stuff
that way before - between both OS's on the same PC?)

[I personally dual boot between XP and Ubuntu 8.4.01]

But cheers for the imput. Hopefully I'm one step closer to answering the issue
(with everyone else's help).

:)

---

### Post by GeordieJedi on 2008-10-30
@ Coreigh =

They have the padlock symbol on them. (I can read/look at them.
 But not delete/alter/move them).

I had burnt the CD using nero on XP. Chucked the disc into the
 drive and just copied the files (using nautilus)

---

### Post by Duck2006 on 2008-10-30
Sorry wrong post.

---

### Post by nisaky on 2008-10-30
select them, pres right click, properties -> permissions and select him as owner, and give folder access: create and delete and file access: read/write.

---

### Post by CatKiller on 2008-10-30
It doesn't matter how the files were created. The fact that they are read-only is a property of them being on an optical disc. Potentially it might be different if they were on a CD-RW. But certainly any other writeable medium (ie, hard disks, USB drives, floppy disks, and so on) doesn't have this property.

---

### Post by GeordieJedi on 2008-10-30
Areet Catkiller.
 I agree completley with you (regards the data coming from a read-only medium.
 - I was thinking the same thing myself initially).

However I didn't think I sufferd the same problem myself on my desktop PC.

(* I've actually just tried it as I was typing this. And......
I've just sufferd the same problem......
I've just copied two files from differn't LXF cover discs.
And sufferd the same problem.....)

Curiouser and curiouser!

---

### Post by akelsall on 2008-10-30
When you copied the files over, where you logged in as your friend, or under an account you set up for yourself (it's unclear if you are adrian, or if you're friend is adrian). It might just be a simple permissions issue (specifically, the owner of the file). 

Google the "chown" command and try to change the owner of the file. Think that might fix your problem.

---

### Post by GeordieJedi on 2008-10-30
Hi akelsall.

Sorry If I've confused the issue. :(

Right here goes.

The laptop belongs to a friend of mine called adrian.
On the laptop, I'm logged in as adrian.

I put some files on CD and DVD from "my" own desktop PC
(However this was on M$ XP, and I was logged on as an administrator).

Hope this makes things a little clearer.

Thanks to everyone who's responded so far.

---

### Post by Kellemora on 2008-10-30
Hi GJ

That was a big problem for us when we first switched my office over to Ubuntu, we could not access ANY of the mirrored backup files, nor any files sent to another computer to the one it was needed on.

Clients would bring us data files and we couldn't get permission to open the files.  Like you, they had a big FAT LOCK hanging on them.

But don't despair, it's easy to fix this.

Open a Root Terminal, type nautilus, then go to the folder (don't want to waste time doing each file individually) Select the folder by right click and select Permissions.
It probably says NOBODY as User, NO ONE as Group, and all the boxes are Read Only.

In your case, you could change User to Adrian, Group to Adrian and select Read Write for the Any User at the bottom.
I normally just select All Users and Guests - Read & Write and this fixes it.
Then later on as you open an use each file, it gets saved with the necessary permissions.

Now you can go out of root and access those files from the user Adrian's log-in.

IF your files are not in a folder (and they probably can't be moved into one either) you can just select ALL and then right click on properties and follow the above.

This works for me, whereas I mess up a lot trying to use command line fixes for things like this.

One other oddity you may find has to do with file sharing.
If you have files on computer A that you need on computer B, you will find the same permission problems if you copy the files from computer A TO computer B.
To alleviate this problem, share the necessary files on computer A, go to computer B and FETCH the files from computer A, then they will be A-OK as far as permissions go.

TTUL
Gary

---

### Post by GeordieJedi on 2008-10-30
Areet Kellemora.

Thanks you very much for your clear and succinct answer.
Its very much appreciated. I'll do as you and the others suggested
and report back tomorrow.

(BTW thans to EVERYONE who has replied to this and many other of my threads.

 This is one of the main reasons that I use Ubuntu as much as I do....
I'm spending less and less time in XP. (Only for a couple of apps
and some games....Dawn of War is Mint!)

But seriously a big fat CHEERS to all)
 :)

---

