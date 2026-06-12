---
title: "Anyone interested in a project?"
date: 2008-10-16
forum: Programming Talk
---

### Post by curvedinfinity on 2008-10-16
Hey all,
I'd like to test the waters for interest for a new project, which I have been formulating for quite some time. This project tries to solve this idea:

**Why isn't it easier to share *my* things over the internet?**

The key ingredient to the answer of this question is the user experience. I personally know a lot about computers, so I can set up an HTTP server on my desktop and then a dynamic DNS and serve my files to anyone in a matter of minutes. However, most people will never get to the point where they are capable of doing this on their own. People would love this capability if they knew the kind of flexibility it offers, but it simply requires too much technical knowledge and steps to complete.

What do I propose then?

**A way to look at a file on someone else's computer with zero configuration, using user interfaces that people are already familiar with.**

What implementation do I suggest?

A new bittorrent-based "filesystem" consisting of three parts:
[list]
[*]An http BT tracker, with per-user tracking
[*]A special BT seeder that syncs a local directory with the tracker
[*]A BT protocol URI for firefox, so you can download bittorrent files directly through the browser
[/list]

The usage flow would look like this:
[list]
[*]Bob wants to share a file
[*]Bob makes an account on the tracker
[*]Bob downloads the seeder, specifying ~/Web as the share directory
[*]Bob puts an image in the Web directory
[*]Bob sends Tom the link to his image, dtp://tracker.com/Bob/image.png
[*]Tom opens the image in Firefox, which automatically uses bittorrent to retrieve it
[/list]

Anyway, please tell me if you are interested in this idea. I'd be willing to prototype much of it, but I'd need help slogging the whole way. :)

---

### Post by mssever on 2008-10-16
> **curvedinfinity said:**
> snip
That doesn't sound any simpler than the existing methods (one of the web-based filesharing sites, e-mail attachements, etc). However, I do think that making a filesystem for a filesharing site would be cool. Box.net has a public API, so it might be a good starting point. But I have no experience with FUSE.

---

### Post by henchman on 2008-10-16
Well, maybe i haven't understood your idea completeley right... but for images we have imageshack, for videos youtube and for the normal files (eg. without preview needed) we have sites like megaupload or rapidshare... all sites are able to do something like a 'one click' upload afaik...

if you like to use BT then you may just use it the way you described... pack, upload, send someone the url...

as mentioned before, a filesystem-like approach would be cool, but i see no real advantage for this against the above mentioned sites... because content can be best shared through web sites, imho.

a filesystem approach may be nice for a personal backup system or for the online 'USB flash drive'... just mount it on one computer, copy your files, mount on another one on another continent and then download the files again. but this approach seems to be more for individuals not wanting to share their files with a large amount of people...

---

### Post by Rich78 on 2008-10-16
Doesn't ftp already do this with even less configuration or am I missing something?

I can't really see a use for this at all sorry.

---

### Post by sethvath on 2008-10-16
Is the BT part similar to what allpeers tried to achieve? [http://mashable.com/2006/01/03/allpeers-p2p-file-sharing-extension-for-firefox/](http://mashable.com/2006/01/03/allpeers-p2p-file-sharing-extension-for-firefox/)

As for data sharing between work colleagues, [http://www.activecollab.com/](http://www.activecollab.com/) is what I use.

---

### Post by GavinZac on 2008-10-18
Is this not just DropBox?

[www.dropbox.com](www.dropbox.com)

---

