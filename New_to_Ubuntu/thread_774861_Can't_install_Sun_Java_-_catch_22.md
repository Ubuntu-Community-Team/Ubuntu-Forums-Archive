---
title: "Can't install Sun Java - catch 22"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by dvdivx on 2008-04-29
Want to install Sun Java Runtime. Two files are needed but neither will install since they are dependent on each other. Install is for 32 bit 8.04.

sun-java6-bin_6-06-0ubuntu1_i386.deb
sun-java6-jre_6-06-0ubuntu1_all.deb

Those are the needed files from what I can tell from packages.ubuntu.com. Neither will install through Synaptic Package Manager as both list the other one as a dependency.

---

### Post by Sef on 2008-04-29
Are you using a 32-bit or 64-bit system?

If you are using the 32-bit system, then go to Applications > Add/Remove and in search type "Sun Java 6" (without the quotes) and click on the top one.

If you are using 64-bit system, then go to Applications > Add/Remove and in search type "OpenJdk" (without the quotes) and click on Openjdk.

---

### Post by Tatty on 2008-04-29
Go to Applications->Add/Remove then search for "java runtime"

---

### Post by gandaran on 2008-04-29
on add/remove, also select the sun java6 plugin for install, if you don't see these options on add/remove, you must enable the repositories first and then on add/remove select all applications available.

---

### Post by kansasnoob on 2008-04-29
Hmmm, I'm scratching my head. I don't know if sun-java6 is available without medibuntu or not. Anyway, what I do is this:

Install the medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Note: remember to add the GPG Key!

When done I close the terminal and open the Synaptic Package Manager, then I click on "Settings>Repositories". Under the "Ubuntu Software" tab "main", "universe", "restricted", and "multiverse" should all be ticked.

Now click on the "Third party Software" tab. There you want the "Hardy Partner", and the "Medibuntu .. /Hardy free/nonfree ticked. IMPORTANT NOTE: YOU DO NOT WANT THE "SOURCE CODE" BOXES TICKED IF YOUR A NOOB LIKE ME!

Everything else there should be fine unless you want to click on the Statistical tab and tick that box, that just lets Ubuntu know what's being used the most, but don't worry about it.

So click on close.

Now, in the upper left hand corner of Synaptic you'll see a Reload button. Click on it and wait. When it's done running you can see if there are any upgrades available.

When you're all done with that you can just click on "Search" and type in: sun-java6

I install all sun-java6 but sun-java6-doc and sun-java6-source. *doc just wastes space and *source can break stuff!

Then while I'm there I install lots of stuff, but everyones list is different.

I install all "gstreamer", and I mean ALL, the good, bad, and ugly!
Then "totem", "totem-gstreamer" & "totem-mozilla". (Also totem-xine")

Then ALL "vlc".

Then "flashplugin-nonfree".

Then "acroread", which is Adobe reader.

And finally ............ "non-free-codecs".

Then I have a fully functional desktop for my purposes.

It's all easy using the search tool in synaptic and you can select whatever seems right and then just click install and grab a snack and a glass of moo-juice. Just be a bit careful, crack open a note pad and have fun.

---

### Post by dvdivx on 2008-04-29
I was hoping to get an offline installer since I can't get the wireless card working yet. There doesn't appear to be an offline installer for it that works.

---

### Post by gandaran on 2008-04-30
> **dvdivx said:**
> I was hoping to get an offline installer since I can't get the wireless card working yet. There doesn't appear to be an offline installer for it that works.

yes you can install offline, but you must get all dependencies packages

sun-java6-plugin
sun-java6-jre
sun-java6-bin
java-common 

test them so you can find out which installs first. 

you can also install by downloading the linux java package from the sun site,I don't recommend this, as you won't be able to uninstall later and doesn't include a plugin.

---

