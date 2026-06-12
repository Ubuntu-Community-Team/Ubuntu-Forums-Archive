---
title: "Ubuntu 11.10 activate recommended NVIDIA driver error."
date: 2011-10-13
forum: New to Ubuntu
---

### Post by luisgustavo on 2011-10-13
Hello, I just installed ubuntu 11.10. So I went to activate additional drivers (NVIDIA) and got this error:
 If you need I can post the file jockey.log

[[IMG]http://s2.postimage.org/2yhw8oomc/Screenshot_at_2011_10_13_15_20_17.jpg[/IMG]]("http://postimage.org/image/2yhw8oomc/")

Thank you.
[IMG]http://postimage.org/image/2yhw8oomc/[/IMG]

---

### Post by sikander3786 on 2011-10-13
Welcome to the forums :)

Please attach the jockey.log file from /var/log which contains the error information.

If you don't know how to get to it, press Alt + F2 and enter:

```
nautilus /var/log
```

Find the file named 'jockey.log' and attach it with your post.

---

### Post by Tarast on 2011-10-13
Are you connected to the Internet? Make sure your connected it should active it with out problems

---

### Post by luisgustavo on 2011-10-13
I'm connected! The file is attached, I put in .doc because .log and .txt refused to upload.

---

### Post by pleger on 2011-10-14
> **luisgustavo said:**
> I'm connected! The file is attached, I put in .doc because .log and .txt refused to upload.

Hi,
  I have the same problem here. My laptop is a Lenovo g640. Please, I need a solution.

---

### Post by luisgustavo on 2011-10-14
After a while my computer not restart anymore. So I ended up reinstalling nvidia, and I see now it has installed additional drivers too.

You should try. What I did was:

```

sudo apt-get remove nvidia-current
sudo apt-get remove nvidia-common
sudo apt-get remove nvidia-settings

sudo apt-get install nvidia-current
sudo apt-get install nvidia-common
sudo apt-get install nvidia-settings

```

I did this at the boot prompt, pressing CTRL+ALT+1 ;)

---

