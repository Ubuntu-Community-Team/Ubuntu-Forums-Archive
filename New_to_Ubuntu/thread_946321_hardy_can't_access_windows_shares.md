---
title: "hardy can't access windows shares"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by gantengx on 2008-10-13
I'm running ubuntu hardy heron using VirtualBox on windows vista host. As like other users, I have problems accessing windows shares.

I installed samba, and whenever I tried to explore my windows share using nautlius, I can only see my computer and then no windows shares at all.

Next, I tried to type smb://computername/mysharedfolder and _sometimes works_. Other times, it asks me for permission (which is weird because I don't set password protected sharing in vista). After a while I figured out what's wrong.

I went to Computer Management on vista and check on my shares, and for some reason ubuntu tries to connect to my shared folder, like 10 connections simultaneously (vista default share policy is to allow maximum 10 simultaneous connections). No wonder I could not even access my own shared folder using my vista. It asks me for password. I had to disconnect all the connections from ubuntu first, then I can get into my shared folder in vista (still can't browse the list of shared folder though, i have to write down the addres of the shared folder).

Can anyone confirm this bug?

---

### Post by techieguy_100 on 2008-10-13
My problem is similar.  I have followed all the steps of gangtengx, but have not had any success at all.  When checking the shares on my vista machine, one attempt at connecting from Ubuntu creates 3 IPC$ connections, no errors I simply see no shares.  Connecting to my XP machine I see in my security log an invalid password message.  My password is valid, I can access shares on my Ubuntu machine from xp but not Vista.  I also reach a dead end when trying to install my windows(Vista) shared printer on Ubuntu.

---

### Post by techieguy_100 on 2008-10-15
Has this problem truly stumped all the gurus?  I see posts up the wazoo on this problem, but the only ones replying are the rookies & newbies.

---

### Post by gantengx on 2008-10-15
i think it is.. it is a known bug for nautilus to access windows share in hardy heron, i'm posting this just to make sure people know why nautilus sometime can access the windows share but not all the time.

---

### Post by Sponzenbroekske on 2008-10-15
> **gantengx said:**
> i think it is.. it is a known bug for nautilus to access windows share in hardy heron, i'm posting this just to make sure people know why nautilus sometime can access the windows share but not all the time.

maybe you should try Krusader instead of nautilus
```
sudo apt-get install krusader
```

---

### Post by gantengx on 2008-10-15
> **Sponzenbroekske said:**
> maybe you should try Krusader instead of nautilus
```
sudo apt-get install krusader
```
that is one way to workaround this problem, but i think it is the best for the nautilus/gnome team to actually solve this bug. hopefully interprid won't have this problem

---

### Post by Nxion on 2008-10-15
I did some looking around and it seems that there are alot of people having issues similar to yours. Like this for [example.]("http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg213745.html") 

Another way to connect, which I use rather then the gui is from the terminal. I found this guide that might be useful:
[URL="http://ubuntuforums.org/showthread.php?t=288534"]
http://ubuntuforums.org/showthread.php?t=288534[/URL]

Hope that helps :)

---

### Post by halitech on 2008-10-15
try it with using ```
smb://IPaddress/usershare
```

seeems the bug is mainly when accessing it by share name but seems to work 99% of the time with the IP address. Once you have the share, you can always bookmark it so you don't have to try and connect everytime.

---

### Post by Ocxic on 2008-10-15
you'll have to setup virtualbox network in a spicific way in ourder to get that to work, it has to deal with the way networking is setup for the virtual machine, check the virtualbox manual for details.

---

### Post by gantengx on 2008-10-15
> **halitech said:**
> try it with using ```
smb://IPaddress/usershare
```

seeems the bug is mainly when accessing it by share name but seems to work 99% of the time with the IP address. Once you have the share, you can always bookmark it so you don't have to try and connect everytime.
Yes, i did that as well. The problem lies in the implementation of samba by nautilus. Because when I actually managed to connect to my computer, then I went to check on the Computer Management on windows and I noticed that ubuntu tries to connect as many connections as possible simultaneously (where 10 is the default limit).

---

### Post by gantengx on 2008-10-15
> **Ocxic said:**
> you'll have to setup virtualbox network in a spicific way in ourder to get that to work, it has to deal with the way networking is setup for the virtual machine, check the virtualbox manual for details.
The network in virtualbox is not a problem, it works fine.

---

### Post by Nxion on 2008-10-16
Here is another guide I though you would like:
[URL="http://ubuntuforums.org/showthread.php?t=202605"]
http://ubuntuforums.org/showthread.php?t=202605[/URL]

---

### Post by techieguy_100 on 2008-10-23
OK, my attempt from the terminal nets the results below, it's better than the gui, but still no joy :(

user@ubuntu:~$ smbclient -L shttle1
Password: 
Domain=[SHTTLE1] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       Remote IPC
	download        Disk      
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
Domain=[SHTTLE1] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
user@ubuntu:~$ smb://192.168.0.102/download
bash: smb://192.168.0.102/download: No such file or directory
user@ubuntu:~$ 

end result?  I can see my shares but I still can't access them.  Any help would be deeply appreciated.

Glen

---

### Post by Kellemora on 2008-10-23
Hi Techie

Maybe that's because one has to view the problem as a Noob to figure it out!

When the engine runs rough and continually dies, a noob puts more gas in the tank, the tech tears the engine apart.

I have 7 computers here, had a whale of a time trying to get the network working properly.  Tried every single thing the guru's said to try, but nothing worked.

Knowing my smb.conf file was perfect I did the least obvious thing to try.

I just uninstalled and reinstalled Samba until the Network did work properly.  
On some computers, it worked the first try, on others, well as they say, three times a charm.

When the smb.conf file from a machine that works perfectly reads identical to one that don't work at all, you're looking in the Wrong Place for a fix.

Everybody laughed, but those who tried uninstalling and reinstalling Samba, well, for us, our networks are up and running perfectly.
Those who didn't, well, they are still working on the problem, hi hi.....

One other thing interesting is that in Ubuntu, we can see the shares on other drives, such as CentOS, Debian, etc. no problem.  Never got it to do that from those other Distro's though.

TTUL
Gary

---

### Post by ArtInvent on 2008-11-02
This is an incredibly longstanding and annoying bug. It's not a problem with samba or networking - it's got to be a nautilus bug. Fire up dolphin or some other KDE file browser and the shares appear just fine. I've been looking for a solution for this for some time and the only solution seems to be to dump nautilus because the guys at Gnome and/or Ubuntu can't seem to be bothered to fix this.

---

### Post by pablo180 on 2009-01-18
> **ArtInvent said:**
> This is an incredibly longstanding and annoying bug. It's not a problem with samba or networking - it's got to be a nautilus bug. Fire up dolphin or some other KDE file browser and the shares appear just fine. I've been looking for a solution for this for some time and the only solution seems to be to dump nautilus because the guys at Gnome and/or Ubuntu can't seem to be bothered to fix this.

I agree. Far from being the super reliable, dependable operating system that I have been telling my friends, and anyone else who'd listen, that it was, since Hardy I have to stand there looking sheepish with a grey screen, as it crashes. Then ask them if they wouldn't mind moving the files onto my laptop for me, on their XP machine, as I can't. 

Ubuntu seems to be getting more and more like Windows used to be, they seem more intent on rushing out new versions, rather than fixing the problems with the old ones. The advice these days always seems to be 'Updrade as the new version doesn't have these problems', except invariably it has a whole host of others.

I don't think this bug will be fixed, at least in Hardy, which is a shame.

---

