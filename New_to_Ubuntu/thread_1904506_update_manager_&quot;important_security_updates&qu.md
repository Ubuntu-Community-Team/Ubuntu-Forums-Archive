---
title: "update manager &quot;important security updates&quot;"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Geoff16W on 2012-01-04
I just installed Ubuntu 11.10 about 2 weeks ago. Now the update manager is asking me to install 57 important security updates or 92.5 mb. 

Should I accept all these updates regularly? I don't enjoy having stuff on my machine that I don't know about. Still I'm rather new to all this stuff. Should I just install all of these? Should install some of them, or should I just install them as needed.

Thanks for your advice.

---

### Post by Buntumatic on 2012-01-04
GNU/Linux is under rapid development. You should be glad you are running an operating system that keeps up with time, just install all updates.

---

### Post by QIII on 2012-01-04
Yes, you should install them.

While this may seem like a large number of updates, you have to remember that any Linux distro is made up of a bunch of discrete parts and the software you have installed is developed by a range of people who work generally independently.

Those updates are for a lot of different pieces.  You get them in "real time" as the developers get them in the stream, rather than waiting for a periodic update.

You are not getting a bunch of extra stuff.

I don't even wait for the update notification.  While I'm working, I update and upgrade daily.

---

### Post by the.phantom on 2012-01-04
you can click the arrow next to "descriptions" and expand the bottom of the update window

then if you click a update

you will see a description AND change

think you will see most are for security and why the update and get that "warm and fuzzy feeling"

and quite often after a new release there will be several large updates with in a few weeks

---

### Post by Basher101 on 2012-01-04
usually updates never take more than ~ 10 MB. It is a new Kernel version that takes that much space. The Kernel alone is about ~ 80 MB.

just to give you an idea what is taking the space

---

### Post by sammiev on 2012-01-04
Security Updates should be taken as soon as possible. I always look to see what they are for first. :)

---

### Post by Basher101 on 2012-01-04
> **sammiev said:**
> Security Updates should be taken as soon as possible. I always look to see what they are for first. :)

+1

i always take a second and third look at the recommended updates as alot of KDE stuff wants to get installed that i do not want nor need :3

---

### Post by mcduck on 2012-01-05
> **sammiev said:**
> Security Updates should be taken as soon as possible. I always look to see what they are for first. :)

+1 from me as well. Keeping your system updated is one of the most important concepts of Linux security.

Also keep in mind that the updates on Ubuntu *will never add anything new to your system*. They are only replacing packages you already have with a new version of the same package.

After being released, Ubuntu only gets important security updates, and fixes for more serious bugs. Both are the kind of updates you'll definitely want to install. Updating a package version after release requires very good reasons and in general it's never done to add new features or things like that.

---

### Post by mcduck on 2012-01-05
> **Basher101 said:**
> +1

i always take a second and third look at the recommended updates as alot of KDE stuff wants to get installed that i do not want nor need :3

If the updates are offering you KDE packages, that means you already have those KDE packages installed. Uninstall them if you don't want them, otherwise you really should update them.

---

### Post by Geoff16W on 2012-01-05
Thanks everybody. Updates are installed and I feel better knowing everyone else is installing them. :)
jw

---

### Post by Momof9Blessings on 2012-01-05
Will updates mess up other software?  For example, I have CS5 installed with WINE and now I can't get it to start....

Do I need to go thru the tweaks to get it running again?


oops it is working....  I tried to make a link to the exe file - but then I went to the folder with the exe file and tried that one and it worked.... kind of weird.... :(

---

### Post by mcduck on 2012-01-05
> **Momof9Blessings said:**
> Will updates mess up other software?  For example, I have CS5 installed with WINE and now I can't get it to start....

Do I need to go thru the tweaks to get it running again?


oops it is working....  I tried to make a link to the exe file - but then I went to the folder with the exe file and tried that one and it worked.... kind of weird.... :(

no, at least the updates from official repositories shouldn't mess anything, that's pretty much the reason why the update policy is so strict and often the maintainers even apply security patches to the current versions of programs instead of updating the package to latest available version to keep things as stable as possible.

I don't think a link to an .exe would work, but creating a *launcher* should work just fine. Just set the command to "wine /path/to/yourprogram.exe" (or whatever is required to run the application in Wine, it's been years since I've used it myself...)

---

### Post by Momof9Blessings on 2012-01-06
Do you have to close everything when there are updates???

NOT that it is slow to close everything NOT like in windows.....

---

### Post by mcduck on 2012-01-06
> **Momof9Blessings said:**
> Do you have to close everything when there are updates???

NOT that it is slow to close everything NOT like in windows.....

No, not usually. Or actually I can't even remember ever having to close a program on Linux to update it... :D And you don't need to reboot either for anything else than kernel updates (and even then you can keep on using the computer as long as you want before the reboot).

---

