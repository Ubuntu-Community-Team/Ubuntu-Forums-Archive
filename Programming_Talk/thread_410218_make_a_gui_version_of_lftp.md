---
title: "make a gui version of lftp"
date: 2007-04-15
forum: Programming Talk
---

### Post by nix4me on 2007-04-15
How hard would it be to program a gui that controls all the functionality of lftp.  Lftp is a great command line ftp client but I have noticed the lack of a "great" gui ftp client.

Would a python frontend be the way to go?  Or would it take a ground up effort to adapt the lftp source into a program with a gui?

nix4me

---

### Post by nix4me on 2007-07-25
Anyone have any thoughts on this?

lftp is truly the best ftp client.  A gui frontend for it would be awesome.  I just don't have the skills to do it.

nix4me

---

### Post by AlexThomson_NZ on 2007-07-25
> **nix4me said:**
> How hard would it be to program a gui that controls all the functionality of lftp.  Lftp is a great command line ftp client but I have noticed the lack of a "great" gui ftp client.

Would a python frontend be the way to go?  Or would it take a ground up effort to adapt the lftp source into a program with a gui?

nix4me

How hard it is depends on your level of experience.  I can't see anything *toooo* tricky in doing it.  Network programming is not too tricky in linux (I am learning it myself at the moment).  I wouldn't bother trying to migrate the source-code though, it's a 650k executable and probably quite complex.  You would probably learn more starting from scratch.  What's wrong with foff or Filezilla anyway?

Probably not a program you could jump right in and do off the bat with no experience, whatever the language tho...

---

### Post by smah77 on 2007-07-25
> **nix4me said:**
> Anyone have any thoughts on this?

lftp is truly the best ftp client.  A gui frontend for it would be awesome.  I just don't have the skills to do it.

nix4me

I've never tried anything quite like this, but I'd imagine doing a PyGTK frontend wouldn't be too tricky.  You shouldn't have to know anything about network protocols or that sort of thing, just how to start up lftp, send it text strings, and read its output, all from within a python program.

---

### Post by AlexThomson_NZ on 2007-07-25
Well, if you were going to do it that way, you can just use:
```

system("iftp blah blah");

```

In a C program, and whip up a Glade interface around it...

---

### Post by nix4me on 2007-07-25
Filezilla and the like are not as feature rich as lftp.  I've tried all gui ftp clients and they all have different limitations.  GFTP just plain sucks.  kftpgrabber is decent, but buggy on fxp.  kasablance does not support PRET.  kbear is crap.  filezilla, no PRET.  etc, etc.

Lftp is awesome.  It does anything and everything.


A pyGTK front-end would be a good start I guess.  What would be awesome is taking the gftp look, and apply the lftp commandset to it.

I have no idea.

Maybe someone will read this that has the skills and interest.

nix4me

---

### Post by AlexThomson_NZ on 2007-07-25
Just out of curiosity, are there particular features that are missing from the gnome FTP clients, particularly Filezilla?

Maybe you might have more luck getting those devs to add features, rather than starting your own?

If there is a real need for a decent gnome FTP client, I might be interested- am somewhat between projects at the moment, and this is the sort of project I enjoy (plugging a need for fully Gnome HIG compliant apps)

---

### Post by nix4me on 2007-07-25
filezilla is missing PRET and SSCN support.  I have asked the devs and they refuse to add it.  They claim there is no RFC for those features.

The drftpd server requires PRET for site to site encrypted transfers.

The only clients on linux that support PRET are kftpgrabber and lftp.  Kftpgrabber works well but it still has some bugs which prevent some fxp transfers.  lftp works perfectly.

On the windows side, flashfxp and ftprush are shining examples of compliant ftp clients.  They refuse to port to linux though.

nix4me

---

### Post by AlexThomson_NZ on 2007-07-25
Cheers for the info!

I'm a bit out of the loop with FTP- obviously the FTP world has moved on since my day (I haven't used it since the windows/warez days before syntaptic).  I'll have to look into the whole PRET thing...

---

### Post by nix4me on 2007-07-27
i mis-spoke on what PRET does.  It is pre-transfer commands allowing distributed ftp servers to be used.  Drftpd is an example.

SSCN is related to the secure site to site transfers.

nix4me

---

### Post by Primefalcon on 2008-12-22
I actually Love lftp I use it over all other clients....

one of the things I do really like about it you never get logged out with it, not even after days, I think it takes care of reauthenticating for you and everything if your server logs you out.

Lftp really does rock

A GUI would actually be welcome as well, as long as you had a nice degree of lftp functionality such as reverse mirroring and keeping you logged in and so

---

### Post by gardara on 2009-01-23
Has anyone done some work on this?

I came across a mono gui, but haven't tried it and probably won't, since it's written with mono... [http://developer.novell.com/wiki/index.php/GmFtp](http://developer.novell.com/wiki/index.php/GmFtp)

I personally hope someone makes a decent C++ or python gui.

---

### Post by Wednesday2009 on 2009-04-15
:guitar::popcorn:
Thanks a lot for what you've discuss. It's so useful for me
[[color=#FFFFFF]_pret auto_[/color]](http://pret-auto.org)

---

### Post by bobtom115 on 2009-06-18
Hi all, I am a new member of forum :popcorn:


[[color=#FFFFFF]_pret personnel_[/color]](http://simulationpretpersonnel.com)

---

