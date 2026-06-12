---
title: "Permissions"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by chisao101` on 2011-11-17
I have just installed Ubuntu 11 x64 2 days ago in Virtual Box with a host of Windows 7 Ult x64.

I wanted to use it as a web development machine (still learning php/mysql but have some experience) and learn the basics of Ubuntu at the same time. I figured if I had a project to do, it would force me to run into some things in the OS that I would have to learn. After reading many forum posts and learning how to get phpmyadmin, apache2 and mysql installed, I ran into a problem. I cannot save files in the /var/www folder. I did some google searching and came up with a lot of people saying to do this or do that, but then I saw other people saying that it was dangerous to mess around with permissions. I know Linux OS's are different than Windows as far as permissions go. I know that the root user has the ability to do many things that might damage the OS. So I want to know once and for all that I am going to do this the right way. There is no sense learning it the wrong way and then having to fix it later.

So, my question is, how do I make my user account have the ability to work in the www folder without risking any damage, or opening up unwanted security risks?

Remember, I am very skilled in Windows, but a complete noob in any Linux distributions. Ubuntu is my first, and I've only been in it for 2 days.

Thanks in advance for any help...;)

---

### Post by dniMretsaM on 2011-11-17
You need to make yourself the owner of the folder. The easiest way to do this is to run the following command in terminal:
```
sudo chown -R yourname:yourname /var/www/
```

NOTE: If you made this folder, this will be fine (which I'm guessing you did. I don't have this folder on my computer). If this is a system directory, it could pose a security risk to change the owner from root.

---

### Post by JKyleOKC on 2011-11-17
The /var/www directory is created when you install Apache, and it **is** a system folder in the sense that it contains files that can modify your web server. Consequently there's a possibility of creating a security vulnerability by changing its ownership -- but so long as the write permission for it is restricted to the owner the directory would only be vulnerable if an intruder gained access as you, and then the web server would be only a minor part of your troubles.

I would leave the owner unchanged, but make certain the group for the folder is "www-data" (which is a pre-defined system group intended for just this purpose) and that the group has write permission in addition to the owner. Then add yourself to the www-data group, via the users/groups tool or the addgroup CLI program (which requires using sudo since it modifies system data).

This is the whole purpose behind the "group" permissions for files and directories: to allow more than one user to modify files or folders, while leaving their ownership unchanged. It's somewhat similar to the groups available in WinXP and later, but much more fine-grained.

---

### Post by 3rdalbum on 2011-11-17
> **dniMretsaM said:**
> You need to make yourself the owner of the folder. The easiest way to do this is to run the following command in terminal:
```
sudo chown -R yourname:yourname /var/www/
```

NOTE: If you made this folder, this will be fine (which I'm guessing you did. I don't have this folder on my computer). If this is a system directory, it could pose a security risk to change the owner from root.

IMHO this is the wrong way to go about this as it's a loosening of security policy. (the /var/www directory is created when Apache is installed which is why not everybody has it already)

The correct way to do this is to copy your files to the /var/www directory as root. You can either run a copy command in the terminal using 'sudo', or you can just run a file manager as root.

You can run the file manager as root by putting this into the terminal:

```
gksudo nautilus
```

Use this file manager window to copy the files where they need to go. Close it when you're done, to avoid accidentally using it for other non-root stuff.

**EDIT:** JKyle's solution is probably better than mine. However you can remember 'gksudo nautilus' for whenever you want to modify other root-owned things occasionally.

---

### Post by chisao101` on 2011-11-17
> **JKyleOKC said:**
> The /var/www directory is created when you install Apache, and it **is** a system folder in the sense that it contains files that can modify your web server. Consequently there's a possibility of creating a security vulnerability by changing its ownership -- but so long as the write permission for it is restricted to the owner the directory would only be vulnerable if an intruder gained access as you, and then the web server would be only a minor part of your troubles.

I would leave the owner unchanged, but make certain the group for the folder is "www-data" (which is a pre-defined system group intended for just this purpose) and that the group has write permission in addition to the owner. Then add yourself to the www-data group, via the users/groups tool or the addgroup CLI program (which requires using sudo since it modifies system data).

This is the whole purpose behind the "group" permissions for files and directories: to allow more than one user to modify files or folders, while leaving their ownership unchanged. It's somewhat similar to the groups available in WinXP and later, but much more fine-grained.
OK. This is what I was looking for. I want to do this without opening any security holes, even though this is in a virtual box and only a web testing server, not a real web server. I just don't want to start my ubuntu experience with bad habits.
now the problem is, how do i do all that?

by the way, thanks to all of you for your input!

---

### Post by matt_symes on 2011-11-17
Hi

I use JKyleOKC's solution on my server. It's the most flexible approach.

EDIT:

Case-sensitive.

```
sudo usermod -aG www-data <your_user_name>
```Then reboot your server.

Kind regards

---

### Post by chisao101` on 2011-11-17
> **matt_symes said:**
> Hi

I use JKyleOKC's solution on my server. It's the most flexible approach.

EDIT:

Case-sensitive.

```
sudo usermod -aG www-data <your_user_name>
```Then reboot your server.

Kind regards
Awesome! Thanks. I'll try it out. I will post and let you know how it goes.

---

### Post by chisao101` on 2011-11-17
I applied the code, it asked for my password i hit enter and it went right back to the original prompt without letting me know anything was done. I rebooted and tried to just save a file called text and I got this:
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

same thing I've been getting the whole time. Am I doing something wrong? :confused:

---

### Post by matt_symes on 2011-11-17
Hi

Let's take a look.

Please post the output of

```
ls -ld /var/www/
```and 

```
groups
```and lastly

```
grep www-data /etc/passwd
```Kind regards

---

### Post by chisao101` on 2011-11-17
> **matt_symes said:**
> Hi

Let's take a look.

Please post the output of

```
ls -ld /var/www/
```and 

```
groups
```and lastly

```
grep www-data /etc/passwd
```Kind regards
Ok, the output of the first one is:
```
drwxr-xr-x 2 root root 4096 2011-11-16 21:23 /var/www/
```The next one:
```
developer adm dialout cdrom www-data plugdev lpadmin admin sambashare
```I named the machine 'developer' and that's what the user account is called.

And lastly:
```
www-data:x:33:33:www-data:/var/www:/bin/sh
```


Can you tell me where I could go to learn what all that means?

---

### Post by matt_symes on 2011-11-17
Hi
> [FONT=monospace]
[/FONT]drwxr-xr-x 2 root root 4096 2011-11-16 21:23 /var/www/

Your problem is here. The folder is owned by root and not ww-data.

Did you chown the folder to root ? It should be owned by www-data. It has been on all the lamp stacks i have set up.

```
sudo chown www-data:www-data /var/www
```

You should then be good to go.

Kind regards

---

### Post by matt_symes on 2011-11-17
Hi

> Can you tell me where I could go to learn what all that means?

I'll leave this question open to others as it's now 2.45am here.

Kind regards

---

### Post by chisao101` on 2011-11-17
> **matt_symes said:**
> Hi



I'll leave this question open to others as it's now 2.45am here.

Kind regards
Thank you very much!


EDIT: Ok, I tried that and it still won't let me save. I am trying to just create an html file called test.html and save it in the www folder. 
I can open the index.html that was put there during my LAMP install. I don't think I could open that file yesterday, although I may be wrong.
Anyway, thanks for your help. I am going to bed now. I will try again tomorrow.

---

### Post by JKyleOKC on 2011-11-17
> **chisao101` said:**
> Ok, the output of the first one is:
```
drwxr-xr-x 2 root root 4096 2011-11-16 21:23 /var/www/
```The next one:
```
developer adm dialout cdrom www-data plugdev lpadmin admin sambashare
```I named the machine 'developer' and that's what the user account is called.

And lastly:
```
www-data:x:33:33:www-data:/var/www:/bin/sh
```


Can you tell me where I could go to learn what all that means?The "man" pages are supposed to be the "where" you ask for, but their quality varies widely from not enough detail to too much detail, and often they are so full of jargon that they are incomprehensible to newcomers.

In your first result, the "drwxr-xr-x" shows the permissions for the directory. The "d" shows that it's a directory; an ordinary file would have "-" as the first character. The "rwx" shows that the owner has read, write, and execute permission -- but for a directory, "execute" means "is able to browse its content" (which is not at all obvious). The next "r-x" triplet shows that the group had read and execute, but not write, and the final one shows that everyone else can also read and execute but not write.

The "2" shows that the directory has two links. Every directory has two, one to itself and the other to its parent. Next comes the owner name, followed by the group name. The 4096 is the size in bytes of the directory, followed by the date and time it was last modified, and finally by the directory name.

The second result is a list of the groups to which your user belongs.

The third defines a number of properties for the www-data group, including its GID or Group Identifier (the 33) which can become important to you when you get around to modifying some filesystem mounting configurations but which doesn't help much right now.

While you're getting up to speed, you may find the "xman" program helpful. It's a way to display "man" pages in a separate window to look up details, and includes helpful search capability. I've created a launcher on my panel so that I can just click the button and bring it up.

---

### Post by JKyleOKC on 2011-11-17
> **chisao101` said:**
> EDIT: Ok, I tried that and it still won't let me save. I am trying to just create an html file called test.html and save it in the www folder.The reason that it wouldn't is that the group permissions for the directory are "r-x" but they must be "rwx" to let group members write to it.

To change it, you can use this code: ```
sudo chmod 775 /var/www-data
```Others may suggest using the alternate "letter" permission code rather than the "775" but to me the number is easier to remember. It's in octal, not decimal, and each digit represents one of the triplets explained in my previous message. The current number would be "755" and changing to "775" adds the middle bit to the "group" digit.

You can also do it from the "places" display by right-clicking the folder, selecting its "properties" and going to the permissions tab, but you have to be in super-user mode for this to work. The command-line approach is much simpler.

And getting no response at all, just another prompt, is the usual reaction when a command succeeds. Only when something goes wrong does the system tell you about it!

---

### Post by matt_symes on 2011-11-17
Hi

Sorry, i am an idiot. It's late here.

> drwxr-xr-x 2 root root 4096 2011-11-16 21:23 /var/www/                      You also need to change the permission for the group on the directory to give yourself write access .

```
sudo chmod 775 /var/www/
```Then members of the group www-data will also be able to write to the folder.

Edit: beaten to it :)

Kind regards

---

### Post by chisao101` on 2011-11-18
JKyleOKC and matt_symes, you guys are awesome. Thanks a ton for the help.
With the explanation you gave JkyleOKC, I totally understand what all that is now. 
Seriously, you guys have been a great help and I really appreciate it.

:D

EDIT: By the way...it works perfectly now. Thanks again guys!

---

### Post by matt_symes on 2011-11-18
Hi

> With the explanation you gave JkyleOKC, I totally understand what all that is now. 

I agree. He's pretty good. :popcorn:

Could you mark this thread as solved using the thread tools at the top of this thread.

Kind regards

---

### Post by JKyleOKC on 2011-11-18
> **matt_symes said:**
> I agree. He's pretty good.Thanks for the kind words, Matt! Translating engineering jargon into plain language is what I did for a living from 1959 until the early 1980s, when I transitioned into writing software (originally to help me write tech manuals and how-to articles for electronics magazines). I figure it's the best way I can pay forward for all the help I've gotten from others along the way.

---

