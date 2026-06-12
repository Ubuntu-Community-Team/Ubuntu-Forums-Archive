---
title: "program naming convention for linux"
date: 2009-07-16
forum: Programming Talk
---

### Post by e24ohm on 2009-07-16
Folks:
I am studying Linux at school; however, I do not fully understand the naming convention used when dealing with applications.

what does the format mean and what parts mean what? for example i have this version of vlc.

vlc-0.9.8a.tar.bz2

I under stand the (tar.bz2) is a compressed file; however, i do not get the version part. another example is the Ubuntu download format.

would be great if anyone can offer any help or tips to remember or to understand the convention.

thank you.
E

---

### Post by JordyD on 2009-07-16
The version number is often decided by the application's writer, there is no standard that I'm aware of. But Ubuntu (or Debian) packages do have a specific format, and breaking the format will just make it hard for people to use their package manager to find your program. Here is more information [How to make a "Basic" .deb]("http://ubuntuforums.org/showthread.php?t=910717").

---

### Post by c0mput3r_n3rD on 2009-07-16
It's usually a date and a version number. But like the above post said it's not a standard.  Find how the writer of the program you want to know about formatted there version by researching it.

Ubuntu 9.4 = Ubuntu April 2009.

---

### Post by c0mput3r_n3rD on 2009-07-16
Oh and just a side note:  Linux doesn't open files based on there extension like Windows does.  Linux actually looks at the contents of the file and opens it appropriately.

---

### Post by JordyD on 2009-07-16
> **c0mput3r_n3rD said:**
> Oh and just a side note:  Linux doesn't open files based on there extension like Windows does.  Linux actually looks at the contents of the file and opens it appropriately.

Actually, that depends. GNOME opens some files based on file extension, and opens some files based on contents. Even KDE opens files based on file extensions.

For example:
GNOME will categorize a key as a key regardless of file extension, but if you change the file extension of one of your files from .odf to .sh, all the sudden it thinks it's a shell script.

**EDIT:** For clarification, c0mput3r_n3rD is correct, but if you explicitly give a file an extension, it will ignore the contents of the file and treat it as that extension.

**EDIT2:** I said 'regardless of file extension', but really, it should have said 'without file extension'.

---

### Post by snova on 2009-07-16
> **e24ohm said:**
> what does the format mean and what parts mean what? for example i have this version of vlc.

vlc-0.9.8a.tar.bz2

I under stand the (tar.bz2) is a compressed file; however, i do not get the version part. another example is the Ubuntu download format.

It can be anything the author wants, but it's typically **<major>.<minor>.<revision>**, or something similar.

[http://en.wikipedia.org/wiki/Software_versioning](http://en.wikipedia.org/wiki/Software_versioning)

> **c0mput3r_n3rD said:**
> It's usually a date and a version number. But like the above post said it's not a standard.  Find how the writer of the program you want to know about formatted there version by researching it.

Ubuntu 9.4 = Ubuntu April 2009.

I very rarely see version numbers with embedded dates, except for Ubuntu releases.

> **c0mput3r_n3rD said:**
> Oh and just a side note:  Linux doesn't open files based on there extension like Windows does.  Linux actually looks at the contents of the file and opens it appropriately.

You'd be surprised. KDE, at any rate, places some importance on extensions (though it can still tell you what kind of file it is, the default application seems to be based on the filename). I don't remember what Gnome does.

And anyway, "Linux" could care less, since on the command line it's your job to remember what kind of file something is, the applications don't bother as long as it's valid.

---

### Post by JordyD on 2009-07-16
> **snova said:**
> And anyway, "Linux" could care less, since on the command line it's your job to remember what kind of file something is, the applications don't bother as long as it's valid.

:D That's why we like to use file extensions. That way we always know what kind of file it is.

---

### Post by e24ohm on 2009-07-16
thanks folks this  has been very helpful...

cheers!!!

---

### Post by c0mput3r_n3rD on 2009-07-16
> **JordyD said:**
> Actually, that depends. GNOME opens some files based on file extension, and opens some files based on contents. Even KDE opens files based on file extensions.

For example:
GNOME will categorize a key as a key regardless of file extension, but if you change the file extension of one of your files from .odf to .sh, all the sudden it thinks it's a shell script.

**EDIT:** For clarification, c0mput3r_n3rD is correct, but if you explicitly give a file an extension, it will ignore the contents of the file and treat it as that extension.

I learned something new :)

---

