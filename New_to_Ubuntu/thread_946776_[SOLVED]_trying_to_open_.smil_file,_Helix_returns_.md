---
title: "[SOLVED] trying to open .smil file, Helix returns &amp;quot;missing application/x-pn-realmedia"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Amanda HazLaPaz on 2008-10-13
This is a CarTalk show.[http://www.cartalk.com/Radio/Show/show.smil]("http://www.cartalk.com/Radio/Show/show.smil")

I'd like to listen to it. Mplayer, Movie Player, VLC yield nothing. Totem gave me a screen and a playlist. Firefox let me play the NPR foreword.

Installed Helix, and Helix returned error message "missing application/x-pn-realmedia". Not listed in Synaptic. I'm running 8.04.1. Where in the world would I find it? Or enable it? [174 Google matches]("http://www.google.com/search?hl=en&q=application%2Fx-pn-realmedia&btnG=Google+Search&aq=f&oq=")

[IMG]http://farm4.static.flickr.com/3059/2938667119_e277762280.jpg?v=0[/IMG]

(PS: Also tried the link at work on the Windows machine and it gave me guff over not having the correct version of RealPlayer installed! Didn't try Windows media there.)

---

### Post by NewJack on 2008-10-14
You may need to install RealPlayer. 

Check out this information from the Hardy Wiki:

 > Installing Real Player 11 and Configuring Mozilla Plugin

The following steps show how to install Real Player 11 and Mozilla Plugin for Firefox 3.0 browsers running on Hardy Heron.

Download Real Player 11 from:

  [www.real.com/linux](www.real.com/linux)

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

  chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin
  

Use the following default installation directory during the installation:

  /opt/real/RealPlayer

The installer will copy the files and create menu shortcuts. Then run the following commands.

  cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

Open Firefox and type about:plugins in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

If found, your Real Plugin is installed properly!

Good Luck, hope that helps!

Joe

---

### Post by Amanda HazLaPaz on 2008-10-14
Thank you, installation of RealPlayer was exactly what I needed to play the .smil file!

I appreciate all your help. You're very kind.

---

### Post by NewJack on 2008-10-14
No problem.  That is what the Ubuntu Community is all about!

Joe

---

