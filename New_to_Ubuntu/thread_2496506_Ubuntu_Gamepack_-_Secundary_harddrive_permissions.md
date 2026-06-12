---
title: "Ubuntu Gamepack - Secundary harddrive permissions ?"
date: 2024-04-01
forum: New to Ubuntu
---

### Post by jlassesen on 2024-04-01
Greetings.

Fairly new at Linux, as i've only been messing with it for a few months. Long time windows "addict".

I've been on OpenSuse Tumbleweed for the past few months, and i do like it. But it has it's issues. Frequent crashes following updates...
And as i am primarily a gamer, i started messing with a couple gaming distros, and i ended up at "Ubuntu Gamepack". Seems like a very good OS...

However... New distro, new set of issues...

So, my primary issue, is that i have my games on my secundary harddrive,  which is mounted, as far as i can tell. Something that happens automatically in this distro, which i love... QoL for sure... But i can only copy from it... I can't move, delete or in any other way mess with the data on that drive...

So, adding that drive to my Steam, so it can read/write data on it, is not possible. - I'm thinking, maybe it's got to do with Permissions? Or, maybe the drive hasn't been "owned" as i usually do in Tumbleweed? (chown)

Ok, how do i do that? Get my distro to accept my secundary drive, and thus have Steam able to add it to it's library ?

Thanks in advance ?!

Keep in mind, i'm still a newb, so keep replies simple please !

---

### Post by jlassesen on 2024-04-01
Update.

I've tried following this guide :
[https://linuxsimply.com/linux-change-permissions-on-mounted-drive/](https://linuxsimply.com/linux-change-permissions-on-mounted-drive/)

Had no effect.

I've tried to follow some advice from a buddy, using chmod 777 /dev/sda1 (And "Games" as that's what i named my drive.) I've even tried /dev/media/sda1 - And it continues to say "No such file of directory"...

It's getting infuriating...

---

### Post by jlassesen on 2024-04-01
Ok, this is confounding the life out of me.

I logged onto the terminal as root. Made some changes to permissions. Rebooted the machine, and it seems to have undone the changes i made? What the hell ???

---

### Post by jlassesen on 2024-04-01
Update : Finally got access to my drive. I can cut/delete/what ever on it now.

I altered permissions through Nautilus.

Now, here's my next issue : I added the game folder to steam. And it works.

I then reboot my computer, and it "forgets" that i added it...

---

### Post by Impavidus on 2024-04-01
I've got no experience with steam or games stored on a secondary hard drive, so can't help with that, but I may be able to give you some leads.

/dev/sda1 and similar things are devices (dev stands for device). That means that it's a raw sequence of a few billion bytes as present on your hard drive. Those bytes can be interpreted as a filesystem, but to access files, you don't access /dev/sda1 directly. Instead, you mount the filesystem at some directory, then the filesystem becomes accessible at that directory as a nice directory tree. For internal hard drives, it's usually best to mount them automatically at boot time. You can use [fstab]("https://help.ubuntu.com/community/Fstab") for that. After mounting it, you can set permissions and ownership on individual files and directories, provided the filesystem is a Linux filesystem supporting such permissions and ownership.

You can create an empty directory to mount your filesystem. There are very few rules for that and a number of useful conventions.

---

### Post by jlassesen on 2024-04-02
Thank you for the reply.

---

