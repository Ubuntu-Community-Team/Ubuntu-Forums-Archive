---
title: "Running AWN on slower system?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Anonono on 2008-09-27
Compiz won't run on my PC, is there a different compositing window manager that will run AWN? Or is there a way to activate Compiz without most of the effects?

---

### Post by Xiong Chiamiov on 2008-09-27
If you install compizconfig-settings-manager, then you'll be able to adjust which Compiz plugins are enabled.

---

### Post by Anonono on 2008-09-27
I installed it, but I can't find an option to actually make Compiz the window manager.

---

### Post by psycosmyth on 2008-09-27
I have pondered this as well. There are similar docks but not as reliable as Avant. What video card do you have? Like said before, you can disable all plugins with the manager and have a chance.

---

### Post by Xiong Chiamiov on 2008-09-27
> **Anonono said:**
> I installed it, but I can't find an option to actually make Compiz the window manager.
I believe it's on the left side, somewhere?  You can run compiz though with the command
```

compiz --replace

```
...although that might be a compiz-fuzion rather than compiz.  I'm a little rusty.

---

### Post by Anonono on 2008-09-28
> **psycosmyth said:**
> I have pondered this as well. There are similar docks but not as reliable as Avant. What video card do you have? Like said before, you can disable all plugins with the manager and have a chance.
It's actually intergrated graphics. It's fully capable of rendering 3D objects in Windows, but I don't think it can in Linux.

@Xiong Chiamiov: I got this: > Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

Is this bad?

---

### Post by rossjman1 on 2008-09-28
You can take these steps to turn on compositing in Metacity (the default WM in Ubuntu): [http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)
> ...The main advantage of using Metacity&#8217;s compositing is that you can run applications such as Screenlets, Awn, and GNOME Do that would otherwise need Compiz for their eye-candy...

... You don&#8217;t need accelerated graphics to run Metacity with compositing. It even works well inside VirtualBox! If your computer can&#8217;t run Compiz, give this a try...

---

### Post by Xiong Chiamiov on 2008-09-28
That means you can't run compiz.  You might want to take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=836858").

---

### Post by Anonono on 2008-09-28
> **rossjman1 said:**
> You can take these steps to turn on compositing in Metacity (the default WM in Ubuntu): [http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)
I love you.

I'm now running AWN without a hitch. Thanks everyone!

---

