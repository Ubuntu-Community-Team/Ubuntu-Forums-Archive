---
title: "Anti-virus/anti-spyware protection?"
date: 2009-09-23
forum: Recurring Discussions
---

### Post by zking on 2009-09-23
I'm new to Ubuntu. 

I heard Ubuntu is very safe from viruses and spyware. 

Would it still be necessary to download an anti-virus/anti-spyware protection suite on Ubuntu? If so, which program in particular? 

Thanks,

---

### Post by Viva on 2009-09-23
Anti Virus/Spyware is not needed in ubuntu. You can install an antivirus like clam/avg/antivir if you want to check your windows drive for windows viruses.

---

### Post by tom.swartz07 on 2009-09-23
Congrats on making the switch.

Because of the way that Ubuntu runs, and the way that files are opened and executed, there are practically no viruses that would cause any harm. (There is one, but you have to willingly download it and compile it yourself, so it probably will not even be on your radar)


If you still have a Windows or Mac partition, like I do, then you might be worried about viruses from files there. I would suggest AVG. Like practically all Linux programs, it's free. It will allow you to scan your files for any possible nasties that would be hiding in there.

Hopefully this helps! I hope your first foray into Ubuntu is a great one!

Tom

---

### Post by jrusso2 on 2009-09-23
Here comes the daily AV argument thread.

---

### Post by tom.swartz07 on 2009-09-23
Additionally, you might find some of this documentation useful:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)


Also, it would be wise to point out that disk defragmentation is also a thing of the past. The ext3 (and in the next update ext4) file systems are much less prone to fragmentation. 
This thread: [http://ubuntuforums.org/showthread.php?t=1065695](http://ubuntuforums.org/showthread.php?t=1065695) discusses some other basic topics for beginners such as yourself.


Hope this helps!

---

### Post by jmszr on 2009-09-23
zking,

bodhi.zazen's sticky on Ubuntu security may be of interest to you: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by hoppipolla on 2009-09-24
My security consists of a copy of ClamAV that I like NEVER use (but it's nice to have it there!) and the standard Ubuntu firewall :)

If I were you, just search "Virus Scanner" and "Gufw" in Add/Remove and install them, and you're good to go ^_^

Hoppi!

---

### Post by vernonrj on 2009-09-24
Having virus protection is always a good idea. I enjoy avast! for linux personally.

---

### Post by handy on 2009-09-24
> **jrusso2 said:**
> Here comes the daily AV argument thread.

:lolflag:

---

### Post by handy on 2009-09-24
> **vernonrj said:**
> Having virus protection is always a good idea. I enjoy avast! for linux personally.

I know I'm going to regret this, but I have to ask you why you said that?

The only reason I can see that the use of anti-virus software is valid for a Linux machine, is if your Linux machine is serving windows machines.

I run an IPCop headless firewall/router which also has other services running, including Privoxy (which is a great privacy filter) & ClamAV.  The only reason I run ClamAV (anti-virus software) is that when it is running via IPCop it doesn't slow our internet speed at all (neither does Privoxy when run this way); so due to that, I say to hell with it, I'll use it.  

BUT I DON'T NEED ANTI-VIRUS SOFTWARE ON LINUX AT ALL.

I do need Privoxy though.

---

### Post by aysiu on 2009-09-24
Having antivirus software installed is not virus protection.

---

### Post by DianJoubert.com on 2009-09-24
> **jrusso2 said:**
> Here comes the daily AV argument thread.

I can see why you said this. I'm now more confused than before. lol :lolflag:

---

### Post by DianJoubert.com on 2009-09-24
> **aysiu said:**
> Having antivirus software installed is not virus protection.

Ok, missed this comment. Yes, this makes sense! In such a short sentence it all comes together. Humans are the biggest virus activators even if we have AV. 

AV just makes the masses feel safer when browsing or downloading - this is how the AV companies milk it. They sell a solution to people to cure their fear of viruses.

I'm running Ubuntu as my main system. If I need to use windows I run it inside abuntu with virtual box. Windows has it's own AV.

The only question I now have. Is windows isolated within the virtual box? If for any reason windows do get infected, will it affect my Ubuntu?

---

### Post by Chronon on 2009-09-24
It is confined to the virtual drive (a file on your harddrive) unless you specifically enable shared folders or USB pass-through, etc.  It might be wise to keep a backup of the Windows virtual machine.  If anything happens just replace the infected virtual drive with a copy of your backup.

---

### Post by juancarlospaco on 2009-09-25
*Hahaha...* :)
So if you run MS-DOS on VirtualBox then you need a DOS AV runing on Ubuntu?
LOL

---

### Post by WalmartSniperLX on 2009-09-25
Simply put: No

..you do not need anti-virus software of any type on Ubuntu. Technically, you don't 'need' it in Windows either. However, you're at a very tiny risk of having any sort of infection due to the way Ubuntu works when compared to windows. Just remember that the user is the ultimate form of anti-virus protection. 

Hope you enjoy Ubuntu/GNU/Linux as much as we do!

---

### Post by speedwell68 on 2009-09-25
I run AV software purely to protect anyone I know with Windows.  I do a periodic scan and if I do find anything it will be lurking in my email folders, which could potentially be passed on to a Windows PC.  Whilst a virus cannot effect a Linux PC it can pass one on to a Windows PC.

---

### Post by DianJoubert.com on 2009-09-25
> **speedwell68 said:**
> I run AV software purely to protect anyone I know with Windows.  I do a periodic scan and if I do find anything it will be lurking in my email folders, which could potentially be passed on to a Windows PC.  Whilst a virus cannot effect a Linux PC it can pass one on to a Windows PC.

I take it you don't run AV on your ubuntu then?

---

### Post by cstudent on 2009-09-28
I clean Windows machines for people. I copy their personal files over to a USB hard drive and then use my Ubuntu machine to scan that drive with Avast for Linux before I replace the files back on their newly reformatted and restored Windows machine. So there are uses for anti-virus software under Linux.

---

### Post by Exodist on 2009-09-29
> **cstudent said:**
> I clean Windows machines for people. I copy their personal files over to a USB hard drive and then use my Ubuntu machine to scan that drive with Avast for Linux before I replace the files back on their newly reformatted and restored Windows machine. So there are uses for anti-virus software under Linux.

Thats pretty smart!

---

