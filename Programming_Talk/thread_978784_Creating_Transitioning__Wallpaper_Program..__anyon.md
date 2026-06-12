---
title: "Creating Transitioning  Wallpaper Program..  anyone want to help out?"
date: 2008-11-11
forum: Programming Talk
---

### Post by MR.UNOWEN on 2008-11-11
Hello,

So currently there's no good wallpaper transitioning program out there for Ubuntu. For some time apple has been able to do this, but Linux hasn't. There are plenty of wallpaper changers, but none of them can make a smooth transition. So I thought to myself, why don't I make one. Right now I have a lot of experience in Java and a fair amount in C. If someone could point me in the direction of some good references to read up on for Images and GUI for Linux that would be nice.

Also I'm looking for people who are also interested in doing this as well. The more people that can join in, the better. Feel free to join in. I'll probably have the least experience in the group, so feel free to lead once we can get a group started on this.

---

### Post by Bodsda on 2008-11-11
Any simple python work that you need I could do. But when i say simple i mean simple, lol, i dont have much knowledge nor experience but I can always research things i dont know.

---

### Post by Namtabmai on 2008-11-11
Hi,

The major problem you'll find when trying to do desktop wallpaper transitions is that Gnome doesn't support anything other than static background. It also creates a flicker when switching static files, so simply quickly switching between pre-rendered images for a transition is out.

Your best bet to implementing this is to use xwinwrap and then create a simple opengl program that fades between to static images.

Unfortunately xwinwrap isn't in the repos so you're first step will be getting this into the repositories, developing a opengl program to do the transitions will be simple in comparisons.

Oh and using xwinwrap obviously requires hardware rendering so it will be compiz only.

---

### Post by Bodsda on 2008-11-11
just a thought, can the compiz wallpapa plugin not do this? and if i remember correctly xwinrap takes desktop control away form nautilus so you say goodbye to your desktop icons

---

### Post by MR.UNOWEN on 2008-11-11
Well using compiz doesn't sound bad. Just wondering can compiz effect the wallpaper without effecting everything else on the desktop?

---

### Post by days_of_ruin on 2008-11-11
You mean like what this guy did?[http://ubuntuforums.org/showthread.php?t=784881]("http://ubuntuforums.org/showthread.php?t=784881")

---

### Post by loell on 2008-11-11
there is this **xml-wall** script? someone suggested this in the forum, where it offers smooth transition. i wish you guys could do the same but with a fancy gui and iff possible have the option to load the wallpaper in memory to lessen disk i/o.

---

### Post by samjh on 2008-11-12
> **MR.UNOWEN said:**
> So currently there's no good wallpaper transitioning program out there for Ubuntu. For some time apple has been able to do this, but Linux hasn't. There are plenty of wallpaper changers, but none of them can make a smooth transition. So I thought to myself, why don't I make one. Right now I have a lot of experience in Java and a fair amount in C. If someone could point me in the direction of some good references to read up on for Images and GUI for Linux that would be nice.

Gnome implemented this one or two versions ago.  Fedora introduced it with Fedora 8.

You're late for the party. ;)

---

### Post by crazyfuturamanoob on 2008-11-12
Perhaps a script for compiz?

---

### Post by MR.UNOWEN on 2008-11-12
> **samjh said:**
> Gnome implemented this one or two versions ago.  Fedora introduced it with Fedora 8.

You're late for the party. ;)

If it's the script based one... then no, it's still buggy. The frame rate is too choppy from image to image and still eats up a good amount of the CPU. I'm running 2 x 3.0GH, so it should be running smooth, but it's not.

If its not, let me know which one you're talking about.

---

### Post by samjh on 2008-11-12
> **MR.UNOWEN said:**
> If it's the script based one... then no, it's still buggy. The frame rate is too choppy from image to image and still eats up a good amount of the CPU. I'm running 2 x 3.0GH, so it should be running smooth, but it's not.

If its not, let me know which one you're talking about.

I'm talking about [this sort of animated wallpaper](http://www.gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443).  The user chooses the xml control file (eg. AllDayLong.xml) instead of an image.  Very smooth and uses no perceptible CPU power.

If that's the same system you're talking about, the problems are not caused by the wallpaper system.  I've never heard of the problems you're talking about at all.

---

### Post by Sorivenul on 2008-11-13
> **loell said:**
> there is this **xml-wall** script? Someone suggested this in the forum, where it offers smooth transition. I wish you guys could do the same but with a fancy gui and iff possible have the option to load the wallpaper in memory to lessen disk i/o.
+1.  This is present in Fedora for sure, if anybody wants to see it in action.

---

### Post by MR.UNOWEN on 2008-11-13
Just to let you guys know I already know about the xml-wall script based one and I've used it, but it's still not perfect. Transitions are about 2 to 3 frames a sec, I want the transitions appear seamless like on the mac. If a low end mac can pull this off, I don't see why Ubuntu can't do it as well.

Since Ubuntu is open source... I should be able get my hands on the code that's behind the xml-script that produces the transitions, right? Does anyone know where I can find that code (not the script, I already saw that)?

Also does anyone know where I can find the source code behind the appearance preference app? I want to try integrating the wallpaper transitioning into it.

---

### Post by samjh on 2008-11-13
Go into the Gnome SVN repository and take a look:
[http://svn.gnome.org/viewvc/](http://svn.gnome.org/viewvc/)

I don't know exactly which files contain the source.  You might need to post on the Gnome developers' mailing list to find that out.

---

