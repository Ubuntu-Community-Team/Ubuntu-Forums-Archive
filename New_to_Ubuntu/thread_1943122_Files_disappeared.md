---
title: "Files disappeared"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by gbsk on 2012-03-19
Lately, when my cursor freezes, I have no alternative to turn off the  computer and restart it. Last night I came home and my wife used the  computer during the day.  I use Ubuntu 11.10.  The cursor was frozen  when I arrived so I restarted the computer.  Today we tried to find some  files.  There are no files in downloads or files or anyplace,  Does  anyone know where the files disappeared and how I can find them?  All  the files were previously saved.

Thanks
GB

---

### Post by winh8r on 2012-03-19
If your computer freezes up the safe way to shut it down and restart is this:

press and hold down the ALT key.

press and release the PrintScreen (PrtScr/SysReq) key

Then slowly type these letters 

R E I S U B 

This will save everything,unmount the filesystem cleanly and reboot the machine and avoid filesystem damage and data loss.

If you boot your machine from a Live CD and run this command from the terminal:

```
sudo e2fsck -C0 -p -f -v /dev/sdb
```

where /dev/sdb is the name of the disk on your machine.

you can find the name by running
```

df -h
```

This will check and attempt to repair the filesystem, but you must run it from a Live CD as the filesystem must be unmounted.

When this is finished you can remove the live cd and reboot the machine.

If your files are still not visible then run the live cd again and open a terminal and enter 

```
sudo apt-get install testdisk
```

testdisk/photorec should be able to find the missing files and allow you to recover them.

there is a step by step guide to using this utility at:

[http://www.cgsecurity.org/]("http://www.cgsecurity.org/")

Read the guide carefully before proceeding, and ask if you have any questions.

Hope this helps you.

---

### Post by sanderj on 2012-03-19
> **gbsk said:**
> Lately, when my cursor freezes, I have no alternative to turn off the  computer and restart it. Last night I came home and my wife used the  computer during the day.  I use Ubuntu 11.10.  The cursor was frozen  when I arrived so I restarted the computer.  Today we tried to find some  files.  There are no files in downloads or files or anyplace,  Does  anyone know where the files disappeared and how I can find them?  All  the files were previously saved.

Thanks
GB

Not an answer to your question, but a freezing computer is not a good thing. And power-flipping is not good either. So, after trying to get your files back, you should try to solve that (root cause) problem (probably best in a separate forum thread). Two basic things I do with a frozen system:
- press the numlock or capslock key: does it change the corresponding light?
- can you ping / ssh the frozen system from another system?

---

### Post by gbsk on 2012-03-20
I am not that advanced with Linux.  I downloaded Ubuntu from my son's computer.  I then upgraded to 11.10 when it came out probably in Nov.  or Dec.  I can understand the saving of files when the cursor freezes but did not know it when it happened.  I cannot remember it but will write it down for further use in the future.  I do not hAVE A LIVE cd so cannot start that way.  I do not understand how to put the info in the  terminal and entering the code.  How do I do this?  I did download the program you suggested.  I opened it and only programs from Saturday came up.  That is  when it crashed.  Am I doing something wrong?

Thanks for helping.

GB


> **winh8r said:**
> If your computer freezes up the safe way to shut it down and restart is this:

press and hold down the ALT key.

press and release the PrintScreen (PrtScr/SysReq) key

Then slowly type these letters 

R E I S U B 

This will save everything,unmount the filesystem cleanly and reboot the machine and avoid filesystem damage and data loss.

If you boot your machine from a Live CD and run this command from the terminal:

```
sudo e2fsck -C0 -p -f -v /dev/sdb
```where /dev/sdb is the name of the disk on your machine.

you can find the name by running
```

df -h
```This will check and attempt to repair the filesystem, but you must run it from a Live CD as the filesystem must be unmounted.

When this is finished you can remove the live cd and reboot the machine.

If your files are still not visible then run the live cd again and open a terminal and enter 

```
sudo apt-get install testdisk
```testdisk/photorec should be able to find the missing files and allow you to recover them.

there is a step by step guide to using this utility at:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Read the guide carefully before proceeding, and ask if you have any questions.

Hope this helps you.

---

### Post by winh8r on 2012-03-20
To open a terminal you can either:

press control + alt + T 

**OR**

Enter the word "terminal" in the search box on the Unity dash and click on the terminal that shows up in results.

The commands can be copied and pasted using your mouse, just highlight the command , either right click and select copy, or middle click, then go to the terminal and depending on which method you used either right click and select paste or middle click and the command will appear at the flashing "prompt". All you need to do then is hit enter and the command will run.

It would be a good idea to get a live cd, as they are very useful if you have any filesystem problems or need to recover data, where you are required to access the filesystem when it is unmounted (not being used by the operating system)

---

