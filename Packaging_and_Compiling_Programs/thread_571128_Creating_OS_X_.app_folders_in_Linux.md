---
title: "Creating OS X .app folders in Linux?"
date: 2007-10-08
forum: Packaging and Compiling Programs
---

### Post by Cheiron on 2007-10-08
I'm working on a cross-platform game and am hoping to create an OS X port of it. I don't have access to a mac, and so am unable to use the xcode tool for creating .app folders. Are there any tools for creating .app folders on other operating systems? I'd prefer Linux, but can also use windows if required.

Thanks

---

### Post by kidders on 2007-10-10
Hi there,

You may well know this already (if so, I'm sorry), but you don't need any special apps to create a basic Mac application bundle ... assuming, that is, you have figured out how to make your system cross-compile your binaries/libraries/etc.

Application bundles are a bit like JAR archives, in that they have a predefined internal structure ... they're just not compressed. Creating them manually *can* get a little tedious though, if you have to make a lot of them, or you're localising your application. Technically, all you really need to make one is "mkdir" and a text editor. Details like file associations, and so on, are all described using XML.

Is this all old news to you?

---

### Post by 3rdalbum on 2007-10-10
For the first iteration of your game, why not just use an archive that the user will just have to decompress into their home directory? You don't actually need to use an OS X package, and you'll have a quick way of getting your application out there for testing rather than having to fiddle around with getting the packaging format correct.

---

### Post by Auria on 2007-10-10
So i think, the question boils down to : Have you suceeded in building mac binaries and you're only lost as to how to make the bundle, or were you asking how to make mac binaries on linux?

If it's th former, you may be interested by the way i did it for Supertux [http://supertux.lethargik.org/wiki/User:RavuAlHemio/Mac_OS_X_compilation#Building_an_app_bundle](http://supertux.lethargik.org/wiki/User:RavuAlHemio/Mac_OS_X_compilation#Building_an_app_bundle) It's simply a few mkdirs and copying a XML file, icon file is not mandatory.

I think the real challenge here is finding how to cross-compile it. If your game links against libraries, e.g. SDL, linking it in properly will be more difficult.
On OS X, there is 2 ways of building (dynamic) libraries : frameworks and dylibs. Frameworks can be placed inside the app bundle in /Contents/Frameworks, but dylibs are much more difficult.

And if you don't know at all how to corss-compile... i know neither :(

---

### Post by Cheiron on 2007-10-13
Auria

Thanks for the link!. Our game is written in Ruby, so we don't need to compile anything. We've got a tarball out but we're just looking to distribute it nicely.

Does anyone know if there are ruby-gtk bindings that we can include with our package?

---

### Post by Auria on 2007-10-13
> **Cheiron said:**
> 
Does anyone know if there are ruby-gtk bindings that we can include with our package?

Ouch, i guess you know quite little about OS X :)

GTK does not run very well on OS X atm.
There are 2 versions : one using X11.app, a "fake" (and very crappy) X11 server by Apple. It's not very nice, and there's also no binary distribution available. Installation involves compilling stuff from source and installing the X11 server (it's not there by default). If you were on mac you could compile the sources yourself and included the binaries inside your app, but forget about cross-compilling that.
The second version is a native one, but it's still alpha. No binary either.

So, to make a distributable binary on OS X you'd need someone rather knowledgeable, i think you can forget about cross-compilation! (at least for now, in the future there may be GTK installers available when the native version gets stable)

---

