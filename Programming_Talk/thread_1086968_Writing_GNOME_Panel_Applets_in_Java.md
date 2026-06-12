---
title: "Writing GNOME Panel Applets in Java"
date: 2009-03-04
forum: Programming Talk
---

### Post by C-- on 2009-03-04
Hello everyone. I understand that the java-gnome bindings allow for writing GTK+ applications in Java instead of C. However, I can't seem to find any information on a Java binding for the GNOME Panel Applet library. Specifically, I cannot find any Java methods that allow for calls to modify a panel applet object, or that call the PANEL_APPLET_BONOBO_FACTORY function to actually build an applet and place it in the gnome panel. Does anyone know if this functionality exists, or if it is a part of the java-gnome bindings? Or, will I need to develop the applet in C?

---

### Post by cabalas on 2009-03-04
I would avoid the bonobo if I were as I'm pretty sure it has been deprecated (if it hasn't it's on the books to happen soon) it may be of more use to look into D-Bus which does have java bindings (api: [http://dbus.freedesktop.org/doc/dbus-java/](http://dbus.freedesktop.org/doc/dbus-java/)) another option if you find you can't use java to do what you want is python they have a tutorial at [http://pygtk.org/articles/applets_arturogf/](http://pygtk.org/articles/applets_arturogf/) (though it does still use bonobo I couldn't find one that uses D-Bus) and could be worth looking into.

---

### Post by C-- on 2009-03-04
> **cabalas said:**
> I would avoid the bonobo if I were as I'm pretty sure it has been deprecated (if it hasn't it's on the books to happen soon) it may be of more use to look into D-Bus which does have java bindings (api: [http://dbus.freedesktop.org/doc/dbus-java/](http://dbus.freedesktop.org/doc/dbus-java/)) another option if you find you can't use java to do what you want is python they have a tutorial at [http://pygtk.org/articles/applets_arturogf/](http://pygtk.org/articles/applets_arturogf/) (though it does still use bonobo I couldn't find one that uses D-Bus) and could be worth looking into.


Thanks for your suggestion. Is there a way to get the gnome panel to use D-Bus instead of Bonobo, or are they interchangeable?  Unfortunately, I have to develop the applet in Java because it needs to interact with another program that is written in Java.

---

### Post by cabalas on 2009-03-04
To be honest I'm not sure if they are interchangeable (as I've never dabbled with bonobo) but it's what the GNOME guys suggest to use instead so I would assume that largely it should be for what you want to do. Seeing as D-Bus is an IPC system, if you integrated it into your java app it could free you up to write the applet in a different language and just use D-Bus to communicate between the two.

---

### Post by C-- on 2009-03-05
> **cabalas said:**
> To be honest I'm not sure if they are interchangeable (as I've never dabbled with bonobo) but it's what the GNOME guys suggest to use instead so I would assume that largely it should be for what you want to do. Seeing as D-Bus is an IPC system, if you integrated it into your java app it could free you up to write the applet in a different language and just use D-Bus to communicate between the two.

Thanks again for all of you help so far. 

Unfortunately I don't think I'd be able to integrate DBus into the Java application and then have the applet connect to it, as the application has already been written by other people and I don't have access to the raw source. The way it's set up now is I have to use a Java class that notifies you when you have updated information, and then pull that information from the class. As long as I can write the applet in Java, I'm ok.

Therefore, all the DBus code I would have to deal with would not be between the applet and the application, but between the applet and the gnome panel.

Now, Java bindings do exist for libgtk, but not for libpanelapplet (which uses Bonobo through the PANEL_APPLET_BONOBO_FACTORY function). I can write a gtk application in Java, but I cannot put it into a gnome applet from what I have been able to find. I could be wrong. 

Because of this, and because Bonobo is being replaced by DBus, I now need to figure out how to put a panel applet in the panel with DBus.

In the Java bindings for DBus, I can't seem to find any documentation or tutorials that specifically point out how to how to put an applet in the panel. All indication points to that this is the case, that DBus *has* to be used to put an applet in the panel now, but again I cannot find any documentation on this matter. Once I can do it with DBus Java bindings, I'll have no problem talking with the application.

---

### Post by C-- on 2009-03-05
See this is what I'm talking about.

[http://lists.freedesktop.org/archives/dbus/2006-January/003961.html](http://lists.freedesktop.org/archives/dbus/2006-January/003961.html)


In this transcript about porting gnome applets to DBus:

> yes, I know, I think it's important to keep the compatibility. Although
porting an applet to dbus is really easy, having a migration period will
make the process less painful. 
I've been working on that for a while and I think I've found a good way
to keep the compatibility with bonobo applets. I'll send an updated
patch as soon as I have something.  


And this text is over 3 years old! So it's obviously possible but there's no documentation on it that I can find at all.

---

