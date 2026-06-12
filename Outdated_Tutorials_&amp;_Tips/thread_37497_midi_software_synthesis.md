---
title: "midi software synthesis"
date: 2005-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by alainhenry on 2005-05-27
This is to answer this query, from another thread where it was out of context.  

[QUOTE=vidyu]I followed the steps from [http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo](http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo) , but when I type timidity -iA -B2,8 -Os1l -s 44100 it shows me that is opening 128:0 (I`m not sure for the number of the port) and other ports and does nothing else until i "ctrl-c" it. And then when I type pmidi -p 128:0 music.mid i did not hear any sound. I`m not sure that my card have hardware  synthesizer. How can I find that? Thank you for the answers and again all my apologies for my bad english.[/QUOTE]

You should launch the command 
   timidity -iA -B2,8 -Os1l -s 44100
in a first terminal (I found timidity -iA also worked), and leave it running.  Then open a second terminal to issue the other command 
   pmidi -p 128:0 music.mid

Alain

---

