---
title: "Had to remove Compiz to repair my desktop now I cannot reinstall Compiz"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by painguin on 2011-09-27
So it started here...  I was stuck in a boot loop and was able to fix it by using the command "sudo chmod a-x /usr/bin/compiz".  So basically I had to remove Compiz to fix my "boot loop" problem.  

(This is an x64 wubi install)
Now, however, Compiz is gone even after I reinstalled it.  I ran "compiz --replace" and received the output "command not found".  The only window manager I can use is Metacity, I cannot change it through the compiz fusion icon either.  

I checked the drivers for my NVIDIA GeForce GTS 450 (or 480) and it shows that they are installed correctly just as before.  However, I am still facing this issue.  Compiz does not work at all.  I can access the Compiz Advanced Settings Manager and make changes but they have no effect.  

I don't know what to do.  I'm not an expert with Linux but have been using different distros for 5 years at least.  Mostly Ubuntu...  Anyway, I've managed to fix one issue with the help of a friend and now I have another problem.  Any suggestions???


Thanks, 


PAinguIN

---

### Post by wildmanne39 on 2011-09-27
Hi, that command changes permissions of compiz it did not uninstall it, I will research and see what I find on this issue.
Thank you

---

### Post by painguin on 2011-09-27
> **wildmanne39 said:**
> Hi, that command changes permissions of compiz it did not uninstall it, I will research and see what I find on this issue.
Thank you

Ahhhh, ok, that's what "chmod" does right?  Allow you to change permissions on files and folders?  So what does the "a-x" option do?

And thank you for your help!

PAinguIN

---

### Post by wildmanne39 on 2011-09-27
Hi, I am not an expert on chmod, you can run 
```
chmod man
```
in a terminal to get a better understanding of its use.

What happens when you try to install compiz again do you get a permission error?

How are you trying to reinstall it with synaptic or the terminal?

What version of ubuntu are you using?
Thank you

---

### Post by painguin on 2011-09-27
> **wildmanne39 said:**
> Hi, I am not an expert on chmod, you can run 
```
chmod man
```
in a terminal to get a better understanding of its use.

What happens when you try to install compiz again do you get a permission error?

How are you trying to reinstall it with synaptic or the terminal?

What version of ubuntu are you using?
Thank you

Cook, thanks for the tip!  

I do not get an error when  I reinstall Compiz.  Only if I run "compiz --replace" do I get the "command not found" error.  Actually, to get that error,  I have to use "sudo compiz --replace"...

I've reinstalled it using both the Synaptec Package Manager and "apt-get" (or was it dpkg...I'm pretty sure I used aptitude).  Anyway, I've even "removed" Compiz using Synaptec and reinstalled to see if it would matter, it didn't.  Lol!

The version I am using is Ubuntu 11.04 x64 (natty) and it is a wubi install.  

I think that some of my problems emerged because I ran out of free space in "/" and another folder as well.  But I managed to resolve that for now.  I am just going to have to install Ubuntu on it's own disc or partition.  In fact, that is why I am in this mess now, I ran the live cd to check out my partition table and after that I could not login to the desktop.  That was fixed, of course, when I changed permissions for Compiz.

I have installed "pyrit" and was in the process of creating the password DB and ran out of space.  I freed some up, finished with all the passwords I could store and began to convert those into there respective Pairwise Master Key's which took up the newly expanded virtual disk space I created of 30+ GB's.

If I could just reinstall Ubuntu and restore all of my programs, db's, settings, etc that would be fine.  But the last tarball I made started to copy /host/program files/.  I should have added "--exclude=/host/" to the string and I could have avoided that possibly but I'm not sure.  And that's an entirely different issue altogether.

So yes, Ubuntu 11.04 x64 (natty).  I'm also running the classic gnome desktop, I do not like Unity and hope that they do not completely replace the classic gnome desktop environment with it.

I hope this helps and if more info is needed let me know.  I can copy/paste some logs here or the output of a program if it will help.

Thanks!

PAinguIN

---

### Post by wildmanne39 on 2011-09-27
Hi, the fact that you ran out of space in / is the reason you could not boot ubuntu.

Since you are using wubi it would be best to do a normal dual boot install, and if you need help on that you should start a new thread with a good title.

We can probably get your permissions changed back but it sounds like you should do a normal install, then remember commands in the terminal using sudo can have bad results.

If you do not know what a command does type its name in the terminal with man after it, and that will open the manual pages for that command.
Thank you

---

### Post by painguin on 2011-09-27
> **wildmanne39 said:**
> Hi, the fact that you ran out of space in / is the reason you could not boot ubuntu.

Since you are using wubi it would be best to do a normal dual boot install, and if you need help on that you should start a new thread with a good title.

We can probably get your permissions changed back but it sounds like you should do a normal install, then remember commands in the terminal using sudo can have bad results.

If you do not know what a command does type its name in the terminal with man after it, and that will open the manual pages for that command.
Thank you

I see, so then I may not have even needed to change the permissions with Compiz as I created that free space in the same sitting as I ran the "chmod a-x compiz" (or whatever it actually was).

I won't have a problem installing Ubuntu on its on disk or partition.  I've had a few boxes with only Linux distros installed but this time I wish to move forward in learning how to use Linux as a whole.  Also, as a Network Admin by trade I am also wishing to learn more about pyrit and how it uses the cores of ones GPU to process information instead of just the systems processor.  

Anyway, 

I'll backup using this 
"tar cvpzf backup.tgz --exclude=/proc --exclude=/mnt --exclude=/backup.tgz --exclude=/lost+found --exclude=/sys --exclude=/dev --exclude=/host /" 

I should be able to restore my backup in the newly installed Ubuntu using this...
"tar xvpfz backup.tgz -C /"

It will overwrite ALL of the new files in that partition with the ones in the tarball.  I just don't want it to roll over the issue I'm having into the new installation.

Anyway, I guess I'll try to make a backup and restore it after installing Ubuntu again.  

Thank you for your advice, I really appreciate it. If you have any other thoughts please feel free to share them with me. 

Regards, 

PAinguIN

---

### Post by cpmman on 2011-09-27
> **wildmanne39 said:**
> 
If you do not know what a command does type its name in the terminal with** man after it,** and that will open the manual pages for that command.
Thank you

That should be type ```
man <command>
```i.e with man **before** it.

e.g. ```
man chmod
```

---

### Post by wildmanne39 on 2011-09-27
Hi, like I said I have not used chmod much but I have been reading on it and I believe that this will change the permission back.
```
sudo chmod a+x /usr/bin/compiz
```
I wrote this backwards earlier man chmod as cpmman stated.

I would not import your files from the wubi install but that is up to you.

Is there files there that are important?
Thank you

---

### Post by painguin on 2011-09-27
> **wildmanne39 said:**
> Hi, like I said I have not used chmod much but I have been reading on it and I believe that this will change the permission back.
```
sudo chmod a+x /usr/bin/compiz
```
I wrote this backwards earlier man chmod as cpmman stated.

I would not import your files from the wubi install but that is up to you.

Is there files there that are important?
Thank you

Saweet!  I'll try that here in just a minute and let you know what happens.  

So bad idea to import the wubi files to the new install?  Makes sense...

There are some things I do not want to lose but could reinstall if I had to.  The "pyrit" installation along with the libraries and cuda deg tools that must be installed along with it.  Then I would have to rebuild the massive wordlist db that literally took hours to build and then converting all of the words in that db to there PMK's also.  That alone took 2 days at about 15,000pmk's/sec.  It's a huge db.

But, doing it all over again would allow me to become more familiar with the installation as well as the terminal.

But if the command you posted above works then I won't have to worry about it.  Lol!

PAinguIN

---

### Post by wildmanne39 on 2011-09-27
Hi, you could install Deja Dup from synaptic then just back up the files you want by setting it in preferences to back up just certain folders.
Thank you

---

### Post by painguin on 2011-09-27
> **wildmanne39 said:**
> Hi, you could install Deja Dup from synaptic then just back up the files you want by setting it in preferences to back up just certain folders.
Thank you

Nice, have you used it before?

---

### Post by wildmanne39 on 2011-09-27
Hi, yes I have it back up my system daily, I have not had to used it to restore yet but I do not think there will be a problem when I do, it is very easy to use.
Thank you

---

### Post by painguin on 2011-09-27
It worked wildmanne39!  I ran the command you suggested and then I ran "compiz --replace" and just like that it was back!  LOL!  

Wow, I really appreciate all of the time you put into this.  It would have taken me forever to figure it out, if ever.  LOL! 

Again, thank you very, very much!

PAinguIN

---

### Post by wildmanne39 on 2011-09-27
Hi, your welcome! I am glad it worked.

---

### Post by Blasphemist on 2011-09-27
Glad to see the progress. This may be a help to you for converting to a dual boot. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by painguin on 2011-09-27
> **wildmanne39 said:**
> Hi, your welcome! I am glad it worked.

Me too!  :D

Thanks again!

---

### Post by painguin on 2011-09-27
> **Blasphemist said:**
> Glad to see the progress. This may be a help to you for converting to a dual boot. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Thanks Blasphemist!

PAinguIN

---

### Post by wildmanne39 on 2011-09-27
Hi, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by painguin on 2011-09-28
> **wildmanne39 said:**
> Hi, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

Solved!  And thank you!

PAinguIN

---

