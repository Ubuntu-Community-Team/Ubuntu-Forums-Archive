---
title: "Help needed for code sudo chown -R user:user /media/&lt;mount-point of the partition&gt;"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by crip720 on 2014-06-04
Hi I am trying to get root permission on sda6 that has Ubuntu 14.04 installed,with no usable graphics[ no graphics or low graphics, only root shell no network]. Mount says it is /dev/sda6 on / media /e141f9cf-o633-4336-904e-9b7387b03ea9 type ext4 [rw,nosuid,nodev,uhelper=udisks]  . user name is drip  .  I would like to delete X11 in /etc  that is in 14.04 and copy X11 into /etc of 14.04 from either the installed Lubuntu 12.04 on sda1, or better yet from the working live cd of LXLE 12.04 .  I am very good with copy and paste of commands but tend to get confuse/ make mistakes if  command has sections that I have to fill in.  This is related to my other post on cyberblade card,  adding old xorg to X11 does not seem to work.  Please help with filling in 
sudo chown -R **user:user** /media/[I]<mount-point of the partition> I think it should go drip:drip /media/dev/sda6.  
please add anything I need or another way of doing this, plus which OS it should be done in.How do I go back to normal font.  Thanks, Colin
[/I]

---

### Post by TheFu on 2014-06-05
The core issue is the "nosuid" mount option. Remove that and normal file permissions should be possible - with normal sudo/root access.

---

### Post by crip720 on 2014-06-05
Can you tell me how to do that?  Do I just do mount command and backspace nosuid  to remove it  or something else.  Like I said I am not good with making my own commands.  Thanks.  Colin.

---

### Post by steeldriver on 2014-06-05
What are you trying to do exactly?

If you simply want to COPY a known good xorg.conf file from the running live system (bear in mind - it may not actually use one, since the config may just be probed dynamically when the X server starts) to a previously installed system that is mounted in /media, then you should be able to do that just using

```

sudo cp /etc/X11/xorg.conf   /media/e141f9cf-o633-4336-904e-9b7387b03ea9/etc/X11/

```

Remember you can use tab completion so you don't have to type the long hex UUID string. I'd recommend backing up the original xorg.conf FIRST just in case that's not really the problem and you need to get it back, e.g.

```

sudo cp /media/e141f9cf-o633-4336-904e-9b7387b03ea9/etc/X11/xorg.conf{,.mybak}

```

You shouldn't need suid because you're not executing a command **on **the /media/xxx/ filesystem. You **certainly **shouldn't be trying to recursively chmod /media/xxx as that will leave it completely useless when you exit the live system and try to reboot the Linux system on /dev/sda6.

---

### Post by TheFu on 2014-06-05
How was that partition mounted?  That will determine where the change is needed.  Mounting it again without removing whatever causes the no-suid stuff may not do what you desire.

OTOH, solving the root issue like Steeldriver suggests (if that really is the real problem), would be better than changing permissions on some other file system in a way that would make it 90% less useful in the future.

---

### Post by crip720 on 2014-06-05
To Steeldriver , what I want to do is delete the X11 in 14.04, and then copy the working X11 from the live cd or the installed 12.04, and pasting X11 back in.  Have tried pasting the older xorg scripts but not working .  To  the Fu, I usually just mount it by going in nautilus and typing my password[ same for both] or if in 14.04 typing mount -n -o  remount, rw /  the second way to mount it as read/write from read only so I can use some commands in it.  I just need a way to work with 14.04 from the other install or live cd.  Thanks,  Colin.

---

