---
title: "Server-Less Firefox XUL -- Possible?"
date: 2006-12-31
forum: Programming Talk
---

### Post by SuperMike on 2006-12-31
For those who don't know...There's a way to make a Firefox chrome file that you can load instead of Firefox, and it can automatically connect to a website. The chrome file can have custom menus, coloring, titlebar, and many other features and buttons and be a completely different Firefox interface. In fact, the default interface in Firefox is itself a chrome file. Composing these chrome files is done in a language called XUL.

The way I have learned to interact with this is to bring up a web server. However, if you're going to make a rich client standalone app, a lightweight, embeddable web server on an alternate port and with a good GPL license is more suitable. I've found the best one for me for that is thttpd. This can then call CGI to do what it needs, and you can pick your language of choice like ngs-js, php, python, perl, java, C, etc.

The question I have for you is...can this XUL, instead of interfacing with a web server, simply load up and interface with Javascript and "go outside the sandbox" on the Linux PC? The reason I ask is because it could make an awesome platform for making installers for Linux and not require a backend web server, if I could figure out how to make that work.

---

### Post by yaaarrrgg on 2007-01-06
cool stuff! ... i hadn't seen this before.  from the site:

[http://www.xulplanet.com/tutorials/xultu/intro.html](http://www.xulplanet.com/tutorials/xultu/intro.html)

it sounds like stand alone apps are possible (i'm guessing as long as they don't require postbacks to a server?)

have you tried to launch the xul app at the command line with (in the same directory as your xul file)

```

firefox yourfile.xul

```

I tried this on a simple example, and seemed to work.  also, you can reference local files ont he hard drive with the file:///path/to/file url syntax (if you haven't tried this)

i'm not sure what file sstem restictions there are in javascript for this kind of app, but  might be fairly limited  for security reasons.

---

### Post by SuperMike on 2007-01-07
Thanks so much for responding. I wondered if anyone else would try this. I guess I'm going to have to experiment with how far Firefox's Javascript will let me go on Ubuntu if it uses a special chrome XUL file. If it can let me execute a script on the hard drive such as to interact with sqlite databases, you do know what this means, don't you? Yeah, it means you could build something as rich as a Quickbooks knockoff that works with Firefox as the UI, Javascript as the language, and sqlite as the database.

---

### Post by airtonix on 2007-05-14
you da man!

here is supermikes latest [HOWTO ]("http://ubuntuforums.org/showthread.php?t=333862")for this topic.

---

### Post by RawMustard on 2007-05-14
XUL doesn't need a webserver, just use [xulrunner]("http://developer.mozilla.org/en/docs/XULRunner") apt-get install xulrunner

Apps run from xulrunner have access to the file system; unlike xul loaded from a remote server from what I understand.

---

### Post by SuperMike on 2007-05-15
Yep, I've learned that too now, and one can rollout standalone apps that interface with a database, spawn a process and parse the output, read/write files, and so on. My yt2mp3 and simplexul examples on code.google.com are examples of some neat things you can do with this.

---

### Post by RawMustard on 2007-05-18
It's pretty good huh, I'm trying to write a chromeless fullscreen browser at the moment, thinking of turning it into a media type browser and player.  Have you seen [Songbird]("http://www.songbirdnest.com/")?  It's a bit too cluttered and commercially oriented but is a good example of what can be done!

Cheers

---

### Post by SuperMike on 2007-05-21
Songbird, in my opinion, went way overboard with how they used XPCOM. They didn't have to go to that extreme by making all their stuff into XPCOM components. This might be why Songbird still has a lot of bugs.

---

