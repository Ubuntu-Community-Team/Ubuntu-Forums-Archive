---
title: "Graphically manage files on headless server?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-09-22
Is there a way to remotely, graphically manipulate the files on my headless ubuntu server?  I have a bunch of files to transfer to it, but my home network is way to slow, and I don't want to tie up my laptop.  I have the drive hooked up to the router, but I am not comfortable enough with the CLI to feel comfortable that I won't wind up deleting these important files.  

I use gftp to transfer files from my laptop to my server and visa versa.  Is there a similar graphical program that I can use to manipulate the filesystem on the server?  I don't have a monitor I can hook up to it, and I would rather not install a DE just for this anyway.  I am thinking something like an SSH file manager or something.

Thanks

JTS

---

### Post by Whiffle on 2008-09-22
If you've got ssh running on the server, you can connect to it via ssh by using the "Connect to Server" option on the Places menu.  Select SSH from the dropdown menu and fill in your info and you're on your way.

---

### Post by willca on 2008-09-23
If you are logged in on that headless box. Check first if ssh is running and you can connect to it.

simply at the shell session

$ ssh localhost

If this prompts you for a login then its there to serve.

So I assume you are on a windows box and want to login remotely?
If so, I will google for winscp and use that.

I hope you are on an Ubuntu linux box instead :)
Then do it this way without the gui since I never really used one or had a need for it.

$ scp -r username@remotemachine:/some/directory/to/grab/files/from /some/directory/locally/to/save/files/to

The -r will just pull all the files in that directory you specify as source.

Now in case you dont want to grab all the files, say just all the files ending in ".log" or ".html".

$ scp -r [email]username@remotemachine:/some/directory/to/grab/files/from/*.html[/email]  /some/directory/locally/to/save/files/to
I hope this helps.

---

### Post by jimmy the saint on 2008-09-23
I actually run xubuntu on my laptop, so the nautilus network freature was not available.  I set up my old tower with Ubuntu on it to try it out.  The problem I have with nautilus doing it is that it seems to route all the files over the network, even though it is copying them from one drive to another on the same machine!!  This is making an otherwise quick process extrememly slow.  I guess I am stuck with the CLI.

---

### Post by Whiffle on 2008-09-23
Give midnight commander a shot ( mc ).  Go to the "Right" or "Left" menu, click "Shell link...", type in   user@machine , and go.  F5 copies.

---

