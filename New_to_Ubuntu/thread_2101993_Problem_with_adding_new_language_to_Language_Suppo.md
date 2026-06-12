---
title: "Problem with adding new language to Language Support"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by kwyang on 2013-01-06
I'm trying to add a new language to my PC. When I click the Install/Remove language button, I select the language I wanted to add, then I'm prompted to software center that ask for my password for downloading the package. when I type in my password, It's suppose to download the file after this steps. But instead of downloading, another screen pops out asking me to insert my Ubuntu CD/DVD to install package. 

I have tried this method before on my previous attempt and it works without any problem. I'm using Ubuntu 12.4. I hope someone out there can help me with my problem. Thanks in advance :P


[IMG][[img]http://s2.postimage.org/ih2jhesxx/error.jpg[/img]](http://postimage.org/image/ih2jhesxx/)[/IMG]

---

### Post by TOMBSTONEV2 on 2013-01-06
I am thinking perhaps it needs some guidance from the cd for proper text format. You have tried inserting the ubuntu disc no?

---

### Post by iMac71 on 2013-01-06
since the image you posted shows that the CD contains Ubuntu 12.10 "Quantal Quetzal", while you write in your post that you're using Ubuntu 12.04 "Precise Pangolin", the problem might derive from trying to install a newer language pack in an older system.

---

### Post by NikTh on 2013-01-06
Hi , 
probably you have the cdrom enabled in Ubuntu's repositories.. take a look. 

Open Update Manager and click "Settings" , then goto "Ubuntu Software" tab  and see if CdRom is marked. It shouldn't be. 

or you can give here some more info by applying the command below to a terminal (CTLR+ALT+T)  and post back the results
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
``` [U]
Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read.[/U] [See here how]("http://i.stack.imgur.com/zADbK.png")
 


Thanks

---

### Post by kwyang on 2013-01-06
> **TOMBSTONEV2 said:**
> I am thinking perhaps it needs some guidance from the cd for proper text format. You have tried inserting the ubuntu disc no?

I haven't try insert a cd since I use a usb stick to install.

---

### Post by kwyang on 2013-01-06
Thanks a lot Nikth and everyone else above that tried to help me. It's just as you said my cd rom is marked. once I unmarked it I'm able to download the language pack.

---

