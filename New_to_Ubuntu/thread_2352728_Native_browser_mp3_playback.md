---
title: "Native browser mp3 playback"
date: 2017-02-15
forum: New to Ubuntu
---

### Post by lysander6662 on 2017-02-15
How does one get native mp3 playback within the browser [I use Opera]? I'm trying to get Bandcamp to play mp3s but it always says I need to enable Flash or native mp3 playback. I've tried

```
sudo apt-get install ubuntu-restricted-extras
```

with no luck. What else should I be doing?

---

### Post by howefield on 2017-02-15
If you are getting an error like this...

[ATTACH=CONFIG]273726[/ATTACH]

and want to install flash, I suggest enabling the Partner repository by loading up the Software & Updates application and from the "*Other Software*" tab select Canonical Partners (you don't need the source repository)

[ATTACH=CONFIG]273727[/ATTACH]

Close out and reload the softwares sources when prompted.

Then use your package manager of choice to install the adobe-flashplugin package. I'd use the terminal..

```
sudo apt install adobe-flashplugin
```

Close Opera browser if opened and restart.

---

### Post by lysander6662 on 2017-02-15
Thank you very much, I'll try this tonight. I would have thought that Flash was already installed since I have YouTube working. But maybe I'm wrong?

---

### Post by howefield on 2017-02-15
> **lysander6662 said:**
> Thank you very much, I'll try this tonight. I would have thought that Flash was already installed since I have YouTube working. But maybe I'm wrong?

Not having flash installed doesn't preclude youtube from playing, eg it could be using html5 to play video.

Going to [this page]("http://www.adobe.com/uk/software/flash/about/") will tell you if/what you have installed with regards flash.

Or you may have flash installed but not a version compatible with Opera.

---

### Post by Perfect Storm on 2017-02-15
/me ninjaed by howefield 

Isn't youtube html5 [https://www.youtube.com/html5?hl=en&gl=EN](https://www.youtube.com/html5?hl=en&gl=EN)

---

### Post by lysander6662 on 2017-02-15
Ah, I didn't realise that YouTube worked via HTML5 these days. 

Apparently they've switched over

[http://www.theverge.com/2015/1/27/7926001/youtube-drops-flash-for-html5-video-default](http://www.theverge.com/2015/1/27/7926001/youtube-drops-flash-for-html5-video-default)

That would explain it. Thanks very much to both of you.

---

### Post by lysander6662 on 2017-02-15
According to this page, Flash has been successfully installed now. 

[http://www.adobe.com/uk/software/flash/about/](http://www.adobe.com/uk/software/flash/about/)

Bandcamp doesn't work still, however. This time, no error message comes up, but the tracks still don't play. Any idea what I could be doing wrong?

---

### Post by Perfect Storm on 2017-02-15
i'm guessing it's this site you mean [https://bandcamp.com/](https://bandcamp.com/) works fine here. I use chrome without installing extra flash.

Try a different browser like chrome which comes with its own flash plugin.

---

### Post by howefield on 2017-02-15
> **lysander6662 said:**
> According to this page, Flash has been successfully installed now.

It has been quite hard keeping up with how best to install flash this past year or so.. :)

There are 2 variations of flash, currently NPAPI: 24.0.0.194 and PPAPI: 24.0.0.194. The former being suitable for the Firefox web browser and the latter being suitable for Opera or Chromium or Chrome style browsers.

You installed flash via ubuntu-restricted-extras which will give you the NPAPI version, ie Firefox should be fine but not Opera. So you are back to installing the adobe-flashplugin as per post #2. This package will install both versions of flash so all browsers should be ok for flash content. If you decide to install this I'd suggest purging the already installed flashplugin-installer.

On a side note, I'd caution against ubuntu-restricted-extras, but only for the reason that it contains several packages some of which you may not need or even want. It isn't a bad idea to install this package, but perhaps not necessarily a good idea either ;)

---

### Post by lysander6662 on 2017-02-15
OK, so I purged and reinstalled via the method in post #2, still no luck I'm afraid. Most strange. I found this link

[http://ubuntuhandbook.org/index.php/2016/10/pepper-flash-chromium-opera-ubuntu/](http://ubuntuhandbook.org/index.php/2016/10/pepper-flash-chromium-opera-ubuntu/)

And got as far as stage 3 before thinking I would mess things up and didn't go any further!

---

### Post by howefield on 2017-02-15
> **lysander6662 said:**
> OK, so I purged and reinstalled via the method in post #2, still no luck I'm afraid. Most strange. I found this link

What does the [About Flash]("http://www.adobe.com/uk/software/flash/about/") page say about your version, and you restarted Opera ?

---

### Post by lysander6662 on 2017-02-15
I did indeed. All it says is this:

**You have version 24,0,0,194 installed**

Doesn't say which though....

---

### Post by howefield on 2017-02-15
Stumped then, I can repeat it - uninstall adobe-flashplugin and bandcamp stops playing and errors, reinstall adobe-flashplugin and plays no problem, lather, rinse, repeat ad nauseam.

What is the output of the terminal command..

```
apt-cache policy adobe-flashplugin
```

---

### Post by Geoffrey_Arndt on 2017-02-15
Maybe worth checking out Chromium . . . the open-source browser that Chrome is built on.   Very solid media support.

---

### Post by lysander6662 on 2017-02-15
> **howefield said:**
> Stumped then, I can repeat it - uninstall adobe-flashplugin and bandcamp stops playing and errors, reinstall adobe-flashplugin and plays no problem, lather, rinse, repeat ad nauseam.

What is the output of the terminal command.. 

Thank you for your help, which has been invaluable throughout this thread and others. Weird that it's not working. Output is

```
lysander@psychopig-xxiii:~$ apt-cache policy adobe-flashpluginadobe-flashplugin:
  Installed: 1:20170110.1-0ubuntu0.16.04.1
  Candidate: 1:20170110.1-0ubuntu0.16.04.1
  Version table:
 *** 1:20170110.1-0ubuntu0.16.04.1 500
        500 http://archive.canonical.com/ubuntu xenial/partner amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by mc4man on 2017-02-15
Another continuing problem with opera, best solution is to use just about any other browser.
If you must you'd need to replace /usr/lib/x86_64-linux-gnu/opera/libffmpeg.so with libffmpeg.so extracted from the latest chromium-codecs-ffmpeg-extra_**56**... package. 
Then your bandcamp, ect. would work, at least till opera upgraded at which point the search & replace would start again..

Ex. in screens, .deb downloaded from here - [https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage/+packages](https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage/+packages)
Right click on downloaded .deb > extract here, open extracted folder > right click on data.tar.xz > extract here > open /usr/lib/chromium-browser to find file -  screen 1
Put in the  /usr/lib/x86_64-linux-gnu/opera/ folder as root - screen 2
opera working on bandcamp - screen 3

---

### Post by howefield on 2017-02-16
> **mc4man said:**
> If you must you'd need to replace /usr/lib/x86_64-linux-gnu/opera/libffmpeg.so with libffmpeg.so extracted from the latest chromium-codecs-ffmpeg-extra_**56**... package. 

Hmm.. forgot about this, I'd filed this away when last you wrote about it in case I started using Opera again, although didn't need it when testing bandcamp with Opera version 43.0.2442.806.

---

### Post by lysander6662 on 2017-02-16
> **mc4man said:**
> Another continuing problem with opera, best solution is to use just about any other browser.
If you must you'd need to replace /usr/lib/x86_64-linux-gnu/opera/libffmpeg.so with libffmpeg.so extracted from the latest chromium-codecs-ffmpeg-extra_**56**... package. 
Then your bandcamp, ect. would work, at least till opera upgraded at which point the search & replace would start again..

Ex. in screens, .deb downloaded from here - [https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage/+packages](https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage/+packages)
Right click on downloaded .deb > extract here, open extracted folder > right click on data.tar.xz > extract here > open /usr/lib/chromium-browser to find file -  screen 1
Put in the  /usr/lib/x86_64-linux-gnu/opera/ folder as root - screen 2
opera working on bandcamp - screen 3

I think for now I'll take your advice by using Firefox instead for Bandcamp. Opera does update itself quite often and I don't want to have to keep updating other parts of it for Bandcamp. It's not a site I play through that often, and at least it works in Firefox. I've been using Opera since I owned my first PC in 2004 and am not about to change it, but for one site it's fine. It would be great if they had a client. Anyway, I find it unusual that Opera don't do this themselves, they must be aware of it.

---

### Post by mc4man on 2017-02-16
> **lysander6662 said:**
> I think for now I'll take your advice by using Firefox instead for Bandcamp. Opera does update itself quite often and I don't want to have to keep updating other parts of it for Bandcamp. It's not a site I play through that often, and at least it works in Firefox. I've been using Opera since I owned my first PC in 2004 and am not about to change it, but for one site it's fine. It would be great if they had a client. Anyway, I find it unusual that Opera don't do this themselves, they must be aware of it.
Probably better as a month ago one needed to use the .so from the chromium-55 package. Now that .so doesn't work & it needs the .so from the -56 package (which hasn't yet released in Ubuntu). 
So likely a never ending process unless opera decided to start supporting such stuff better.

(- A lot of these codec issues in Opera come from them not being willing or able to get the licensing they'd need to offer support.

---

### Post by lysander6662 on 2017-03-12
OK, this works now. I have no idea what I did but some of the recent updates must have helped.

---

