---
title: "Skype 4 for linux"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by abduljones on 2012-11-14
Like many, I am having a problem with the new version of skype. Initially, I downloaded it- I think from the skype website, but to be honest, I'm no longer sure, and it was working okay other than the video not working. I searched the forum and tried various suggestions (mainly working around the LD_PRELOAD instruction) which ended up with me unable to launch skype at all, either from its icon or through the terminal. I purged skype and have tried reinstalling from the skype website, from the soft ware centre and from the synaptic package manager, but the program doesn't respond. I've tried trawling through related post to no avail. Nothing has worked, so I need someone now to tell me what you need to know to help me. It's become a matter of principle now!

---

### Post by acimi66 on 2012-11-14
Do you have some more details about which version of linux you are using.

Have you tried using an older version of Skype? 

Let us know

---

### Post by squakie on 2012-11-15
You may want to try these in a terminal window:

sudo apt-get remove skype <press enter> -> this may give an error, if so, just continue

sudo apt-get purge skype <press enter>

Hopefully those will completely remove skype from your system so you can start over.  However, I do have one concern:  other dependencies that were added for what you were trying to install that aren't getting removed just by removing skype.  It's possible some newer version of a library, etc., was installed in that process that must be removed for a new install (hopefully just from either synaptic or the software center) to be successful.

acimi66 asked for some information in their post - I would like to add to that:

- which version of skype you installed and tried prior to getting the newer version, and how (software center, synaptic?)

- a link to the skype you downloaded and tried to install

- the exact steps you've gone through, for example:

installed from software center

wasn't working

removed with software center

downloaded new version xxxxxxxx from xxxxxxxx

installed new version

wasn't working

removed new version via xxxxxxxxxxxx

Well, you get the idea.  It may seem like a lot, but perhaps there is something in what you did that might help us.  In addition, was the problem all along that you could make a call but couldn't use your video?

---

### Post by abduljones on 2012-11-15
Thank you for your prompt replies
I am using ubuntu 12.04 lts
The original skype installation occurred on a skype free system. I originally went to the skype web site to get the download, but I'm not sure if I installed it. The reason I'm not sure is that when, later, I tried installing the Skype website one, the software centre asked me if I wanted to use an older version instead and not to install the software unless I was sure it was okay to do so. I don't remember that happening during the first installation, so it's highly probable I used the version in the software centre first.
   The first installation worked insofar as I could make a call to another computer and could hear the callee. There was no video, however and it was while I was trying various suggestions to get the video working that I lost skype completely. One thing that has occurred to me is that I did have Cheese installed in order to check my webcam was actually working (which it is) and I uninstalled it later in case it was interfering with the skype software. Could something important have been uninstalled when Chees was uninstalled?

   Thereafter, I purged and reinstalled from Skype, Software Centre and synaptic package manager. I've get an icon but it does nothing but flash.
  Anyway I'm just going to try Squakie's command lines and I might try reinstalling Cheese as well and report back


 An hour later... Removed and purged Skype. Reinstalled Cheese, reinstalled Skype 4.008, both from the software centre. No Luck. Also ran gstreamer-poperties and got:

tracey@tracey-HP-Compaq-6720s:~$ gstreamer-properties

(gstreamer-properties:3408): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:3408): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
tracey@tracey-HP-Compaq-6720s:~$ 

   Is any of this relevant? I have tried working out what these are, but can't find much information. Anyway, onwards...

---

### Post by acimi66 on 2012-11-24
Sorry I didn't get back to you. I forgot to add e-mail updates.

As it stands you are not able to get it to work from either the SC or skype download page and you have lost your webcam as well?

I think the webcam is a separate issue.

---

