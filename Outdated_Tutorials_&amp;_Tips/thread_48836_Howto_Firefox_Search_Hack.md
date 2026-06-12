---
title: "Howto Firefox Search Hack"
date: 2005-07-14
forum: Outdated Tutorials &amp; Tips
---

### Post by aragorn2909 on 2005-07-14
I saw this on tv earlier tonight, pretty cool.  

copy this into a text editor

<search
version="7.1"
name="Your Site's Title"
description="Search www.yoursite.com"
action="http://www.google.com/search"
searchForm="http://www.google.com"
method="GET"
>

<input name="sourceid" value="Mozilla-search">
<input name="sitesearch" value="www.yoursite.com">
<input name="q" user="">
</search>

"Your Site's Title" will be the search's name inside Firefox's search bar (I used Ubuntu Forums)
Where it says *yoursite*, just put the address of the site youd like to search (my example, [www.ubuntuforums.org](www.ubuntuforums.org))
Then, save the text document as *yoursitesname*.src to  /usr/lib/mozilla-firefox/searchplugins
Next, create a 16x16 icon (gif or png), naming it the same as the src file, *yoursitesname*.gif/png, and saving it also to /usr/lib/mozilla-firefox/searchplugins
Restart Firefox

---

### Post by bored2k on 2005-07-14
You just saved me a bunch on car insurance !! Nice guide, I was looking like for something like this for animenfo.com

---

### Post by nickless on 2005-07-14
[QUOTE=bored2k]You just saved me a bunch on car insurance !! Nice guide, I was looking like for something like this for animenfo.com[/QUOTE]
haha me too :D
thx ;)

...and looki what I found searching for the animenfo picture :D
[http://mastino.student.utwente.nl/~webmind/projects/mozilla-search/plugin/](http://mastino.student.utwente.nl/~webmind/projects/mozilla-search/plugin/)

ohh and before I forget it, you saw this on tv? :D

---

### Post by aragorn2909 on 2005-07-14
[QUOTE=nickless]ohh and before I forget it, you saw this on tv? :D[/QUOTE]
G4 in the US.  It was a Windows only guide, so I adapted it for here.  All credit goes to them for this hack. Apparently, this O'Reilly [article](http://hacks.oreilly.com/pub/h/3033) served as the basis for the g4 hack, perhaps all credit goes there?  Either way, enjoy.

---

### Post by arnieboy on 2005-07-14
awesome! missed out on the TV show but thanks for the HOWTO!

---

### Post by bored2k on 2005-07-14
> **nickless]haha me too :D
thx  said:**
> http://mastino.student.utwente.nl/~webmind/projects/mozilla-search/plugin/[/url]

ohh and before I forget it, you saw this on tv? :D
 I'm so loving you man. Oh my word those plugins ROCK ! Did you do them yourself ? If so, how ?

---

### Post by zarathustra on 2005-07-14
I've noticed you can't use the address bar as the "I'm feeling lucky" option on Google - like you can on Windows Firefox. Is there any way to enable this?

---

### Post by Wolki on 2005-07-15
[QUOTE=zarathustra]I've noticed you can't use the address bar as the "I'm feeling lucky" option on Google - like you can on Windows Firefox. Is there any way to enable this?[/QUOTE]

Works here perfectly. Are you using Ubuntu's Firefox?

---

### Post by zarathustra on 2005-07-15
Yes, should I try manually installing it? I don't seem to automatically upgrade extensions on this either.

---

### Post by kiddo on 2005-07-15
Me me me me! I know the solution! :P I've been scratching my head for months until I went to the network preferences, and below my hostname (computer name), REMOVED stuff that I wrote in "domain name". So make it look somewhat like this.

[[img]http://img339.imageshack.us/img339/5267/screenshotnetworksettings6hc.png[/img]]("http://img339.imageshack.us/my.php?image=screenshotnetworksettings6hc.png")

P.s.: that google site search form is a very old trick, but VERY difficult to find on the net... I'll sure copy-paste that in a text file instead of opening my php file everytime

---

### Post by zarathustra on 2005-07-16
Ah, thank you very much! I've always found this useful for when you can't remember web addresses.

---

### Post by nickless on 2005-07-16
[QUOTE=bored2k]I'm so loving you man. Oh my word those plugins ROCK ! Did you do them yourself ? If so, how ?[/QUOTE]
Yay :D an admin loves me!
Sadly I am not that geeky ;) Only thing I really learned in my short time with Linux is finding solutions via google :razz:

---

