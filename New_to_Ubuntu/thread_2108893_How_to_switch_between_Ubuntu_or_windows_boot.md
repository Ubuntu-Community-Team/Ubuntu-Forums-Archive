---
title: "How to switch between Ubuntu or windows boot"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by jimi58 on 2013-01-25
Hi,
I just successfully installed Ubuntu on a 300gb partition on my Gateway but I don't know how to boot into Ubuntu instead of Windows 7 when it restarts.

---

### Post by pspencil on 2013-01-25
In my case, the Ubuntu, when installed, is the default system to boot in. 

How do you install ubuntu? 

I used to face the same problem as you, but when i change the way i install ubuntu, it works.

---

### Post by Frogs Hair on 2013-01-25
Hello and Welcome

When you boot you should see a screen similar to the screen shot below and you move between selections by using the arrow keys and press enter to boot the selection.

---

### Post by jimi58 on 2013-01-25
I created a partition first then installed it from a CD to that partition. It seems to have went through the whole install process but now I can't seem to get it boot into Ubuntu during reboot.

---

### Post by sandyd on 2013-01-25
> **jimi58 said:**
> Hi,
I just successfully installed Ubuntu on a 300gb partition on my Gateway but I don't know how to boot into Ubuntu instead of Windows 7 when it restarts.

Hi, we will need to know a bit more about your partition to help.

Please boot from a Ubuntu Live CD/DVD/USB (the media that you installed from), connect to the internet, and run the following from the terminal (Unity Dash -> Type in "terminal")

```

wget http://hivelocity.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvfz bootinfoscript-061.tar.gz
./bootinfoscript
```
and upload RESULTS.txt, which is mentioned when the script finishes running.

---

### Post by jimi58 on 2013-01-25
Yeah it just looks like the normal Win startup instead of the screenshot.

---

### Post by jimi58 on 2013-01-25
Thanks, here's what I get;

ubuntu@ubuntu:~$ wget  [http://superb-dca.dl.sourceforge.net/project/bootinfoscript/tar](http://superb-dca.dl.sourceforge.net/project/bootinfoscript/tar) wvfz  bootinfoscript-061.tar.gz./bootinfoscript
--2013-01-26 02:55:23--  [http://superb-dca.dl.sourceforge.net/project/bootinfoscript/tar](http://superb-dca.dl.sourceforge.net/project/bootinfoscript/tar)
Resolving [superb-dca.dl.sourceforge.net]("http://superb-dca.dl.sourceforge.net") (superb-dca.dl.sourceforge.net)... failed: Name or service not known.
wget: unable to resolve host address `superb-dca.dl.sourceforge.net'
--2013-01-26 02:55:25--  [http://wvfz/](http://wvfz/)
Resolving wvfz (wvfz)... failed: Name or service not known.
wget: unable to resolve host address `wvfz'
--2013-01-26 02:55:28--  [http://bootinfoscript-061.tar.gz./bootinfoscript](http://bootinfoscript-061.tar.gz./bootinfoscript)
Resolving bootinfoscript-061.tar.gz. (bootinfoscript-061.tar.gz.)... failed: Name or service not known.
wget: unable to resolve host address  `bootinfoscript-061.tar.gz.'

---

### Post by sandyd on 2013-01-25
> **jimi58 said:**
> Thanks, here's what I get;

ubuntu@ubuntu:~$ wget  [http://superb-dca.dl.sourceforge.net/project/bootinfoscript/tar](http://superb-dca.dl.sourceforge.net/project/bootinfoscript/tar) wvfz  bootinfoscript-061.tar.gz./bootinfoscript
--2013-01-26 02:55:23--  [http://superb-dca.dl.sourceforge.net/project/bootinfoscript/tar](http://superb-dca.dl.sourceforge.net/project/bootinfoscript/tar)
Resolving [superb-dca.dl.sourceforge.net]("http://superb-dca.dl.sourceforge.net") (superb-dca.dl.sourceforge.net)... failed: Name or service not known.
wget: unable to resolve host address `superb-dca.dl.sourceforge.net'
--2013-01-26 02:55:25--  [http://wvfz/](http://wvfz/)
Resolving wvfz (wvfz)... failed: Name or service not known.
wget: unable to resolve host address `wvfz'
--2013-01-26 02:55:28--  [http://bootinfoscript-061.tar.gz./bootinfoscript](http://bootinfoscript-061.tar.gz./bootinfoscript)
Resolving bootinfoscript-061.tar.gz. (bootinfoscript-061.tar.gz.)... failed: Name or service not known.
wget: unable to resolve host address  `bootinfoscript-061.tar.gz.'

Hi, please make sure you are connected to the internet, and paste one line at a time.

You can also use the instructions at [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) , though you have to have internet as well.

---

### Post by jimi58 on 2013-01-25
Sorry,
Typed this;
 "wget http://superb-dca.dl.sourceforge.net/project/bootinfoscript/"
and got this response
--2013-01-26 03:03:02--  [http://superb-dca.dl.sourceforge.net/project/bootinfoscript/](http://superb-dca.dl.sourceforge.net/project/bootinfoscript/)
Resolving [superb-dca.dl.sourceforge.net]("http://superb-dca.dl.sourceforge.net") (superb-dca.dl.sourceforge.net)... failed: Name or service not known.
wget: unable to resolve host address `superb-dca.dl.sourceforge.net'

---

### Post by sandyd on 2013-01-25
> **jimi58 said:**
> Sorry,
Typed this;
 "wget http://superb-dca.dl.sourceforge.net/project/bootinfoscript/"
and got this response
--2013-01-26 03:03:02--  [http://superb-dca.dl.sourceforge.net/project/bootinfoscript/](http://superb-dca.dl.sourceforge.net/project/bootinfoscript/)
Resolving [superb-dca.dl.sourceforge.net]("http://superb-dca.dl.sourceforge.net") (superb-dca.dl.sourceforge.net)... failed: Name or service not known.
wget: unable to resolve host address `superb-dca.dl.sourceforge.net'

There was an typo in the original script - should work now

---

### Post by jimi58 on 2013-01-25
This from the last line typed;

ubuntu@ubuntu:~$ ./bootinfoscript

Boot Info Script 0.61      [1 April 2012]

Please use "sudo" or become "root" to run this script.

  Run the script as sudoer:

    sudo ./bootinfoscript <outputfile>

  or if your operating system does not use sudo:

    su -
    ./bootinfoscript <outputfile>

For more info, see the help:

    ./bootinfoscript --help

---

### Post by DBOBA on 2013-01-26
Entering the BIOS

1. start pc
2. press rapidly or one time the key - F2 or F8 or F10 (You may have to restart several times until the BIOS window opens)
3. when it opens navigate to the "Boot" column by using the arrow keys left or right
4. when boot column is highlighted at the top use down arrow and navigate to the partition you made it should be in the line up
5. use the keys to move this partition to the top of the order usually F5 or F6 - make sure to "Note" what drive is at the top of the order so you can change it back when you want to use Windows
6. navigate to exit and save settings
When saved your PC will start from to boot from that partition and should open UBUNTU
Reverse order to change back to Win7
Hope this works for you

DBOBA

---

### Post by zombifier25 on 2013-01-26
> **jimi58 said:**
> This from the last line typed;

ubuntu@ubuntu:~$ ./bootinfoscript

Boot Info Script 0.61      [1 April 2012]

Please use "sudo" or become "root" to run this script.

  Run the script as sudoer:

    sudo ./bootinfoscript <outputfile>

  or if your operating system does not use sudo:

    su -
    ./bootinfoscript <outputfile>

For more info, see the help:

    ./bootinfoscript --help
You need to run it as root:
```
sudo ./bootinfoscript
```

---

### Post by jimi58 on 2013-01-26
Hi guys,
Thanks for all your help. I did a complete reinstall and now everything's working fine. I appreciate it!

---

