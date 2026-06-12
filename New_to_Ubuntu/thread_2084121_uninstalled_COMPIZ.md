---
title: "uninstalled COMPIZ"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by travelfool on 2012-11-14
hello,

last night I UNINSTALLED compiz from the media centre. I was trying to install compiz config setting manager but was not paying attention and simpy uninstalled compiz instead :confused:. I reinstalled compiz straight away after, but now i have no icons on the left side (where dash normally is) and no bar at the top. 

I still have all my fles and i can still sccess Terminal.

I have Ubuntu 12.10 upgraded from 12.4. I am sure i just have to update compiz (or so i hope) but have no idea what to type

what can I i do please???

thank you

---

### Post by Frogs Hair on 2012-11-14
Try the following to reset Unity. Ctrl + Alt + T ```
setsid unity
```

---

### Post by travelfool on 2012-11-14
did not work... get

execvp: No such fie or directory

anything else???

thanks

---

### Post by Frogs Hair on 2012-11-14
Check your version with the following command because the reset command works as posted on my 12.10 installation. ```
lsb_release -a
```

---

### Post by Frogs Hair on 2012-11-14
See if the Unity plugin is installed also it may have been removed with compiz and not reinstalled. You can do this from the software center. ```
software-center
```

---

### Post by deadflowr on 2012-11-14
So you got compiz reinstalled?
Then, since you don't have icons, I guess, install the compizconfig-settings-manager through a terminal


```
sudo apt-get install compizconfig-settings-manager
```

, and when installed open with ccsm in terminal and look for the unity shell plugin and make sure it is checked(enabled).

You'll need to actually click on the unity shell plugin icon-thingy as unlike others the enable function is in it and not like the others that can be checked without entering the various categories.

---

### Post by travelfool on 2012-11-14
ok...i get

No LSB modules are available
Distributor ID: Ubuntu
Description: Ubuntu 12.10
Release: 12.10
Codename: quantal

---

### Post by travelfool on 2012-11-14
which unity am i looking for? 

thanks

---

### Post by travelfool on 2012-11-14
So you got compiz reinstalled?

am not 100% sure.

i tried to reinstall it in software centre and it said installed?!?

to make it clear - i have NO unity on the left at all and NO bar at the top....I am using my girlfriend laptop to use the internet

cheers all

---

### Post by Frogs Hair on 2012-11-14
You can check to see if Compiz and Unity are installed from the software center. 12.10 only includes a single version of Unity.

---

### Post by travelfool on 2012-11-14
hey guys/gals

thank you very much...unity was uninstalled...cheers for your help

:KS

---

### Post by travelfool on 2012-11-14
I do have some other queries as well thought. this all happened before i uninstalled compiz

VLC player just unisntalled by it self ...have reinstalled and it works fine, just wated to know why?

in Ubunut Tweak>Tweaks>Workspace i have set it so when i place the mouse in different corners on the screen it 'show windows', 'show desktop' and 'show workspaces' but it only works some times - and when 'show desktop' does work firefox never goes away!

Ubuntu 12.10 seems to take longer to start up and runs slower than 12.4.
I have Intel(R) Core(TM)2 Duo CPU T5670 @ 1.80GHz Memory 2.0 GB - is this good enough for 12.10?

any help much appreciated! you guys are another reason Ubuntu is so fantastic!! :guitar:


just an afterthought...should I be putting this in a new thread?

---

### Post by travelfool on 2012-11-14
> **travelfool said:**
> I do have some other queries as well thought. this all happened before i uninstalled compiz

VLC player just unisntalled by it self ...have reinstalled and it works fine, just wated to know why?

in Ubunut Tweak>Tweaks>Workspace i have set it so when i place the mouse in different corners on the screen it 'show windows', 'show desktop' and 'show workspaces' but it only works some times - and when 'show desktop' does work firefox never goes away!

Ubuntu 12.10 seems to take longer to start up and runs slower than 12.4.
I have Intel(R) Core(TM)2 Duo CPU T5670 @ 1.80GHz Memory 2.0 GB - is this good enough for 12.10?

any help much appreciated! you guys are another reason Ubuntu is so fantastic!! :guitar:


just an afterthought...should I be putting this in a new thread?


Will post these in a new thread...thank you again all!!

---

