---
title: "Log-in Screen Resolution"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Polish Rifle on 2008-07-30
My normal resolution when I'm using my computer is fine.  But the resolution is so high that I can't see what I'm typing in the log-in screen when it asks me for my username/password.  I can't even read the options or tell what the icons are.

---

### Post by philinux on 2008-07-30
If you want to do with a GUI install and run startupmanager. It's in synaptic. Or

```
sudo apt-get install startupmanager
```

---

### Post by Polish Rifle on 2008-07-30
What exactly does startupmanager do?

---

### Post by philinux on 2008-07-30
Sets up the startup/login resolution and other useful stuff.

---

### Post by Polish Rifle on 2008-07-31
Startupmanager did not change the log-in screen resolution at all.  I tried every combination of resolution and color depth.  It also has my screen blank, instead of showing the Ubuntu load bar.  

I had it restore the defaults and nothing happened...so I'm stuck with my new settings.  

Oh well, just some minor things.  I'll live with the Ubuntu load bar and SUPER small log-in screen I guess.

---

### Post by philinux on 2008-07-31
> **Polish Rifle said:**
> Startupmanager did not change the log-in screen resolution at all.  I tried every combination of resolution and color depth.  It also has my screen blank, instead of showing the Ubuntu load bar.  

I had it restore the defaults and nothing happened...so I'm stuck with my new settings.  

Oh well, just some minor things.  I'll live with the Ubuntu load bar and SUPER small log-in screen I guess.

Worked a treat for me. Have you got your graphics card configured ok.

Whats the make. This will show you.
```
lspci | grep VGA
```

Also check in System>Admin>Hardware drivers.

Are you running Hardy, if so did you upgrade or fresh install.

---

### Post by Polish Rifle on 2008-07-31
I'm not at my computer at the moment but I have a very poor video card, and yes I'm running hardy with current updates.

Thanks for working with me Phil.


-Phil

---

### Post by philinux on 2008-07-31
> **Polish Rifle said:**
> I'm not at my computer at the moment but I have a very poor video card, and yes I'm running hardy with current updates.


Was it a gutsy upgrade or fresh install?

---

### Post by Polish Rifle on 2008-08-01
Fresh install using the alternate-text CD.

---

### Post by Polish Rifle on 2008-08-02
Actually....is there a way to do away with the log in screen?  I don't even want/need it.

---

### Post by Masoris on 2008-08-02
> **Polish Rifle said:**
> Actually....is there a way to do away with the log in screen?  I don't even want/need it.

Use Autologin: System > Administrator > Login Window > Security > Enable Automatic Login

---

### Post by Redptc on 2008-08-02
This thread may help you in your search for a solution. It guides you to a point where you can change the resolution in the Grub menu which could be causing the problem. [HTML]http://ubuntuforums.org/showthread.php?t=847171[/HTML]
You may have a similar effect carrying through to the login window.

Have fun and good luck!

---

### Post by Polish Rifle on 2008-08-02
Wow....this just keeps on getting worse...I'd be happy just to go back to my default settings.  Here are my new problems:


- Log-in resolution is still small (don't care about this anymore)
- Automatic Log-in screen is one color
- I do not have the option to restart/shutdown my computer anymore since I enabled automatic log-in.

Is there a way just to return to my original settings?

---

