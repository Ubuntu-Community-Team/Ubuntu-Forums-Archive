---
title: "Ubuntu vs Windows 7 torrenting and Networking altogether"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by daithy on 2012-10-31
Hi, first of all about me:
I am fairly new to Linux. I have been using Windows since I was a kid, not because of preference, but it was always present on the machine, so I am pretty used to Windows and simplicity, but then again I do not like Windows's rigitness and it's awful start ups, well thats just windows, like one big toilet that gets fuller and more clogged no matter how you clean up your registery or defrag or clean up or whatnot, however it can be be reliable at times with certain things e.g. 'networking'

I have Ubuntu 12.10 about a week now, I have backtrack as well, on my other hdd I'm still keeping my Win7.

I must say that I like Ubuntu a lot! but it has it's issues and I would like if I said no , right out of the box the screen was dimmed and couldn't be brightened becuase it's using alternative driver for my nvidia 7900 gs,ok. I do enjoy compiz and wobbly windows but sometimes the screen goes nuts and I gotta minimalize to make the screen act normally again, I have some issue with usb speakers everytime I change the alternative video driver ( I know it sounds crazy) to proprietry Nvidia, sounds starts to crackle when listening to youtube and etc. 
Also when you want to install programs on ubuntu,man! that's annoying if it isn't in the Software Center, I like the terminal but! this is time consuming especially when you are looking for suitable program so might install and reinstall perhaps 3-4 similar programs!

But overall I like Ubuntu's Graphical Interface, start ups are ok, and you can download pretty much you need.

Oh ya another thing, bought recently a webcam (it actually is microsoft as it happens),, the webcam has built-in drivers,although when plugged in Ubuntu, it was recognised straightaway but in skype there are no webcam settings, cannot adjust anything! It works but..........whereas in Windows it's just spot on and webcam settings are present in skype,hmmm

This was just a little user experience, now the point of this thread:
Torrenting :guitar:

I was impressed how Ubuntu connects to a network even before it properly starts up (healthy sign, maybe not)

I went for Utorrent because thats what I am used to use as windows user, even though I found it very unpopular in the Linux community, I was getting great results.
When I realised that the linux v. of utorrent is a sorry a$$ excuse and it's installed into the web browser, I was disgusted:( , I tried to run it via WINE and it had problems finding paths and had graphical issues.
I gave up
After a research  I tried

Transmission - insanily slow!

Ktorrent - I was amased that I had to download, I think it was 200mb via  Software Center , I would expect something like 7 mb for bittorrent client:confused: , anyway it was slow, I was at 300 kb/s on average

Deluge - That was probably the best of them all, but still bad around 600 kb/s

and all of them are fluctuating a lot ,not very stable with their speed.
And yes I have a port forwared that I always use, works fine with utorrent, used it with all of them.

Now I got pissed off, switched over to Win7 and download a file in utorrent, and bang there I get 2.3 mb/s as usual
I will post a screen shot below

I went back to Ubuntu, downloaded the plain .ugly version of utorrent, set it up to the right port, and to my suprise it was a lot, I mean far better than the stated clients above, what a disgrace, but still not close to the windows version, in fairness it reach up to good speed but it was fluctuating too, it can't hold on to the speed,
widows version holds the speed to the max

Maybe Ubuntu ain't that good and win7 ain't that bad, what are your views on this?


Both are the same torrent files, names are marked for my security  purposes

[IMG]http://imageshack.us/a/img801/2240/windowsutorrent.gif[/IMG][IMG]http://imageshack.us/a/img571/6981/linuxg.png[/IMG]

[IMG]http://imageshack.us/photo/my-images/801/windowsutorrent.gif/ http://imageshack.us/photo/my-images/571/linuxg.png/[/IMG][IMG]http://ubuntuforums.org/<a href=http://imageshack.us/photo/my-images/801/windowsutorrent.gif/ target=_blank>[img=http://imageshack.us/a/img801/2240/windowsutorrent.th.gif]</a> <a href=http://imageshack.us/photo/my-images/571/linuxg.png/ target=_blank>[img=http://imageshack.us/a/img571/6981/linuxg.th.png]</a>[/IMG]

---

### Post by pompel9 on 2012-11-01
When I use deluge I get speed on between 1.2 and 2.4 MB/s, all depending on how many seeds.

But I have yet to try it out in 12.10. The above speed was on 12.04.1


Have you checked under additional drivers. Maybe you ethernet card needs proprietary drivers to work properly. You can find additional drivers in software sources, the last tab.

---

### Post by HiImTye on 2012-11-01
in the slow one, you are connected to 36 sharers, and the other you are connected to 75 sharers (or somewhere around there, both are hard to read)
with a 500MB/s upload limit, the calculator optimizes for 94.85kB/s (7×13.55kB/s), which is the absolute best case uploading scenario per peer, using all of their dedicated upload slots. if you figure the average user doesn't even have their settings optimized for uploading to boost their downloads, they are likely optimized for something like 3-4kB/s per slot and run 4 slots per torrent. you are also sharing this with other peers.

the best thing to do to boost your speeds is optimize your uploads to boost your downloads

---

### Post by Cheesemill on 2012-11-01
I've never had any problems  with Deluge.

If I connect to a suitable torrent I can always max out my line at around 17Mb/s (which is as fast as it will go).

If you are looking for a good torrent to test with the [Arch Linux ISO]("https://www.archlinux.org/iso/2012.10.06/archlinux-2012.10.06-dual.iso.torrent") is always very fast.

---

### Post by Linuxisfast on 2012-11-01
Transmission has never ever given me grief one the ports are opened up properly, Ktorrent is great as well and the reason you needed to download all them files is because its KDE based, in case you used Kubuntu, it would be standard.

---

