---
title: "Ubuntu 12.04 LTS Server SAMBA problems"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by haakondaniel on 2012-05-12
Hi! 

I'm new to Ubuntu and I don't have much exprience with linux.
I've just installed Ubuntu 12.04 LTS Server on my dedicated server computer, everything works pretty good except for Samba. I've downloaded the program and installed it, that part works, but when I try to launch the program it doesn't happen anything after I've entered my password. Can anyone help me with this? Or is there some other way to share files on my ubuntu server with my other windows computers connected to the network? 

I hope someone out there can help me with this one :)

---

### Post by Morbius1 on 2012-05-12
> I've downloaded the program and installed it, that part works, but when I  try to launch the program it doesn't happen anything after I've entered  my password.
You've downloaded what program?

Are you talking about the "samba" package itself? It's not something that's launched.

---

### Post by haakondaniel on 2012-05-12
Okay like I said, I'm new to Ubuntu :P 
I followed a guide, downloaded Samba from ubuntu software center and installed it. 
When I try to start Samba, I get the screen where you enter the password and then nothing happens after I've entered my password.

---

### Post by Morbius1 on 2012-05-12
Could you please post a link to the guide because this statement is confusing:
> When I try to start Samba, I get the screen where you enter the password  and then nothing happens after I've entered my password.     "samba" is a service not a program. To start the service one does this:
```
sudo service smbd start
```The only 2 possible responses are ( and I'm paraphrasing here ):
** smbd starting
** smbd has already started
[COLOR=Blue]EDIT[/COLOR]: Well, I guess there's a 3rd response:
** service smbd not found

---

