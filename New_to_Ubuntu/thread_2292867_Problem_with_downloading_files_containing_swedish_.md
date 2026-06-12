---
title: "Problem with downloading files containing swedish letter"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by Thoger on 2015-08-31
I have this problem that when I download a file containing swedish letters I get two files one containing data and one with 0 data it looks like this the file containing data:
   OPF S&#1113701;gmyra AB 8 20141231 ver 1.pdf and one with "right name" containing no data  OPF Sågmyra AB 8 20141231 ver 1.pdf
I'm running Ubuntu 14.04 with KDE on a chromebook

---

### Post by Double.J on 2015-09-01
Hi there!

Can I ask a bit more information? 
When you say Swedish letters, do you mean the fonts used in Ubuntu? And secondly, from where did you download the pdf files?

If it is the languages and fonts used inside ubuntu that is causing the problem, you shouldn't need to get them from anywhere else, The software repositories have all of that stuff. 

Having a look through (as I'm not Swedish) it seems that the language code in Ubuntu for Swedish is   sv_SE. You can check your system has Swedish language by putting this into a terminal:

```

sudo apt-get install language-pack-sv
```


And then check out [this page ]("https://help.ubuntu.com/stable/ubuntu-help/session-language.html")on setting languages in Ubuntu.

Hope it helps!
[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][COLOR=#111111]

[/COLOR][/FONT]

---

### Post by Thoger on 2015-09-01
It didn't help. I download files from thunderbird and I use ownclould from my own server. It has worked perfect before on my chromebook, I suspect that somebody in the crouton group or someone else had made some changes, I've installed all language files and everything should be alright. It still work perfect on my stationary computer and I have the same file installed, never any problems. I guess I'll have to by a new laptop and install the "real" ubuntu it's very stable and I love it. I've been running Suse for some years but I like ubuntu better. Thank you for your help :D
PS When you have a problem like this, owncloud goes bananas and my files on the server gets corrupted and it ends up with empty files and lost data. It's totally out of control

---

