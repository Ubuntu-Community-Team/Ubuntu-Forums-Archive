---
title: "'FILESYSTEM' Help.."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by nommo777 on 2008-08-05
hello everyone..I have successfully installed ubuntu for the first time and now ia m exploring the town. One main source of confusion for me is the directory structure. You see, the filesystem 'drive' contains many sub folders. Now i have installed the LAMP package successfully, only to find that the root 'www' folder ends up in var, while the config files end up in some other folder.This is a big change from Windows where everything used to be dumped in a specific folder in 'Program Files'.Please help me out by providing info about the filesystem directory, or by pointing out a resource..Thanks in advance.

---

### Post by Paqman on 2008-08-05
[This is a nice graph of the filesystem](http://img81.imageshack.us/img81/3769/linuxfilestructure6xk.jpg)

---

### Post by fuzzyk.k on 2008-08-05
the linux file system organization is quite diffrent try this 
[http://brajeshwar.com/2008/filesystem-file-organization-in-linux/](http://brajeshwar.com/2008/filesystem-file-organization-in-linux/)

---

### Post by bpowell2005 on 2008-08-05
> **nommo777 said:**
> hello everyone..I have successfully installed ubuntu for the first time and now ia m exploring the town. One main source of confusion for me is the directory structure. You see, the filesystem 'drive' contains many sub folders. Now i have installed the LAMP package successfully, only to find that the root 'www' folder ends up in var, while the config files end up in some other folder.This is a big change from Windows where everything used to be dumped in a specific folder in 'Program Files'.Please help me out by providing info about the filesystem directory, or by pointing out a resource..Thanks in advance.

Here is a chart that explains (high level) what is generally put in each directory; YMMV of course.

[http://www.linuxconfig.org/images/7/79/Dirtree.jpg](http://www.linuxconfig.org/images/7/79/Dirtree.jpg)

I'm still getting used to it, but getting better at finding what I'm looking for. If I learned how to do it on Windows, I can learn how to do it in Linux.

---

### Post by nommo777 on 2008-08-05
> **Paqman said:**
> [This is a nice graph of the filesystem](http://img81.imageshack.us/img81/3769/linuxfilestructure6xk.jpg)
Thanks a lot paqman, so is there any way i can bring the 'www' folder to my desktop, something like a shortcut?

---

### Post by nommo777 on 2008-08-05
> **fuzzyk.k said:**
> the linux file system organization is quite diffrent try this 
[http://brajeshwar.com/2008/filesystem-file-organization-in-linux/](http://brajeshwar.com/2008/filesystem-file-organization-in-linux/)
thanks fuzzy k!!

---

### Post by nommo777 on 2008-08-05
> **bpowell2005 said:**
> Here is a chart that explains (high level) what is generally put in each directory; YMMV of course.

[http://www.linuxconfig.org/images/7/79/Dirtree.jpg](http://www.linuxconfig.org/images/7/79/Dirtree.jpg)

I'm still getting used to it, but getting better at finding what I'm looking for. If I learned how to do it on Windows, I can learn how to do it in Linux.
so true..

---

### Post by eightmillion on 2008-08-05
> Thanks a lot paqman, so is there any way i can bring the 'www' folder to my desktop, something like a shortcut?

nommo7, you can create a symbolic link to it on your desktop.
> ln -s /var/www ~/Desktop/

---

### Post by bpowell2005 on 2008-08-05
> **nommo777 said:**
> Thanks a lot paqman, so is there any way i can bring the 'www' folder to my desktop, something like a shortcut?

You can find the "www" folder by browsing using Nautilus (by going to Places, Home, and then moving around until you find www (by clicking "up" probably)...when you see 'www' right click it and say "create link" you'll see a new item appear which is a link to 'www' just drag that onto you desktop, and it's a shortcut to 'www'.

---

### Post by nommo777 on 2008-08-05
> **bpowell2005 said:**
> You can find the "www" folder by browsing using Nautilus (by going to Places, Home, and then moving around until you find www (by clicking "up" probably)...when you see 'www' right click it and say "create link" you'll see a new item appear which is a link to 'www' just drag that onto you desktop, and it's a shortcut to 'www'.
well , idid that but the link is not showing up on the desktop, however, i can see it in nautilus..

---

### Post by nommo777 on 2008-08-05
> **eightmillion said:**
> nommo7, you can create a symbolic link to it on your desktop.
thanks 8million, that worked..

---

### Post by Bucky Ball on 2008-08-05
> If I learned how to do it on Windows, I can learn how to do it in Linux.

... and you will also realise it is more logical and easier to follow eventually, once you 'unlearn' a few things. :)

You might find this general Ubuntu page interesting;

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

... and here are some commands to print and reference as you go;

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

You will eventually want to 'untar' a file;

[http://www.pendrivelinux.com/2007/10/12/how-to-open-a-tar-file-in-unix-or-linux/](http://www.pendrivelinux.com/2007/10/12/how-to-open-a-tar-file-in-unix-or-linux/)

Not all things need to be installed this way, but get used to the terminal is a good idea; you will get more out of your computing experience ... :)

Good luck and have fun ...

---

### Post by nommo777 on 2008-08-05
> **Bucky Ball said:**
> ... and you will also realise it is more logical and easier to follow eventually, once you 'unlearn' a few things. :)
thats right, wish i had learned it before..anyway, it's never too late to learn (or unlearn in this case)..

---

### Post by hyper_ch on 2008-08-05
if you've worked with it for a while it's not a complicated at it seems and it will become much more logical than windows ;)

---

