---
title: "Black and white DVD iso"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Nevyn on 2008-09-11
Hi!

Got my old MacGyver collection made into iso's so that I don't scratch the discs. However, when I try and play the iso's (mounted with Gmount-iso at /media/temp-mnt-iso ) I only get it to play in black and white. Tried both with Movieplayer xine and Gstreamer, and VLC, and no luck with either. Am I missing a plugin or can anybody point me in the direction of a better movie player (I've had some trouble with a few video clips my friends have sent me aswell).

Thanks in advance =)

---

### Post by Thanoulis on 2008-09-11
Try *mplayer*...are you sure you created those iso's correctly?

---

### Post by Nevyn on 2008-09-12
Yep, they work perfectly on my both my old win-machines, and I also got it to work once last week. That was the first time I tried it on Ubuntu and I did so with vlc and MoviePlayer gstream. Result: black and white video with slow motion movements. Then I tried it with Xine and it worked perfectly.

I've tried Mplayer before aswell but since I got the dvd's in vob-format and I haven't figured out a way to get Mplayer to open the whole folder with vob-files it's been of no use to me.

I'm still thinking of the possibility that I'm missing plugins, anyone got an idea of where to find out what plugins I need?

---

### Post by Liviu-Theodor on 2008-09-12
Have you installed [FONT="Courier New"]ubuntu restricted extras[/FONT] from the [FONT="Courier New"]Application -> Add-Remove...[/FONT]? Also, I find **vlc** a good program to view movies.

---

### Post by mikewhatever on 2008-09-12
> **Liviu-Theodor said:**
> Have you installed [FONT="Courier New"]ubuntu restricted extras[/FONT] from the [FONT="Courier New"]Application -> Add-Remove...[/FONT]? Also, I find **vlc** a good program to view movies.

Restricted extras is completely unneeded. It brings in a lot of stuff unrelated to multimedia, such as java, msfonts and unrar. As for VLC, re-read post #1.

Nevyn, I don't get it. Does it work with Xine?

---

### Post by Nevyn on 2008-09-12
Well, I have the possibility to open the vob-files with Movie Player, Movie Player (Xine), and Movie Player (Gstreamer). I have tried them all and as I said previously it did work to play them one time with the Xine-option. Without any configuration (I only played a little music and read an online news paper) it would not work after that. Sorry if I was a bit vague there.

I'll try a complete remove and re-install and give it another go.

=)

---

### Post by Liviu-Theodor on 2008-09-15
> **mikewhatever said:**
> Restricted extras is completely unneeded. It brings in a lot of stuff unrelated to multimedia, such as java, msfonts and unrar. As for VLC, re-read post #1.

Nevyn, I don't get it. Does it work with Xine?

I forgot to say about installing [FONT="Courier New"]libdvdcss2[/FONT] in Synaptic. Does it help?

---

