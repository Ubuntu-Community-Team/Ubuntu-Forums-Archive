---
title: "How to run gnome art??"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by friendofpugs on 2008-05-08
Hi all!

Last night I downloaded and installed gnome-art (per the Ubuntu for non-geeks book) and I was able to install a new desktop background, window themes, start screen, etc. However, when I go to run Art Manager today, it does nothing. The cursor spins a disc and does nothing. So I checked the properties of the icon, to see what action/executable it runs, and I get "gnome-art" which obviously does nothing. I searched my files for gnome-art and came up with a handful of folders/icons. I just want to run the program again to get a new background image. Help!

Thanks for taking it easy on this noob! :confused:

---

### Post by LeoSolaris on 2008-05-09
I read your post, then went to gnome art to test it out. I got the same thing.

When I put it into the terminal I got this error message:

```
12:59:15 on Fri May 09 - leo:~$gnome-art
/usr/lib/ruby/1.8/net/protocol.rb:133:in `sysread': Connection reset by peer (Errno::ECONNRESET)
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
    from /usr/bin/gnome-art:25

```

From  the looks of things, art.gnome.org is stopping it, not anything Ubuntu is doing.

For now, just head over to art.gnome.org or gnome-look.org and pick them up manually. You can install them by dragging them onto the appropriate window most of the time. and if not, just find the install button.

---

### Post by RedMartin on 2008-05-22
A little late but I can't get Art Manager to do anything either. I also can't find any explanations as to why.

---

### Post by alsh0083 on 2008-05-24
[http://developer.berlios.de/projects/gnomeartng/](http://developer.berlios.de/projects/gnomeartng/)

I use this since the one in repositories doesn't work.

---

### Post by Tuxoid on 2008-05-25
It stopped working for me too. There's a bug in launchpad. I'd suggest subscribing to the bug to check how the status is updating:

[https://bugs.launchpad.net/ubuntu/+source/ruby-gnome2/+bug/230082](https://bugs.launchpad.net/ubuntu/+source/ruby-gnome2/+bug/230082)

It's marked as a bug for 64-bit x86, but I have reported the same problem on my 32 x86 processor.

---

