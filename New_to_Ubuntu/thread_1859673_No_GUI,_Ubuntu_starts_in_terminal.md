---
title: "No GUI, Ubuntu starts in terminal"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by shico90 on 2011-10-14
Hello, I'm new to Ubuntu. I installed it using Wubi. At first I had a problem installing it as it came at a point before installation and it just stopped with blank screen, But anyway I overcome it by using the setup in safe graphic mode or something (I can't remember the name).
Now when I start the Ubuntu it starts up in terminal with no GUI and asks me about the user name and password.
I started it in recovery mood and choosed dpkg tool, It updated the Ubuntu for an hour or something and after a restart no change, still starts in terminal.
My VGA is  NVIDIA GeForce 8200M G.
Please if anyone can help me, Thanks.

---

### Post by Johnb0y on 2011-10-14
can you give a litle more information please? 
i.e. which ubuntu verion you trying to use? 
have you tried - formatting the whole drive again and starting from scratch? etc.

---

### Post by shico90 on 2011-10-14
> **Johnb0y said:**
> can you give a litle more information please? 
i.e. which ubuntu verion you trying to use? 
have you tried - formatting the whole drive again and starting from scratch? etc.
Thank you so much for trying to help, I Logged in with a mode that doesn't need the VGA and I updates the driver and after a restart, It worked fine.
Thanks so much

---

### Post by haqking on 2011-10-14
> **shico90 said:**
> Hello, I'm new to Ubuntu. I installed it using Wubi. At first I had a problem installing it as it came at a point before installation and it just stopped with blank screen, But anyway I overcome it by using the setup in safe graphic mode or something (I can't remember the name).
Now when I start the Ubuntu it starts up in terminal with no GUI and asks me about the user name and password.
I started it in recovery mood and choosed dpkg tool, It updated the Ubuntu for an hour or something and after a restart no change, still starts in terminal.
My VGA is  NVIDIA GeForce 8200M G.
Please if anyone can help me, Thanks.

Did you install the desktop version or server version as server does not come with a GUI.

Once you login you can do the following depending on what version of ubunut you have.

```
startx
```

or

```
sudo /etc/init.d/gdm start
```

this is only if you have a desktop manager installed

---

### Post by haqking on 2011-10-14
> **shico90 said:**
> Thank you so much for trying to help, I Logged in with a mode that doesn't need the VGA and I updates the driver and after a restart, It worked fine.
Thanks so much

oh well cool you got it sorted.

remember to use thread tools to mark the thread as solved, cheers

---

