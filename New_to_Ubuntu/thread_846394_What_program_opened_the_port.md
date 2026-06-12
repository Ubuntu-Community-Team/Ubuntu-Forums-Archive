---
title: "What program opened the port"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by MidnightJulia on 2008-07-01
Hi! 

I just run nmap against my own computer only to find that a port was open. Since there wasn't any open port the day before I would like to know what program is listening to that port. How do I find this program? :)

/MJ

---

### Post by Inxsible on 2008-07-01
What was the port number? If it is a standard port for eg. 22 - it will be ssh, 80 -http

you can then guess what app it was...

you could also install a GUI frontend for iptables like Firestarter or GuardDog and scan that port number to see what app is requesting access to it.

---

### Post by brian_p on 2008-07-01
> **MidnightJulia said:**
> Hi! 

I just run nmap against my own computer only to find that a port was open. Since there wasn't any open port the day before I would like to know what program is listening to that port. How do I find this program? :)

Giving the command you ran and its output would eliminate the guesswork.

---

### Post by sdennie on 2008-07-01
Try:

```

sudo netstat -apn

```

The information you are looking for is likely towards the top of that output.

---

### Post by MidnightJulia on 2008-07-01
> **brian_p said:**
> Giving the command you ran and its output would eliminate the guesswork.

I just ran: "nmap 127.0.0.1"

Interesting ports on localhost (127.0.0.1):
Not shown: 1712 closed ports
PORT    STATE SERVICE
25/tcp  open  smtp
631/tcp open  ipp

I was woundering why port 25 was opened and by who. Is the 631 port supposed to be open because it has been for as long as I can remember :/

---

### Post by brian_p on 2008-07-01
> **MidnightJulia said:**
> I just ran: "nmap 127.0.0.1"

And what did you get, please.

---

### Post by MidnightJulia on 2008-07-01
> **brian_p said:**
> And what did you get, please.

Edited post above. Sorry about that :)

---

### Post by brian_p on 2008-07-01
> **MidnightJulia said:**
> I just ran: "nmap 127.0.0.1"

Interesting ports on localhost (127.0.0.1):
Not shown: 1712 closed ports
PORT    STATE SERVICE
25/tcp  open  smtp
631/tcp open  ipp

I was woundering why port 25 was opened and by who. Is the 631 port supposed to be open because it has been for as long as I can remember :/

631 is fine; it's for printing (cups) and comes with the default install of Ubuntu.

25 is also ok. You must have installed an MTA (Mail Transport Agent) or it came as a dependency of something else you installed. It could be exim4 or postfix,

```
sudo lsof -i :25
```

will tell you. Suppose it is postfix. Do

```
apt-get remove postfix
```

If something depends on it it will show up and might jog your memeory. If it is the only thing to be removed you can go ahead or leave it. Leaving it on the system is safe as it will only deliver mail to the local machine.

---

### Post by Inxsible on 2008-07-01
smtp is a mail protocol. Do you use an email client. That could explain it opening the port for Evolution or Thunderbird or a similar software to use that port

---

### Post by brian_p on 2008-07-01
> **Inxsible said:**
> smtp is a mail protocol. Do you use an email client. That could explain it opening the port for Evolution or Thunderbird or a similar software to use that port

An MTA can receive mail, which is why it needs a clearly defined port to listen on. Evolution and thunderbird send mail and do not listen on a port. Also, neither depend on an MTA.

---

### Post by PinkFloyd102489 on 2008-07-01
You probably installed sendmail, postfix, or something like that.

---

### Post by MidnightJulia on 2008-07-02
First of all. Thanks for all the help. I've learnt alot from the answers in this thread. I have copied parts to a document for later reference.

When I did the lsof I got this:

```
user@oden:~$ sudo lsof -i :25
[sudo] password for user: 
COMMAND  PID        USER   FD   TYPE DEVICE SIZE NODE NAME
exim4   5274 Debian-exim    3u  IPv4  13057       TCP localhost:smtp (LISTEN)
```

So I tried to remove the exim4

```
user@oden:~$ sudo apt-get remove exim4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package exim4 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But it seems like it doesn't exist. Nmap still reports the port as open.

---

### Post by MidnightJulia on 2008-07-02
> **PinkFloyd102489 said:**
> You probably installed sendmail, postfix, or something like that.

I haven't got ether sendmail or postfix. Just checked it out ;)

---

### Post by Vivaldi Gloria on 2008-07-02
> **MidnightJulia said:**
> I haven't got ether sendmail or postfix. Just checked it out ;)

You obviously have exim4. If you didn't install it yourself them maybe it came as a dependency of rkhunter or another program.

Edit: Nevermind. I didn' see post 12.

---

### Post by brian_p on 2008-07-02
> **MidnightJulia said:**
> 
```
user@oden:~$ sudo apt-get remove exim4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package exim4 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But it seems like it doesn't exist. Nmap still reports the port as open.

exim4 is a metapackage (apt-cache show exim4). Installing it is a way of getting all the necessary packages to have exim4 up and running. You either didn't use it or removed it some time in the past. Once it has done its job it may be removed.

```
sudo apt-get -s remove --purge exim4-base

```

is more likely to succeed.

---

### Post by mcduck on 2008-07-02
You probably shouldn't even run nmap from the same machine. There will always be ports that are open to localhost but not to outside machines..

---

### Post by MidnightJulia on 2008-07-02
> **mcduck said:**
> You probably shouldn't even run nmap from the same machine. There will always be ports that are open to localhost but not to outside machines..

Really? Is there any way to get around this? I didn't know this.

I'll try to nmap my computer asap from another one in the network :)

Oftopic: > Running "rm -rf" permanently deletes files. Make sure you know what you are doing before running it!

If I'm not mistaken - it doesn't permanently delete files? Otherwise - why would anyone neeed a program like "wipe"?

---

### Post by MidnightJulia on 2008-07-02
> **brian_p said:**
> exim4 is a metapackage (apt-cache show exim4). Installing it is a way of getting all the necessary packages to have exim4 up and running. You either didn't use it or removed it some time in the past. Once it has done its job it may be removed.

```
sudo apt-get -s remove --purge exim4-base

```

is more likely to succeed.

Thank you Brian! I've solved the *problem* now! Without your help this would have taken me much longer time to solve. (That -s variable btw was a gem.) The smtp port is now closed. 

It's cool how much you can learn in just a few day on this forum and the irc. For the first time in like 7 years computers seem really fun again.

---

### Post by mcduck on 2008-07-03
> **MidnightJulia said:**
> Really? Is there any way to get around this? I didn't know this.

I'll try to nmap my computer asap from another one in the network :)

Oftopic: 

If I'm not mistaken - it doesn't permanently delete files? Otherwise - why would anyone neeed a program like "wipe"?

Yeag, the answer is to run nmap from a remote machine. That will be more like the real situation, checking for ports visible from outside machines.

(For example, I run Apache on my laptop for development purposes. It's configured to only serve localhost. So, if I run nmap from that laptop it will report port 80 as open, but if I run it from any other machine in my network the same port will be closed.)

Offtopic:
Yes, it removes them as permanently as possible in normal use. Meaning that recovering them can be extremely hard to do. :D

Using some disk shredding tool is needed when extremely hard is not hard enough and you want something closer to "impossible".

---

### Post by MidnightJulia on 2008-07-03
> **mcduck said:**
> Yeag, the answer is to run nmap from a remote machine. That will be more like the real situation, checking for ports visible from outside machines.

(For example, I run Apache on my laptop for development purposes. It's configured to only serve localhost. So, if I run nmap from that laptop it will report port 80 as open, but if I run it from any other machine in my network the same port will be closed.)

I never thought about that, but when you say it, it seems logical. So now I've got a reason to setup ssh-server on another computer in the network :) 

> **mcduck said:**
> Offtopic:
Yes, it removes them as permanently as possible in normal use. Meaning that recovering them can be extremely hard to do. :D

Using some disk shredding tool is needed when extremely hard is not hard enough and you want something closer to "impossible".

Still extremely hard and permanently aren't the same thing ;)  

In what way does it differ from just using the ubuntu trashcan? Does it perform any type of overwriting of the data? If I'd hock my hd to another computer and used some type of data recovery software that still would work wouldn't it?

---

### Post by mcduck on 2008-07-03
> **MidnightJulia said:**
> I never thought about that, but when you say it, it seems logical. So now I've got a reason to setup ssh-server on another computer in the network :) 



Still extremely hard and permanently aren't the same thing ;)  

In what way does it differ from just using the ubuntu trashcan? Does it perform any type of overwriting of the data? If I'd hock my hd to another computer and used some type of data recovery software that still would work wouldn't it?
THe first difference would be that there is that the files don't go to any trashcanb.

While normal delete doesn't actually delete anyhting on the file system level, it only moves the fiels to trash can. The files are deleted from the file system only when you empty the trash.

Rm deletes the files immediately. It doesn't do any overwriting, it's just a "remove file"-tool, not "remove-file-and overwrite-with-random-data-100-times". That kind of tools are not usually needed on daily use.

So, if you find a recovery tool that supports Linux file systems, you may still be able to recover files deleted with rm. But it's nowhere close to being as easy as it is with FAT partitions.

From normal desktop user's point-of-view, the files deleted with rm are gone forever.

(The reason I have that warning as sig is that some time ago there was some annoying person trolling this forum, responding to new user's questions by always suggesting them to run "sudo rm -rf" which recursively removes all files, without asking for any confirmations. Quite many beginners ended loosing their files or having to re-install Ubuntu.)

---

