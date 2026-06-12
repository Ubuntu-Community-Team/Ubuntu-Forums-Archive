---
title: "Mark Multiple Packages in Synaptic"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by Iggy64 on 2012-12-16
Here is a real noob question:

When I remove a package, this sometimes causes a dozen or more other packages to become "autoremovable" or orphaned.  I find myself clicking each package individually and marking it for removal (or complete removal).  Is it possible to select multiple packages and remove them with a single action?

I can see why this might not be possible, as sometimes one removal requires a decision about removing another.

However, I can find no info on this "batch mark" and remove issue.

Can someone give a definitive answer?

Thanks?

---

### Post by Dennis N on 2012-12-16
On lower left of Synaptic Main Screen select **Status** button. 
In the pane in the upper left, select **Installed (auto removable)**.
All matching packages will be shown on the right.

To remove the matching packages:
Left-click on the first, shift-left-click on the last, so that all are selected. Then press Delete (this marks them for removal), and then press Apply button. 

Using Shift-Delete will instead mark for complete removal.

---

### Post by Baldrick_NZ on 2012-12-17
```
sudo apt-get autoremove
``` in a terminal will also deal with them, and quicker than Synaptic too.

---

### Post by Iggy64 on 2012-12-17
Thanks to both of you for helping me out with this.  

I have used autoremove (in Terminal) and auto removable (in Synaptic).  As a noob, I don't have a total grasp on what this category includes.  I have read that these are packages that are no longer needed, since nothing depends on them anymore.

However, I have these other categories: orphans, local/obsolete, and so on.  Sometimes, I have multiple orphans to completely remove.  Now I wonder: are the orphans taken away by autoremove?  

Although I have read through the Synaptic literature, I'm still very hazy on what goes into each category.

---

### Post by audiomick on 2012-12-17
> **Iggy64 said:**
> I have used autoremove (in Terminal)... As a noob, I don't have a total grasp on what this category includes. 

Did you know you can get an explanation of commands with man?

in the terminal, do
```
man <command>
```

Some man pages are pretty cryptic, but the one for apt-get is not so bad.

Do
```
man apt-get
```

and scroll down to the explanation of autoremove.

As far as I understand it, the purpose of the option -autoremove is to do exactly what you are looking for.

---

### Post by Iggy64 on 2012-12-18
Audiomick,

Thanks for making time to clarify those things.  The man command (I guess that means "manual") will really help me learn Linux faster, as well as make better use of the Terminal.  

I'll start using "man" on autoremove, purge, and so on --- to get further info on cleaning up my installation.

Again, thanks for offering help.

---

### Post by audiomick on 2012-12-18
> **Iggy64 said:**
>  The man command (I guess that means "manual") 

That's about it. Man has it's own man page.

```
man man
```

glad I could be of help. ;)

---

