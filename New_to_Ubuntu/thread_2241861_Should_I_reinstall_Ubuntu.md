---
title: "Should I reinstall Ubuntu?"
date: 2014-08-28
forum: New to Ubuntu
---

### Post by david278 on 2014-08-28
Hello,

I just bought dedicated server and... I installed Ubuntu desktop edition. I don't use GUI at all so I don't know why I did this... I understand that GUI takes more resources. Should I reinstall that Ubuntu to server edition?

I ask because I've already moved 500gb data to that server and it'll be annoying to do it again. I use that dedicated server for personal seedbox and few python apps. What should I do then? Is it worth to do it all again? It is one day work for me but if it will help me in longer period I can do it. I have to note that I'm very, very beginner administrator and I do everything now by following tutorials.

Thanks for answering my question.

---

### Post by mooreted on 2014-08-28
It depends: Is it working for you? Doing what you need it to do? On a powerful, modern machine the overhead is actually pretty small. On the other hand; a server doesn't need a GUI and the server addition has a lot of administrative features not included in the desktop version. If your goal is to learn Linux server administration then you should be using the server addition. If it's just a file server, it doesn't really matter.

---

### Post by grahammechanical on 2014-08-28
Have you put your data files on a separate partition? Perhaps on a another hard disk?

---

### Post by david278 on 2014-08-28
File server and there'll be one python app which will be runned 24/7 + transmission for torrents which now takes 50% of CPU.
I won't learn my administration skills on this server.

Maybe can I delete this GUI? If not... how can I connect to that gui?

@up. I think yes, because in folder /home I have 2TB (I read it is sda3) free space and there I have my data but in folder var etc I have only 10gb free space so I think these partions are diffrent. I'm pretty new to Linux so I can be wrong.

---

### Post by mastablasta on 2014-08-29
yes, GUI is taking unnecessary resources.

> **david278 said:**
> 
Maybe can I delete this GUI? 

remove Ubuntu-desktop meta package?

> 
If not... how can I connect to that gui?

yes, via SSH

> 
@up. I think yes, because in folder /home I have 2TB (I read it is sda3) free space and there I have my data but in folder var etc I have only 10gb free space so I think these partions are diffrent. I'm pretty new to Linux so I can be wrong.
unless /home is on a separate partition (in which case you can just reformat and reinstall on /) then this is a very bad idea. you should have a separate data partition on server.

if you are not well versed with command line but you would like to administrate the server there are numerous option to administer via web GUI (you connect to server via browser). 
Have a look at Zentyal (community edition is free), Webmin, Ajenti...or for file server you may look at own cloud, open media vault...

even if you have a webui you can still administer via command line.

---

### Post by mörgæs on 2014-08-29
Yes, I would reinstall.

If a large number of applications (as in a complete GUI) are not used they should not be there. You will have a more secure environment if you keep only the necessary stuff. 

It's not a matter of disk space nor performance, just good practice. Keeping the system minimal lowers the risk of security breaches.

---

### Post by MartyBuntu on 2014-08-29
Leave well enough alone.

If your machine has room for the small overhead of the added GUI desktop and it doesn't impact performance, I wouldn't trouble myself.
On the next install, yeah...go server edition.

---

