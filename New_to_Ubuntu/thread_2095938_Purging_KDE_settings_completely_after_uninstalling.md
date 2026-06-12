---
title: "Purging KDE settings completely after uninstalling"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by zeemanCharmz on 2012-12-18
Hallo INTERNET!!..
I uninstalled KDE recently. And now when I am updating my Ubuntu, I find that there are packages with prefix kde or something, which really tells me that maybe there is something that I ought to have done after removing KDE.

I need to purge all KDE settings, so that I dont have such problems in future. Please Help me on how best I can do that!!..

Thank you in advance!!..

---

### Post by dannyboy79 on 2012-12-18
here's a command that will remove all of kubuntu stuff but use at your own risk. 

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by rburkartjo on 2012-12-18
i have used the link dan provided before to remove and worked for me. will remove 99% but some kde programs might have to be installed manually.

---

### Post by zeemanCharmz on 2012-12-18
Great!!.. 
Let me be checking that out!!..

---

### Post by oldos2er on 2012-12-18
> **zeemanCharmz said:**
> I need to purge all KDE settings, 

```
rm -rf /home/user/.kde/
```

---

### Post by zeemanCharmz on 2012-12-18
Ok I have seen that before [dannyboy79]("http://ubuntuforums.org/member.php?u=108777") when I wanted to uninstall. But now that I have already removed KDE, I want a way of stopping KDE updates from downloading, whenever I run a sudo apt-get update or upgrade.
One other thing is that I had installed KDE while I was still in 11.10. I then upgraded to 12.04 and then to 12.10, I had read in your link that your blog only works safely on "a default Ubuntu installation".
So instead I followed this link:
[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-10/ubuntu-12-10-how-to-completely-uninstallremove-a-packagesoftwareprogram](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-10/ubuntu-12-10-how-to-completely-uninstallremove-a-packagesoftwareprogram)
Now I want to find out if there is a way of also removing the upgrades because I only removed the packages I installed in 11.10.

---

### Post by zeemanCharmz on 2012-12-18
> **oldos2er said:**
> ```
rm -rf /home/user/.kde/
```
 These are the results:
[img]http://ubuntuforums.org/attachment.php?attachmentid=228850&stc=1&d=1355852082[/img]
It doesnt seem to do anything!!..
Thanx nonetheless!!..

---

### Post by dannyboy79 on 2012-12-18
removing the .kde folder will only remove settings of kde installed apps. Are you sure you don't use any kde apps anymore? I wouldn't remove that folder if I were you. Basically, when you run an update or upgrade, just see what is updating and go to synaptic and remove that package. that's the only way to do it in my opinion.

---

### Post by audiomick on 2012-12-18
Did you give it your password? You wont see what you type. Type your password and hit enter.

Also, just go into your /home/user folder, enable "view hidden folders" from the edit menu, or use ctrl+h, and have a look if the folder is there or not.

---

### Post by dannyboy79 on 2012-12-18
> **zeemanCharmz said:**
> These are the results:
[img]http://ubuntuforums.org/attachment.php?attachmentid=228850&stc=1&d=1355852082[/img]
It doesnt seem to do anything!!..
Thanx nonetheless!!..it's not working because I doubt your username is "user"

but again, unless you're positive you don't have not a 1 kde app, I wouldn't remove that folder.

---

### Post by oldos2er on 2012-12-18
> **zeemanCharmz said:**
> These are the results:
[img]http://ubuntuforums.org/attachment.php?attachmentid=228850&stc=1&d=1355852082[/img]
It doesnt seem to do anything!!..
Thanx nonetheless!!..

No need to use "sudo" inside your home folder; and change "user" to your actual user name.

---

### Post by zeemanCharmz on 2012-12-18
> **audiomick said:**
> 
Also, just go into your /home/user folder, enable "view hidden folders" from the edit menu, or use ctrl+h, and have a look if the folder is there or not.

Thanx I had checked before and there is nothing. Does that mean that it is fixed and I wont start to download any updates from KDE anymore??..

@ Dannyboy.. looks lyk you got yoself another youtube subscriber lol!!..

---

### Post by zeemanCharmz on 2012-12-18
> **dannyboy79 said:**
> it's not working because I doubt your username is "user"

but again, unless you're positive you don't have not a 1 kde app, I wouldn't remove that folder.
you'r right about the username.. I have put in my username and there is no change.. Well I think if because I checked the dir and there is no such folder..

---

### Post by oldos2er on 2012-12-18
> **zeemanCharmz said:**
> Thanx I had checked before and there is nothing. Does that mean that it is fixed and I wont start to download any updates from KDE anymore??..

If you don't have any KDE packages installed, you won't get updates for them. The psychocats.net command given previously should uninstall them all.

---

### Post by monkeybrain2012 on 2012-12-18
The .kde folder only stores your settings, which has nothing to do with kde packages being updated or not. If you don't want package x being updated you need to remove it from the package manager (synaptic or the Software Centre) or use "sudo apt-get remove x" from the terminal. The reason why these are not removed is probably that you have installed some kde applications and they were installed as dependencies, but if that is the case removing these packages will also remove the applications which depend on these packages.

You can also try first
"sudo apt-get autoremove",this will remove packages that were installed as dependencies for something else but they are no longer needed because the something else has been removed.

---

