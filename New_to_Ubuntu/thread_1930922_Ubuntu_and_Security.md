---
title: "Ubuntu and Security"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by RomaSonic777 on 2012-02-24
Hi All,

I am new to Linux and found that Ubuntu is a good place for beginners to start. I managed to virtualize my mac via vmware and have installed 11.10. What tools do you recommend regarding security? Basically i want to monitor incoming and outgoing connections and a good AV/malware scanner. Also how can i check running programs and kill unnecessary processes? Any help would be very appreciated.

---

### Post by HermanAB on 2012-02-24
Howdy,

Ubuntu Linux is pretty secure by default.  The only security tool you really need is a good memory, to remember a long password.

You can view your network with tcpdump and the processes with ps.

---

### Post by Leisko on 2012-02-24
> **RomaSonic777 said:**
> Hi All,

and a good AV/malware scanner. Also how can i check running programs and kill unnecessary processes? Any help would be very appreciated.

You don't need AV-scanner on Ubuntu. But if you send files between Windows and Linux, then you could scan Windows viruses with ClamAV.

And you can check running programs and kill processes with system monitor. e.g. gnome-system-monitor.

---

### Post by sudodus on 2012-02-24
You can also have a look at the following link
[[COLOR="Red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
although it states that it is not meant for servers, it is a good introduction.

---

### Post by CharlesA on 2012-02-24
> **sudodus said:**
> You can also have a look at the following link
[[COLOR="Red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
although it states that it is not meant for servers, it is a good introduction.
It's a good start for servers too, as it has a ton of info. :)

Which reminds me I need to add that to my sig.

---

### Post by RomaSonic777 on 2012-02-24
> **HermanAB said:**
> Howdy,

Ubuntu Linux is pretty secure by default.  The only security tool you really need is a good memory, to remember a long password.

You can view your network with tcpdump and the processes with ps.

Hi Herman,

Thanks for replying. Does tcpdump give the ability to deny certain connections? 

About the ps. When entering this in terminal if gives no output. I tried ps (username) but this gives an error: unsupported option (BSD syntax). I did a search and found that "ps aux" or "ps ux" work great to see running processes. Thanks for the heads up.


> **Leisko said:**
> You don't need AV-scanner on Ubuntu. But if you  send files between Windows and Linux, then you could scan Windows  viruses with ClamAV.

And you can check running programs and kill processes with system monitor. e.g. gnome-system-monitor.

I don't exactly know how to send files between Ubuntu and my mac. For example i tried to upload a picture to my photobucket using Ubuntu. The picture could not be found as it is stored on my Mac files. Not completely sure how to do this. Can you share some more about this?

About the system monitor. I found it and find it easier killing processes instead in terminal. What is the exact difference anyway? I mean what are the possibilities of terminal and what is it used for?


> **sudodus said:**
> You can also have a look at the following link
[[COLOR=Red]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")
although it states that it is not meant for servers, it is a good introduction.

Wow that's a chunk of information, will look into this later. Thanks for sharing.


> **CharlesA said:**
> It's a good start for servers too, as it has a ton of info. :smile:

Which reminds me I need to add that to my sig.

Thank you all for taking the time to help out.

---

### Post by CharlesA on 2012-02-24
> **RomaSonic777 said:**
> Hi Herman,

Thanks for replying. Does tcpdump give the ability to deny certain connections?

TCPdump just tells you which connections are active. You'd need to mess with the firewall settings to deny certain connections. Check out ufw or gufw.

> I don't exactly know how to send files between Ubuntu and my mac. For example i tried to upload a picture to my photobucket using Ubuntu. The picture could not be found as it is stored on my Mac files. Not completely sure how to do this. Can you share some more about this?

You can probably share files using NFS or Samba, since it's a mac.

I found a video about setting up Samba, that might help:
[http://www.youtube.com/watch?v=deb2jRm3c7g](http://www.youtube.com/watch?v=deb2jRm3c7g)

> About the system monitor. I found it and find it easier killing processes instead in terminal. What is the exact difference anyway? I mean what are the possibilities of terminal and what is it used for?

It's just a different way to get things done. Most people give instructions for the terminal because you can run a variety of different desktop environments and/or window managers - KDE, Gnome shell, Unity, etc.

---

### Post by RomaSonic777 on 2012-02-24
> **CharlesA said:**
> TCPdump just tells you which connections are active. You'd need to mess with the firewall settings to deny certain connections. Check out ufw or gufw.

Thanks a million Charles. I just installed gufw and enabled ufw. This gives a bit more ease of mind knowing that a firewall is installed :) I will instal TCPdump also and see what rules are suspicious and add them in gufw. I will learn more about this.



> **CharlesA said:**
> You can probably share files using NFS or Samba, since it's a mac.

I found a video about setting up Samba, that might help:
[http://www.youtube.com/watch?v=deb2jRm3c7g](http://www.youtube.com/watch?v=deb2jRm3c7g)

I will look into this later. Thanks for sharing the link.



> **CharlesA said:**
> It's just a different way to get things done. Most people give instructions for the terminal because you can run a variety of different desktop environments and/or window managers - KDE, Gnome shell, Unity, etc.

Are there any tutorials available to learn more about terminal and commands and can you pls share a link?

---

### Post by CharlesA on 2012-02-24
> **RomaSonic777 said:**
> 
Are there any tutorials available to learn more about terminal and commands and can you pls share a link?

I know of this: [http://ss64.com/bash/](http://ss64.com/bash/)

Might give you a headache tho. ;)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by RomaSonic777 on 2012-02-25
Perfect. Just what i was looking for.

---

### Post by agillator on 2012-02-25
Roma, at some point do check out the manual page and perhaps a tutorial on iptables. That is actually the firewall you are using, ufw and gufw are handy (and good) front ends, much easier to use. However, they are limited in what they can/will do. There is much, much more iptables itself is capable of. Perhaps you don't need the additional capability, perhaps you do. At least you will know it is there. Much of it you can get to through ufw/gufw if you try. Some you need to do manually. Obviously there is no rush, but it sounds to me as if you would find it handy to know.

---

### Post by jmszr on 2012-02-25
RomaSonic777,

Just in case you overlooked this command line "Sticky" at the beginning of the ABT subforum: [http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108) ; you will find it a most excellent resource.

Hope that helps.

---

### Post by Mach101 on 2012-02-25
> **HermanAB said:**
> Howdy,

Ubuntu Linux is pretty secure by default.  The only security tool you really need is a good memory, to remember a long password.

You can view your network with tcpdump and the processes with ps.

I am new to Linux and it sounds great that the system is virus free, but what about Malwares and in case of receiving an affected file, how to deal with these?

---

### Post by agillator on 2012-02-26
Mach101, what kind of 'malware' are you concerned about? Look at the permission system on *nix systems. The first thing that has to happen for malware to work is it must have permission to execute. How is it going to get permission to execute? There are ways, obviously, but most involve some error by you the user - publishing a password, executing a file you know nothing about, etc. So your first line of defense is your good common sense. Now, if you are running a MySQL server or an FTP server or something there are hazards you need to be aware of, but those are security subjects for those systems, not Linux. The key for the system, then, is your password. If you have a good password, protect it, someone is really going to have problems. If the system password file is stolen then that might help someone gain access, but stealing that is not easy. Security is a complicated subject and you are right to be concerned. But, I think you will find that Linux is pretty secure just out of the box. As a matter of fact, I have heard (and do not know the truth for sure) that the reason the NSA (yes, the National Security Agency) helped develop and release SELinux was because they found Windows to be impossible to secure and Linux to be almost secure enough to suit them as it comes off the shelf. Just some tweaking needed. Of course they found a hard way to do it so few adopted their system, but . . . . So, to get an answer to your question that satisfies you, do a little digging on Google or whatever, look into the iptables firewall a little. I think you will be reassured.

---

### Post by RomaSonic777 on 2012-02-26
> **agillator said:**
> Roma, at some point do check out the manual page and perhaps a tutorial on iptables. That is actually the firewall you are using, ufw and gufw are handy (and good) front ends, much easier to use. However, they are limited in what they can/will do. There is much, much more iptables itself is capable of. Perhaps you don't need the additional capability, perhaps you do. At least you will know it is there. Much of it you can get to through ufw/gufw if you try. Some you need to do manually. Obviously there is no rush, but it sounds to me as if you would find it handy to know.

Agillator,

Thanks for the info. I am learning more on this at [[COLOR="Blue"]Iptables firewall tutorial[/COLOR]]("https://help.ubuntu.com/community/IptablesHowTo") It is a chunk of information though but i will get through it. I did get the TCPdump to log all connections but not completely able to understand the data it gives. I am getting a more clear picture now on how to block a possible "suspicious connection" of the output in TCPdump via gufw but really need to learn more on how to understand the data

What do you exactly mean with -Manual Page- ?

---

### Post by haqking on 2012-02-26
> **RomaSonic777 said:**
> Agillator,

Thanks for the info. I am learning more on this at [[COLOR="Blue"]Iptables firewall tutorial[/COLOR]]("https://help.ubuntu.com/community/IptablesHowTo") It is a chunk of information though but i will get through it. I did get the TCPdump to log all connections but not completely able to understand the data it gives. I am getting a more clear picture now on how to block a possible "suspicious connection" of the output in TCPdump via ugfw but really need to learn more on how to understand the data.

**What do you exactly mean with -Manual Page-?**

```
man iptables

```

---

### Post by RomaSonic777 on 2012-02-26
> **jmszr said:**
> RomaSonic777,

Just in case you overlooked this command line "Sticky" at the beginning of the ABT subforum: [http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108) ; you will find it a most excellent resource.

Hope that helps.

Thanks Jmszr. I appreciate that very much.

---

### Post by RomaSonic777 on 2012-02-26
> **haqking said:**
> ```
man iptables

```

Wow 2352 lines of even more information :) Thanks for the heads up HaqKing.

---

### Post by haqking on 2012-02-26
> **RomaSonic777 said:**
> Wow 2352 lines of even more information :) Thanks for the heads up HaqKing.

there is a man page for most things.

except 

```
man woman
```

;-)

---

### Post by sudodus on 2012-02-26
> **haqking said:**
> there is a man page for most things.

Except 

```
man woman
```

;-)
+1 :-)

---

### Post by RomaSonic777 on 2012-02-26
> **haqking said:**
> there is a man page for most things.

except 

```
man woman
```

;-)

A lot of men would be very happy if there was

---

### Post by Mach101 on 2012-02-26
Thanks for the reply alligator.
Searching googles gives an indication that the problem is not so huge as it is with Windows. However there are antivirus company such as Avast offering a freeware version for homeusers. I guess there is a risk that the system/PC get infected. But my main concern is, that is it necessary to have an antivirus installed?

---

### Post by sudodus on 2012-02-26
Have a look at this thread
[[COLOR="Red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by RomaSonic777 on 2012-02-26
How can i check permissions for files and if they have execute permission and how to change that? I was reading [[COLOR="Blue"]File permissions[/COLOR]]("https://help.ubuntu.com/community/FilePermissions") but i get command not found when, for example, entering -rw-r--r--

---

### Post by sudodus on 2012-02-26
> **RomaSonic777 said:**
> How can i check permissions for files and if they have execute permission and how to change that? I was reading [[COLOR="Blue"]File permissions[/COLOR]]("https://help.ubuntu.com/community/FilePermissions") but i get command not found when, for example, entering -rw-r--r--
```
ls -l
``` or
```
ls -la
``` to show also hidden files

---

### Post by RomaSonic777 on 2012-02-26
Thanks Sudodus. That did it. I did noticed that some files are set to CHMOD (1). What files are absolutely needed to be (1)? I don't want to make changes that will break or cause the system to malfunction.

---

### Post by sudodus on 2012-02-26
> **RomaSonic777 said:**
> Thanks Sudodus. That did it. I did noticed that some files are set to CHMOD (1). What files are absolutely needed to be (1)? I don't want to make changes that will break or cause the system to malfunction.
What do you mean by CHMOD (1)?

---

### Post by agillator on 2012-02-26
Romasonic, at this point let me say 'Welcome to Linux.' You are seeing several things here. One is the supposed complexity of Linux and why some are afraid of it until they try it. Another is that there is, in many opinions including mine, far more help and support available than for questions and problems in Windows. Of course we all expect that when you see someone else have the same questions you have just had, you will be anxious to jump in and help them as you were helped. There IS a learning curve, but it is well worth the effort. 

Back to your original question. Yes, there are virus checkers out there. Most of us don't bother with them, not because they are not fine pieces of work, but because at least at this stage they aren't really necessary. Most are not the 'on access' type you are used to. They are 'on demand'. In other words, you specifically run them when you want your system (or a piece of it) checked. There are some that are on access, but those are not for workstations, but for mail servers themselves. If you run your own mail server, take a look at ClamAV, for example. 

Run a test to demonstrate. Send yourself an executable file as an attachment to an email. When you receive it, save it and try to execute it. I don't know what email client you are using, but I will almost guarantee you that it will NOT be executable UNLESS you change permissions to make it executable. For you to get infected you almost HAVE to cooperate and almost do it yourself, at least through email. If you arbitrarily download a file from somewhere on the internet it probably is also not going to be executable unless you make it so. Downloading a file to be run by another program - Apache, for example - is another story. But do you begin to see the pattern? A virus or any kind of 'malware' on Linux is not such an easy proposition without the assistance of the user - not impossible, but certainly not easy.

---

### Post by RomaSonic777 on 2012-02-28
> **sudodus said:**
> What do you mean by CHMOD (1)?

Sudodus, by this i mean the permissions for a certain file or files. Check out [[COLOR="Blue"]CHMOD[/COLOR]]("http://en.wikipedia.org/wiki/Chmod") for more

---

### Post by RomaSonic777 on 2012-02-28
> **agillator said:**
> Romasonic, at this point let me say 'Welcome to Linux.' You are seeing several things here. One is the supposed complexity of Linux and why some are afraid of it until they try it. Another is that there is, in many opinions including mine, far more help and support available than for questions and problems in Windows. Of course we all expect that when you see someone else have the same questions you have just had, you will be anxious to jump in and help them as you were helped. There IS a learning curve, but it is well worth the effort. 

Back to your original question. Yes, there are virus checkers out there. Most of us don't bother with them, not because they are not fine pieces of work, but because at least at this stage they aren't really necessary. Most are not the 'on access' type you are used to. They are 'on demand'. In other words, you specifically run them when you want your system (or a piece of it) checked. There are some that are on access, but those are not for workstations, but for mail servers themselves. If you run your own mail server, take a look at ClamAV, for example. 

Run a test to demonstrate. Send yourself an executable file as an attachment to an email. When you receive it, save it and try to execute it. I don't know what email client you are using, but I will almost guarantee you that it will NOT be executable UNLESS you change permissions to make it executable. For you to get infected you almost HAVE to cooperate and almost do it yourself, at least through email. If you arbitrarily download a file from somewhere on the internet it probably is also not going to be executable unless you make it so. Downloading a file to be run by another program - Apache, for example - is another story. But do you begin to see the pattern? A virus or any kind of 'malware' on Linux is not such an easy proposition without the assistance of the user - not impossible, but certainly not easy.

Thanks Agillator,

This gives me even more peace of mind. On Windows you can get drive by'd and not even know it. Will definitely help out if i am able to.

---

### Post by sudodus on 2012-02-28
> **RomaSonic777 said:**
> Sudodus, by this i mean the permissions for a certain file or files. Check out [[COLOR="Blue"]CHMOD[/COLOR]]("http://en.wikipedia.org/wiki/Chmod") for more
Is this what you mean?

**S_IXOTH  00001  execute/search by others**

No I don't think so, but what permission is set, when you describe it as CHMOD (1)?
- user, group, others
- read, write, execute/search

---

### Post by RomaSonic777 on 2012-03-02
> **sudodus said:**
> Is this what you mean?

**S_IXOTH  00001  execute/search by others**

No I don't think so, but what permission is set, when you describe it as CHMOD (1)?
- user, group, others
- read, write, execute/search

This means it is set to execute, check out: [[COLOR="Blue"]File Permissions[/COLOR]]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by sudodus on 2012-03-04
> **RomaSonic777 said:**
> Thanks Sudodus. That did it. I did noticed that some files are set to CHMOD (1). What files are absolutely needed to be (1)? I don't want to make changes that will break or cause the system to malfunction.
Files that need execute permissions are

1. Directories, that you want to open, and you decide if they should be possible to open for the owner, the group, or others (who are logged in).

2. Files that you want to execute (binary executable programs or shell scripts), and you decide if they should be possible to open for the owner, the group, or others (who are logged in).

If you do not know how a file or directory is used, you should not tamper with the permissions, because the system needs permissions on many files. If you suspect that it is created or changed by an intruder, ask specifically about that file or directory, and hope that a security expert will read your post and reply ;-)

---

### Post by cheatos on 2012-03-04
Hi there, I tried this tcpdump command to see my connections, but somehow it doesn't work, should I be concerned now?

```
user@PC:~$ tcpdump
tcpdump: no suitable device found

```

Can it be possible that my network card driver or whatever it is called in ubuntu isn't installed correctly?
I'm running lubuntu11.04 by the way

---

### Post by CharlesA on 2012-03-04
You probably have to tell it what interface to monitor.

```
tcpdump eth0
```

---

### Post by cheatos on 2012-03-04
No, still the same:

```
tcpdump eth0
tcpdump: no suitable device found

```

---

### Post by CharlesA on 2012-03-04
Check out the man page then. It'll say what it needs to run.

---

### Post by RomaSonic777 on 2012-03-04
> **sudodus said:**
> Files that need execute permissions are

1. Directories, that you want to open, and you decide if they should be possible to open for the owner, the group, or others (who are logged in).

2. Files that you want to execute (binary executable programs or shell scripts), and you decide if they should be possible to open for the owner, the group, or others (who are logged in).

If you do not know how a file or directory is used, you should not tamper with the permissions, because the system needs permissions on many files. If you suspect that it is created or changed by an intruder, ask specifically about that file or directory, and hope that a security expert will read your post and reply ;-)

Hi Sudodus,

Thanks for pointing that out. I appreciate your help very much.

---

