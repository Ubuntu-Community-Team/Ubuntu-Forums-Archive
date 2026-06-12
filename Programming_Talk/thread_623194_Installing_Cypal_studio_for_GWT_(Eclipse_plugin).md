---
title: "Installing Cypal studio for GWT (Eclipse plugin)"
date: 2007-11-25
forum: Programming Talk
---

### Post by Fireblend on 2007-11-25
Hello, I'm having issues installing the following plugin in Eclipse:

[http://www.cypal.in/studiodocs](http://www.cypal.in/studiodocs)

As I'm trying to learn GWT, this seems pretty interesting, however, I don't seem to be able to install it. I have no idea what Eclipse directory it refers to in the installation howto, which is obviously aimed at Windows users.

When I unzip the contents of the plugin I get the folder with a "features" and "plugins" folders inside, but I have no idea what to do with these, or the main folder. How do I install an Eclipse plugin under Ubuntu? I've tried dropping the folders everywhere, with no avail.

Any help would be greatly appreciated, thanks in advance.

---

### Post by cuscus1986 on 2007-11-27
I happened to stumble across this thread when searching about Eclipse. I hadn't realised that there was a plugin to help with GWT development so I was interested in taking a quick look.

I am assuming that you installed Eclipse using the Ubuntu package manager in the applications menu.

As you said you need to unzip the file and you should have two folders, one called *features* and the other *plugins*. What you want to do is copy the contents of *features* to */usr/lib/eclipse/features* and the contents of *plugins* to */usr/lib/eclipse/plugins*. Then just restart Eclipse if it's already running and head to *Help -> About Eclipse SDK* and click on *Plug-in Details*. In the list that appears you should see an entry for the plugin. The provider is Cypal Solutions if that helps.

If you find that */usr/lib/eclipse* doesn't exist then you will need to do a little more investigation. But don't worry it shouldn't take to long. If you head to *Help -> About Eclipse SDK* and click on *Configuration Details*, you should get a text file inside a window. Look for the line *- launcher* and the line just below that should be where Eclipse is located. If you head to that directory you should find all the folders I mentioned above in the same folder as the launcher.

Hopefully that made sense and my appalling attempts at English grammar haven't thrown you too much. :) If you have any more questions just give me a shout.

---

