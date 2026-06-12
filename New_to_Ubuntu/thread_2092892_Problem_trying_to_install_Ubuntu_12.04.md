---
title: "Problem trying to install Ubuntu 12.04"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Ymurti on 2012-12-09
Please help! 

I am trying to install Ubuntu 12.04 in my new Acer netbook. The problem is when I come to the window where I have to choose the installation type, I have only 2 options:

1) Erase disk and install Ubuntu

2) Something else

I do not have the option to install alongside Windows.

Please see the picture attached.

I do want to install Ubuntu but I want to keep Windows for while. 

Thank you for your help.

---

### Post by alexandari on 2012-12-09
"Something else" means that you can resize your hard disk the way you want so you can have both Windows and Ubuntu on the same computer. In other words,make a partition only for ubuntu and install it there. Another option for having ubuntu next to windows is installing it via **Wubi**
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer) Here's a link. You can google it some more and find out more about it :)

---

### Post by BlinkinCat on 2012-12-09
Before you plunge on into selecting something else, it may be that at present windows takes up all four partitions on your hard disk.
One of these can be resized to allow you to put Ubuntu on that partition. Someone with more knowledge than I can explain how to do that.

Cheers - :)

---

### Post by vasa1 on 2012-12-09
> **Ymurti said:**
> Please help! 

I am trying to install Ubuntu 12.04 in my new Acer netbook. The problem is when I come to the window where I have to choose the installation type, I have only 2 options:

1) Erase disk and install Ubuntu

2) Something else

I do not have the option to install alongside Windows.

Please see the picture attached.

I do want to install Ubuntu but I want to keep Windows for while. 

Thank you for your help.

That's odd. Why doesn't Ubiquity (Ubuntu's installer) see the Windows OS? BTW, is this Win7 or Win8?

---

### Post by BlinkinCat on 2012-12-09
Some reading here -

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


For others to see your partition setup -

```
sudo fdisk -l
```

---

### Post by verzx on 2012-12-09
> **BlinkinCat said:**
> Before you plunge on into selecting something else, it may be that at present windows takes up all four partitions on your hard disk.
One of these can be resized to allow you to put Ubuntu on that partition. Someone with more knowledge than I can explain how to do that.

I agree, it could be that you have more than 4 partitions or it could be that you're not selecting the windows partition when you are trying to install it. Or try selecting the same partition which windows is on then it should give you the option to install it alongside windows. Then the next form should be an option to shrink the Windows partition.

---

### Post by BlinkinCat on 2012-12-09
> **verzx said:**
> I agree, it could be that you have more than 4 partitions or it could be that you're not selecting the windows partition when you are trying to install it. Or try selecting the same partition which windows is on then it should give you the option to install it alongside windows. Then the next form should be an option to shrink the Windows partition.

Hi,

I have added the show partitions command in #5

Cheers - :)

---

### Post by Ymurti on 2012-12-09
> **BlinkinCat said:**
> Some reading here -

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


For others to see your partition setup -

```
sudo fdisk -l
```

I have Widows 8

Thank You for your quick reply here it is the result of fdisk -l

---

### Post by Ymurti on 2012-12-09
I have created a new partition using gparted but even though I can not install Ubuntu. Attached is a picture of what gparted is showing.

---

### Post by BlinkinCat on 2012-12-09
Hi again,

Unfortunately I am unable to help any further but there are others in forum who can. I suggest you wait for further assistance. In the meantime you could look at this thread which discusses some of the issues of dual booting with Windows 8 -
[http://ubuntuforums.org/showthread.php?t=2055842](http://ubuntuforums.org/showthread.php?t=2055842)

All the best - :)

---

### Post by Ymurti on 2012-12-09
Thank you all. I managed to install Ubuntu alongside Windows 8

[http://www.intowindows.com/dual-boot-windows-8-and-ubuntu/](http://www.intowindows.com/dual-boot-windows-8-and-ubuntu/)


Hare Krishna!):P

---

### Post by BlinkinCat on 2012-12-09
Hi Ymurti,

Congratulations in sorting it all out. I hope my interference did not delay the outcome too much.

  All the best - ):P

---

