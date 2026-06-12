---
title: "how to clean up the names on mp3 files"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by fignig on 2008-06-19
j/w how to clean up the names on my mp3 files. is there anyway to do multiple songs at the same time. such as removing like the same phrase, or track #'s from the title. and such as things like that. 

i just want the format: "Artist's Name" - "Song Name"
and no more superfluous characters

---

### Post by RomeReactor on 2008-06-19
Hi. If you want a graphical way to batch-rename, try Thunar; search for it in Synaptic, or to install from the terminal:
```
sudo aptitude install thunar
```
Then you can find 'Bulk Rename' in 'Applications->Accessories'.

---

### Post by tjwoosta on 2008-06-19
i use exaile (media player) to do this

just highlight a bunch at once and right click then click edit track information, then highlight all the ones you want to change and change it

Edit: nevermind i see now that you mean from the actual file name

yes i agree thunar

---

### Post by amaroKer on 2008-06-19
I find amarok does the job quite well.  You only need to have your ID3 tags filled in, and use the "move/copy songs to collection" function.  Ensure that you set your preferences for outgoing file names, or risk being disappointed.  If you do not know the info for a particular song, amarok can fill them in automatically (per file).

---

### Post by krendar on 2008-06-20
Another option, especially if you want to edit the id3 tags as well:

[EasyTag]("http://easytag.sourceforge.net/")

Install via Synaptic. I recommend you read the documentation on the link above first (though its not hard to use).

---

### Post by Fingers &amp; Thumbs on 2008-06-20
Yeah Easytag's a brilliant tool for id3 manipulation, and can even help tidy up filenames, but if it's just filenames you want to tidy up then thunars bulk rename has all the options you could need.

---

