---
title: "Command LIne Programs needing a GUI"
date: 2006-11-14
forum: Programming Talk
---

### Post by neilp85 on 2006-11-14
I'm looking for command line programs that are still in need of a decent graphical frontend. It could also be config files like fstab. I know this topic has been brought up before but I feel that it is still important. Desktop Linux is still in it's emergence and there are many users who fear the command line. My main motivation behind this is that I'm looking for a new project to start and figure I should do something that could be beneficial to the Linux/OSS community. 

As people offer up suggestions I can add them to this post so that we might be able to build a comprehensive list. This way other people like me out there can find inspiration for a new project.

Ideas for better/new GUIs:

CVS
xserver-xorg
grub
Abook (address book)
Remind (calendar)

---

### Post by ciscosurfer on 2006-11-14
A new graphical front-end for CVS.  There's gcvs, but it's not-so-pretty, and there's lincvs, but that's written with the qt...it would be nice if you could come up with a new front-end for CVS that is gtk+ based and matches the look and feel of Ubuntu (GNOME-like).  Just a suggestion.  Lincvs is nice (for KDE--and ok, for GNOME too) but I'd like to see something for GNOME that's updated.

---

### Post by tubasoldier on 2006-11-14
> **neilp85 said:**
> I'm looking for command line programs that are still in need of a decent graphical frontend. It could also be config files like fstab.


I think if you look at Mandriva's Control Center that would be a great basis of ideas. But not necessarily they way they set it up. Things I think that could use a GUI:

xorg - I think this is pretty self explanatory.

grub - being able to add and subtract entries. Also the ability to drag and drop in a new grub image.

I'll add in more as I think of them.

---

### Post by ciscosurfer on 2006-11-14
> **tubasoldier said:**
> I think if you look at Mandriva's Control Center that would be a great basis of ideas. But not necessarily they way they set it up. Things I think that could use a GUI:

xorg - I think this is pretty self explanatory.

grub - being able to add and subtract entries. Also the ability to drag and drop in a new grub image. I'll add in more as I think of them.[LIST=1]
[*]Do you mean xserver-xorg?  If so, I agree.
[*]As for GRUB, you can try [GrubEd]("http://www.ubuntuforums.org/showthread.php?t=228104") (it's really great!)[/LIST]

---

### Post by neilp85 on 2006-11-14
> **ciscosurfer said:**
> A new graphical front-end for CVS.
This is something that I also think could use improvement, however it's a much larger undertaking than what I'm looking to get involved in at the moment.

---

### Post by David Marrs on 2006-11-15
Abook and Remind (an address book and calendar) are two very useful command line apps that would benefit from a user interface. Remind in particular could do with one, as it has so many switches. You could even combine them with an email client to make a simplified alternative to evolution, which I find annoyingly complicated. If you wrote such an app, I'd be sure to use it :)

---

### Post by neilp85 on 2006-11-15
> **David Marrs said:**
> Abook and Remind (an address book and calendar)

I'm not sure how well Abook would translate to a graphical frontend since it's ncurses based but thanks for the input.

---

### Post by tzulberti on 2006-11-15
I agree with the cvs front end

---

### Post by cwaldbieser on 2006-11-15
> **neilp85 said:**
> I'm looking for command line programs that are still in need of a decent graphical frontend. It could also be config files like fstab. I know this topic has been brought up before but I feel that it is still important. Desktop Linux is still in it's emergence and there are many users who fear the command line. My main motivation behind this is that I'm looking for a new project to start and figure I should do something that could be beneficial to the Linux/OSS community. 

As people offer up suggestions I can add them to this post so that we might be able to build a comprehensive list. This way other people like me out there can find inspiration for a new project.

Ideas for better/new GUIs:

CVS
xserver-xorg
grub
Abook (address book)
Remind (calendar)


Maybe some kind of simple file sharing configuration.  Last time I checked, SWAT requires you to enable the root account to log in, which goes somewhat against the Ubuntu way of doing things.  There are other GUIs for file sharing, but none of them is perfect.

Just browse the other help forums and look for solutions where command line solutions are given.  If you think you could provide a helpful front-end, go for it.

---

### Post by neilp85 on 2006-11-15
> **cwaldbieser said:**
> Just browse the other help forums and look for solutions where command line solutions are given.  If you think you could provide a helpful front-end, go for it.

Good idea, I never even thought of that.

---

