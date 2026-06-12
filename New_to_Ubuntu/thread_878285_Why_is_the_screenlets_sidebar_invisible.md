---
title: "Why is the screenlets sidebar invisible?"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Rukaru on 2008-08-02
I got the screenlets sidebar for the newest version of screenlets, which, according to synaptic, I already have. At first I thought it wasn't coming up, but then when I right clicked it showed the menu/options for the bar, so it was obviously there. I really want to give it a skin/theme but any time I've tried, nothing happens. I have tried everything and nothing works.

Also, there are 2 sidebars now, and any time I select "quit this sidebar", it quits all of them. When I restart the sidebar, they are both back.

So yeah....I really don't want invisible sidebars, so any help would be great.

---

### Post by Vadi on 2008-08-02
I don't remember about invisible sidebars, but I believe there is an option to quit just one instance of a screenlet. Something like "delete this screenlet" I think.

---

### Post by Rukaru on 2008-08-02
> **Vadi said:**
> I don't remember about invisible sidebars, but I believe there is an option to quit just one instance of a screenlet. Something like "delete this screenlet" I think.

Yeah it has the option to delete just the one or all of them, but clicking to delete just the one makes them all go.

---

### Post by Vadi on 2008-08-02
Sorry, don't remember then. I got google gadgets in the end and I'm happy :)

---

### Post by Rukaru on 2008-08-02
> **Vadi said:**
> Sorry, don't remember then. I got google gadgets in the end and I'm happy :)


Well I'm not :).  Hopefully someone here knows what to do.

---

### Post by unutbu on 2008-08-02
Perhaps try 

```
gconf-editor
```

I don't use screenlets, so sorry if this is baloney. But from the apt-cache description screenlets looks to be a GNOME app, so it may be configurable through gconf-editor.

---

### Post by Rukaru on 2008-08-02
> **unutbu said:**
> Perhaps try 

```
gconf-editor
```

I don't use screenlets, so sorry if this is baloney. But from the apt-cache description screenlets looks to be a GNOME app, so it may be configurable through gconf-editor.

I'm new with this...what is the gconf editor?

---

### Post by unutbu on 2008-08-02
I'm rather new to gconf-editor too, but I've noticed it sometimes allows the user to configure options that are unavailabe through the apps own preference menu. So I thought it might be helpful here since you probably tried configuring screenlets through whatever normal channels it provides.

Here is the gconf-editors own description of itself:

```
The GNOME Desktop and many applications use GConf to store user preferences and system
configuration data.  GConf provides a central storage location for preferences,
simplifying configuration management for users and system administrators.  More
information about GConf can be found in the GNOME System Administrator's Guide.
```

If you run gconf-editor and then press F1, you'll get a lot more information about how to use gconf-editor.

---

### Post by Vadi on 2008-08-02
Eh... you won't have much luck with it, as it's one big place full of settings. It's not recommended that you tinker with it.

Check out the screenlets forums instead here for help: [http://forum.compiz-fusion.org/forumdisplay.php?f=102](http://forum.compiz-fusion.org/forumdisplay.php?f=102)

---

### Post by donmiguel on 2008-08-24
hey there
i have the exacat same problem, it's so annoying...and i cannot figure out what the problem is...
did you find a solution or such?

greets

```

python /home/don/.screenlets/Sidebar/SidebarScreenlet.pyCachingBackend: Loading instances from cache
Found a running session of Sidebar, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Sidebar was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.don.running
Loading instances in: /home/don/.config/Screenlets/Sidebar/default/
No instance(s) found in session-path, creating new one.
UPDATING SHAPE
LOAD NEW THEME: default
FOUND: /home/don/.screenlets/Sidebar/themes/default
UPDATING SHAPE
UPDATING SHAPE
UPDATING SHAPE
/home/don/.screenlets/Sidebar/SidebarScreenlet.py:727: DeprecationWarning: 
  self.ebox.set_uposition(999999,999999)
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 1460, in expose
    self.on_draw(ctx)
  File "/home/don/.screenlets/Sidebar/SidebarScreenlet.py", line 730, in on_draw
    self.draw_scaled_image(ctx,0,0,self.mypath + 'themes/' + self.theme_name +'/sidebar.png',self.size,gtk.gdk.screen_height())
**AttributeError: 'SidebarScreenlet' object has no attribute 'draw_scaled_image'**
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 1460, in expose
    self.on_draw(ctx)
  File "/home/don/.screenlets/Sidebar/SidebarScreenlet.py", line 730, in on_draw
    self.draw_scaled_image(ctx,0,0,self.mypath + 'themes/' + self.theme_name +'/sidebar.png',self.size,gtk.gdk.screen_height())
**AttributeError: 'SidebarScreenlet' object has no attribute 'draw_scaled_image'**
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 1460, in expose
    self.on_draw(ctx)
  File "/home/don/.screenlets/Sidebar/SidebarScreenlet.py", line 730, in on_draw
    self.draw_scaled_image(ctx,0,0,self.mypath + 'themes/' + self.theme_name +'/sidebar.png',self.size,gtk.gdk.screen_height())
**AttributeError: 'SidebarScreenlet' object has no attribute 'draw_scaled_image'**
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 1460, in expose
    self.on_draw(ctx)
  File "/home/don/.screenlets/Sidebar/SidebarScreenlet.py", line 730, in on_draw
    self.draw_scaled_image(ctx,0,0,self.mypath + 'themes/' + self.theme_name +'/sidebar.png',self.size,gtk.gdk.screen_height())
**AttributeError: 'SidebarScreenlet' object has no attribute 'draw_scaled_image'**
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 1460, in expose
    self.on_draw(ctx)
  File "/home/don/.screenlets/Sidebar/SidebarScreenlet.py", line 730, in on_draw
    self.draw_scaled_image(ctx,0,0,self.mypath + 'themes/' + self.theme_name +'/sidebar.png',self.size,gtk.gdk.screen_height())
**AttributeError: 'SidebarScreenlet' object has no attribute 'draw_scaled_image'**
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 1460, in expose
    self.on_draw(ctx)
  File "/home/don/.screenlets/Sidebar/SidebarScreenlet.py", line 730, in on_draw
    self.draw_scaled_image(ctx,0,0,self.mypath + 'themes/' + self.theme_name +'/sidebar.png',self.size,gtk.gdk.screen_height())
**AttributeError: 'SidebarScreenlet' object has no attribute 'draw_scaled_image'**
CachingBackend: Saving <#Sidebar1> :) ...

```

---

### Post by rekado on 2008-08-28
I've got the very same issue. I added the newest Sidebar screenlet from gnome-look.org as the Sidebar somehow didn't show up in the screenlets manager. When I faced this error I just had a look at "/usr/lib/python2.5/site-packages/screenlets/__init__.py"; the error message is correct and the method "draw_scaled_image" does not exist. Previous versions also didn't use that method; they displayed the Sidebar by using "render" and then did scaling within that method.
Could it be that the Sidebar screenlet is too new / the screenlets base code is too old?



EDIT:
I've had a look at the German ubuntuusers.de forum. They recommend to

1. delete all folders and files in /home/****/.screenlets/
2. install the Screenlets framework 0.1 from source code: [https://code.launchpad.net/screenlets/trunk/0.1](https://code.launchpad.net/screenlets/trunk/0.1)

I'm not at my Ubuntu machine now, but I will try it tonight and report back.

---

### Post by rekado on 2008-08-29
Tested it. Didn't work. Just made some things worse. Maybe I did it wrong... Could somebody else test it and report, please?

---

### Post by Cuttysark on 2008-08-29
I had this exact problem a couple of days ago. The sidebar showed as an option in the Launch Screenlets menu but when I selected it nothing appeared. Right clicking on the extreme right of my screen however, showed the menu you would expect from the sidebar, but regardless of which theme I chose, nothing showed.

I chose Get More Screenlets from the daemon, which took me to the Screenlets.org site, and there clicked on sidebar and chose download. This took me to the sidebar page at gnome-look.org, and I elected to download version 0.6 for screenlets 0.0.9 and higher (I'm running Hardy Heron. After it downloaded, again to the screenlets daemon and chose Install Screenlet and navigated to my downloads folder, and let it do its thing. Sidebar then appeared in the top half of Launch Screenlets and when I chose that, there it was in all its glory.

---

### Post by rekado on 2008-09-16
Yes, downloading an old version does make it visible, but you lose many new features like the horizontal placement. I remember, though, using the newest version with these new positioning options some time ago without the visibility issue.

---

### Post by Nat90 on 2008-10-15
That makes three of us with invisible sidebars

---

