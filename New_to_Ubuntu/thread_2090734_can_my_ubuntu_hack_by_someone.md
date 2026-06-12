---
title: "can my ubuntu hack by someone??"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by vibaviattigala on 2012-12-03
my friend made a bet with me to come live with skype if i tell him my ip address he said he can hack my ubuntu delete fiels he also said he can get the my username passworld for my isp i dont know anything about ubuntu

what should i do am i safe can he hack?

---

### Post by mastablasta on 2012-12-03
no system is foolproof.
 
you can use strong user password, encrypt your files, configure the firewall (which is not really necessary if you already use router). if you use router with firewall he would have to hack that one first. again strong password there would make it harder.
 
then you can watch him do it or fail trying. :-) 
 
i am not sure if i understand this correctly but he plans to do it via skype?

---

### Post by grahammechanical on 2012-12-03
This I think is a key point,

>  i tell him my ip address

I will not say that it is impossible for someone to find our ip address but if your friend was such a clever person he would not need for you to tell him your ip address.

Does he want to know your passwords as well? My advice would be not to have a bet with people like that.

If someone had physical access to my machine while I was logged in they could delete documents in the same way that I can delete documents but they cannot change/delete system files because even I need my password to do that.

I am the administrator on this machine but Ubuntu only allows me to use the machine as a standard user. When I try to do something that only the administrator is allowed to do I am asked to authenticate that I am the administrator by entering my password. In this way Ubuntu protects us.

Regards.

---

### Post by Herman on 2012-12-03
Wasn't skype bought out by Microsoft Windows some time ago?

Your friend may know of vulnerabilities in skype that the maintainers of the program haven't patched yet. 

When we install Ubuntu it is quite secure by default and then most of us enable extra repositories to allow us to install all kinds of programs. 
Each repository contains a different category or grade of software according to whether or not it is maintained by Canonical or provided by the community, whether or not the software is supported by the Ubuntu Security Team and so on.

I don't think skype is a Ubuntu program, I think there are  Gnu/Linux alternatives for it but I'm not sure if they can be used for communicating with Windows users or not. Google Talk is very good, but that's not a Ubuntu program either, but at least it's not Windows.

In the old days, we used to manually edit a file in Ubuntu called /etc/apt/sources.list and that contains notes about the status of the repositories the user might want to enable. I'm sure there are messages with the new automated GUI way of doing things to inform users but I am not sure if many users take the time to read and interpret them properly, or are aware of the implications.

If you want to take a peek at your /etc/apt/sources.list file you can do so with the following command,
```
cat /etc/apt/sources.list
```Lines that have two hashes at the start are comments,  lines with one hash mark are repositories that are not enabled and lines that do not have a hash at the start of the line are repositories that are live and enabled, and those are pointing to addresses on the internet where your computer will look for software each time you look for updates or add new programs.

It is quite possible to install programs in Ubuntu that contain vulnerabilities just like in any other operating system. 
As the above poster,  grahammechanical, mentioned, we have to type our sudo password before we are allowed to change anything important or install and remove programs in Ubuntu which does give us a good degree of protection from malicious programs which might try to install other programs without our knowledge or consent as often happens in certain other operating systems.
The other thing about typing our sudo password is, we're supposed to think twice before we do and ask ourselves, 'is this change I'm about to make to my operating system okay or not?'

:) Hey if you want to have some fun, boot a Ubuntu LiveCD and install skype in that, (it will remain in memory for the duration of your CD session, you'll have to install it again each time you reboot your CD),  and let your friend have a try and see what happens. He can't do any harm to a live CD. You could even copy a few files into it to make it look like a real operating system. Make sure no file systems from your hard disk are mounted when the live CD operating is running skype though, just to be sure.

---

### Post by Soul-Sing on 2012-12-03
having an ip adress= no hack. How many times do I see this here.
your 'friend' could stress your system, if you want this. If you don't want that, its a crime. Simple.
Linux is out-of-the-box a great rel. save oper. system.
- zero open ports policy
- trusted software sources
- sudo
Give this a try:
```
sudo ufw enable
```

---

