---
title: "Best home server/media center os"
date: 2009-01-11
forum: Other OS Talk
---

### Post by PurposeOfReason on 2009-01-11
I have a spare computer that I have lying around and got the idea to turn it into a sort of server/media center. I would put all my music/videos and whatnot on it, and hook it up to the tv and use xbmc or the like to play it all there, then mount the HDD with music on it through my other computer remotely for mpd to use (can that be done?). Same goes for pictures and all that. Beyond that, I would like to have a webpage for it, using a static ip, where I could link to all the folders for documents/pictures/etc. for access to them easily if I'm not at home.

From what I gather, all of this is possible, having one computer keep all my documents and all that, as well as being able to play them for a media fronend and even remote access. I was thinking of using freebsd but the 64bit version does not have a nvidia driver for it (will have a 9600gt in the box) and don't know if I would take a big hit on video (1080p) playback.

Thanks for any light you can shed on this project.

---

### Post by handy on 2009-01-11
Have a look at FreeNAS, is is tiny, based on FreeBSD, it has a great web browser based GUI.

I have it set up on a test machine, I have been storing media on it, it can be set up as a torrent slave as well, I'm part way through doing that to my test box.

On a 10/100 LAN, I can be copying a large file across to FreeNAS, whilst it is also downloading torrents & streaming a movie to another computer.

I haven't looked into some of the things you want to do, if you have a look around on their website & forum you should be able to find out if they are possible.

For my use, FreeNAS is brilliant, I'm going to build a low power MiniITX box for it.

---

### Post by ghindo on 2009-01-11
> **handy said:**
> For my use, FreeNAS is brilliant, I'm going to build a low power MiniITX box for it.If/when you end up doing that, would you mind doing a little write-up about it here on the forums or on your site?  I would love to read about that.

---

### Post by PurposeOfReason on 2009-01-11
FreeNAS looks nice from my quick reading of it. Though it didn't say anything about it being able to have a desktop GUI so run a media center front/backend. Do you know if that is possible?

---

### Post by handy on 2009-01-11
> **ghindo said:**
> If/when you end up doing that, would you mind doing a little write-up about it here on the forums or on your site?  I would love to read about that.
[B]
*[Edit:][/B] I'm in the process of trying to organize parts, from two sources, one has posted what I require to his supplier, so I expect a quote this coming week, which if I give the go ahead, it should (depending on availability of all components) mean I could have the parts by next weekend.  We'll see.) /edit*

Yes, I will for sure.

The easiest part is the hardware.

If I get inspired I'll do a how-to on setting up FreeNAS, NFS, Transmission watch directory (which is the fiddly part) so FreeNAS can be a torrent slave.

The way I see it with that lot, is once you have it set up the first time, you back up all of your configuration files into multiple safe places.  Then for me, (who has a deteriorating memory) writing up a how-to gives me a step by step recovery procedure in the future if/when I need it, & has the very welcome added feature of making it easier for someone else too.  Everybody wins. :-)  

> **PurposeOfReason said:**
> FreeNAS looks nice from my quick reading of it. Though it didn't say anything about it being able to have a desktop GUI so run a media center front/backend. Do you know if that is possible?

Usually once FreeNAS is set up, it would be run headless & you access its great configuration/monitoring GUI via your web browser from wherever using a username/password.

Any computers that you have made a connection to FreeNAS with you can access FreeNAS from, streaming video/audio media, images or whatever, FreeNAS doesn't care.

So the front end access to this data seems to me to be the potential sticking point for you & FreeNAS.

Have a look at [*_GeeXbox_*]("http://www.geexbox.org/en/index.html") apparently it works very well with FreeNAS, though I don't know if it will solve your problems.

---

### Post by billgoldberg on 2009-01-11
On the revision3 website, on the systm page, there is a video guide to freenas.

Check it out if you are intrested.

I suggest you give Boxee a try as the media center.

---

### Post by fistfullofroses on 2009-01-11
Install Mythbuntu, and then apt-get apache, and whatever media server/streamer you want.

---

### Post by PurposeOfReason on 2009-01-11
Mythbuntu would be pointless for me. Too much for what I need I should say. Any linux system can do the network filesystem with samba, and can make the web directory using apache. Really, I'm looking for something small, quick, and secure that I can shove a good media player on.

---

### Post by fistfullofroses on 2009-01-11
Well, in that case I would use Slackware/Arch.

---

### Post by PurposeOfReason on 2009-01-11
I'm more thinking a minimal debian as arch is a rolling release and from using it as a desktop, don't think it would be the best server. Slackware, I could try it I guess. Never done it at least.

---

### Post by Sorivenul on 2009-01-11
FreeNAS gets my vote here, too. I think it should be doable.

---

### Post by handy on 2009-01-11
> **billgoldberg said:**
> On the revision3 website, on the systm page, there is a video guide to freenas.

Check it out if you are intrested.

I suggest you give Boxee a try as the media center.

Thanks for bringing revision3 into my awareness billgoldberg.  I had a quick look at the forums last night & was pretty impressed with the quality of information.  Though it was only a quick look. :-)

---

