---
title: "Need Help Please"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by BostonBigGuy on 2008-08-11
[B]I just received the CD for Ubunta on Saturday, August 9, 2008. I place the CD into my CD Drive and choice to install Ubunta as a secondary os.  Now after installing Ubunta I get at start up a choice to boot to WinXP or Ubunta.  Now when I choice WinXP I keep getting this error

autochk program not found - skipping AUTOCHK

then it (computer) just keeps going back to the beginning where I can choise the os again.  I even tied to boot Ubunta but nothing happens there either.

I have a lot of programs that I use every day and now I can't even boot to it.  I choice to run Ubunta as a secondary os so that I could learn more about Ubunta programs but now I stuck in limbo.  Can't boot to WinXP Home Edition or Ubunta Desktop Edition.

Any help would be appriciated.

CD I had received is:

8.04.1 LTS
Desktop Edition

Thanks.

BostonBigGuy[/B]

---

### Post by tuxxy on 2008-08-11
Maybe the windows partition is set to NTFS hidden?  [this]("http://www.hardwareanalysis.com/content/topic/16969/") link seems to cover similar problems, maybe it will help

---

### Post by laffinet on 2008-08-11
Can you provide some more detail, please:

What install method did you use (guided partitioning, manual partitioning etc.)

Also, can you boot into the Live Disc (boot the Ubuntu CD you received and choose the Try Ubuntu/Live CD option), open a terminal, run 
```
sudo fdisk -l 
```
and post the output here.

---

### Post by BostonBigGuy on 2008-08-11
When I received the disk in the mail ... I put it into the cd drive and I believe it was the first option that you can do ... I don't have an option now to see what the options were when you put it into the cd drive but if you can tell me what the options were I can tell you which one I had picked ... I run the cd/live (I guess) and everything ran okey, again I guess ... but couldn't find where I could type that code that you asked me to ... sorry ... I'm a nebie and this is driving me nuts ... so please be simple when asking me to do certain things ... step by step if you don't mind ... [email]("BostonBigGuy@gmail.com") me if you wish or I can give you my aol or yahoo im so we can chat ... thanks again ... BostonBigGuy

---

### Post by AbtZ on 2008-08-11
Please use proper paragraphs when posting -- it makes your posts easier for us to read.

To open a terminal you click Applications->Accessories->Terminal when running Ubuntu from the Live CD. This is where you should enter the command laffinet gave you.

---

### Post by hyper_ch on 2008-08-11
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by BostonBigGuy on 2008-08-11
Here's what I get on that command.

Usage: fdisk [-b SSZ] [-u] DISK    Change partition table
       fdisk -* [-b] [-u] SSZ      List partition table(s)
       fdisk -s PARTITION          Give partition size(s) in blocks
       fdisk -v                    Give fdisk version
Here DISK is something like /dev/hnb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

* on the second line there was a funny looking long z that I don't have on my keyboard.

Hope this helps you to help me.

---

### Post by john test on 2008-08-11
The funny looking z might be a tilde ~ upper left on most keyboards
The output you posted seems as though you spelled the command wrong
sudo fdisk -l  where the last character is a lower case L

---

### Post by matthewcraig on 2008-08-11
Sorry you are still having trouble diagnosing your problem.  Let me see if I can help a little with that command.

When you a command gives you output like that, where it describes the proper use of the command line parameters, then it means you got the syntax wrong.  The command required only one dash and a letter:  the dash is typically next to the plus (+) symbol, and the letter is a lower case L - not to be confused with a 1 (one).

So, from the command line (in the terminal application), type ...
```
sudo fdisk -l
```
This will ask you for your password, unless you are running from the live-cd installation disk, in which case it will not ask for a password.

You should see the output of your hard disk parititions.  Cut and paste the output in this message thread.

In the future, you should start getting familiar with the commands you run - or are asked to run - by searching for them first on Google.  There is a lot of information available on Linux technology, on the Internet, so no reason not to educate yourself while you troubleshoot.  Especially when someone asks you to run a command with "sudo"... the "sudo" command enables Ubuntu to have distructive capabilities.

---

### Post by BostonBigGuy on 2008-08-11
I can't copy & paste due to the computer I am on now ... I can't get on the internet with the one I'm having this problem with but here is the response I get from that command: I'm using Live/CD

    Device Boot   Start        End      Blocks     Id     System
/dev/sdal    *        1       9729    78148161     17     Hidden HPFS/NTFS

Thanks again for your help.
BostonBigGuy

---

### Post by john test on 2008-08-12
It looks like the output of fsck -l comes up with Hidden just as guessed in the second post of this thread.  Did the links given by tuxxy help at all?

---

### Post by BostonBigGuy on 2008-08-12
[B]Here's my biggest problem ... The computer I'm using now does not have any kind of drive, floppy or disk ... It only allows me to view or leave meessages ... So I need help in getting that NTFS unhidden so that I'll be able to access my files ... I don't have either WinXP Home Edition original disk as well as the restore disk ... So I'm stuck in limbo as of right now ... Any suggestion on how I can fix this problem would be appriciated ... I can see all my files using Live/CD ...

Thanks

BostonBigGuy[/B]

---

