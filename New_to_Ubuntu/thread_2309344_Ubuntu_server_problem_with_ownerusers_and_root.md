---
title: "Ubuntu server problem with ownerusers and root"
date: 2016-01-09
forum: New to Ubuntu
---

### Post by caglar2 on 2016-01-09
Guys &#305; am really in trouble. 

I need help as soon as possible. My problem is that,

I have ubuntu server on online.net I wanted to change some owneruser. Damn it changed all . Actually i dont remember which code i used. Anyway. And i can not do anything with my normal user now. But anyything. It says, permition denied for everything. 

When i want to go su root it doesnt accept passport.  I  open it in rescuemood and change root password. root password works on rescuemood but when i back to normal system. It doesnt accept. 

Guyss I really need help. 

Thanks

---

### Post by caglar2 on 2016-01-09
I also did this....When i changed on bootmode i can be root. But when i back normal mode root doesnt work 
[https://documentation.online.net/en/serveur-dedie/rescue/change-root-password](https://documentation.online.net/en/serveur-dedie/rescue/change-root-password)

---

### Post by andy-tehinternets on 2016-01-09
Can you find the command you originally typed in your bash history?

---

### Post by caglar2 on 2016-01-09
> **andy-tehinternets said:**
> Can you find the command you originally typed in your bash history?

Unfortunetly no :( 

-bash: /home/tchmdycm/.bash_history: Permission denied


emacs ~/.bash_history

Actually i need to change rootpassword in rescue mod. But i can not. If i can connect root, i can backup all datas and do something different :( Now everything says Permission denied

---

### Post by sandyd on 2016-01-09
Can you access bash_history from rescue mode?

---

### Post by caglar2 on 2016-01-10
unfortunetly  no . I am really in trouble... If there is someone to look i can share my infos and also skype. I tried everything!

---

### Post by QIII on 2016-01-10
It will be very hard to divine a solution without knowing what you did.

Were you changing file permissions?  Were you using the chown command?

Do you remember what directories you were working in?  Did you do anything recursively?

Were you following some instructions we can look at?

---

### Post by caglar2 on 2016-01-10
Ok , wanna explaine ,

I connected with my user which is i could do everything. User name is tchmdycm. But it is not root.  

Then I wanted change one hosts permition. And i though, i can change in one time easly. And i found a code and &#305; use this code. This code changed all permitions in hosts. Now all files looks on different user which was normal user on the host. User name is cmmlkcm . 

When i wanted do something on my server like download my files , it says permition denied. There are my files but i can not touch. 

Then i wanted login as Root to change, i couldnt. And i open ticket and asked the company they told me that look this document.d
[https://documentation.online.net/en/serveur-dedie/rescue/change-root-password](https://documentation.online.net/en/serveur-dedie/rescue/change-root-password)
[COLOR=#3B393E][FONT=Open Sans]
[/FONT][/COLOR]Then i did what exactly write there. I can be root on rescue mod. But when i close rescue mod nothing changed. I also can not find my files in rescue mod. 

I am not sure which code i used but i guess it was [COLOR=#000000]chown 


[/COLOR]Btw there is KVM over ip  on my system. I also used it and nothing work  :(


@QIII , I really need help.

---

### Post by sandyd on 2016-01-10
After you've mounted all your partitions in rescue mode, post the output of
```

ls -la /mnt/sda2/home/

```

---

