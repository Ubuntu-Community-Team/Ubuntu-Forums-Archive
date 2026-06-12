---
title: "[SOLVED] using nautilus to browse ssh share"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-07-21
I recently been trying out some other de or wm's and I'm now using fluxbox.

I always connected to my ssh servers using ubuntu's "connect to server" script in "places".

I can't access it in fluxbox.

I thought that it would be as easy as doing

ssh://username@server/ in nautilus but this doesn't seem to be the case (in kde fish://username@server/ in konqueror worked fine).

Nautilus keeps saying "couldn't find /home/rw/ssh://... ".

I'm sure I'm missing something, but what?

---

### Post by billgoldberg on 2008-07-21
In nautilus when I go to "file -> connect to server" There isn't a drop down menu of protocols to choose.

Just "custom location".

It was working fine in gnome.

Is this fluxbox related or is something else going on?

When I enter "ssh://rw@192.168.1.3/" or "sftp://rw@192.168.1.3/" or "ssh://rw@192.168.1.3 /home." , ...

It just says "nautilus doesn't know how to handle ssh" (or sftp).

--

I just installed konqueror again (and all the packages that come with ti :( )  and the fish://rw@192.168.1.3/ still works. So the server is running fine on the other computer.

It goes without saying that I don't want konqueror and all of the mess that comes with in on my pc, I try to keep things as light as possible.

I would use thunar, but it doesn't do ssh.

If anyone knows a light-weight file manager that handles ssh. Please tell so.

---

### Post by billgoldberg on 2008-07-22
I'm going to have to bump this one as I need ssh in nautilus to work.

---

### Post by jordanmthomas on 2008-07-22
It's a problem likely related to gnome-vfs and there being no gnome-session running.
As a temporary workaround, you could mount your ssh share using sshfs and browse using nautilus that way.

Unfortunately I don't know of a way to make it work as expected at the moment, and I can confirm the same behavior with openbox.

---

### Post by billgoldberg on 2008-07-22
> **jordanmthomas said:**
> It's a problem likely related to gnome-vfs and there being no gnome-session running.
As a temporary workaround, you could mount your ssh share using sshfs and browse using nautilus that way.

Unfortunately I don't know of a way to make it work as expected at the moment, and I can confirm the same behavior with openbox.

That was what I was thinking.

Too bad.

I knew about sshfs but just using the nautilus "connect to server" script is easier.

Oh well, you can't have it all.

Just asking again, are there any other file managers that can handle ssh (not konqueror)?

---

### Post by hyper_ch on 2008-07-22
why is nautilus connect to server scritp easier?

---

### Post by tact on 2008-07-22
> **billgoldberg said:**
> I'm going to have to bump this one as I need ssh in nautilus to work.

Works fine here...   ubuntu 8.04.1 fully updated.  

Just typed ssh://ip.addr.of.box

Was presented with a nice little dialog box telling me that the box I am connecting to is unknown to me and asking whether to connect anyway.

When I clicked connect... another dialog for username/password...  once entered up popped a nautilus window with all the files/folders in "/" on the remote box (just happened to be a solaris box).

To confirm some of the other experiences... if I typed "ssh://machine_name" I got the same "cannot connect because the box was found" message that others have mentioned.  Of course it means "was NOT found"...  

I believe that after the FIRST connection (after keys/certs have been exchanged) then you can use the "ssh://username@ip.addr.ess/share" format.

Just gotta know how to use the tools.

Cheers

---

### Post by billgoldberg on 2008-07-22
> **tact said:**
> Works fine here...   ubuntu 8.04.1 fully updated.  

Just typed ssh://ip.addr.of.box

Was presented with a nice little dialog box telling me that the box I am connecting to is unknown to me and asking whether to connect anyway.

When I clicked connect... another dialog for username/password...  once entered up popped a nautilus window with all the files/folders in "/" on the remote box (just happened to be a solaris box).

To confirm some of the other experiences... if I typed "ssh://machine_name" I got the same "cannot connect because the box was found" message that others have mentioned.  Of course it means "was NOT found"...  

I believe that after the FIRST connection (after keys/certs have been exchanged) then you can use the "ssh://username@ip.addr.ess/share" format.

Just gotta know how to use the tools.

Cheers

Thanks, but I got nautilus ssh working fine in Ubuntu. It's because I'm using fluxbox that it isn't working as expected.

---

### Post by billgoldberg on 2008-07-22
> **hyper_ch said:**
> why is nautilus connect to server scritp easier?

There I just type ssh://rw@192.168.1.3/ to connect.

With sshfs, I have to install fuse and some other stuff and add it so it start on boot.

---

### Post by tact on 2008-07-22
> **billgoldberg said:**
> Thanks, but I got nautilus ssh working fine in Ubuntu. It's because I'm using fluxbox that it isn't working as expected.

Ok...   Sorry didn't pick up on that.    Out of my depth now but.... isn't nautilus, nautilus?   I can ssh even from nautilus running on OpenSolaris.  ??

Cheers

---

### Post by billgoldberg on 2008-07-22
> **tact said:**
> Ok...   Sorry didn't pick up on that.    Out of my depth now but.... isn't nautilus, nautilus?   I can ssh even from nautilus running on OpenSolaris.  ??

Cheers

No.

I believe I can't use ssh and smb because gnome-vfs isn't loaded and nautilus uses that to access ssh and smb shares.

It still works fine using gnome, but I find myself using fluxbox all the time now. 

It's more fun.

--

I marked it as solved. Well actually nautilus still can't do it on fluxbox, but I'm just using the terminal to browse the ssh share.

---

### Post by hyper_ch on 2008-07-22
> **billgoldberg said:**
> With sshfs, I have to install fuse and some other stuff and add it so it start on boot.

I think sshfs is almost as simple ... only "difficulty" in my opinion is finding out the uid and gid.

Anyway, good you solved it ;)

---

