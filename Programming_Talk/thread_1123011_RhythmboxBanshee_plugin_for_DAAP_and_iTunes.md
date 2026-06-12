---
title: "Rhythmbox/Banshee plugin for DAAP and iTunes"
date: 2009-04-11
forum: Programming Talk
---

### Post by jamesisin on 2009-04-11
Let me start off by saying I am not a developer (but I play one on TV).  I understand some coding but don't get carried away.

I am working to get iTunes to play flac files.  I was able to make great progress in getting iTunes to play flacs locally by using three components (either Fluke or separately the Xiph QuickTime Component, the FLACImporter, and the OggS application).

The problem is that in order to play a flac in iTunes I have to touch that file (either with Fluke or with OggS directly). This touch tells Spotlight to set the metadata called kMDItemFSTypeCode for that particular file as 1332176723 in Spotlight&#8217;s datastore.

If you are a Mac dev and would like to investigate that aspect of the matter see my post:

[http://www.soundunreason.com/InkWell/?p=928](http://www.soundunreason.com/InkWell/?p=928)

Now, how does this relate to Ubuntu?

The other possible way to get these files accepted by iTunes across DAAP is to have Rhythmbox (which I have been using) lie to iTunes.  It should tell iTunes that the flac is an ogg and I think this will convince iTunes to go ahead and play the file.

I am guessing Banshee plugins work with Rhythmbox?  Either way, what would it take to develop a plugin for Rhythmbox to lie to iTunes?

---

### Post by jamesisin on 2009-04-12
I envision something where a second DAAP share is created with iTunes prepending it.  So if your normal share is called MusicShare, the lying DAAP share will also show up on the network called iTunesMusicShare (this is merely a suggestion).

A flac from a local (OggS touched) flac file will display as &#8220;Kind: QuickTime movie file&#8221; in the Get Info dialog in iTunes.  These files will play (in iTunes and QuickTime) thanks to the two QT additions from my blog post.

However, a flac through the DAAP connection will show as &#8220;Kind: MPEG audio file (remote)&#8221; which is not handled in the same fashion.  These files sit dead in the water.

This share should send out the normal information except it would identify the files as "Kind: QuickTime movie file" so as to dupe iTunes into using the aforementioned components for playback.

Any takers?

---

### Post by jamesisin on 2009-04-12
According to one xiph developer:

> [arkadini:] the problem is the only way to make iTunes paly non-itunes supported files through daap seems to be for the server to send different mime types if the client is iTunes

So it would seem a solution would be to take the existing DAAP plugin for Rhythmbox and add a couple lines of code to mask the mime type for flacs.

Sounds cool, eh?

---

### Post by jamesisin on 2009-04-13
For interested parties:

[http://brainstorm.ubuntu.com/idea/19207](http://brainstorm.ubuntu.com/idea/19207)

---

### Post by jamesisin on 2010-02-09
Admit it.  It's a delicious hack.

---

