---
title: "ruby - require gtk.  will it only work with linux?"
date: 2006-08-26
forum: Programming Talk
---

### Post by pulper on 2006-08-26
hi everyone:

quick question here - maybe stupid but thought i'd ask.

if i use the gtk library in ruby, will that end any cross-platform programing for that program?

i am used to programming in MS Visual Foxpro and do enjoy it.  I've just started programming in Linux and just started within Ubuntu.  Ruby was suggested to me, and I went a bit through the "helloworld" tutorial of the Ruby-Gnome and i liked how it worked for creating a GUI (similar to what I'm used to).

If the GTK library would not work with windows (which i'm assuming), is there a cross-platform library that will work with both windows and linux that creates a GUI in Ruby?

I am new to this so feel free to talk at a low level :-)

Thanks,

Paul

---

### Post by kaamos on 2006-08-26
Hello!

> If the GTK library would not work with windows (which i'm assuming), is there a cross-platform library that will work with both windows and linux that creates a GUI in Ruby?

I have absolutely no experience with ruby but gtk is available for linux, mac(with X11) and windows.

---

### Post by pulper on 2006-08-26
thanks kaamos.  i just assumed it wouldn't but did some looking after your post and found that you are correct.

thanks again,

paul

---

### Post by ifokkema on 2006-08-26
GTK was created for The GIMP, an image manipulation program. Installation of The GIMP in Windows works like this: First, install GTK. Then, install The GIMP. It will be the same for your script. First, install GTK. Then, run your script.

Make sure it checks for GTK first, and let it die nicely if it's not there.

---

### Post by Daverz on 2006-08-26
I'd ask this question on the Ruby-Gnome mailing list.  Beyond the fact that Gtk works well on windows, there are practical issues like distributing code to users who have neither Ruby nor Gtk.  Windows users tend to expect applications to have installers. So you want to get info from people who have acutally done this.

I recommend this distribution of gtk for windows:

[http://gladewin32.sourceforge.net/modules/news/](http://gladewin32.sourceforge.net/modules/news/)

But it all depends on what the Ruby-Gnome folks use; I use this with pygtk.

---

### Post by pulper on 2006-08-27
Thanks Daverz.  This if for programming for our office so i can make sure that they have all the necessary components.  good info on windows gtk - thanks.

paul

---

