---
title: "Trouble running script"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Jimbo13 on 2008-11-09
I'm trying to install a tv tuner (Kworld ATSC 120) I found directions to add the firmware for it.

[http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028](http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028)

```

# In order to use, you need to:
#       1) Download the windows driver with something like:
#               wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
#       2) Extract the file hcw85bda.sys from the zip into the current dir:
#               unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
#       3) run the script:
#               linux/Documentation/video4linux/extract_xc3028.pl
#       4) copy the generated file:
#               cp xc3028-v27.fw /lib/firmware

```


Everything works until I get to step 3, I get the following error.

```

linux/Documentation/video4linux/extract_xc3028.pl
bash: linux/Documentation/video4linux/extract_xc3028.pl: No such file or directory
```



I'm not sure what I am doing wrong, I think the article may  assume knowledge I don't have.  The zip file didn't produce xc3028.pl either and at no time did the directions point me to download a different file.

So any guidance would be helpful, I am a Ubuntu/linux noob but I usually can follow directions with no problem.

Thanks, Jim.

---

### Post by MasterSander on 2008-11-09
if you're new to ubuntu, I'd advice you to do step 1 and 2 graphically, just download the file and unzip it not through the terminal. Then make sure you navigate to where the script is located. In terminal, the default folder is your home folder, navigate to where the script is with cd /home/yourname/download/location if you unzipped it in your home folder. If you think you're in the right place, type ls to check if it's there, then type ./scriptname to execute it.

---

### Post by cariboo on 2008-11-09
It looks like you need the kernel source. See here:

[https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide)

to get the kernel source.

Jim

---

### Post by Jimbo13 on 2008-11-09
Thanks, I was reading the directions on step 3 to literally.

I found the script file at: 
ubuntu-intrepid/Documentation/video4linux/extract_xc3028.pl

So heres what I did,

Opened a terminal in the folder

```
./extract_xc3028.pl
Permission denied

sudo ./extract_xc3028.pl
sudo: ./extract_xc3028.pl: command not found
```


Do I need to download something to run a perl script? My system identifies it with a PERL icon.

---

