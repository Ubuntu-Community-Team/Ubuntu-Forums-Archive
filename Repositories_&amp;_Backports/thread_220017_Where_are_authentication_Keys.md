---
title: "Where are authentication Keys ??"
date: 2006-07-20
forum: Repositories &amp; Backports
---

### Post by David TAkle on 2006-07-20
Newbie to Linux.  Been going around in circles for hours trying to figure out how to get Thunderbird with the Synaptic Package Manager.  It tells me it can't be authenticated.  I assume that means I lack the right authentication key.  I have the 2 default keys installed with Ubuntu.  Too many questions...
1. Why do I need another authenticaion key to download something that is in the Supported Repositories ???
2. All the docs say to get a key I need to know the owner of the Repository. I can't figure out how to find that either.
3. Even if I found the owner, I wouldn't know how that helps me.
4. I thought this package stuff was supposed to be easy.  But it's nearly impossible!  I can't figure out why this is so hard, and why I can't find any information on the topic that is written for a person who does not already know the answer.
Driving me nuts!!

](*,)

---

### Post by mlind on 2006-07-20
hiya,

are you using 3rd party repository to get Thunderbird?

You should have default Ubuntu gpg keys already on the APT keyring, so installing Thunderbird should be as peachy as
```

sudo aptitude install mozilla-thunderbird

```

Write that command on terminal (ALT+F2, then type gnome-terminal)


/edit
If you have somehow removed default key(s)
/usr/share/keyrings contains the public key for repos

---

### Post by David TAkle on 2006-07-20
p.s.
Found one page that ALMOST explains the issue.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
But it adds more questions:
1. I can see no correlation between the URI (or any other info about the respository) and the field supplied as the name of the key server.  Where does the key server come from?
2. Where do they find the keyhash to enter?

---

### Post by mlind on 2006-07-20
> **David TAkle said:**
> p.s.
Found one page that ALMOST explains the issue.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
But it adds more questions:
1. I can see no correlation between the URI (or any other info about the respository) and the field supplied as the name of the key server.  Where does the key server come from?
2. Where do they find the keyhash to enter?

All ubuntu packages are digitally signed, so that you are getting them from trusted source. You don't need to enter anything keyhash related, authentication process is automatic.
If you have somehow managed to delete default keys, you just have to import keys again on APT keyring.

Could you provide error you're getting so it's easier to determine what the actual problem is?

---

### Post by David TAkle on 2006-07-20
mlind:
thanks for replying.  But your post only confused me more.
1. I have not removed any keys
2. I have only selected the binary repositories that were part of the install
3. your command line command is working.  But I haven't learned anything.  How did you arrive at the syntax necessary to do the install.  Does it check for authentication?  If so, why did it succeed?  If not, then how do I know it's ok?
4. Finally, I would really like to use the Synaptic Package Manager, and I am no closer to accomplishing that either.

Please help !!

---

### Post by David TAkle on 2006-07-20
I didn't do anything remotely like deleting keys.  I clicked on "Restore Defaults" in the dialog box and nothing changed.
When I select a package in the Package Manager, it issues a warning saying "Can't Authenticate"

---

### Post by mscman on 2006-07-20
Perhaps this HowTo will help you learn more about how package management works:

[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by mlind on 2006-07-20
> **David TAkle said:**
> mlind:
thanks for replying.  But your post only confused me more.
1. I have not removed any keys


Then it's okay. Synaptic sometimes has problems like these, I don't use it personally. To see what authentication keys are currently on APT keyring, from Synaptic > Settings > Repositories > Authentication. 

There should be atleast two Ubuntu signing keys which Synaptic will use automatically to verify package authenticy when you download a package from Ubuntu repository.

> **David TAkle said:**
> 
2. I have only selected the binary repositories that were part of the install


Yes, you won't probably need source repositories if you don't plan to build something from sources yourself. But you should enable other available repositories (restricted, multiverse, universe) using Synaptic, if those aren't already enabled

> **David TAkle said:**
> 
3. your command line command is working.  But I haven't learned anything.  How did you arrive at the syntax necessary to do the install.  Does it check for authentication?  If so, why did it succeed?  If not, then how do I know it's ok?


Synaptic is graphical management application for APT which handles all the package management stuff. aptitude and apt-get are command-line based tools for APT. It's matter of personal preference what you use, but aptitude is little bit smarter than the others.

aptitude does authentication checking, and smartly tracks dependencies of your installed packages. If you're wondering about syntax, commands
```

aptitude --help
man aptitude

```
will help.


> **David TAkle said:**
> 
4. Finally, I would really like to use the Synaptic Package Manager, and I am no closer to accomplishing that either.


Please keep using it. It works really well, but for some reason had trouble authenticating your downloads. This is usually fixed by changing the mirror of the repository for something else, but I'm not sure if this is possible from Synaptic.

If problem persists, I'll help you to change the repository mirror Synaptic currently uses.

---

### Post by jrjr on 2006-07-23
I am getting this authentication warning when I try to install wine. Is it anything to worry about? I checked a few others and they were ok.

---

### Post by mlind on 2006-07-23
> **jrjr said:**
> I am getting this authentication warning when I try to install wine. Is it anything to worry about? I checked a few others and they were ok.

Did you get the warning when installing from Ubuntu official repository or from wineHQ repository? If you used the latter, you should import their gpg key.
As long as those are warnings and not errors, it's nothing to worry about though.

---

### Post by jrjr on 2006-07-23
I just used synaptic. Im not sure where they come from!!
I have automatix installed and that changes sources.list if that makes a difference.. so I can proceed?

---

### Post by mlind on 2006-07-23
> **jrjr said:**
> I just used synaptic. Im not sure where they come from!!
I have automatix installed and that changes sources.list if that makes a difference.. so I can proceed?

Repository is signed using gpg key, so you know you're donwloading from trusted and authenticated source.

If your sources.list contains
```

deb http://wine.budgetdedicated.com/apt dapper main

```

You can safely download packges there. Those warnings are just for note that you're downloading from untrusted source.

---

### Post by jrjr on 2006-07-23
> **mlind said:**
> 

If your sources.list contains
```

deb http://wine.budgetdedicated.com/apt dapper main

```


Yes that is there.
I see that the rest of them in my sources.list file have 2 related lines starting with

deb http:  
deb-src

This entry only has the one though.

---

### Post by jrjr on 2006-07-23
Do you think I should use Synaptic, Automatix, or use these directions?

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=install+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=install+wine)

---

### Post by mlind on 2006-07-23
> **jrjr said:**
> Do you think I should use Synaptic, Automatix, or use these directions?

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=install+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=install+wine)

I have no experience of automatix. I've used insturctions on WineHQ's site
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by jrjr on 2006-07-23
Thanks I will check it out....:)

---

