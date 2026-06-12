---
title: "ARGH! Odd gVim text coloration?"
date: 2006-04-12
forum: Programming Talk
---

### Post by DonQuixote on 2006-04-12
Hey all,

I was using gVim and I guess I pressed a combination of keys and voila! I now have a bright red background color behind every instance of every string of ");" in one of my files, like this [COLOR="Red"]**);**[/COLOR], well ok, not like that... it's the background that is red.

I have NO idea what I did, or how to change it back.

Any help would be most appreciated!

Thanks!

---

### Post by DonQuixote on 2006-04-13
Ok... it seems that I somehow used the "Find" command... what I need to know is how to turn it off?

Thanks!

---

### Post by jrib on 2006-04-13
well there is the newbie method I used for a while:
```
/asdjfioasjfois
```

Which would search for 'asdjfioasjfois' and of course fail so there is no highlight.

Then there is the smart way, by doing ```
:nohlsearch
``` or ```
:noh
``` for short.

And you can disable it for the rest of your session with ```
:set nohlsearch
```

Add that to your ~/.(g)vimrc of course to never have to bother again.

---

### Post by xenmax on 2006-04-13
I would also do _jason's method of tying a few gibberish characters to turn off search highlighting, but i recently found this method which I prefer now - add a key mapping to turn off search highlighting in (g)vimrc file:
```
map <silent> <F3> :nohl<CR>
```
When i hit F3, highlight is off. Note that this DOES NOT clear search buffer. Next time i hit "n" or "N", i get search highlight back.:)

---

### Post by DonQuixote on 2006-04-13
Guys,

Thanks so much for the help!

---

### Post by DonQuixote on 2006-04-13
xenmax,

Is that command exactly as I would enter it into the .vimrc file?

Thanks!

---

### Post by xenmax on 2006-04-13
>  Is that command exactly as I would enter it into the .vimrc file?
Yes, that should work.

---

### Post by RafG on 2006-04-13
[QUOTE=xenmax]```
map <silent> <F3> :nohl<CR>
```
When i hit F3, highlight is off. Note that this DOES NOT clear search buffer. Next time i hit "n" or "N", i get search highlight back.:)[/QUOTE]

I use a 'toggle'. In case anyone is interested:
```
map <F6> :set hls!<bar>set hls?<CR>
```

---

### Post by jrib on 2006-04-16
[QUOTE=RafG]I use a 'toggle'. In case anyone is interested:
```
map <F6> :set hls!<bar>set hls?<CR>
```[/QUOTE]

This is great, I'm going to use it.  Thanks!

---

