---
title: "Can't Locate other HDD after installation"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by n0eL on 2008-09-28
Can anyone help me?

I am a complete newbie at xubuntu and I recently just installed it on my old computer.  Before it was using win98 with two HDD.  I was using the other one for backup.  I installed xubuntu on the other drive but upon log in I don't know how to find my backup drive.  I think it is still in fat32 and I don't want to format it cause I will loose my backup files.

I tried looking for answers and found this [http://ph.ubuntuforums.com/showthread.php?t=884768](http://ph.ubuntuforums.com/showthread.php?t=884768)

But upon trying this solution.  I don't know the name of my backup drive thus I can't mount it. Thanks for your reply and help.

---

### Post by Xiong Chiamiov on 2008-09-28
Please post the output of
```

sudo fdisk -l

```

(Ne[ed help finding the terminal]("http://www.psychocats.net/ubuntu/terminal")?)

---

### Post by n0eL on 2008-09-28
thanks a lot.. it turned out the my other hdd is /dev/hdb1 
your reply was really helpful..

Thanks a million..

---

