---
title: "resolution in 8.0.4"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Mr. Mulder on 2008-05-17
its stuck at 800x600, i don't think its detected my laptops's nvidia chip so i searched through the forum and found out i needed to download nvidia x server settings which i did, so then i go to System > Administration > Nvidia X Server settings and get:

[[IMG]http://img260.imageshack.us/img260/6631/29809404pw2.th.png[/IMG]](http://img260.imageshack.us/my.php?image=29809404pw2.png)

so then I do what it says and get:

[[IMG]http://img296.imageshack.us/img296/6344/80624220vj8.th.png[/IMG]](http://img296.imageshack.us/my.php?image=80624220vj8.png)

what do i need to go to get a much higher resolution, I'm still a beginner at linux so there's much I don't know how to do...


Thanks

---

### Post by Xiong Chiamiov on 2008-05-17
Whenever you get an error saying you don't have permissions, you should run the command with "sudo" infront of it, like this:
```

sudo nvidia-xconfig

```
(BTW, if you want to just add sudo to the last command you entered, you can just type "sudo !!" - nifty trick)

There are some interesting things going on with the kernel included in Hardy and the NVIDIA drivers.  For most people, the solution has seemed to be to shut down GDM and install the latest beta from the NVIDIA site:
Write this down, as the second command will drop you to a command prompt.
Download the 2nd driver on [this page]("http://www.nvidia.com/object/linux_display_archive.html").  Make sure you know where you saved it (home directory is preferable).
Press ctrl+alt+f2
```

sudo /etc/init.d/gdm stop
cd [where the driver is]
sudo chmod +x NVID[press tab to autocomplete]
sudo ./NVID[tab again]
startx

```

---

### Post by Mr. Mulder on 2008-05-17
thanks, that was going great until it said i needed the 64bit drivers! looking on that link i can't seem to find one?

---

### Post by Xiong Chiamiov on 2008-05-17
Are you running a 64-bit OS?

That link came from the more general page [here]("http://www.nvidia.com/object/unix.html").  Just click the archive link under the section you want.

---

### Post by Mr. Mulder on 2008-05-17
I'm not sure if the version i downloaded was 64bit but my laptop is 64bit and when i tried that driver you suggested it said the platform had to be x86_64 

I just tried it with a 64bit driver and got a bit further, got a text screen with some colour come up saying

"error: you appear to be running x server; please exit x before installing. For further details, please see the section... etc"

I ran sudo /etc/init.d/gdm stop first so im not sure how this could be?

---

### Post by Xiong Chiamiov on 2008-05-17
Try
```

kill -KILL X

```

---

### Post by Mr. Mulder on 2008-05-17
Thanks, it says arguments must be process or job ID's?

---

### Post by Xiong Chiamiov on 2008-05-17
Uhm, [this]("http://ubuntuforums.org/showpost.php?p=930222&postcount=3") might work better.

---

### Post by Mr. Mulder on 2008-05-17
Once again thanks for your help, I tried that then tried installing it again but get the same error of x is already running?  :confused:

---

### Post by Xiong Chiamiov on 2008-05-17
Hmm, after trying to kill it, do you get any output from this again:
```

ps -ef |grep X

```

EDIT: Ah, I guess I better go to bed, since it's 4 ;).  I'll subscribe to this thread and see if I can help you if you don't get it figured out.

---

### Post by Mr. Mulder on 2008-05-17
4:00am!? you animal! ;) 

I rebooted, tried everything you said again and its working perfectly, got my max resolution! Thanks for all your efforts!

---

### Post by Xiong Chiamiov on 2008-05-17
> **Mr. Mulder said:**
> 4:00am!? you animal! ;) 

I rebooted, tried everything you said again and its working perfectly, got my max resolution! Thanks for all your efforts!
Animal?  Nah, just a college student.

Glad that it worked.  Always happy when I can ease the pain that I went through for someone else.

---

