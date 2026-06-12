---
title: "[new application] Thumbnailer for audio files"
date: 2008-03-08
forum: Outdated Tutorials &amp; Tips
---

### Post by stephantom on 2008-03-08
Step right up folks, gaze upon the miracle of all file thumbnailers because I am happy to present to you a shiny new script to do just that.

[center][img]http://img3.imagebanana.com/img/05lji7bf/Screenshot.png[/img][/center]

Yup, it generates thumbnails from your audio files (mp3 and flac to be precise).
The magic is done through extracting three seconds of audio data from the input file (starting from 00:10 because a lot of songs tend to have silence at the beginning).
So the files will have to have a minimum length of 13 seconds or they don't get a thumbnail.
The extraction is done using sox - a really wonderful tool for song editing - which also converts it to raw text data. This textual data is then trimmed and fed to gnuplot which produces the graph. The composite tool from the ImageMagick project then helps us to overlay an icon.

I'll attach a debian package to this post (it depends on sox, gnuplot and imagemagick). It's essentially just a bash script, so it should work on other architectures than i386, I guess.


Things you can customize:
[list][*]If you know your way around gnuplot you can probably change the color of the graph (currently it's red) or tweak it otherwise. Please let me know what you're doing and show examples! :-)
[*]You can replace the music note icon with any file you like (it's in /usr/share/audiothumb/overlay.png). Just try have it about the same size (or adjust the placement options in /usr/bin/audiothumb [line 12]).[/list]

Things I can't figure out right now:
[list][*]How to get rid of the frame/border that nautilus draws around every thumb. I imagine the thumbs would look nicer without them. Anyone know how to turn them off?
[*]How to enable this for ogg vorbis files. Their MIME type has a plus sign in them and gconf keys don't like plus signs.[/list]


Please post thoughts and feedback on this! :-)

---

### Post by franestepona on 2008-03-10
Does it need any special repository? It seems that it cant find the dependences, it's complaining about libsox-fmt-flac. Any idea? By the way great tool.

---

### Post by stephantom on 2008-03-10
> **franestepona said:**
> Does it need any special repository? It seems that it cant find the dependences, it's complaining about libsox-fmt-flac. Any idea? By the way great tool.

The libsox-fmt-* packages are available from the universe repositories (at least in hardy). However, they are missing in all earlier repositories.
I would take a wild guess and say that these were split up in the main debian repositories. I've attached a modified package to this post, please let me know whether it works.

---

### Post by franestepona on 2008-03-10
Thanks! Now the package is installed, but it doesn seems to work (or i just dont know how it works) I though it would generate thumbnails right from the nautilus browser, but it didnt, I tryed 

```
[22:07:22]Fran@FransMachine: audiothumb '/home/fran/Media/Music/04 Toca'\''s Miracle 2008 (Wez Clarke Funky Dub).mp3' 
sox sox: -: output clipped 101 samples; decrease volume?
composite: missing an image filename `/tmp/graphy.png'.

```

Am I missing something?

---

### Post by ryanhaigh on 2008-03-10
Very cool idea, you should put something up on brainstorm to see if you can get this into hardy+1. You might even get it made into a python script or some other language which would speed it up.

---

### Post by stephantom on 2008-03-10
> **franestepona said:**
> Am I missing something?
Yes you are. Did you relogin/kill nautilus after you installed the package?
If you'd like to generate a thumb manually you have to supply an input filename *and* an output filename.

Example:
```
$~ audiothumb input.mp3 output-thumb.png
```


Edit:
I think I see the problem now. When the package is installed, the gconf keys that tell the file manager what to do are installed for the super user and not the currently logged in user.
A temporary fix is to run ```
gconftool-2 --install-schema-file=/usr/share/gconf/schemas/audiothumb.schemas
``` to manually install the keys. But I've got to find a way to automate that. Stay tuned.


@ryanhaigh:
I don't see how a python script could speed this script up. It basically depends on how fast the third party tools work which are called from the script (as far as my understanding goes). But I'll dig into it.

---

### Post by Fab on 2008-03-10
Installed the gutsy deb, works so far, except that I only get the graph and no note icon overlayed. Any advice?

edit

Sorry, the overlay is there, but only when I mouseover. Any way to get this to show permanently?

---

### Post by stephantom on 2008-03-11
> **Fab said:**
> Sorry, the overlay is there, but only when I mouseover. Any way to get this to show permanently?

Nope, what you see is the standard sound overlay produced by nautilus what.
Going to look into it.

---

### Post by franestepona on 2008-03-12
Now it works! It's so cool, I think that should be included in Hardy. I also have problems with the overlay, I cant see it at all. But in my case Nautilus doesnt draw a black frame around the icon.

Thanks for the application!

---

### Post by KillerKiwi on 2008-03-13
very cool... the gnome frame is based on ithe image size.. just make the images smaller.

Maybe use python and grab the gtk colors for the wave?

---

### Post by pingpongboss on 2008-03-13
I'm not sure I understand what kind of thumbnail this is supposed to produce. Can someone post a screenshot or something?

---

### Post by blacksm1th on 2008-03-13
i get this after install of  "audiothumb_0.1.1~gutsy.deb":
[IMG]http://img84.imageshack.us/img84/1763/screenshotyr1.png[/IMG]

EDIT: i like it but how to make note icon to appear?

---

### Post by blacksm1th on 2008-04-26
This is from Hardy's Nautilus now with note icon :):
[IMG]http://img254.imageshack.us/img254/9153/screenshotvx6.png[/IMG]
Very very nice.

---

### Post by vkshiu on 2008-04-27
Does this work for Konqurer in Kubuntu?

---

