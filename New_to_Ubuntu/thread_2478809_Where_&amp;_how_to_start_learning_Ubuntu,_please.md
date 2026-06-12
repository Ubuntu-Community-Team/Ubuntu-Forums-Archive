---
title: "Where &amp; how to start learning Ubuntu, please?"
date: 2022-09-06
forum: New to Ubuntu
---

### Post by kuen2 on 2022-09-06
Entirely new to Ubuntu.  Have been thinking about learning it recently.  Where and how to start it, please?
Thanks.
Kuen

---

### Post by pantazi on 2022-09-06
I downloaded Ubuntu five years ago just to avoid W10, read a lot from this forum and YouTube videos. Learned to walk before running and never looked back. Made a few errors (correcting them taught me more). I am 74 years of age.
Although you will read 'Ubuntu is for geeks', the OS is perfect for general use and if you cover the basics and don't overreach, you'll find, if you are inquisitive, you'll want to extend your knowledge further.
Good luck!

---

### Post by ajgreeny on 2022-09-06
If you have a separate machine on which you can install it, keeping the Windows machine you currently use completely unscathed, just use Ubuntu for the basics as a start.

Unless you are more knowledgeable about dual booting I suggest you avoid that until you know more, particularly if currently using Windows 8 or newer.

A really good alternative is to use a virtual install on, for example, Virtualbox which allows you too try things out, and if you break the VM simply reinstall it.

---

### Post by ActionParsnip on 2022-09-06
Just using the OS is a good start. Just the same way as you learned Windows.....

---

### Post by The Cog on 2022-09-06
I agree with all of the above. Nothing beats actually using it to do something. Any simple task that takes your fancy as interesting. But learn to walk before you try running. 
Don't expect your Windows skills to transfer directly over. Some things will be very similar and maybe lead you into a false sense of knowing your way around. Other things will be unexpectedly and wildly different. Linux is not Windows. They made different decisions on some quite fundamental design aspects.

One example is the file system layout. Some folders don't contain files at all. For instance, /dev contains device driver interfaces. /dev/sda (if present) will look like a file and you can read and write it like a file, but will be a bit -for-bit image of a hard disk including the partition table and all the partitions. Writing to it will likely overwrite the partition table and leave the disk unusable. /proc contains configuration settings of running processes, /proc/net contains the running network configuration items. Writing to these can crash processes and alter the network settings. There is nothing like this in Windows that I know of. It's an API, not real files.
Also, if you insert a USB drive (labelled BACKUP for instance), you don't see a BACKUP: drive appear - you will likely find a new folder appear in /media/your-name/BACKUP instead. I recently saw a post from a Linux newcomer getting very indignant about the fact that his stick didn't create a new separate BACKUP: file tree somehow divorced from all the rest of the system file tree.
So, read about the filesystem layout early on - that's something you will need to know.

Learn just a little about using the terminal. Get familiar with the idea of a "current working directory" and how to navigate the tree, list and copy files.
Good luck, and enjoy learning.

---

### Post by kuen2 on 2022-09-06
Thank you, Pantazi.

[COLOR=#000000]"downloaded Ubuntu five years ago just to avoid W10,"
Why is that?  Does Windows 10 cause trouble with Ubuntu?
Thanks.
Kuen
[/COLOR]

---

### Post by kuen2 on 2022-09-06
Thank you, Ajgreeny.

"[COLOR=#000000]If you have a separate machine..."
Yes, I have an old machine which was bought in 2009 running Windows 7.  

What are the basic requirements for installing a basic version of ubuntu?

Again, thanks.
Kuen[/COLOR]

---

### Post by kuen2 on 2022-09-06
> **ActionParsnip said:**
> Just using the OS is a good start. Just the same way as you learned Windows.....

Thank you.

Are you kidding?  I have never touched ubuntu so far but saw someone use it ten years ago.  I remember, I could not understand any of what the man was doing on his PC with ubuntu OS.

Appreciate.
Kuen

---

### Post by kuen2 on 2022-09-06
Thank you, The Cog.

It is so much different from Windows that it scares me to even start learning.

Many years ago, I heard people say that one has to give ubuntu orders for it to work for you.  For heavens, how do I know to give what orders!  

Appreciate.
Kuen

---

### Post by Impavidus on 2022-09-06
You have a graphical user interface (GUI), a web browser, text editors, word processor, spreadsheet program, video and music player, etc. That's all the same as on Windows.

There are some important differences:
- Most software is installed from repositories. It has been like that in the Linux world for ages. Now guess where Apple and Android got that idea from. Don't install software you downloaded from random websites, unless there's no other way and you know you can trust it. There are several tools you can use to install software from these repositories.
- All files and directories are in one tree. If you plug in some external drive, it gets attached to the tree somewhere. The tree even has some pseudo-filesystems, which allow you to get information about running processes etc. Not something most beginners need.
- File permissions are at the core of security: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
- There's no need to run a virus scanner in the background all the time. Malware exists, but is rare, and the main security threat to your computer is that hominid sitting at your desk.
- The GUI is just another application.
- There's a tool for installing third-party drivers. Look for "additional drivers". Don't look for them on the web; the tool should select and install the drivers almost automatically.
- You have much more freedom. You can do whatever you want, including breaking your system. That doesn't mean there's a tool readily available for everything you might want. Maybe you have to write the tool yourself, which may be a problem for some.
- The command line actually gives you power.
- Some hardware manufacturers just don't provide good Linux drivers and don't provide the information needed to create such drivers to the community.

Ubuntu 22.04 may be a bit heavy for a computer from 2009. I think a decent 64-bit dual-core CPU, about 4GiB of memory, 40GB hard drive space and decent graphics are the minimum for Ubuntu, but this isn't a very hard line. For older computers, you can use lighter flavours (Xubuntu, Lubuntu etc.). They have some lighter applications installed as defaults, including a lighter GUI. I think about 1GiB of memory, a 64-bit CPU and about 20GB of hard drive are the bare minimum.

---

### Post by Dennis N on 2022-09-06
> **kuen2 said:**
> Entirely new to Ubuntu.  Have been thinking about learning it recently.  Where and how to start it, please?
Thanks.
Kuen

Personally, in 2007 as a refugee from Win XP, I bought a book which had an Ubuntu CD to install it. I read the entire book first, so got a general idea of how Linux worked and what to expect. Soon after, I joined these Ubuntu Forums. Be sure any book is aimed at beginners. You can Google and find some specific books currently offered.

---

### Post by The Cog on 2022-09-06
> **kuen2 said:**
> Thank you, The Cog.
Many years ago, I heard people say that one has to give ubuntu orders for it to work for you.  For heavens, how do I know to give what orders!  
Kuen

The same is true of Windows. There are lots of admin tasks you can't do without knowing a few powershell commands. Don't kill yourself trying to memorise every command. I suggest you learn these few though.
pwd : print working directory, says which directory you're in
cd : change to a different directory
ls : list the files in a directory
cp : copy files from one place to another
gedit : edit a file
exit : close the command session
firefox : launch firefox (same approach for most programs, just name them to run them)
That list is not too hard, and will give you a taste of things.

More advanced is **[FONT=Courier New][COLOR="#0000CD"]lshw | less[/COLOR][/FONT]** which will list your hardware and pass the result into **less** which is a viewer that allows you to scroll up and down the list (use Q to quit less). Piping the output of one command into the input of another is a common and extremely powerful thing to be able to do, and probably the first time you use it will be to pass some text into grep which is a text searching utility. e.g. **[FONT=Courier New][COLOR="#0000CD"]lshw | grep -A3 network[/COLOR][/FONT]** (list hardware and search for the word network and the following 3 lines). Things like that may not be needed for a long time though, so for a start, just note that these kinds of things are possible.

---

### Post by kuen2 on 2022-09-06
Thank you, Impavidus.


After reading what you have said, I have a question to myself: Who uses ubuntu or linux?
My answer:
1. Computer programmers and/or experts who know the machine and language inside out.
2. Smart guys who enjoy the kick of it.
3. Guys who have nothing but time to kill.


I am of the category of 3. mentioned above, but I do not want to get myself frustrated,though.


About my question:
1. I am an aboriginal of one of the islands in the southwestern pacific.
2. I learnt English & Chinese & a bit of Spanish and German.
3. Every time I started learning a new language, the first stage was and probably still is to learn the letters, phonics and some simple grammar rules.
4. This is what in my mind when I ask the question here.
5. Can or may ubuntu be learnt in the same or similar manner as learning a language?


Thank you for the detailed instructions.


Kuen

---

### Post by pantazi on 2022-09-07
> **kuen2 said:**
> Thank you, Pantazi.

[COLOR=#000000]"downloaded Ubuntu five years ago just to avoid W10,"
Why is that?  Does Windows 10 cause trouble with Ubuntu?
Thanks.
Kuen
[/COLOR]

No.
 I didn't want to change my laptop just to accommodate a lot of Microsoft bloatware, so I  went all in and wiped W7, downloaded Ubuntu 16.04 LTS (long term support) and began learning by doing, which I suggest you do too. You will find your computer runs faster and you will exercise your brain cells more!
 
The basics are quite straightforward if you completely ignore your Window's experience. I've since upgraded through 18.04 to 20.04 LTS, bought a newer second-hand laptop and enjoy playing with ideas floated here and on YouTube.

I think you've been given excellent advice so far, so don't over think it, just do it. You'll wish, as I did, you didn't do it years ago.

---

### Post by Impavidus on 2022-09-07
You don't have to be a programmer to use Ubuntu, but to do something special, you need a bit more technical knowledge than on Windows. At the same time, Ubuntu allows you to do really special things, that are simply impossible on Windows.

When I started using Ubuntu, I didn't know it either. I did have some user experience with Unix at university though.

If you're just a simple user who wants to browse the web and write some documents, you don't have to know the internals of Ubuntu. If you want more, you learn the basics. You look up more details when you need them.

---

### Post by mIk3_08 on 2022-09-07
> **kuen2 said:**
> Who uses ubuntu or linux? 
> **Impavidus said:**
> Ubuntu allows you to do really special thing, that are simply impossible on Windows.
Yes!  I strongly agree with Impavidus. There are a lot of amazing and special  things here in Linux Ubuntu that MS windows don't have. When I discover it, I  was really amaze and that is just a few things I've learned here in Linux Ubuntu.  I was just a newbie like you are but If you really love computing their are  a lot more of special things here in Linux Ubuntu that you will discover and  possibly you will conquer the world of computing here in Linux world  thru internet. Regards and cheers.

---

### Post by TheFu on 2022-09-12
I get this question all the time. Enough to write an article about it: [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)

The main thing is to get lots of time using the OS.  If you use it only a few hours a week, then you'll never climb the learning hill.  Use it 7 hours a day for everything and as you need to learn how to do something new, you'll learn it.  For anything that you can't figure out, drop back to Windows for 1 hour and git 'er done.   The next day, start with Linux again ... 

After a few months getting the little stuff learned, then is the time to learn that the GUI isn't the OS.  If using just the GUI, you are using about 20% of the power your system has.  Unlock the other 80% by learning the CLI and a shell.  

For other resources, follow link above.

Always remember that the GUI is just another program, not the OS.

---

