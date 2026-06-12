---
title: "Unraring"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-09-03
Hey guys,

I'm now using Linux Mint, but I was getting this same problem in Ubuntu. Anyways, I've got the program Unrar installed from the Package Manager. And whenever I download a file that comes in rar's or zip's, when I try to extract it, I get a window that pops up that asks me for a password.

But the thing is, these files don't require a password to be opened. If I download the exact same file, from the exact same site in Windows, and hit Extract with Winrar, the files extract without a problem. No password window pops up.

Has anyone else came across this problem? Is it some kind of option I need to enable or disable somewhere? I've got Wine installed, should I just install Winrar?

Thank you for any and all help.

---

### Post by iaculallad on 2008-09-03
From what location are you trying to extract the file? Outside of your /home partition?

---

### Post by jemate18 on 2008-09-03
> **h8uthemost said:**
> Hey guys,

I'm now using Linux Mint, but I was getting this same problem in Ubuntu. Anyways, I've got the program Unrar installed from the Package Manager. And whenever I download a file that comes in rar's or zip's, when I try to extract it, I get a window that pops up that asks me for a password.

But the thing is, these files don't require a password to be opened. If I download the exact same file, from the exact same site in Windows, and hit Extract with Winrar, the files extract without a problem. No password window pops up.

Has anyone else came across this problem? Is it some kind of option I need to enable or disable somewhere? I've got Wine installed, should I just install Winrar?

Thank you for any and all help.

Yes I have experienced it. I have downloaded and installed Peazip
> [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

select PeaZip for Linux GTK2 widgetset DEB

---

### Post by Tatty on 2008-09-03
What sort of password prompt is it?

It could be that you are attempting to extract it somewhere you need root privilages so the system is asking for a sudoer password.

---

### Post by RealG187 on 2008-09-03
Some archives have passwords, no matter what program.

If you downloaded it, then try the website as a password, example when I upload [Homebrew]("http://bestwikiever.wikidot.com/Homebrew") files for the forum I run I make the password psphomebrew.net, which is the site's domain name.

Try with or without www. (this one time I copied and pasted the url from the file name since the URL was in the file name).

If it was on a forum, try the uploaders username or otherwise look in the post.

If it's an archive you made and you dont know the password, then ....

---

### Post by h8uthemost on 2008-09-03
I tried Peazip, and it tells me I've encountered an error. The there's a little hint box at the bottom of the window that says check to see if there's a password to use. But there isn't. Like I've mentioned, I've downloaded this same exact file on Windows, and it extracts perfectly.

I'm downloading the file straight to my desktop and trying to extract it there.

---

### Post by jemate18 on 2008-09-04
> **h8uthemost said:**
> I tried Peazip, and it tells me I've encountered an error. The there's a little hint box at the bottom of the window that says check to see if there's a password to use. But there isn't. Like I've mentioned, I've downloaded this same exact file on Windows, and it extracts perfectly.

I'm downloading the file straight to my desktop and trying to extract it there.

This seldom happens.. I've been using Peazip everytime I encounter that password error with Unrar............ And it works....

---

### Post by h8uthemost on 2008-09-04
Ok. Then maybe the file has been corrupted somehow. I'll try getting it from somewhere else and extracting it.

Thank you for your help.

---

### Post by RealG187 on 2008-09-04
> **h8uthemost said:**
> Ok. Then maybe the file has been corrupted somehow. I'll try getting it from somewhere else and extracting it.

Thank you for your help.

But if it worked in windows it shouldnt be corrupted, try running the windows based unrar program you used under wine and see if that works

---

