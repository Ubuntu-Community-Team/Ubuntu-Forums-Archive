---
title: "[SOLVED] How do I replace Linux Mint with Kubuntu, while still having Windows 10?"
date: 2016-05-16
forum: New to Ubuntu
---

### Post by xiujk71 on 2016-05-16
Hello!! This is my first thread here. 

Tried Kubuntu, and loved it, and would like to replace my Linux Mint with a clean install. I would like to do it without touching anything in my Windows 10 Boot.

When I go to manual install and check the partitions, I found that my ext4's mount point are not shown. One is supposed to be / and another is /home, which are my Mint's partitons

Here's a picture (sadly from my phone): [https://app.box.com/s/8wgf3h9cvyz20ln3lpto42rvgwf8mn9c](https://app.box.com/s/8wgf3h9cvyz20ln3lpto42rvgwf8mn9c)

How do I go about replacing my Linux Mint install, while still retaining Kubuntu?

Thanks!

---

### Post by bearlake on 2016-05-17
We see a /dev/sda8 and a /dev/sda9 which is not labeled and are likely Linux Mint and /home or Kubuntu ( if installed ).
You really need to add as much info as possible, or it's any ones guess.

---

### Post by xiujk71 on 2016-05-17
Yeah, thats my Linux Mint install, one is '/' and other is '/home'. Kubuntu is not installed.
Would liked to format the two partition and install Kubuntu.

I  assume its just formatting the two ext4 drives, relabel them and  install Kubuntu. But the labels are not recognized so I was thinking  that something might be wrong, I dont want to risk it and break my  Windows install.

---

### Post by sudodus on 2016-05-17
When installing, at the the partitioning window, you choose ***Something else***, and you should be able to identify and select the correct partitions.

-o-

Finally a general advice: Please ***backup*** everything, that you don't want to lose (your personal files and Windows). Anytime things can go wrong (human mistake or hardware failure, or maybe there is a power outage). Installing operating systems is particularly risky.

---

### Post by xiujk71 on 2016-05-17
> **sudodus said:**
> When installing, at the the partitioning window, you choose ***Something else***, and you should be able to identify and select the correct partitions.

-o-

Finally a general advice: Please ***backup*** everything, that you don't want to lose (your personal files and Windows). Anytime things can go wrong (human mistake or hardware failure, or maybe there is a power outage). Installing operating systems is particularly risky.

There was only "Manual", but it works the same way as "Something else" in Linux Mint, which will end up the same as the picture.
I took a risk, formatted ext4 partitions with mount points '/' and '/home', and now the installation works. Thanks!

---

### Post by oldrocker99 on 2016-05-17
Thanks for marking the thread as [SOLVED.]!

---

