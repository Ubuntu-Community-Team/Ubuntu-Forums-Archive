---
title: "What is OpenSSH"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by cheatos on 2011-09-18
I just searched for an easy explanation of what OpenSSH is about and especially what it is good for or why I should use it but haven't found any useful information.

Can someone explain to a really new linux user what OpenSSH is for and how I can use it?

(I have an iPod and have jailbroken it, in the Cydia app-store I've also found a lot of stuff on that SSH thing, but I really don't get the point in what to do with SSH)

---

### Post by haqking on 2011-09-18
> **cheatos said:**
> I just searched for an easy explanation of what OpenSSH is about and especially what it is good for or why I should use it but haven't found any useful information.

Can someone explain to a really new linux user what OpenSSH is for and how I can use it?

(I have an iPod and have jailbroken it, in the Cydia app-store I've also found a lot of stuff on that SSH thing, but I really don't get the point in what to do with SSH)


SSH is a secure mechanism to allow you to connect to a remote machine (usually a server) and act as if you were physically sat at the machine using the console.

It is secure and fast, you can also use ssh-X which forwards the X requests back to your local machine so you can run graphical apps locally but from the remote server.

read here [https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

though usually used to remotely administer a server it can also be used and is often to allow you to connect to a linux desktop also, and carry out secure admin.

---

### Post by PierreRobiquet on 2011-09-18
OpenSSH is both a SSH server and client. I would imagine you're wondering about the server part the most, it basically allows you to remotely and securely access the command line of a Linux computer that you are currently not present. For example people use it to administer servers that are on the other side of the world. With your iPod it will allow you to remotely send commands to it rather than having to type them on the small virtual keyboard.

---

### Post by dniMretsaM on 2011-09-18
In short, OpenSSH is a secure way to remotely control another computer. For a longer explanation, check out the OpenSSH [Wiki page]("http://en.wikipedia.org/wiki/OpenSSH").

---

### Post by haqking on 2011-09-18
> **dniMretsaM said:**
> In short, OpenSSH is a secure way to transfer files (instead of insecure FTP). For a longer explanation, check out the OpenSSH [Wiki page]("http://en.wikipedia.org/wiki/OpenSSH").


SSH is a secure shell, SCP or SFTP is a secure way to transfer files to be exact.

SSH just allows a secure remote connection, you may never transfer anything at all, just thought i would add that as to not confuse the OP.

---

### Post by dniMretsaM on 2011-09-18
> **haqking said:**
> SSH is a secure shell, SCP or SFTP is a secure way to transfer files to be exact.

SSH just allows a secure remote connection, you may never transfer anything at all, just thought i would add that as to not confuse the OP.

You missed my edit. But can't it also be used for file transfers? I think jailbroken iDevices use it for that purpose. Or do they just use it to connect and a different protocol to do the actual transferring? Because as far as I know none of the iDevice SSH clients I ever used had a place to select a separate protocol for file transfers.

---

### Post by haqking on 2011-09-18
> **dniMretsaM said:**
> You missed my edit. But can't it also be used for file transfers? I think jailbroken iDevices use it for that purpose. Or do they just use it to connect and a different protocol to do the actual transferring?

edit ? it stills says the same ? i wasnt picking at you, i was just making it clear for the OP that SSH is not specifically for securely transferring files, it is a Secure Shell used for remote administration.  No file transfer may ever take place, if they do you will use SCP or SFTP etc to do so.

As for SSH on an iPhone i dont know as i dont use IPhones but on my Android i use SSH apps to do just as i do on my laptop which is to get a SSH shell up on my phone, whether i transfer files or not ;-)

peace

---

### Post by dniMretsaM on 2011-09-18
In my edit I added that it's used for remotely controlling computers. Anyway, I'll take that out of my first post.

---

### Post by haqking on 2011-09-18
> **dniMretsaM said:**
> In my edit I added that it's used for remotely controlling computers. Anyway, I'll take that out of my first post.


ha no worries, like i said i was just trying to clarify for the OP.

SSH is a protocol used for a secure connection, usually to remotely administer a system as if sat at the console of the system locally.

Part of this administration may be to transfer files but to do that you would use SCP or SFTP which use the SSH underlying protocol to make the action secure.

I cant remember the last time i actually transferred files when SSH to a server to administer it, it would of been to administer the machine as if sat at the console.

But yes you are right in a way, as most home users who use SSH on the machines do so for the purpose of file transfer, but using SCP or SFTP as part of that.

peace

---

### Post by cheatos on 2011-09-19
ok, first of all thanks a lot for all your responses.
It seems like I'll have to look through those wiki pages and all you've posted before getting started with SSH, right?

One more question I do have, because you have spoken about that a lot, what is a shell?
I think if I get what a shell is, I might understand what SSH is good for.

(I don't know if I could find a clear definition of a shell in the wiki, but atm I have just a little time before I have to go...)

Thank you all

---

### Post by Lisiano on 2011-09-19
Bash, SH, ZSH - All of those are shells. Basically open your Terminal (Ctrl+Alt+T) and you get a shell.
Might I also add that SSH is also a good tool to access some stuff on the nerwork of the remote server. For example you can use SSH to provide a printer to a remote server. You can use it to mask yourself as another person. For example I'm currently on mobile data, but if you looked at my IP and ISP you will see that I'm actually on the fastest and biggest ISP in my country. It let's me browse the web a bit faster (Compression) and hides me from the mobile operator. You can also do neat stuff like connect your PC to another and play games using it. Basically, SSH is one of the best things in Linux. Beside the Linux Kernel that is. IMHO.

---

### Post by cheatos on 2011-09-19
Ok, I do think I get the point about ssh and a shell right now but still I'm a bit scared of using ssh.
Are there some special things I should be careful about when starting to use Ssh? Still I'll keep on reading for a while before actually trying it out as it seems to me like a pretty powerful instrument which could easily be used to break your OS, right?

But thanks for all your help, I'll mark this as solved, as I think I can get more detailed infoation at other places of the forum.

---

### Post by Lisiano on 2011-09-19
We make it sound like so but it can't break anything. Unless you SSH into a machine and run a command that could destroy it, but that is a exception.
My advice - Don't be scared, until you start using the extra features of SSH, all you need to know is that SSH is just a remote "Gnome Terminal" of sorts. Although there is 1 thing you should be careful about, sometimes if you use SSH for a while, minimize the terminal with it and do some work on your computer, then there might be a chance that you will confuse the SSH session for a local terminal, usually it is harmless but sometimes annoying. For example you want to play some music but when you go to your ~/Music you see that it is empty, just after you get a breakdown you will notice you got SSH open.

Okay and on an ending note I'll also note, since you plan to use a OpenSSH server on your iPhone, you will probably use SSH only to copy files.

---

### Post by haqking on 2011-09-19
> **cheatos said:**
> Ok, I do think I get the point about ssh and a shell right now but still I'm a bit scared of using ssh.
Are there some special things I should be careful about when starting to use Ssh? Still I'll keep on reading for a while before actually trying it out as it seems to me like a pretty powerful instrument which could easily be used to break your OS, right?

But thanks for all your help, I'll mark this as solved, as I think I can get more detailed infoation at other places of the forum.

Well using SSH gives you access like you are sat at the console so the same rules apply which are Linux always assumes you know exaclty what you are doing.
do not login as root and use sudo for elevated priveleges, make sure you are familiar with [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") concepts.  Because if you trash your machine remotely it takes longer to fix it ;-)

---

### Post by Paddy Landau on 2011-09-20
> **haqking said:**
> ... you can also use ssh-X which forwards the X requests back to your local machine so you can run graphical apps locally but from the remote server.
Would this not require a fast Internet connection, so restricted (practically) to broadband?

I see there is also something called [xnest]("apt:xnest"), which (I understand) opens an X window on the local machine rather than the remote machine.

> **Lisiano said:**
> ... you can use SSH to provide a printer to a remote server.
Where can I learn how to do provide a printer to a remote server?

---

### Post by haqking on 2011-09-20
> **Paddy Landau said:**
> Would this not require a fast Internet connection, so restricted (practically) to broadband?



Yes indeed, X can be pretty laggy over a WAN i was mentioning it more as information on SSH in general and its capabilities not meaning for the OP to use X over his cellular connection ;-)

---

### Post by cheatos on 2011-09-20
ok, as you stoill are a very helpful community, what do you think of a special interface for usage of ssh, I've seen HotSSH in the Ubuntu Software Center and I'm thinking about trying this program out for getting connection to my iPhone as I'm not really into terminal commands.

---

### Post by haqking on 2011-09-20
> **cheatos said:**
> ok, as you stoill are a very helpful community, what do you think of a special interface for usage of ssh, I've seen HotSSH in the Ubuntu Software Center and I'm thinking about trying this program out for getting connection to my iPhone as I'm not really into terminal commands.

Not familiar with it, you want to ssh into your phone ? or you want to use your Phone to ssh into a Linux machine ? and is this to be done across a WAN or a LAN ?

---

### Post by cheatos on 2011-09-20
I would like to SSH into my phone from my Desktop computer over my home WLAN. (I think up to 54Mbit/s)

I've also read a lot about setting a root password for the iPhone before using SSH, because others might easily hack into the phone if you don't but on the forums and wiki I've read that the root password should stay disabled, so I'm a little confused baout this, too

---

### Post by haqking on 2011-09-20
> **cheatos said:**
> I would like to SSH into my phone from my Desktop computer over my home WLAN. (I think up to 54Mbit/s)

I've also read a lot about setting a root password for the iPhone before using SSH, because others might easily hack into the phone if you don't but on the forums and wiki I've read that the root password should stay disabled, so I'm a little confused baout this, too

Rooting your phone is often needed to carry out additional tasks, but is never recommended as you can trash your phone with root access ;-)

In Ubuntu the root account is locked by default and so it not recommended you unlock it as all can be achieved by using [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

From a quick google it seems HotSSH is another in a long line of general ssh client/servers.

How it will work on your phone i have no experience of it or SSH into an iphone.

I use a SSH client on my android to SSH into one of my virtual machines across a WAN but thats it, sorry.

---

### Post by Lars Noodén on 2011-09-20
Here is a [Wikibook on OpenSSH](http://en.wikibooks.org/wiki/OpenSSH) that I wrote.

---

### Post by cheatos on 2011-09-20
thanks a lot, I'll be reading your wiki during the next days, maybe I could also find some extra stuff for the phone connection, so I can ensure wether to set the root password or not.

---

