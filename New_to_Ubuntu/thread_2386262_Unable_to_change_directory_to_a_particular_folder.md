---
title: "Unable to change directory to a particular folder"
date: 2018-03-03
forum: New to Ubuntu
---

### Post by mdeepakm on 2018-03-03
HI,

I installed Ubuntu alongside Windows. Later I planned to install Matlab in Ubuntu. Since it said there is not enough space in "Downloads" folder to download and install it, I installed it at this location:

```

/media/deepak/82d940f9-6526-47c8-8053-79204d78529f/deepak/bin
```

So to start Matlab, I tried to go to the above directory and then type the command ./matlab
But sometimes the folder *82d940f9-6526-47c8-8053-79204d78529f *seems to be not present inside */media/*[I]deepak

[/I]I mean, after doing cd /media/deepak/ on using the command *ls* nothing appears.

When I checked "Disk Usage Analyzer" it was there in the expected location. After this, I was able to go to the folder bin and start Matlab.

So every time when I want to start Matlab, first I have to open "Disk Usage Analyzer" and then go to my bin and start Matlab. 

It is my mistake to install Matlab inside that folder with a strange name. But I did that because it was having 500 GB hard disk size

How do I solve this problem, so that the Matlab path is always accessible so that I need not open Disk Usage Analyzer and can add it to PATH environmental variable?

Thanks

---

### Post by ubname on 2018-03-03
media is where external usb are mounted you should reinstall in a better way IMHO.

---

### Post by SeijiSensei on 2018-03-03
The standard location for unpackaged executables is /usr/local/bin. You need to use sudo to put files there.

However you might start by reading [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

