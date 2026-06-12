---
title: "html with ftp access"
date: 2007-06-05
forum: Programming Talk
---

### Post by cong06 on 2007-06-05
In windows Dreamweaver has this cool way of accessing a the ftp.

The only problem is it's too intense.
I want a lightweight program that has enough features for a web-editor, and has ftp access. I _could_ do all my editing on my box and lift it up with a ftp program (filezilla) but I feel like editing them straight to the site would be easier.

Suggestions for a Linux program?

---

### Post by satellite360 on 2007-06-05
[Quanta Plus]("http://quanta.kdewebdev.org/") will allow you to edit files remotely.  Type [ftp://user:password@myserver.com](ftp://user:password@myserver.com) in the open dialog box.

---

### Post by barmazal on 2007-06-05
Never tried it with Aptana but it supposed to do so. I develop locally

---

### Post by barmazal on 2007-06-05
nice one but i don't think at this stage anything from other menus will work

---

### Post by AnRa on 2007-06-05
You can use any KDE or GNOME program you want. For KDE I recommend Kate. With GNOME you have to enable write support in GnomeVFS because it is a little buggy. You can also use Emacs or Vim. ;)

---

### Post by teampoop on 2007-06-05
In Windows I used EditPlus. It has an FTP folder menu built in. I haven't found anything in OSX or Linux that does the same, and am kinda bummed about that fact.

---

### Post by AdamG on 2007-06-05
Nvu is what you (and teampoop) are looking for. It runs on Win/Mac/Lin, and has straight on-the-server editing with FTP. 

You'll have to get a third-party package since it's not in the repos. You may also want to try the closely related KompoZer. 

[http://kompozer.net/](http://kompozer.net/)

---

### Post by cong06 on 2007-06-06
It doesn't look like NVU has any nice, neat way of installing. I guess I'll try Quanta and see if it does what I want.

I looked around for the package for NVU, and it doesn't seem like there is one. I don't like messing around with the ziped files. (clutter, etc). I might break down and do it anyway though. we'll see.

From what I saw, it looked like it has a visual interface? That seems nice, but the more features, the slower it is. And a non-bogged down program is what I'm looking for.

I guess we'll see what I think  :)

---

### Post by cong06 on 2007-06-06
Oh. I guess the other feature that's really important for me in Dreamweaver, is teh dropdown options, to help one figure out what you're supposed to use.

Sometimes it's annoying, but for the most part, I'd like it as a feature. Is this still an option without being too bloated of a program? Does NVU support this?
...
[SIZE="1"](too late do I find out that quanta doesn't have ftp access...guess I'll run through all my installs to remove it. At least it's only a apt-get remove away.)[/SIZE]

---

### Post by AnRa on 2007-06-06
> **cong06 said:**
> [SIZE="1"](too late do I find out that quanta doesn't have ftp access...guess I'll run through all my installs to remove it. At least it's only a apt-get remove away.)[/SIZE]Quanta Plus is a KDE program so it does support FTP access. For accessing a remote file just open it as a normal file (i.e. go to the "Open file..." dialog and type the file location).

---

