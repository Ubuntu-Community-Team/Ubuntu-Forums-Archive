---
title: "A couple questions"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-08
Firstly, sorry for the overly-generic & cliche thread name. I have more than one question to address, and I had no clue what to name the thread.

**Question one:**

I get this message in my terminal:

```

    You have to configure "localepurge" with the command

        dpkg-reconfigure localepurge

    to make /usr/sbin/localepurge actually start to function.

    Nothing to be done, exiting ...

```

I did the command that I'm given, but I'm not sure what options to choose. I'm afraid I'll mess something up.

**Question Two:**

When my computers booting up, after the grub menu, the loading screen shows the 'Kubuntu' loading screen, instead of the 'Ubuntu' one. This isn't really a big deal, every thing loads how I want it to, I just thought it was a bit weird.

[B]
Question Three:[/B]

When I'm shutting down, I get a black screen with a lot of text. It seems like a lot of it is errors, but I'm not sure how to check what it is. Should I be worried about this?

---

### Post by sayakb on 2008-07-08
1. Do it with a **sudo**
```
sudo dpkg-reconfigure localepurge
```2. Install Startupmanager.
```
sudo apt-get install startupmanager
```Goto System->Administration->Startup-Manager and click on **Appearance** tab and change the **Usplash theme** below to [I]ubuntu-theme-usplash

[/I]3. Its not much to worry about, probably some Network Manager related errors.

---

### Post by adobrakic on 2008-07-08
> 
1. Do it with a sudo


Yeah, i do that. But when it asks me to choose locale files, and it looks like it has hundreds of options, I have no idea what to choose.

Thanks for the other answers. :)

---

### Post by ibuclaw on 2008-07-08
If you are english, scroll down and choose all the **en-*** options.

There will be stuff like en-GB and en-US in there. I think there is en-ZW too. But all should be english, and it's best to highlight them, just incase ;)

Regards
Iain

---

