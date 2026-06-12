---
title: "Music in a Webpage"
date: 2009-04-19
forum: Programming Talk
---

### Post by ultblad1 on 2009-04-19
My friends have recently set up a new server, to fool around with PHP and whatnot. Things are going along fine, but I would like the server to be able to play music in the background of a webpage. Yes, I know that this is a bad idea to have music looping in the background, but this is something that I would like to learn.

I am viewing the webpages in Firefox, and I was wondering if there were any easy HTML tags that I could insert to get the music to loop indefinitely in the background. Any help would be appreciated!

---

### Post by Firestom on 2009-04-19
Here is an example code, which I already used before (might be HTML 4.1 and not XHTML 2.0):

[HTML]<embed name="courage" src="/music/aaf/courage.mp3" loop="true" hidden="false" autostart="true"></embed>[/HTML]

---

### Post by dwhitney67 on 2009-04-19
> **Firestom said:**
> Here is an example code, which I already used before (might be HTML 4.1 and not XHTML 2.0):

[HTML]<embed name="courage" src="/music/aaf/courage.mp3" loop="true" hidden="false" autostart="true"></embed>[/HTML]

Sorry to hijack the thread, but I tried this in my webpage.  The audio file plays, yet a video pane appears.  Is this possibly because of the file association Firefox has wrt playing mp3 files?  Firefox is setup to use mplayerplug-in 3.55.  Can you recommend a better plugin that I can use/install that just plays audio and that does not (attempt to) play video?

---

### Post by ultblad1 on 2009-04-19
I'm tried your HTML, but I'm not hearing any music.
The page I'm trying it on is [here]("http://pegjudge.ath.cx:5050/toby/music.html")

Any other ideas?

---

### Post by dwhitney67 on 2009-04-19
> **ultblad1 said:**
> I'm tried you HTML, but I'm not hearing any music.
The page I'm trying it on is [here]("http://pegjudge.ath.cx:5050/toby/music.html")

Any other ideas?

set hidden="false"

---

### Post by ultblad1 on 2009-04-19
I tried that too but nothing happened.

---

### Post by dwhitney67 on 2009-04-19
> **ultblad1 said:**
> I tried that too but nothing happened.

This is my first time doing this too.  But it worked for me; could it possible be that your browser has no file-association setup for MP3 files?  Check your browser's preferences.  With Firefox, Edit->Preferences, then click on "Applications".  Afterwards, search for mp3.

---

### Post by dwhitney67 on 2009-04-19
I found this [reference]("http://www.developingwebs.net/html/mp3.php"), and a few others, that basic state the same... embedding mp3 music in a webpage differs when serving content to Mozilla (i.e. Firefox) and IE.

One thing that I found that I needed to do to stream an mp3 remotely was to rename the file with an m3u extension.  I was unable to stream the music when the mp3 extension was used.

---

