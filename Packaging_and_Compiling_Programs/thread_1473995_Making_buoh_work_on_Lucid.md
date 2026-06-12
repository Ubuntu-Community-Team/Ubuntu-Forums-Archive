---
title: "Making buoh work on Lucid"
date: 2010-05-05
forum: Packaging and Compiling Programs
---

### Post by warnec on 2010-05-05
Hi there. I searched for a nice comic reader for my Ubuntu 10.04, and I were sorry to find no good programs/applets for GNOME to read my favorite "Ctrl+Alt+Del" comic. I saw a nice project called buoh:

[https://launchpad.net/buoh](https://launchpad.net/buoh)

Pity it doesn't seem to be maintained anymore, though. (No packages for newer ubuntu versions)

But I thought: "Hey! Where's your Linux spirit? Do it yourself!"
and even though I completely cannot code, guess what? I made it to work ;)

Full story:

First I tried to download the .deb for older Ubuntus from Launchpad and force it to install. It ran, but when loading a comic crashed because it called a function in now-obsolete libsoup 2.2. Now in the repos we have 2.4, and I had completely no idea how to write a patch to make it work with that :(
Fortunately, Google came to help :

[https://partner-bugzilla.redhat.com/show_bug.cgi?id=430943](https://partner-bugzilla.redhat.com/show_bug.cgi?id=430943)

**(BTW, isn't that weird that an app's source is patched to work nicely and it still isn't packaged for new distros?)**

Well, even after applying the patch, I still couldn't get it to build:

```

checking for BUOH... configure: error: Package requirements (glib-2.0       >= 2.6.0
		  gtk+-2.0       >= 2.6.0
		  libsoup-2.2    >= 2.2.0
		  gconf-2.0      >= 2.2.0) were not met:

No package 'libsoup-2.2' found

```
What You need to do, is to open up "configure" file from buoh's root folder in Gedit, and tell the program to replace every instance of "libsoup-2.2" to "libsoup-2.4". Then it'll work. I wanted to append this fix to an existing patch or at least create a second one, but I suck at this, unfortunately.

And one last fix to make CAD comics work. In /buoh/data folder, edit "comics.xml" so that it looks like this on the 1069th line:
```

generic_uri="http://www.cad-comic.com/comics/cad/%Y%m%d.jpg"

```
[U][CENTER]
And I have my Ctrl+Alt+Del comics back! (I use KDE before w/Comic Plasma widget) 

YAY![/CENTER][/U]

Ok, but why am I telling this to You guys? Why the whole procedure? 

Well, it is simple. I would be very glad to see someone package it for Lucid and make a repo for it. Now that all the patches and info available exist, it can't be hard. I just suck at it and have no idea how to set a repo up on my own.

So, can You help? ;) It has been to long since such a fine piece of software like buoh lies unmaintained and (almost) unusable for new users.

PS.: And of course You need respective "-dev" packages for all dependencies buoh lists! At first, I had completely no idea why it fails... ;)

PPS.: One idea I thought about now - what do You think about writing a patch so that buoh can appear under, say, Programs->Internet? Right now you can't open it through the menu, only Alt+F2 or Terminal...

---

### Post by metallus on 2010-05-12
ok, but how do I add new comics?
for example I want xckd.com or smbc-comics.com or other new comics?

---

### Post by drbin on 2010-05-24
I second that. Please make BUOH available. Its the ONLY application with such -as- functionality.

---

