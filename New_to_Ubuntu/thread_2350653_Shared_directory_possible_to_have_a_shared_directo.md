---
title: "Shared directory: possible to have a shared directory in a dual boot?"
date: 2017-01-26
forum: New to Ubuntu
---

### Post by martemarziano on 2017-01-26
Since at the time of replacing my Win 10, I couldn't settle upon just one distro, I ended up installing two: Ubuntu 16.04 Mate and Mint 18.1 Serena. At the moment I am quite happy with this because it gives me the opportunity to change the environment if I feel like to but then accessing my files from one or the other system is a bit of a hassle involving a lot of clicking. So I just wondered if there is a way of creating a shared directory for both systems for easier access.

---

### Post by howefield on 2017-01-26
On this laptop I have 4 partitions, one for Ubuntu, one for Xubuntu, one for swap and one for a shared Data partition that each OS can access.

Both Ubuntu and Xubuntu have their own /home folder but access to the shared partition via symlinks where the Documents, Downloads, Music, Pictures and Video are stored, this partition is mounted with the fstab file at boot.

This sounds a bit like you want to achieve ?

---

### Post by martemarziano on 2017-01-26
Yes, that's exactly what I had on my mind. But if I understand your post correctly, I should have dedicated a separate partition at the time of installation to be used as the shared directory, which unfortunately I haven't. Still I would be grateful if you could take your time to explain how that is possible using the fstab for the sake of future installation. I am a bit frustrated being on a slow machine and I am thinking of getting one with better performance.

---

### Post by howefield on 2017-01-26
> **martemarziano said:**
> Yes, that's exactly what I had on my mind. But if I understand your post correctly, I should have dedicated a separate partition at the time of installation to be used as the shared directory, which unfortunately I haven't. Still I would be grateful if you could take your time to explain how that is possible using the fstab for the sake of future installation.

Yes, I'll do something later on. 

Each OS should be able to read the folders on the other (both being linux and presumably formatted with the same file system) so if it is a shared folder on one that you want to access from the other, then that too is possible.

> I am a bit frustrated being on a slow machine and I am thinking of getting one with better performance.

Now knowing a bit more about the hardware you are using I can understand that, perhaps Lubuntu with its lighter desktop environment would suit it better. There are even lighter options than that.

---

### Post by martemarziano on 2017-01-26
Thank you, I appreciate it very much! 

You are right, Lubuntu must have been the better option, but I fell for the Mate, what can I do? Now after all the toiling and tweaking and software installations, I fell not being up to redoing the whole process once again. Getting so far, being a tech novice, has taken me quite a bit of time reading and testing and finally after all those trials an errors I have a system that runs satisfactorily but a bit slow. I think I should leave with it for the moment.

ps. I want to express my gratitude towards you and all the other admins who have been so friendly and helpful from the moment I joined this forum. I enjoy using Linux and wish to be able to contribute more to this forum, in a not so distant a future, I hope, when I learn and know more about using Linux.

---

