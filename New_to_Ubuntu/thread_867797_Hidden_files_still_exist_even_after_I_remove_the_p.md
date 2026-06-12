---
title: "Hidden files still exist even after I remove the program"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by stellalie on 2008-07-23
Hi, I'm new to linux, and I'm currently using Xubuntu: Hardy Heron.

I tried to install Tomboy (note-taking application) before with Synaptic, and find it unnecessary. So, I decided to remove it through Synaptic too.

However, I still notice hidden files in /Home folder by the name '.tomboy'. I was wondering:
1.) Synaptic is not uninstalled it properly? I tried '$ sudo aptitude purge tomboy' and those files still exist. Why?
2.) Is it safe to just drag & drop the whole folder to Trash bin?
3.) Is it going to happen to all other application?
4.) Is there any way to keep my computer clean and free from unnecessary files no matter how small they are?

Thanks beforehand!

---

### Post by Potatoj316 on 2008-07-23
in synaptic did you say remove or completly remove?

---

### Post by irshadcharm on 2008-07-23
Run 

1) sudo apt-get clean
2) sudo apt-get autoremove

This will do your job..if the above doesnt work try to delete the tomboy folder from the home directory and give a restart...

---

### Post by Heinzelotto on 2008-07-23
sometimes you want to remove a program but not your custom settings for that program (think of a instant-messenger with saved logs). This is why Synaptic only removes the system-files when you perform a standard "remove"

---

### Post by LaRoza on 2008-07-23
You can delete the .tomboy folder. 

Anything in your home directory can be deleted without affecting the system (however, you'd lose personal settings and data, but if you don't want it is doesn't matter). If you did delete a . directory and start the app, it would just create a default profile.

---

### Post by mali2297 on 2008-07-23
> **stellalie said:**
> 
1.) Synaptic is not uninstalled it properly? I tried '$ sudo aptitude purge tomboy' and those files still exist. Why?

Personal configuration files are not created when you install the program but when you first run it. Synaptic/apt-get/aptitude only removes the files that were added during the installation.
> 
2.) Is it safe to just drag & drop the whole folder to Trash bin?

Yes.
> 
3.) Is it going to happen to all other application?

Basically, yes.
> 
4.) Is there any way to keep my computer clean and free from unnecessary files no matter how small they are?

I just remove them manually. I don't know of any automatic method.

---

### Post by stellalie on 2008-07-23
Thanks guys!!

> **mali2297 said:**
> 
I just remove them manually. I don't know of any automatic method.

I guess currently solved my curiosity...

---

### Post by cardinals_fan on 2008-07-24
```
sudo aptitude purge *app*
```should work

---

### Post by dje on 2008-07-24
also try:
```
sudo apt-get autoremove --purge *myapp*
```

dje

---

