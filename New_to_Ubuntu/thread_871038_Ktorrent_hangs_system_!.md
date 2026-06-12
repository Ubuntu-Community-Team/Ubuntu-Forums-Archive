---
title: "Ktorrent hangs system !"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-26
Hi! I'm Melvin from India. I'm using Ubuntu Linux since i'm fedup of viruses in windows. i've posted previously in he ubuntu forum about a good bittorrent client with lots of features. I've got the reply as Ktorrent. I'm running Gnome, and i installed Ktorrent on it. Now, after some time, Ktorrent hangs the whole computer. nothing on the screen works. What could be wrong, please? How to solve this?

---

### Post by hyper_ch on 2008-07-26
you might be running out of ram - depending on your machine...

ktorrent isn't really a light client.... I personally use rtorrent - which is cli based.

---

### Post by BGFG on 2008-07-26
I'd suggest Transmission or Deluge, they seem to be the frontrunners. I prefer Deluge though, more control over features and in my opinion, faster. Both work extremely well though.

---

### Post by Ximal on 2008-10-20
I have the problem of ktorrent hogging all system resources until I limited it to a maximum of 25% of my cpu though to the life of me I cannot figure out how to limit the use of the ram by ktorrent for only 256 megs of ram memory or 25%of the 1 gig memory if possible .. 

I also tried deluge but am worried because it is not as rich featured or I am un able to understand it... and it does not download as fast as ktorrent seems to be downloading. Is there a way possibly that ktorrent would be set to use only a certain amount of memory from within it' own options ? oh well.. hope someone can help further...

---

### Post by simtaalo on 2008-10-20
sometimes using kde apps in gnome can cause problems, most of the time its fine but occasionally it can cause issues.

deluge is favoured by many users on here as a very good client. personally i just use transmission and never had a problem, but im not a heavy torrent user.

---

### Post by HittingSmoke on 2008-10-20
> **Ximal said:**
> I have the problem of ktorrent hogging all system resources until I limited it to a maximum of 25% of my cpu though to the life of me I cannot figure out how to limit the use of the ram by ktorrent for only 256 megs of ram memory or 25%of the 1 gig memory if possible .. 

I also tried deluge but am worried because it is not as rich featured or I am un able to understand it... and it does not download as fast as ktorrent seems to be downloading. Is there a way possibly that ktorrent would be set to use only a certain amount of memory from within it' own options ? oh well.. hope someone can help further...

I second the vote for Deluge. It may not seem feature rich out of the box, but there are quite a few common torrent client features that can be enabled by using the Plugins menu. Nothing to download, all you have to do is enable them.

I was a loyal utorrent user in Windows and Deluge is the closest I've come to simplicity, low footprint and features for Ubuntu so far. Ya can run utorrent in WINE but I'd much rather sacrifice a few features and have a native Linux app than run anything in wine

---

### Post by sethvath on 2008-10-20
Ktorrent's CPU and ram usage is pretty well documented and reported. [http://ktorrent.org/forum/viewtopic.php?t=2597&sid=16610bce878ccd8aced0d4baa32e4d53](http://ktorrent.org/forum/viewtopic.php?t=2597&sid=16610bce878ccd8aced0d4baa32e4d53)

I did a comparison on a fresh install of intrepid ibex beta for ktorrent, transmission and deluge-torrent. Ktorrent downloaded a 560mb file at 4.2mb/s, transmission at 2.7mb/s and deluge at a miserable 750kb/s. These are the top speeds for the exact same file on 3 different clients.

---

### Post by simtaalo on 2008-10-20
> **sethvath said:**
> 
I did a comparison on a fresh install of intrepid ibex beta for ktorrent, transmission and deluge-torrent. Ktorrent downloaded a 560mb file at 4.2mb/s, transmission at 2.7mb/s and deluge at a miserable 750kb/s. These are the top speeds for the exact same file on 3 different clients.

thats amazing, i never thought the client would make that much difference. well looks like im going to install ktorrent :lolflag:

---

### Post by sethvath on 2008-10-20
> **HittingSmoke said:**
> 
I was a loyal utorrent user in Windows and Deluge is the closest I've come to simplicity, low footprint and features for Ubuntu so far. Ya can run utorrent in WINE but I'd much rather sacrifice a few features and have a native Linux app than run anything in wine

Guess what, utorrent 1.7.7 downloads faster than deluge even under wine. I ought to find some software to plot the average download rate of each client as a chart. Of course YMMV depending on your broadband connection and system spec.

---

### Post by milesinnz on 2008-10-26
Ktorrent used to work fine - up until a few weeks ago - on 512mb - there seems to be a memory problem not necessarily directly related to Ktorrent - but sorry can't find an answer yet, hoping an update will be actioned to correct the issue.

---

### Post by milesinnz on 2008-10-26
Ah, I found out what changed when I was successfully using Ktorrent in the past.

I upgraded to Hardy by a fresh installation and reinstalled Ktorrent from the option in “Applications - add/remove”.

Looking at the Ktorrent applications from System – Administration – Synaptic Package Manager, and doing a “search” for Ktorrent I find there are two Ktorrent packages shown.

I installed the first Ktorrent listed (not the Ktorrent-Kde4 – which was shown correctly as installed already) and of course there are now two versions of Ktorrent under “applications – internet”. Using the second one runs Ktorrent 2.2.5 which I can now see is the one I have been using with no problems for ages! On a 32bit 1.8 ghz 512Mb desktop.

---

### Post by SogdianTux on 2008-12-08
Good to know, I also saw that in Synaptic Package Manager but i wasn't sure.... 
I didn't know why every time i use Ktorrent my CPU usage was between 66% to 90% .... I didn't want to use another Torrent SW cause I tried many and so far Ktorrent has been the best in terms of speed. I'll now go try " (not the Ktorrent-Kde4 " and let you know the results :) 

Thanks

---

### Post by Ximal on 2008-12-12
actually guys i installed lamp... downloaded myphpadmin from the main website and only put it in my www folder when i want to use it ;) and i use [www.torrentflux.com](www.torrentflux.com) 's  torrent prog which when properly installed does everything i need from making a torrent and uploading to allowing me to create logins for friends so they can download via my server then download through zip ... it's a great way also to have your torrents with you on the go if you don't want to ssh or vpn into anything... i like it.. so i've stuck with it... ):P

---

