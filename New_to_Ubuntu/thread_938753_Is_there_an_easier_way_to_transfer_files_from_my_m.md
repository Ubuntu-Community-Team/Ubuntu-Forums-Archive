---
title: "Is there an easier way to transfer files from my media player to my computer?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Marianne_S on 2008-10-05
I have a Creative Zen Vision:M media player, and when using gnomad2 to transfer the files it keeps crashing after transferring 5 or so files (mp3), no matter how much i change my preferences. This makes file transferring take forever. Is there another way? an easier way to do this?

---

### Post by philinux on 2008-10-05
How about just using the file manager nautilus. Or the cp command from the terminal.

---

### Post by Marianne_S on 2008-10-05
Hm yeah, i am one of those newbies who aren't too familiar with terminal commands - however i could get around using cp - if i only could find out how i can find the files in my media player using commands first. he... if that made sense. cos it doesn't appear in my "places" menue (if that made any more sense)

---

### Post by clive littlewood on 2008-10-05
Hi

Have you tried using Amarok or Vlc (both in repos)

These should sync with your player without to much dificulty.

Hope this helps

cl

---

### Post by Marianne_S on 2008-10-05
huh? i can transfer files using vlc? not just play them? this is new to me. how do i do that?

---

### Post by clive littlewood on 2008-10-05
Hi

sorry slip of the brain with vlc, but ok with Amarok

cl

---

### Post by NullHead on 2008-10-05
Does your player work in rhythmbox?

---

### Post by Marianne_S on 2008-10-05
i cannot access my media player without gnomad. or i cannot find it. it is not listed in my places menue when i connect it to my computer. which makes me think i am missing something else. 

i havent installed rythmbox here - but seem to remember it wouldn't be read on my other computer (also with xubuntu, and ubuntu which i had before that)

i have now installed amarok - but without being able to access my creative via my computer to configure my settings i am not able to transfer. 

so how do i fix this? 

really greatful for all the help so far

---

### Post by Marianne_S on 2008-10-05
OK so I have been able to connect my creative to amarok - however it isn't able to transfer, nor play the files. 

does anyone have any suggestions?

---

### Post by philinux on 2008-10-05
Which version of gnomad2 are you running?

---

### Post by Marianne_S on 2008-10-05
gnomad2 2.8.12

---

### Post by philinux on 2008-10-05
Then get the latest version. Download the appropriate deb file.

[http://linux.softpedia.com/progDownload/Gnomad2-Download-3392.html](http://linux.softpedia.com/progDownload/Gnomad2-Download-3392.html)

---

### Post by Marianne_S on 2008-10-05
uh oh, this seems to becoming difficult ok trying to install gnomad2 2.9.1 gives me this error message after doing ./config ( i couldn't access the deb links) :

> No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


but i have gtk+ 2.0 installed.

---

### Post by NullHead on 2008-10-05
Install the dependencies for gnomad with this command: ```
sudo apt-get build-dep gnomad2
``` Then run ./configure again and it *should* build with out error.

---

### Post by Marianne_S on 2008-10-08
ah, i tried it and got the message to put some URI-something in my sources.list - i also tried it on my other computer and it worked fine there - but alas it still crashed during file transfer with gnomad 2.9.1. i also tried amarok on my other computer and had the same problem. 

i will be moving and won't have internet for a while. so i have to figure this one out on my own - or just move 30 gb of music five songs at a time. i keep seeing lots of people complaining about the same issues who have a zen vision:m which makes me suspect it is something wrong with the media player.

---

### Post by bryncoles on 2008-10-08
i have a creative zen player too, and ive never been able to get ubuntu to recognise it as an external drive (awhich is what you would need to see it in 'places'). without mounting it as an external drive, you cant browse it and therefore cant just browse the device in nautilus. 

amarok needs extra plug ins to manage creative products (but usefully i forget which ones it needs!)

but you might like to try ditching gnomad, and installing kzenexplore - its in the repos and when i found it (and figured it out) i switched straight away. its a kde application, but works fine in xubuntu too (as far as i know)

kzenexplore works on a drag and drop basis - so its the closest to a file browser you'll get. thats assuming your creative player works the same as mine!

perhaps you'd like to give kzenexplore a try? i can recommend it...

---

### Post by Marianne_S on 2008-12-06
thanks everyone - status now is - after reinstalling 8.10 rythmbox did recognize my player and transferred approx 300 files - leaving about 3000, but after that it wouldn't transfer at all. *sigh*

what i really wish was for it to work with amarok. i really like how it organized after file type first.

*kzenexplore wouldn't recognize the player, nor did it work with neutrino.

so i guess i have to find someone with a windows pc and mate with them.

---

