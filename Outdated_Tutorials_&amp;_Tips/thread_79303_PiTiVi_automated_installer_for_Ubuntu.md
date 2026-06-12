---
title: "PiTiVi automated installer for Ubuntu"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by kiddo on 2005-10-19
[:KShttp://open-source.nanokron.info/projets/pitivi/deb/]("http://open-source.nanokron.info/projets/pitivi/deb/")

Greetings all! Tonight, after seeing that [many people]("http://forum.ubuntu-fr.org/viewtopic.php?id=10922&p=1") could not install PiTiVi by themselves, I decided to hack together my very first graphical application. This is a script that downloads the debs from my server (it seems people are already using it anyway), installs them, reloads the gstreamer plugins and starts [PiTiVi]("http://www.pitivi.org") for you.

I hope you like it. I learned a lot by writing this small script. Now, here's the disclaimer, and that might explain "why PiTiVi is not included in Breezy IMHO":[LIST]
[*]at the moment I am writing this, we are in PiTiVi 0.1.10. This version is not yet ready for production. A beta is projected to be released before november (I'm really awaiting that... and you can bet I'll try to backport GStreamer0.9 myself if no one does!)
[*]even though you might think that development is currently slow, that is because Bilboed is hacking on GST-Python and GNonlin behind the scenes. He has to do all this background work before advancing further into PiTiVi.[/LIST]Please report any bugs (related to my script) if any, either by email, or try catching me on #pitivi or #specto on irc.freenode.net

---

### Post by kiddo on 2005-10-20
First bugfix, the gst-register command was wrong it seems. The script has been updated on the repository, I'm awaiting some more reports if it works now.

---

### Post by kiddo on 2005-11-24
Another bug fix, thanks to isaric (who disappeared shortly after on IRC?), I think it should work better now... But I'd need people to confirm that.

Take note, however, that we are close to a beta release, and this is mostly just for testing out my script and for fun. PiTiVi 0.1.10 is soon to be deprecated and does not show its "true potential".

---

