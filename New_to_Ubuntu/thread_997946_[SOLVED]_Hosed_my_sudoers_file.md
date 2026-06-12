---
title: "[SOLVED] Hosed my sudoers file"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by akelsall on 2008-11-30
Well, I was trying to back up some of my important files under /etc, and a couple of files where giving me permission problems when trying to back them up (I was just copying them from one folder to another using Nautilus).

Since it wouldn't allow me to do it (and yes, I started nautilus as su), I decided it would be a good idea to chown on the sudoers file. Yep, now I know why that's not a good idea :lolflag:

So, I'm kinds screwed now. When I try to change it back, I get this:

```
sudo chown root:root sudoers
sudo: /etc/sudoers is owned by uid 1004, should be 0

```

So, I try to log in as root, but get this:

```
 su
Password: 
Your account has expired; please contact your system administrator
su: User account has expired

```

Argh!! So, I try to change the expiration date, and get this:

```
 sudo useradd -e 2009-03-01 root
sudo: /etc/sudoers is owned by uid 1004, should be 0

```

When I try to boot via LiveCD and go into recovery mode, I can't, because I need to log in as root, and well, you saw what happened above. 

I'm sure I've provided a good laugh for some of you :lolflag: , but when you stop laughing, can you give me a way to change this back? 

Thanks,

Andy

---

### Post by taurus on 2008-11-30
What do you mean you can't boot with the LiveCD?  The LiveCD doesn't care what happens to your /etc/sudoers on the harddrive.  And besides, you would be able to boot into the recovery mode too.  It will drop you into a shell and you can change the ownership of /etc/sudoers back to root again.

---

### Post by cmnorton on 2008-11-30
I don't use the live CD, but I've got to believe that you can become root without relying on files on the hard drive. I'd look for more instructions on the live CD's use.

However, with Knoppix, you should be able to start a root shell, and then replace the sudoers file with the proper ownership and permissions. 

As an aside, I don't think anyone's having a laugh on you. People have done worse than screw up a file.

As aside, part II, I always keep a recent version of Knoppix, and consider it a very useful tool for getting out of trouble. This is not a knock on Ubuntu, but basically Knoppix is what it is, and that's all that it is. And it's bailed me out many times.

---

### Post by aysiu on 2008-11-30
I echo taurus' recommendation to boot into recovery mode. The live CD is wholly unnecessary.

You can find instructions here:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Once you're in recovery mode, type the command ```
chown root:root /etc/sudoers
```

---

### Post by akelsall on 2008-11-30
Taurus, you're correct. I initially had tried using the LiveCD, but because of my flakey CD drive, it wouldn't boot to the desktop. 

I had mispoke earlier. It was actually when I rebooted and chose the Recovery mode in GRUB that I was unable to log in as root. However, I was finally able to load the LiveCD, go in through the GUI, and assign a root password. I rebooted into Recovery mode and was able to change the sudoers file back to root. So, thanks to you and others for the help. Won't make that mistake again hahaha. If the old saying "An expert is someone who's made the most mistakes" is true, then I'm on my waying to being an Ubuntu/Linux expert!:lolflag:

---

### Post by weose33 on 2008-11-30
In this article from Gamasutra's fille Gamey Progression Pass position, the y4y Group from Singapore's Nanyang Tech shares the challenges they faced and the [lotro gold](http://www.ugamegold.com/c_Lord-Of-The-Rings-Gold/)  outcomes for their basic gamy, Bashy Bashy: Nifty from World, a platformer/beat'em'up crossbreed.

---

