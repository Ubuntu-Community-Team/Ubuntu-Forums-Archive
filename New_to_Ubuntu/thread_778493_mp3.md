---
title: "mp3"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-02
I´ve just intalled ubuntu and i cant play mp3´s, i get an error im totem player that say ¨failed to open reason unknown¨ musicplayer says ¨there is no plugin installed to handle a mp3 file¨

What do i do??

---

### Post by TeoBigusGeekus on 2008-05-02
System->Administration->Synaptic Package Manager
Search for Ubuntu-Restricted-Extras, check the package and install it...

---

### Post by forumache on 2008-05-02
I thought it should offer to download a plugin. At least this is what it did on my computer...

---

### Post by muteXe on 2008-05-02
Yeah, mine too.  It offered a few codecs and allowed you to pick one. From then it all just worked.  Weird.

---

### Post by Canis familiaris on 2008-05-02
> **muteXe said:**
> Yeah, mine too.  It offered a few codecs and allowed you to pick one. From then it all just worked.  Weird.

Perhaps he is using older version of Ubuntu.

---

### Post by muteXe on 2008-05-02
Well this has been the same for me on the last three versions of ubuntu.  Maybe he's installing something earlier than Feisty?  Maybe I guess.... #-o

---

### Post by iSplicer on 2008-05-02
Instead of Totem, you could use VLC, a much better and full featured media player which comes with all codecs required. Just pop up a terminal and type:

sudo apt-get install vlc

---

### Post by Canis familiaris on 2008-05-02
> **muteXe said:**
> Well this has been the same for me on the last three versions of ubuntu.  Maybe he's installing something earlier than Feisty?  Maybe I guess.... #-o

Feisty was the first release for Automatic Codec Installer.
He might be using Edgy, Dapper, Breezy, Hoary or Warty!
or perhaps some weird problem this.

---

### Post by El King on 2008-05-02
Opem Terminal then
> sudo apt-get install ubuntu-restricted-extras

---

### Post by SPr on 2008-05-05
I've just had to do the same after installing Ubuntu 8.04. The difference maybe that I prefer doing fresh installs with the alternative CD; it's so much quicker than waiting for the desktop to load from the Live CD.

Hmmm, I missed out on the auto-installation of nVidea drivers which worked on the alternative CD for 7.10 -  I've just fixed that. I wonder what else is missing...

---

