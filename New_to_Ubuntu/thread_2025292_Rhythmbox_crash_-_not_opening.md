---
title: "Rhythmbox crash - not opening"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by lladnar on 2012-07-14
Hi

I have tried a number of different threads and web options and finally will need some much needed help.  

Rhythmbox was working perfectly!  I wanted to install a plugin to allow me to love/block lastfm radio songs.  So installed asermax/lastfm_extension.  When I went to click it to get it to work, Rhythmbox froze and now will refuse to open.

So far:
I have uninstalled rhythmbox using the terminal and Ubuntu software center
I have reinstall (at different times) rhythmbox via terminal and Ubuntu software center (logging out and in again each time)
I have tried to locate the lastfm_extension and delete it  but have only managed to find the downloaded files.  I have looked through dconf-editor to locate the plugins for rhythmbox and lastfm_extension is not listed.

Running Rhythmbox from terminal window gives me various codes with the same message:

(rhythmbox:3693): Gtk-CRITICAL **: gtk_builder_add_from_file: assertion `filename != NULL' failed
Segmentation fault (core dumped)

I have not been having too much luck with the old music players recently (Amarok just kept failing) now Rhythmbox is not working.  Any suggestions would be very welcome.  :confused:

Regards

---

### Post by Frogs Hair on 2012-07-14
Hello and Welcome

You could install the synaptic package manager and remove the plugin from there. The Rythmbox plugin components for Last.fm seem to be scattered in different folders and I  would leave them alone unless you know exactly what you are looking for. 

I notice the plugin you installed is not in my 12.04 repository so I wonder if it is compatible. You could give Clementine a try , but that does't solve the problem.

---

### Post by lladnar on 2012-07-14
Hi Frogs Hair

Many thanks for your swift reply.  I have installed Synaptic, then did a search for the lastfm_extension - Nothing!  Then searched for all Rhythmbox files still installed and completely removed them.  (They were:  librhythmbox-core5, rhythmbox-data, gir1.2-rb-3.0 and librhythmbox-core6)

Then reinstalled using Software center.  YIPEEE - it is currently searching through my music again and Lastfm is currently playing my radio station as I type.  Thank you so much.  5 hours of my life and a small package manager has saved the day!

Now do I try and find another plugin for Lastfm love/ban buttons or do I just leave it be and do something responsible this fine Saturday???

Many thanks.  ):P

---

### Post by Frogs Hair on 2012-07-14
Check out the Last.fm app in the software center it has the option built in.

---

### Post by lladnar on 2012-07-15
Hi Frogs Hair

Installed suggested application and it works perfectly.  Great suggestion.  Thanks.  Now I am certainly foot tapping!!!

Regards

---

