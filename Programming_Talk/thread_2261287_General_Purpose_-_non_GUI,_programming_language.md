---
title: "General Purpose - non GUI, programming language"
date: 2015-01-17
forum: Programming Talk
---

### Post by Frank P on 2015-01-17
I'm comfortable using PHP / MySQL / Apache but I haven't kept up with any other languages. What would be used for reading, writing, and analyzing directories/files at the command line level. No gui needed

Thanks

Frank

---

### Post by tgalati4 on 2015-01-17
Midnight Commander (mc) is in the repositories:

> mc - Midnight Commander - a powerful file manager
mc-data - Midnight Commander - a powerful file manager -- data files
mc-dbg - Midnight Commander - a powerful file manager - debug package


Bash is probably all you need for simple scripts.  Grep, awk, perl, and sed are useful for searching and parsing files.

---

### Post by Frank P on 2015-01-17
I do use Midnight Commander but it wont do what I need.

My wife has a hard drive on a Windows desktop that has about 10 years of vacation photos scattered around it in directories and subdirectories with no consistent naming conventions or organization.

I need to go thru the drive recursively, picking out the folders with jpgs/pngs  and creating a catalogue with paths, dates, etc. that I can review later. I've done this on a drive on my Ubuntu server using PHP/MySQL but I don't want to move the drive. I could probably do it with PowerShell but I'd rather take the time to learn a cross platform language

Thanks

Frank

---

### Post by trent.josephsen on 2015-01-17
Most people use bash or generic sh for that kind of thing.

Personally, I think most shell languages are really ugly and awkward. Not to mention that for any task X, there are generally a dozen different ways to do X, of which 8 don't work in plain sh, 4 only work in bash, 2 work only in zsh and ksh, and 6 may have side effects Y and/or Z (but not in ksh93, or under the light of a full moon in May, in which case W may happen instead). Perl 5 has this kind of issue but to a much lesser extent, and is a better designed language (IMHO). At the same time, Perl is more suitable for shell-like tasks than Python, which is the other option you're likely to hear recommended here (sometimes in the same breath).

An option you're not likely to hear from someone else: I give Tcl the advantage over Perl for the learner, and Tcl is probably what I would use for this kind of thing most of the time. It has a familiar shell-like syntax, and you can even run it as a shell (tclsh) if you want (I don't suggest using it as your login shell). But the language is clean and simple and it doesn't quite feel like everything invented since 1973 was bolted on. It will run out of steam when writing really big complex stuff, but for the kind of thing you describe, it's what I'd reach for.

So there you have it. At the end of the day only you can make the decision, but any one of Perl, Python or Tcl would be a good choice in my opinion. Hope this helps.

---

### Post by tgalati4 on 2015-01-17
Build a linux desktop with a gui and remotely mount the Windows machine.  The file manager (Nautilus or Caja) will automatically display thumbnails of photos.  This is much faster than trying to parse EXIF data from photos.  Afterall, humans are good at pattern recognition, so this is a Use Case that really benefits from a graphical interface.

If you don't want to build another machine, then you could install a virtual machine on your server and install a lightweight, graphical distro.  Do your photo organizing, then delete the vm when you are finished.  And if you build a vm, then you might as well load *shotwell* or some other photo manager and just import the photos and organize them within the photo manager.

An alternative method is to load a photo manager directly on the server and use a web interface.  [http://galleryproject.org/](http://galleryproject.org/)

---

### Post by Frank P on 2015-01-18
The volume is too large for a photo manager - we're talking several thousand photos - a few too many thumb nails to handle at one time :-)
 I'll do some research on languages. 
Is there a way to mark this thread closed?
Thanks
Frank

---

### Post by Erik1984 on 2015-01-18
There is a Thread Tools dropdown menu (in the bar under the topmost reply button) with an option to mark this thread as solved.

---

### Post by flaymond on 2015-01-20
> What would be used for reading, writing, and analyzing directories/files at the command line level. No gui needed

Then the answer is Perl and Bash. (I gladly to choose Perl instead, but it was ugly). Perl don't have much issue on compatibilities, so in you question..yea..Perl is might be your tool to do those (don't forget the simplicity of python!)

---

### Post by Lars Noodén on 2015-01-20
+1 for perl

I'd say it is the way to go for tasks like you describe.  Don't forget that CPAN modules exist for directory traversal and tens of thousands of other activities, so you won't have to write the script wholly from scratch.  Perl is really flexible and easy to program.

---

### Post by Frank P on 2015-01-20
Thanks for all the suggestions. Since they're all scripting languages (I was expecting compiled) it made realize I already know and use a cross platform scripting language - PHP.  I'll use the CLI version
Thanks
Frank

---

