---
title: "porting the gobolinux filestructure to ubuntu/debian?"
date: 2007-01-23
forum: Other OS Talk
---

### Post by jclmusic on 2007-01-23
first of all, any idea how do the gobolinux people do it? is it a package that 'interprets' the filesystem that way, or just a file manager, or what?

and how would i go about porting it to ubuntu or debian?

---

### Post by RAV TUX on 2007-01-23
> **jclmusic said:**
> first of all, any idea how do the gobolinux people do it? is it a package that 'interprets' the filesystem that way, or just a file manager, or what?

and how would i go about porting it to ubuntu or debian?

**Sticky:**Poll:  			 			[GoboLinux Talk: (Changing the filesystem hierarchy)]("http://ubuntuforums.org/showthread.php?t=295071")

---

### Post by jclmusic on 2007-01-24
i've seen that thread already. i don't see how it answers my question.

---

### Post by 3rdalbum on 2007-01-25
It is actually a kernel patch that creates the pretense of GoboLinux's file system. Any time a Gobo-specific directory is referenced (i.e. "/Applications/GIMP/gimp"), the patch translates it into a traditional filesystem address (i.e. "/usr/bin/gimp").

I might be wrong about that, but I'm sure it's a kernel patch.

---

### Post by jclmusic on 2007-01-26
thanks, man :)

---

### Post by manic007 on 2007-03-01
Hello

I was wondering if anyone knew if there was an official/unofficial port of Gobolinux for Ubuntu? I've used Gobolinux before and its breathtakingly simple! I would dearly love to see that on my Ubuntu box.

PS: I know this issue is famous for starting holy wars. I dont want that, I dont care what the traditional Linux Ayatollah's think, I'm not asking for the Gobo FHS to be incorporated into the next release. There is no need to slag me off and called me stupid or ignorant or a heritic or an infidel or some sort of traitor to the almighty cause. I'm just asking if a package is available so some of us can test it out, nothing more. I am simply asking for the freedom to test it on my Ubuntu box. Thank you.

---

### Post by Nils Olav on 2007-03-01
> **3rdalbum said:**
> It is actually a kernel patch that creates the pretense of GoboLinux's file system. Any time a Gobo-specific directory is referenced (i.e. "/Applications/GIMP/gimp"), the patch translates it into a traditional filesystem address (i.e. "/usr/bin/gimp").

I might be wrong about that, but I'm sure it's a kernel patch.

No, the kernel patch justs hides the compatibility directories.

---

### Post by justin whitaker on 2007-03-01
> **jclmusic said:**
> first of all, any idea how do the gobolinux people do it? is it a package that 'interprets' the filesystem that way, or just a file manager, or what?

and how would i go about porting it to ubuntu or debian?

Gobohide is the core of GoboLinux. What it is is a kernel patch which allows you to hide from the user any folders that you do not want them to, or do not think they should, see. 

The other part of that is this whole Compile application, which allows you to symlink to those hidden directories: this is key to get software installed. 

So you have a mess of symlinks, and a kernel patch. It does not noticeably slow the system down...but I have no idea how that would work with debain/ubuntu systems. You would need to recreate the symlinking stage of Gobolinux's installation of software prior to installing a .deb file.

---

### Post by igknighted on 2007-03-01
I'm not sure this is something that could ever be possible for Ubuntu.  To change the file structure that radically would require moving almost every file on your HD... and then telling every program where everything was moved to.  To try to do this with symlinks would be very repetitive and end up very messy (and probably not work).  I think the best bet is to play with gobo and tweak it to be more like Ubuntu if you really want to try it.

What MIGHT be possible would be to create a file browser (or maybe a nautilus/konquerer mod) to display the files on your system (which are really in a standard linux heirarchy) in a style similar to Gobo, to let you browse it more effectively.

---

### Post by Nils Olav on 2007-03-02
> **igknighted said:**
> I'm not sure this is something that could ever be possible for Ubuntu.  To change the file structure that radically would require moving almost every file on your HD... and then telling every program where everything was moved to.  To try to do this with symlinks would be very repetitive and end up very messy (and probably not work).  I think the best bet is to play with gobo and tweak it to be more like Ubuntu if you really want to try it.

Using symlinks isn't as hard as you suggest, It would work as long as you are careful. Quite a few have done this successfully (but I don't think any of them have distributed their changes) so it's at least possible.

---

