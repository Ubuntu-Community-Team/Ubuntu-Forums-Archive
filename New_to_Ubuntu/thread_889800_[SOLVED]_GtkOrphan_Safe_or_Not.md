---
title: "[SOLVED] GtkOrphan: Safe or Not?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by jfbays on 2008-08-14
I installed GtkOrphan.  It returned 5 "orphaned packages".  Is it safe to remove them as reported?  Or do I need to use caution?  Thanks...

---

### Post by Paqman on 2008-08-14
I use it all the time, never had any trouble with it.

If it accidentally removed some package that was still required by one of your apps, a simple reinstall of that app would fix the problem. There's not a lot it could do to your system that wouldn't be fixable pretty easily.

---

### Post by aysiu on 2008-08-14
> **jfbays said:**
> I installed GtkOrphan.  It returned 5 "orphaned packages".  Is it safe to remove them as reported?  Or do I need to use caution?  Thanks...
It depends on what you mean by "safe."

GtkOrphan actually lists the priority of the package (whether it is critical or not), and it's highly unlikely an orphaned package is going to be critical to the operation of Ubuntu. In other words, it won't render your system unbootable.

However, you may have a package that is important to keeping your sound working or it may be a program few other Ubuntu users use but you use.

Look at the package description and see if it's important or not.

If you're really worried, remove one package at a time, and see what effect it has. Make a note of the package name in case you need to reinstall it.

I'd say, though, unless you have an Eee PC or something with a really small amount of storage (2 GB hard drive or 4 GB hard drive), don't even bother removing those 5 packages.

---

### Post by sayakb on 2008-08-14
You may also create your own Orphaned filter in synaptic. Open Synaptic, goto Settings->Filters.
Press New button, then press the Deselect All button and **check** *Orphaned* under Other. Also rename New Filter 1 to "Orphaned". Press OK and you're done!

---

### Post by Irony on 2008-08-14
I've used it for some time without trouble - list the things that are to be uninstalled so if something doesn't work you can reinstall it... I've not actually had anything incorrectly uninstalled yet.

---

### Post by jfbays on 2008-08-14
OK, I created an "Orphaned" filter in Synaptic.  Now what?  What exactly is this filter going to do, and will it require any input from me?

Concerning GtkOrphan: when I tick the "Show all orphan packages" option, several items show up, including b43-fwcutter.  Are all those items safe to remove?  The last thing that I want to happen is to knock-out my wireless card...

---

### Post by aysiu on 2008-08-14
> **jfbays said:**
> OK, I created an "Orphaned" filter in Synaptic.  Now what?  What exactly is this filter going to do, and will it require any input from me?

Concerning GtkOrphan: when I tick the "Show all orphan packages" option, several items show up, including b43-fwcutter.  Are all those items safe to remove?  The last thing that I want to happen is to knock-out my wireless card...
I think you know the answer.

If something seems alarming to you to remove (b43-fwcutter, for example), don't remove it.

If you're not sure, keep it.

If you decide to remove something, keep track of the package name so you can reinstall it later if something goes wrong.

It's all up to you what to keep and delete. I have no problems removing b43-fwcutter from my Ubuntu, since I don't need it for my wireless to work.

---

### Post by jfbays on 2008-08-14
No, at the moment, I'm not too sure about anything.  For all I know b43-fwcutter is a "Run Once" type of program that can be removed.  For now, however, I think that I'll quit worrying about orphaned packages...  

But, now that its been created, what is the "Orphaned" filter in the Synaptic Package Manager going to do for me?  Thanks...

---

### Post by jfbays on 2008-08-21
I went ahead and uninstalled everything that appeared on GtkOrphan, and everything is still working.  I did get an Error the first time that I ran the Update Manager after removing all the orphans, but that resolved itself on the next update check. So I guess GtkOrphan is "Safe". 

For now, as an Absolute Beginner, I don't have any vital data stored on my Ubuntu box, so I don't mind experimenting -- if it blows up, I'll simply re-install Ubuntu...

---

### Post by the_guv on 2009-08-30
[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html)

---

