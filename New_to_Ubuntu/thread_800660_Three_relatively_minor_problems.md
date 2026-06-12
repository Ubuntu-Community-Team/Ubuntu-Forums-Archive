---
title: "Three relatively minor problems"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Mr. Svinlesha on 2008-05-20
1) I can't get Gnome Art to work.  When I try to launch it, it pops up for a flash of second and then disappears.  I've tried to reinstall via Synaptic, but that hasn't helped.

2) When I launch update-manager from the terminal, I get the following error message: *current dist not found in meta-release file*. (Update manager launches and appears to work normally.) I've tried several solutions to this (see this [page]("http://ubuntuforums.org/showthread.php?t=784138&page=3") and following discussion) but nothing has helped so far.  I don't know how serious this problem is, really, but still -- it's something that isn't working right.  

3) I have a folder in my trash can that I can't delete (wesnoth 1.4).  When I try to delete it I get the following error message: 
> [I]There was an error deleting ABOUT-NLS.

Error removing file: Permission denied.[/I] Followed by the same error message for every file contained in the folder.

Thanks in advance for help, advice, etc.

---

### Post by zvacet on 2008-05-20
To delete files from Trash you can try this (if you are using Hardy)

```
cd .local/share/Trash/files
```

one you are inside you can delete files with 

```
sudo rm -r file_name
```

---

### Post by Mr. Svinlesha on 2008-05-20
Great, thanks **zvacet**!  That worked.

One down, two to go.

Regarding Gnome Art: I could use synaptic to remove it entirely, and then try reinstalling it: I just haven't tried that because I'm afraid I might delete some important dependency or whatnot.

Should I try it?

---

### Post by forestpixie on 2008-05-20
If you do an apt-get remove it won't remove dependencies

```
sudo apt-get remove gnome-art &&sudo apt-get install gnome-art
```

or 

```
sudo apt-get install --reinstall
```

---

### Post by Mr. Svinlesha on 2008-05-20
Thanks, **forestpixie**.  I tried both your suggestions but neither one worked.

---

### Post by forestpixie on 2008-05-20
what didn't work?

---

### Post by Zularan on 2008-05-20
With the GnomeArt opening and closing straight away, one way to help diagnose the issue is to launch it from a terminal, as it flashes up and closes it may output an error or something that might be helpful.

I dont have it installed but I'd assume it's something like:
```
$ gnome-art
``` from the console.

---

### Post by Mr. Svinlesha on 2008-05-20
Like this?
> [I]/usr/lib/ruby/1.8/net/protocol.rb:133:in `sysread': Connection reset by peer (Errno::ECONNRESET)
	from /usr/lib/ruby/1.8/net/protocol.rb:133:in `rbuf_fill'
	from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/lib/ruby/1.8/net/protocol.rb:132:in `rbuf_fill'
	from /usr/lib/ruby/1.8/net/protocol.rb:116:in `readuntil'
	from /usr/lib/ruby/1.8/net/protocol.rb:126:in `readline'
	from /usr/lib/ruby/1.8/net/http.rb:2020:in `read_status_line'
	from /usr/lib/ruby/1.8/net/http.rb:2009:in `read_new'
	 ... 10 levels...
	from /usr/lib/ruby/1.8/open-uri.rb:30:in `open'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:156:in `isConnected'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
	from /usr/bin/gnome-art:25[/I]

---

### Post by Zularan on 2008-05-20
That's the way, sometimes the errors more obvious but I'm afraid I don't know enough to know what the actual problem is from there.  

Did you try reinstalling gnome-art as per forestpixie's post?

---

### Post by forestpixie on 2008-05-20
Try to purge it before you reinstall - also check in your home for a hidden folder, if there is one delete it, then reinstall

```
sudo apt-get remove --purge gnome-art
```

---

### Post by Mr. Svinlesha on 2008-05-20
I've purged, removed the gnome-art subfolder in the .gnome folder, and reinstalled.

Problem still remains.

---

### Post by dean20007 on 2008-05-20
Hi 

It looks like this is a bug that should be fixed in gnome-art_0.2.9

[https://bugs.launchpad.net/ubuntu/+source/gnome-art/+bug/228552]("https://bugs.launchpad.net/ubuntu/+source/gnome-art/+bug/228552")

I tried to grab the latest one out off the debian pool and the application launched...but I couldn't download anything due to another error

---

### Post by Mr. Svinlesha on 2008-05-20
Okay. So, gnome-art is bug, and my recalcitrant folder is now gone from the trashcan.

Can anybody help me with problem number three?  Or is it something I even need to worry about?

---

### Post by forestpixie on 2008-05-20
You can do it from the command line - but can't remember how or use nautilus as root

```
gksudo nautilus
```

Do Ctrl+H to view hidden files and navigate to /home/username/.local/share/Trash

and the file should be there - empty trash as root and it should go

---

### Post by Mr. Svinlesha on 2008-05-20
Ooops, sorry.  I need to be a bit more precise.  The problem with the trash is solved.

The only unsolved mystery is the *current dist not found in meta-release file* error message that I get when I launch update-manager from the terminal.  **Thingymebob** and I tried several different solutions to problem a couple of days ago without success.

---

### Post by forestpixie on 2008-05-20
Sorry - can't help with that - glad rest is sorted for you.

Good luck

---

### Post by noynac on 2008-05-20
> **Mr. Svinlesha said:**
> Ooops, sorry.  I need to be a bit more precise.  The problem with the trash is solved.

The only unsolved mystery is the *current dist not found in meta-release file* error message that I get when I launch update-manager from the terminal.  **Thingymebob** and I tried several different solutions to problem a couple of days ago without success.

Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=800968&highlight=update+manager](http://ubuntuforums.org/showthread.php?t=800968&highlight=update+manager)

...and this bug report:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/174266](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/174266)

---

### Post by Mr. Svinlesha on 2008-05-20
Thanks **noynac**.

Can't really mark this as solved, but at least it's answered for my part.

---

