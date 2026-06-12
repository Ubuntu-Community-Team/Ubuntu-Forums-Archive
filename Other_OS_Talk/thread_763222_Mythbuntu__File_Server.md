---
title: "Mythbuntu / File Server"
date: 2008-04-22
forum: Other OS Talk
---

### Post by afderrick on 2008-04-22
A question for you smart guys, I want to turn my old windows box into a file server.  I was thinking I would put Ubuntu on it and just let it hold files.  Mostly as a backup since I don't fill up my current harddrive even 50%.  The box is sitting in my living room behind the TV currently, so i was thinking about also allowing it to double as a home theater box, like a tivo or something.  So here are my questions:

I was thinking about using Mythbuntu, is this a good choice or is there a more robust easy to use OS out there?

If I run Mythbuntu (or some other linux HTPC OS) will it still work to be used as a file server?  Or should I just allow the box to have 1 main purpose in life?

Quick specs on the box:
Pentium 4 3.0Ghz
2GB RAM
256MB Graphics card (AGP 8X)
Sound Card (not using onboard sound)
CD-R (No DVD burner)
I still need to get the HDTV Tuner card

With the current hardware it ran Ubuntu 7.10 without any problems, I used it for a while before upgrading to my new PC.

---

### Post by gsmanners on 2008-04-22
I prefer straight Ubuntu or Xubuntu to Mythbuntu, but YMMV.

The nice thing about server stuff is that you can just fire them up in the background and they'll keep going even if you have to restart X, so don't worry about that. You should be more worried about how you're going to connect your video to your TV (I like plain old VGA out to the TV).

---

### Post by afderrick on 2008-04-22
Is setting up MythTV in just a regular Ubuntu install easy?  I thought the reason for Mythbuntu was maybe it had a nicer interface or something, not sure.  

Currently I have the PC hooked up via DVI out to HDMI in on the TV.

---

### Post by gsmanners on 2008-04-22
Everything in mythbuntu is also in the "mythbuntu-desktop" meta package in the repos. If you look at its dependencies, you'll see that it's little more than Xubuntu with a lot of mythtv stuff.

I suppose installing mythbuntu probably simplifies the setup a bit, so that may actually be a good way to go.

---

### Post by Calash on 2008-04-23
I converted my Ubuntu/Mythtv setup to Mythbuntu when I upgraded to 7.10.  Really painless, and I prefer the control panel that Mythbuntu has, it simplifies a lot of the configuration.

I have a 2Ghz system that I use for Mythtv, File server via SAMBA and NFS and a basic web server, it gets installed if you pick the Mythweb plugin.  We have 3 computers that actively pull from the file server, and the TV capture never suffers because of it.

---

### Post by afderrick on 2008-04-23
Exactly what I was looking for, appreciate it.  Now to go find a good HDTV tuner card that is easily supported in linux so I don't have extra work.

---

