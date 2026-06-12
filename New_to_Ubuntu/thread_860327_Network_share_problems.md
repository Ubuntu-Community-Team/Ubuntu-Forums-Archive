---
title: "Network share problems"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Korijn on 2008-07-15
Alright, here's our setup.

We have a Linksys WAG200G router (brand new) connected to three PC's in the house. The two I'm concerned with are Ubuntu Linux 8.04 (up-to-date) and XP Pro. They're both connected with a wire.

The Ubuntu pc is a server, running apache2 and samba. It has an external USB drive shared as over the network. I listen to the music stored on it from the other (XP) box. This works. I also have a shared folder (/var/www) where I do my development in. This works as well. The network has become significantly faster since we switched from wireless to wired.

Now, the problem: if, while listening to music from the XP box, I browse any of the shared data on the Ubuntu box, the music starts skipping (every two or three times I open a folder, file, or save, or anything related). WHAT is wrong? This does not happen if I boot up the Ubuntu box in XP and share it from there.

What do I do?

---

### Post by someonestolemyname on 2008-07-18
Sounds like the disk in the Ubuntu machine is pretty slow. You only get skips on the open - save - etc. It can't read the music at the same time it reads/writes files. Nothing that can really be fixed except to maybe increase the buffer on the music player so that it wouldn't be interupted by disk access as much?

Daniel

---

### Post by Korijn on 2008-07-19
Problem is, both shares are on different hard drives. And it also occurs when I listen music from one and work with files on the other!

I increased my media player's buffer from 2 to 20 ms and it still occurs, though much less often. :/ I'm currently defragging one of the drives (an NTFS external hdd) which was a pretty big mess. If it's drive reading speed, that should help a bit as well, I guess.

Any other thoughts?

---

### Post by someonestolemyname on 2008-07-20
That sounds like a great idea. Increase the buffer more if possible, that seems to help. Defragging should help as well.

---

### Post by kindageek on 2008-08-22
I wasn't sure if I should start a new thread or not seeing as how this topic has been marked as "SOLVED".  I'll start here though since I'm having basically the same issue.

I just bought a new hard drive for a spare laptop and I installed Ubuntu 8.04 and hope to have it setup as my music server for playing music over my network.  Ideally, same as with Korijn's setup, the files will be played through a share and on WinXP boxes.

I'm having the same skipping problems as he was having.  Mine occur if I try to read or write to the root music folder or any other down the hierarchy.  It happens sometimes when I'm not even browsing the network.  It also occurs if I set the share on the Ubuntu box to read-only.

More than just skipping though it seems that if I access the share through Windows Explorer, more often than not, the current song playing will get caught in like a 1 second loop and will never recover until I hit STOP and start the song over.

Is this just a fundamental flaw in Linux or Samba that can't handle two things at once?  I'm not knocking on Linux, because while stuff like this works flawlessly in Windows, I'm assuming it all boils down to trying to read/write from a different operating system.

Yes, I tried adjusting the buffer too.  This works for the most part, but then you start having the issue of having to wait for a song to buffer before it starts playing, as well as having to listen to an extra 5-10 seconds after you press stop.

Whew, that was a mouthful.  Do you guys have any other ideas?

---

### Post by Korijn on 2008-08-23
@kindageek: I marked the thread as unsolved for you.

Basically, the following things helped, even if slightly, in my case:
- Defrag the hdd
- Assign static ip's to all comps
- Wire the network
- Increase buffer to maximum size

Unfortunately, increasing the buffer to the max can't be done in a lot of media players and it also slows down the program. I still have the problem every now and then, but seeing as there is apparently nothing else I can do about it, I set the thread as solved. I think we just have to wait 'till someone implements these features into Ubuntu/Samba.

---

### Post by kindageek on 2008-08-23
Hey Korijn,

Ok, I'll give those a try and see what happens.

I've tried most of them already, but not all at once.  As for defragging the HDD, I thought Linux didn't require any defragging?  Are you saying to defrag my WinXP box?  If so, unfortunately for me, that's not going to help seeing as how my WinXP box defrags every night.  =\

I think my main problem is that the laptop running Ubuntu is currently running wireless.  I'll get a wire to it and see what happens.

Thank you for your help!  =)

---

### Post by Korijn on 2008-08-23
My harddrive was NTFS. :)

Glad that we are now able to rule out that the file system was the problem though.

---

