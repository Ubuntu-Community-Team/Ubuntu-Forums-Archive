---
title: "I installed 12.10 but it shows 13.04 in Unity."
date: 2013-03-03
forum: New to Ubuntu
---

### Post by whitefish10 on 2013-03-03
Hi guys, I installed Ubuntu 12.10 and after finishing the updates. I was checking the about menu in Unity and it says 13.04. 

I am wondering what had happened, I think I did something wrong.

Please advise me. Thanks,

---

### Post by pierreyy on 2013-03-03
[FONT=courier new]Are you sure you didn't update to 13.04? Check your system info[/FONT]

---

### Post by ahmad000012 on 2013-03-03
ubuntu 13.04 not release yet
how to you upgrade to 13.04:shock:

---

### Post by mörgæs on 2013-03-03
Please post the output of

```
uname -a
```

---

### Post by whitefish10 on 2013-03-03
```
ahmed@ahmed-PH67A-UD3-B3:~$ sudo uname -a
Linux ahmed-PH67A-UD3-B3 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```


The following is the screenshot.

[IMG]http://s22.postimage.org/ynwu9rk8h/Screenshot_from_2013_03_03_15_00_24.png[/IMG]

My guess I think that I did some sort of beta update without me knowing.

---

### Post by Pilot6 on 2013-03-03
You probably turned on quantal-proposed in Softwre Sources. That's not a good idea.
You may catch a lot of real problems too.

---

### Post by whitefish10 on 2013-03-03
So what do I need to do to fix it? I am not sure but should I reinstall ubuntu?

And honestly speaking, I do have problems and some applications crashes.

---

### Post by arpanaut on 2013-03-03
As raring is using:

linux-image-3.8.0-9-generic	3.8.0-9.18

I would presume that it is some kind of bug in grub or lightdm that is giving that.
I can't find it now but I think there was something in a changelog of grub or lightdm about this error in designation.
Seems you have the proper kernel for quantal so I wouldn't worry about it unless you are having issues.

---

### Post by Mikhail.Inspired on 2013-03-04
If you need to turn off quantal-proposed, there is a checkbox in the Software Properties dialog. Are you having any issues right now? If not, I would suggest turning off quantal-proposed and letting it be.

---

