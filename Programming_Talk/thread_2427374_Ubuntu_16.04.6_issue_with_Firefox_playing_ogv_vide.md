---
title: "Ubuntu 16.04.6 issue with Firefox playing ogv videos"
date: 2019-09-21
forum: Programming Talk
---

### Post by Ulf_Dunkel on 2019-09-21
Hi there.

I have set up an Ubuntu 16.04.6 client (i686) who serves as a video advertisements panel. It loads videos (20 seconds each, no audio) in OGV format from its local hard drive and plays them in the current Firefox 69.0 browser window in an endless loop. The list of videos is created by a PHP script and the videos themselves are played by the document.element.play() function, driven by a JavaScript. Everything was fine with this procedure since Ubuntu 12.x ... up to Ubuntu 16.04.5.

Now I have updated that client to Ubuntu 16.04.6 and it is stuck when playing the first frame(s?) of the first video. I have no idea what has changed and how I can fix this issue. This only occurs in that specific ad.php script which gets the video files from the client's hard drive, not from the web. If I open a website page which plays the same OGV videos, in another browser window, the videos run smoothly to the end as expected.

No PHP errors are shown. The JavaScripts are unchanged. I guess the codecs might have changed from 16.04.5 to 16.04.6 but they all seem to be up-to-date. And no, I cannot update this client to 18.x right now, for reasons.

Edit: The codecs seems to be fine. When I download a sample OGV video like this one ([https://ia800701.us.archive.org/26/items/SampleVideo1280x7205mb/SampleVideo_1280x720_5mb.ogv](https://ia800701.us.archive.org/26/items/SampleVideo1280x7205mb/SampleVideo_1280x720_5mb.ogv)), and let it play in another Firefox window from /localhost/, it also runs smoothly. Maybe it is a video loading timeout issue? I added another JavaScript EventListeners for "load" and it seems as if only the first frame of the first video will be loaded. :-(

Any hints or help are really appreciated.

Thank you.

---

### Post by SeijiSensei on 2019-09-21
Have you tried other browsers like Chromium or its spin-offs like Brave?

---

### Post by Ulf_Dunkel on 2019-09-22
Thank you for your suggestion, SeijiSensei.

This went weird. I firstly installed Chromium, which launches but reacts extremely slow on everything I do within a browser window or URL input bar. When I have clicked into the URL field and type something, I have to wait about 30 seconds (!) until the typed stuff is being shown. When I pick a PHP file from my computer to be shown in the browser window, it won't be loaded at all. It's unusable.

I couldn't even install Brave. It doesn't support 32bit machines.

So I installed Midori, loaded the [http://localhost/ad.php](http://localhost/ad.php) and it runs videos like a charme.

As I cannot change the set up Firefox browser on multiple clients like this one without huge efforts, I would like to find out what has changed in Firefox from Ubuntu 16.04.5 to 16.04.6 that makes it so difficult for it to load my videos when triggered by the document.element.play() function.
[URL="https://support.brave.com/hc/en-us/articles/360018666072-How-do-I-install-Brave-on-Linux-using-the-terminal-"]
[/URL]

---

### Post by Ulf_Dunkel on 2019-09-22
I guess I found and resolved the issue myself now.

Because Midori showed everything as expected, it couldn't be my script (which worked fine since 7 years). Because Firefox plays the videos when loaded as single files, not via the script, it couldn't be a codec. Because updating to Firefox 70.0 beta #8 didn't resolve the issue, it couldn't be Firefox itself, but one of its settings which seems to be different from its state in Ubuntu 16.04.5. By chance, I then saw in the Firefox URL bar, that it shows a tiny icon telling me that autoplay for videos with audio is not allowed. When I switched this (now default?) to "Allow autoplay for video and audio", everything works again as expected.

I can now update all clients via VPN tunnel, sending an updated user preferences file user.js with this line added:
[B]user_pref("media.autoplay.default", 0);

[/B]This line doesn't seem to be part of the default prefs.js if set to 1, though.Maybe this thread can help others, too, who struggle with autoplay mode.

---

