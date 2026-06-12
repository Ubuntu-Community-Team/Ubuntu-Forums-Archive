---
title: "I've downloaded Floola - now what?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Beatbreaker on 2008-06-08
I've downloaded Floola, it seems to work - but where should i copy this (maybe bin) file?

should i put it in .local/share/applications/ ??

will that allow me to access it as i need if i use the terminal or a shortcut icon? - by simply using the command "floola"?

[http://www.floola.com/modules/wiwimod/index.php?page=download](http://www.floola.com/modules/wiwimod/index.php?page=download)

---

### Post by kostkon on 2008-06-08
Put it in */usr/bin* and then you will be able to call by just giving *Floola*.

---

### Post by brian_p on 2008-06-08
> **Beatbreaker said:**
> I've downloaded Floola, it seems to work - but where should i copy this (maybe bin) file?

should i put it in .local/share/applications/ ??

will that allow me to access it as i need if i use the terminal or a shortcut icon? - by simply using the command "floola"?

[http://www.floola.com/modules/wiwimod/index.php?page=download](http://www.floola.com/modules/wiwimod/index.php?page=download)

If you only want it to be available only to you a directory in $HOME is fine. $HOME/bin. $HOME/floola. Something like that.

To be available to everyone /usr/local/bin is the place, not /usr/bin. That's for system files.

---

### Post by propwashz on 2008-06-08
floola should be installed on your iPod ,from what I could see in their documentation...
it also needs some libs installed in linux to use it...
check here--
[http://www.floola.com/modules/wiwimod/index.php?page=docs]("http://www.floola.com/modules/wiwimod/index.php?page=docs")

---

### Post by Beatbreaker on 2008-06-08
Many thanks, i'm yet to test it but i'm sure it'll be fine.

I've used Floola in XP before and really like it, i think it's got some really good tagging options too.

I'll repost if any problems come up

Cheers

---

### Post by Eclipse. on 2008-06-08
From their website:

> 
[COLOR=red]**Make sure your iPod is mounted with read AND write access.**[/COLOR] 

To enable playback you'll need either *gstreamer* or *lib xine* to be installed. If both are installed *gstreamer* will be used.
Floola relies on libstdc++5.  To install it (under Ubuntu) type *sudo apt-get install libstdc++5* via terminal.
To start Floola, just double click on application icon or from console type *./Floola*

---

