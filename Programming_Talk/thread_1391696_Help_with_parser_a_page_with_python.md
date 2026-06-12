---
title: "Help with parser a page with python"
date: 2010-01-27
forum: Programming Talk
---

### Post by davidtuti on 2010-01-27
Hi,

I would like to parse a webpage to can get the url of the video download. I use pyhton and firebug but I cant get the url link.

Example:

The url where I have to get the video link is:
[http://www.rtve.es/mediateca/videos/20100125/saber-comer---salsa-verde-judiones-25-01-10/676590.shtml]("http://www.rtve.es/mediateca/videos/20100125/saber-comer---salsa-verde-judiones-25-01-10/676590.shtml")

The video is 
[http://www.rtve.es/resources/TE_SSAC011/flv/8/2/1264426362028.flv]("http://www.rtve.es/resources/TE_SSAC011/flv/8/2/1264426362028.flv")

Could you help me please?
Many thanks and sorry for my english!

---

### Post by wmcbrine on 2010-01-27
This isn't really a web page parsing issue, because the page doesn't link directly to that video. Instead, it embeds a viewer. Only the viewer knows the URL to the FLV file itself. I can't see any direct correspondence between the elements of the two URLs, nor can I see a way to construct the FLV's URL from the contents of that page. Sorry.

---

### Post by Can+~ on 2010-01-27
This isn't a parsing problem. This is a streamed video loaded by a proprietary plugin.

I suggest you to forget about it, and install the [download helper]("https://addons.mozilla.org/en-US/firefox/addon/3006") plugin for firefox. No need to reinvent the wheel.

---

### Post by davidtuti on 2010-01-28
Many thanks!
I'm trying to downloadm many videos. To do this I would like a script to automatice this task, but I've saw that is too much difficult. :-(
Thanks anyway

---

