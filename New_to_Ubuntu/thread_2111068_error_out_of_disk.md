---
title: "error: out of disk"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by thelegendofdirte on 2013-01-31
new to kubuntu, and i love it, but from what i have gathered is i filled my disk, and now i need to somehow get back in and delete files to get it to start up???

when turning on computer, i get the message (when starting in ubuntu, with linux 3.2.0-36-generic)

Loading Linux 3.2.0-36-generic ...
error: out of disk
Loading initial ramdisk ...
error: out of disk 

press any key to continue

NEED HELP please, like i said, i am extremely new to this os.  (NOTE:  I do not have any sort of software disc, a friend who passed put the os on an old laptop of mine and told me to "try it, youll love it")  Will need beginer step by step instructions

---

### Post by ibjsb4 on 2013-02-01
My guess is your boot is full.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
l /boot
```

And please post the output.

---

### Post by thelegendofdirte on 2013-02-01
I cant open the terminal, when i turn on the computer i am given a menu with,

Ubuntu, with Linux 3.2.0-36-generic
Ubuntu, with Linux 3.2.0-36-generic (recovery mode)
Previous Linux Versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)


if i select the top two or previous versions, i get the error: out of disk, if i do the memory tests it passes all of them without errors and takes me back to that screen

---

### Post by SeijiSensei on 2013-02-01
You'll need to download an installation CD and boot from that.  Then you can mount the hard drive and see what's happening.  Kernel 3.2.0-36-generic comes with Kubuntu 12.04, so the CD is [here](http://cdimage.ubuntu.com/kubuntu/releases/12.04.1/release/).

Boot the CD and choose "Try Ubuntu" when prompted.  Follow the normal procedure you use to connect to your network, then open the browser and return to this thread.

Now open a terminal ("Konsole") from the main menu and type this command at the dollar-sign prompt:

```
$ fdisk -l
```

Copy the results of that command and post it here inside [noparse]```

```[/noparse] tags.  That will give us a starting point for further help.

---

### Post by ibjsb4 on 2013-02-01
Is this a standard install (windows & ubuntu on separate partitions) or is this a wubi install (ubuntu inside windows).

If its a standard install you can use the "live CD" to access it and run the command:

```
df -TH
```

If this is "wubi", I have no idea how to proceed and you will need to wait for someone else to help you.

---

### Post by ibjsb4 on 2013-02-01
Guess were in sync Seiji  :)

---

### Post by SeijiSensei on 2013-02-01
I don't think running df after booting from the CD will report on his hard drive since it won't be mounted, will it? That's why I wanted to wait until he showed us the drive's partition table.

---

### Post by ibjsb4 on 2013-02-01
> **SeijiSensei said:**
> I don't think running df after booting from the CD will report on his hard drive since it won't be mounted, will it? That's why I wanted to wait until he showed us the drive's partition table.

I don't think I want to start second guessing this and just wait to see what the op has to say.

---

### Post by thelegendofdirte on 2013-02-05
i downloaded the disc on the computer i am using that works, but how can i use it on the one that isnt? (there is no windows on the bad, only kubuntu, and this comp is so old it had no cd burner, can i use a flash drive?) a friend told me i will probably have to buy a certain connector and "slave" it to erase files so it will no longer be full???

---

### Post by ibjsb4 on 2013-02-05
You can download Kubuntu 12,04 and burn it to USB.

[http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download)

What kind of computer is this?

---

