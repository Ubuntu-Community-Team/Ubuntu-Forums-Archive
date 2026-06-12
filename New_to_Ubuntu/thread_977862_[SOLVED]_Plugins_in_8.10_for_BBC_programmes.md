---
title: "[SOLVED] Plugins in 8.10 for BBC programmes"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Scunnered on 2008-11-10
It will likely be my mis-understanding but when I was attempting to listen to BBC radio in the UK Philinux advised as follows :

**In Intrepid, soon to be released 30th October there is even a bbc plugin for Totem**.

In the interm from that post I bought a laptop with 8.10 pre-loaded and had hoped to be able to listen to my favourite programmes.  When I attempted to listen to Radio 4 this evening I was unable to listen to it.

The following was displayed:
 
[I]The required software to play this file is not installed. You need to install suitable codecs to play media files. Do you want to search for a codec that supports the selected file?

The search will also include software which is not officially supported.[/I]

Where should I be going from here to achieve my ends

---

### Post by MasterSander on 2008-11-10
click k on search for the codecs, ubuntu isn't allowed to install mp3 codec themselves, you need to give your agreement. So agree and search and install them

---

### Post by Bölvaður on 2008-11-10
> **Scunnered said:**
> 
The following was displayed:
 
[I]The required software to play this file is not installed. You need to install suitable codecs to play media files. Do you want to search for a codec that supports the selected file?

The search will also include software which is not officially supported.[/I]

When this comes up you should press "yes" and it will automatically look for codecs for you that might work with the video you are currently watching.

You can do this by watch the same video again and wait for the popup to come again. If that does not work continue reading &#8595;
If it worked, please mark this thread as solved

You can also go into synaptic package manager from System &#8594; Administrator and try find all the gstreamer plugins (or just one package that contains most popular packages like codecs, flash and such...  ubuntu-restricted-extras)

If that doesnt work, or you have any problems, please post here again :)

---

### Post by Scunnered on 2008-11-11
Many thanks for your replies.  

Searching for Codecs I am offeredGStreamer ffmpeg video plugin which is not what I need.

I can watch videos OK and strangely enough listen to the BBC iPlayeer listen again Radio programmes.  

When I was waiting on my laptop I was able using 8.04 listen to the radio programmes live provided they were on national radio.  Local radio still requires Realplayer but generally I can live without that.

Had a look at the package manager but did not see anything that looked like what I needed.  There was no reference to Total or a BBC plugin.

So near but so far.

I will have to hope that some UK user can assist further 

Again thanks for your assistance

---

### Post by nothingspecial on 2008-11-11
To listen to bbc radio I use rhythmbox. You can add radio stations somewhere its  menus. The correct urls to use are -

BBC Radio 1
URL: mms://wmlive-acl.bbc.co.uk/wms/radio1/radio1_nb_e1s1

BBC Radio 2
URL: mms://wmlive-acl.bbc.co.uk/wms/radio2/radio2_nb_e1s1

BBC Radio 3
URL: mms://wmlive-acl.bbc.co.uk/wms/radio3/radio3_nb_e1s1

BBC Radio 4
URL: mms://wmlive-acl.bbc.co.uk/wms/radio4/radio4_nb_e1s1

BBC 6Music
URL: mms://wmlive.bbc.net.uk/wms/6music/6music_e2s1



BBC Radio 7
URL: mms://wmlive.bbc.co.uk/wms/bbc7/lo_s1

---

### Post by asgard_command on 2008-11-11
My Totem included the bbc plugin and worked from day one, I think the only thing I had instsalled extra by the time I tried it was the restricted extras package.

---

### Post by FreewheelinFrank on 2008-11-11
See if this works for you:

[http://ubuntuforums.org/showpost.php?p=6136177&postcount=14](http://ubuntuforums.org/showpost.php?p=6136177&postcount=14)

---

### Post by Scunnered on 2008-11-11
**nothingspecial**

Your links gave me more hope of success but as I was used to working from the BBC home page and clicking on the radio programme I was hopeful of repeating that method.

[B]asgard_command
[/B]
Having stated that your Total worked from day one was really reassuring and on following the link given by **FreewheelinFrank** confirmed that everything was possible.

On going to Synaptic and using the search I found that both Totem and Mozilla Mplayer were not loaded.  It appeared that the Totem plugins etc were removed during install as they had green boxes against the items and appeared to need re-installed.

I can now listen to all the programmes that I like to listen to and as an extra bonus I can even listen to radio Scotland without the use of Realplayer.  I was not prepared to load Realplayer and was willing to avoid my national station so this is a major plus.

One small problem is that the display of the iPlayer does not permit me to adjust the volume but I can live with that.

My sincere thanks to each and everyone who offered their assistance.

---

