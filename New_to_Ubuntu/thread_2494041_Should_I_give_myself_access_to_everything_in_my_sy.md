---
title: "Should I give myself access to everything in my system?"
date: 2024-01-03
forum: New to Ubuntu
---

### Post by tommy-luciano on 2024-01-03
Hello there, I have a question relating to permissions and/or user account privileges.

I was downloading some software from the App Center, which would bring up the authorization popup window each time I tried to download something. I became tired of it and it made me wonder if there was a way of preventing this, so I did a little research and found out that it is possible to stop that authorization popup window from happening each time I tried to download something, but unfortunately the information I found did not explain sufficiently in terms of risk factor other than briefly mentioning the possibility of giving anyone access to all my files which would allow them to execute commands and install malware. 

If I were to give myself (meaning my user account) access to all files on my system and could disable the authorization popup window, am I taking any big risks that I should avoid? I'm not really sure that I want to go through with it, so if anybody would be able to shed some light on this I would be highly appreciative.

Thanks in advance

~ Tommy. L.

---

### Post by SeijiSensei on 2024-01-03
Yes. You can break your system with a single erroneous command. Ordinary users are locked out of most system directories by design. You should only be able to write to your home directory and /tmp.

A quick solution to the problem you describe is to use the command line. To update all the software on your system, open a terminal and type
```

sudo apt update
sudo apt upgrade

```

That's it. To install a package use "sudo apt install package_name".

---

### Post by ajgreeny on 2024-01-03
And if you should try to change the permissions of many of the files in the system other than those in your /home folder or partition you will quickly find that the whole system will not even boot up or start.

Just don't do it!  Learn to live with the system as it is or you will find your Linux time difficult, and possibly disastrous to the OS.

---

### Post by UltimateCat on 2024-01-03
> **ajgreeny said:**
> And if you should try to change the permissions of many of the files in the system other than those in your /home folder or partition you will quickly find that the whole system will not even boot up or start.

Just don't do it!  Learn to live with the system as it is or you will find your Linux time difficult, and possibly disastrous to the OS.

Agreed:-

---

### Post by ActionParsnip on 2024-01-04
The Linux file system (Like any OS) has sensitive settings and owners. Giving yourself the files won't stop the popup. You'll find that once the OS is setup then the only time that sot of thing shows is during updates.

---

### Post by tommy-luciano on 2024-01-04
Thanks to all of you for taking the time to reply to my post. I can see now that it would probably be a bad idea, some things are better just left as they are. I guess I will just have to learn to live with it, I suppose it's not that annoying really, I was just being impatient.

Appreciate the answers!

Thank you all :D

---

### Post by SeijiSensei on 2024-01-04
Many things are easier to do from the command line than from the GUI. It's worth taking some time to learn basic commands.

---

