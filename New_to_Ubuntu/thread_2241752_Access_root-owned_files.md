---
title: "Access root-owned files"
date: 2014-08-28
forum: New to Ubuntu
---

### Post by nathanbotas on 2014-08-28
Hello everyone,

I've been using Ubuntu 12.04 for 1.5 years now, but I'm still very basic and have tried to keep my terminal usage to a minimum (if there are some symbols or abbreviations that you guys use amongst yourselves, but that don't actually represent what needs to be typed in the terminal, I won't understand what you mean, so examples would be appreciated). Unfortunately, I lost some files somehow, and have been using the Foremost program to extract the files from the dev/sda3 partition.

So far, so good. I've extracted the .ole files to a folder I created, but this folder is owned by root. I cannot for the life of me figure out how to change the ownership of this folder so that I can access it. I tried the gksu nautilus terminal, but I cannot access any of my folders like this as they simply don't appear in the new window that pops up after entering my password in the gksu nautilus prompt. 

I've also tried the CHOWN command, but I can't figure it out. I would appreciate any help. Again, my exact need is changing the ownership from root to myself, nathan.

Sincerely,

Nathan

PS. I assume it's against forum rules to ask two questions in one post, but since it's just a yes/no I thought I'd give it a wing. Is the best way to open .ole files simply by renaming them as .zip files (something I'll be able to do as soon as I can change ownership from root to myself!)? Thanks again

---

### Post by Impavidus on 2014-08-28
If you run gksu nautilus, the nautilus window will start in root's home directory (at /root) instead of your own home directory (at /home/username). But you can just navigate the entire directory tree as alway.

---

### Post by buzzingrobot on 2014-08-28
> **nathanbotas said:**
> 
... I've extracted the .ole files to a folder I created, but this folder is owned by root.

Is it the folder that's owned by root or the files you've copied into the folder?

If you create a folder inside your home folder -- say via a right click in Nautilus -- you own that folder and should have no trouble accessing it. How was this folder created?

File ownership can be changed, (and if they are owned by root then chown needs to be used with sudo), but there's usually a reason for root ownership.

---

### Post by grahammechanical on 2014-08-28
Some folders and files are "hidden." It is simply done by putting a dot ( . ) in front of the file name. In Nautlus we go to the View menu and select "show hidden files." Or press Ctrl+H.

Regards.

---

### Post by deadflowr on 2014-08-28
> **Impavidus said:**
> If you run gksu nautilus, the nautilus window will start in root's home directory (at /root) instead of your own home directory (at /home/username). But you can just navigate the entire directory tree as alway.

To add to this, sort of, you can also drop yourself directly into your home folder by adding the path after the nautilus command
just like when using gedit or another text editor or another program you could launch from a terminal
```
gksu nautilus /home/username
```

---

### Post by nathanbotas on 2014-08-28
In response to buzzingrobot, yes, it's the files that are owned by root, not the folder itself. I misspoke.

Now I have another problem however. I let the foremost extraction file run for 8 hours, and it filled up my recovered folder with so many documents that there is now less than a GB left on my 270GB hard drive. Now, when I start the computer I get this error message @The system is running in low/graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself. When I click on, I have the options to 1. run in low-graphics mode for just one session (but when I try this option the computer is never able to start). 2. reconfigure graphics. 3. troubleshoot the error. 4. exit to console login.

I'm imagining that the best way to solve this is to exit to console login and try to delete the folder containing the root owned files from there. Is that possible and if so, could you guys lend me a hand? I greatly appreciate the help.

---

### Post by nathanbotas on 2014-08-28
Thanks for all your help guys. People like you are what makes Linux great. I really appreciate it--and it's also very nice to see my British brothers on here helping out a not too tech-savy yank such as myself.

---

