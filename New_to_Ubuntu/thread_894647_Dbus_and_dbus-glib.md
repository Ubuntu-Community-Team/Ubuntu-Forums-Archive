---
title: "Dbus and dbus-glib?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by theragingking on 2008-08-19
Hey all,

I've been trying to install audacious 1.5.1 ingutsy. I got the main package installed after some serious dependency wrassling, but I can't seem to get the audacious-plugins package installed. I went ahead and build-dep'd the audacious-plugins dependencies, but now when i go to compile from source (ala [http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually) ) I'm told that a package called dbus-glib, version .60 or higher is required. I go ahead and download .76 to compile from source, but *then I get an error that says:

```
checking for DBUS... no
configure: error: DBus development libraries not found
```

But upon checking, a package titled "dbus" is in fact installed.

What do I do to fix this?

TRK~!

---

### Post by mali2297 on 2008-08-19
Install **libdbus-glib-1-dev** from Synaptic instead of compiling. (It's version 0.74 in Gutsy.)

---

### Post by angryfirelord on 2008-08-19
I wouldn't recommend upgrading D-Bus. It's going to open a can of worms because it probably doesn't have any Ubuntu specifics added to it. I would just do the usual **sudo apt-get install audacious audacious-plugins** and save yourself the headache.

If you need Audacious 1.5 for some reason, I would just upgrade to Hardy.

---

