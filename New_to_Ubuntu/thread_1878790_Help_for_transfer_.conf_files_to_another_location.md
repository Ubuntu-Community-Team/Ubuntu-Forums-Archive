---
title: "Help for transfer .conf files to another location"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by xavi fernandez on 2011-11-10
Hi all, my problem is that I have some files .conf inside the folder downloads that is located at home/downloads    what I need is transfer the files .conf inside a folder that is located in file system in the folder etc/openvpn/keys they must go inside the keys folder. When I try copy paste, doesn't allow me paste.
What can I do? Some one can write for me the command for transfer it from the terminal? because with other applications I know can be easy, but I'm new on it and I don't understand much. I'm running ubuntu 11.10

Thanks in advance!!!

---

### Post by oldos2er on 2011-11-10
Anytime you're going to be working outside your home folder, you need to use root or administrator privileges. In terminal, use 'sudo', for example ```
sudo cp /home/user/Downloads/*.conf /etc/openvn/keys
``` You'll be asked for your password which won't be echoed to the screen when you type it in.

To do the same task graphically, run ```
gksu nautilus
``` to open the file manager Nautilus with root privileges. 'gksu' or 'gksudo' is the GUI equivalent of 'sudo'.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by xavi fernandez on 2011-11-12
Hi all. I'm new in Linux and I'm running ubuntu 11.10. I try install the VPN and I need transfer some files .crt that are in the directory home inside the folder cert but I just need the files, not the folder, I need transfer the .crt files to inside the folder that is located when you open home/file system/etc/openvpn/keys.
I tried with file manager going to tools and choose the folder like a root, I copy all the .crt files, go until the keys folder and when I paste is giving me an error permiss denied.

Any idea what is going on?

Thanks in advance.

---

### Post by flurospar on 2011-11-12
Start your file manager with superuser power:

```
sudo nautilus
```replacing "nautilus" with whatever your file manager is, like "dolphin" or "pcmanfm".

If that fails, the problem may be with the folder itself. Do this:

```

sudo bash
chmod -R +w /etc/openvpn/keys
cp -r /etc/openvpn/keys ~/openvpn-keys
chmod -R -w /etc/openvpn/keys
exit

```

---

### Post by xavi fernandez on 2011-11-12
Thanks a lot flurospar, the first command was working perfect!!! Brilliant!!! now I have all the files in the folder and started new problems with permissions again that I will try figure out before posting it. I'm almost three weeks trying install the vpn, I hope I will get it before expires this version of ubuntu :P

Thanks again!!!

---

### Post by Paqman on 2011-11-12
> **flurospar said:**
> Start your file manager with superuser power:

```
sudo nautilus
```replacing "nautilus" with whatever your file manager is, like "dolphin" or "pcmanfm".


You should use:
```
gksudo nautilus
```
gksudo is prefered for all graphical apps, sudo is for use on the command line. [Why?]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by xavi fernandez on 2011-11-12
Thanks Paqman, I tried as well your way but for try connect the vpn, and still giving me the permission denied when I try import the files .conf from the folder keys to the vpn configuration, I attach a screen shot for make clear the error that is giving to me.

Thanks again!!!

---

### Post by Paqman on 2011-11-12
Check the permissions and ownership of that file. I suspect you'll want to set it so that it's readable by any user. You can change permissions by right clicking on the file and going to the permissions tab.

---

### Post by xavi fernandez on 2011-11-12
Thanks Paqman, I just check the permissions and I think they are ok, they said xavi-Owner, in case I need change it, what should I write there?

---

### Post by Paqman on 2011-11-12
> **xavi fernandez said:**
> Thanks Paqman, I just check the permissions and I think they are ok, they said xavi-Owner, in case I need change it, what should I write there?

That's probably not right for that file. Everything outside your /home folder is normally owned by root, which is why you couldn't move the file into /etc without temporarily becoming root yourself. I don't know anything about setting up VPN, but I suspect that fiel should be owned by root. 

You really need someone better gripped up on this than me to make sure you get your setup right. If you get no luck here take the question to the [networking forum]("http://ubuntuforums.org/forumdisplay.php?f=336"), [askubuntu.com]("http://askubuntu.com/"), or IRC.

---

### Post by oldos2er on 2011-11-12
> **xavi fernandez said:**
> Any idea what is going on?

The same answer I gave you two days ago here: [http://ubuntuforums.org/showthread.php?t=1878790](http://ubuntuforums.org/showthread.php?t=1878790)

---

### Post by howefield on 2011-11-12
Threads merged.

---

### Post by xavi fernandez on 2011-11-13
Thanks for your reply oldos2er, I tried like u said with the command that you told me some time ago, but still, I run in terminal gksu nautilus and after that I went to the vpn connections, on top, next to the clock, configure vpn, vpn, import, and from there I go to file system, etc, open vpn, and then I select the .conf file and is giving me the same error. 
Do u think should I delete everything and start again? 
I attach a screen shot from the error.
Thanks in advance.

---

### Post by oldos2er on 2011-11-13
No, I don't think you should delete and reinstall; what if you run into the same problem again?

I agree with Paqman's suggestion to try the networking forum; include a link back to this thread so people can see what's already been tried.

---

### Post by xavi fernandez on 2011-11-14
Thanks, I posted the thread in the section Networking &Wireless and not answer at all, actually is the second one asking for help for install the vpn and no answer in no one, do you think is the wrong place for ask for it???

---

### Post by oldos2er on 2011-11-14
Patience is a virtue.  :)
Give it some time, and try not to bump posts more than once in 24hrs. Or, try IRC: [http://www.ubuntu.com/support/community/chat](http://www.ubuntu.com/support/community/chat)

---

### Post by xavi fernandez on 2011-11-14
Thanks Oldo, I know I can be annoying sometimes, but I need the connexion with the vpn for internet, because 90% my use I need  VPN, so, I must stay with windows instead use ubuntu, so, I can not learn and practice because I can not be with ubuntu :(

Thanks for your advice and I'm going try the IRC as well. 
But for sure, I will not give up!!!!

---

### Post by oldos2er on 2011-11-14
All right, good luck to you.

---

