---
title: "Nautilus Desktop/File Menu (Right Click)"
date: 2007-01-28
forum: Programming Talk
---

### Post by Rab22 on 2007-01-28
I've tried searching this a while ago for like an hour. I didn't find anything, and to be honest, I really don't want to sink another hour into searching this out.

Now, I know there is a great 'Scripts" entry for nautilus-scripts. But I'm wondering how you customize the actual menus.

If anyone could just point me in the direction of some documentation, that would be great.

Thanks for any help,


-Rick

---

### Post by Tomosaur on 2007-01-28
Not sure it can be done without tampering with the source code, I'm afraid. At least, I'm not aware of any method to do it.

---

### Post by phossal on 2007-01-28
Tomosaur, what's he trying to do?

---

### Post by phossal on 2007-01-28
Wow. This is interesting, and I'm assuming this is the part you guys already know about: [Nautilus Scripts]("http://g-scripts.sourceforge.net/faq.php"). It would be cool (and I'm sure it's *possible*) to customize the entire menu, but adding the functionality of scripts is, in a sense, unrelated. That's just *awesome.*

I installed this package: nautilus-open-terminal. It changed the right-click desktop menu. Now, when I right-click, I have an option for the terminal.

---

### Post by Rab22 on 2007-01-28
> Not sure it can be done without tampering with the source code, I'm afraid. At least, I'm not aware of any method to do it.

Yeah, me either. And that's the issue -- you'd think there would have to be a way to install applications into this menu. I don't know whether or not file-rollers defautly in there, or the program itself adds and entry.

I don't see why there isn't a way to customize this menu. 

> 
Wow. This is interesting, and I'm assuming this is the part you guys already know about: Nautilus Scripts. It would be cool (and I'm sure it's possible) to customize the entire menu, but adding the functionality of scripts is, in a sense, unrelated. That's just awesome.


Yes, that's what I was refering to earlier. It is a fantastic feature -- but I'm looking for something a bit less 'advanced'.

---

### Post by phossal on 2007-01-28
I'll admit I'm completely stupid when it comes to this sort of thing. Short of a few very *specific* examples, I didn't customize my environment very much. I'm still not understanding what you're trying to achieve.

---

### Post by Rab22 on 2007-01-28
Inside nautilus (Desktop or within a folder) if you right click a document you get a context menu that allows to "Open", "Open With", "Create Archive", "Properties", etc.

What I would like to do, is add an option to this menu....without having to add a nautilus-script.

I'm not sure if this is possible -- but file-roller does create a couple entries (Create Archive and Extract Here).

---

### Post by jblebrun on 2007-01-29
> **Rab22 said:**
> Inside nautilus (Desktop or within a folder) if you right click a document you get a context menu that allows to "Open", "Open With", "Create Archive", "Properties", etc.

What I would like to do, is add an option to this menu....without having to add a nautilus-script.

I'm not sure if this is possible -- but file-roller does create a couple entries (Create Archive and Extract Here).

It adds a shared object library to nautilus, which is less trivial than just writing a script...

```

jblebrun@Compaqtic:~$ dpkg --listfiles file-roller
..
..(excluded output)
..
/usr/lib
/usr/lib/nautilus
/usr/lib/nautilus/extensions-1.0
/usr/lib/nautilus/extensions-1.0/libnautilus-fileroller.so
...
..(excluded output)
...

```

---

### Post by aslamp on 2008-10-03
There are instructions here by using compiz-deskmenu. It works very nicely =]. 

[http://ubuntuforums.org/showpost.php?p=5493372&postcount=4](http://ubuntuforums.org/showpost.php?p=5493372&postcount=4)

---

