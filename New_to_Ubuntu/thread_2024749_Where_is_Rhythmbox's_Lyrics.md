---
title: "Where is Rhythmbox's Lyrics?"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-14
I have activated the **Rhythmbox lyric's plug-in**, but no lyrics ever show-up?
Why?
I've tried to do googling, it said that there is a **.patch** file should be filepatch.
How to patch the file?
Please show me.
[SIZE=3]**Thank you.**[/SIZE]

---

### Post by MG&amp;TL on 2012-07-15
Patches typically require rebuilding the application from its source code. This is possible, but undesirable unless you like doing that.

Can you give us a link to the page with the patch instruction? Sometimes it just needs people who've done it before to decrypt it for you. :)

---

### Post by czgirb on 2012-07-16
> **MG&TL said:**
> Patches typically require rebuilding the application from its source code. This is possible, but undesirable unless you like doing that.

Can you give us a link to the page with the patch instruction? Sometimes it just needs people who've done it before to decrypt it for you. :)

The URL is [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=625256](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=625256)

> Attached patch solved problem for me:
cd /usr/lib/rhythmbox/plugins/context
patch -p0 < LyricsTab.patch

***, could you confirm this?
So, as you can see patch seems ugly. I really don't know why one entry != same entry, but their string representations are equivalent.
String representation is smth like <RhythmDBEntry at 0x3963a30>, looks like memory address and is unique for each entry. So, this works.
But why same plugin works in squeeze? May be this is some python problem?
$ python --version
Python 2.6.7

---

### Post by MG&amp;TL on 2012-07-16
Okay, well, we can give it a go.

Download the patch (we'll assume it goes into Downloads/), then run following commands:

```
cd /usr/lib/rhythmbox/plugins/context/

sudo patch -p0 < ~/Downloads/LyricsTab.patch
```

---

### Post by czgirb on 2012-07-16
> **MG&TL said:**
> Okay, well, we can give it a go.

Download the patch (we'll assume it goes into Downloads/), then run following commands:

```
cd /usr/lib/rhythmbox/plugins/context/

sudo patch -p0 < ~/Downloads/LyricsTab.patch
```

> 
***@***:~$ cd /usr/lib/rhythmbox/plugins/context/
***@***:/usr/lib/rhythmbox/plugins/context$ sudo patch -p0 < ~/Downloads/LyricsTab.patch
patching file LyricsTab.py
Hunk #1 FAILED at 140.
1 out of 1 hunk FAILED -- saving rejects to file LyricsTab.py.rej
***@***:/usr/lib/rhythmbox/plugins/context$ 


What it means?

---

### Post by MG&amp;TL on 2012-07-16
> **czgirb said:**
> What it means?

I've no idea. You can try with the --ignore-whitespace flag, but it's possible that Debian's patch doesn't work with Ubuntu.

I also think that the patch is outdated-the Debian version is 0.2.x whereas the Ubuntu version is 2.x.x. 

Try reporting a bug on launchpad, and see where that goes.

Sorry I can't help more.

---

### Post by czgirb on 2012-07-16
> **MG&TL said:**
> 
... Sorry I can't help more.

It's no need to say sorry ... U just help with all you can.
And I very appreciate for that.
Thank you very much.

> **MG&TL said:**
> 
... You can try with the --ignore-whitespace flag ...

What it means?

---

### Post by MG&amp;TL on 2012-07-16
> **czgirb said:**
> 
What it means?

```
sudo patch --ignore-whitespace -p0 < ~/Downloads/LyricsTab.patch
```

;)

---

### Post by davidmohammed on 2012-07-16
hmmm... I note that patch if for an older version of rhythmbox - 11.04 and before probably.

You didnt mention which version of rhythmbox and ubuntu version you were using.

Possibly your version of the lyrics plugin will not work with this old patch version.

---

### Post by czgirb on 2012-07-17
> **davidmohammed said:**
> hmmm... I note that patch if for an older version of rhythmbox - 11.04 and before probably.

You didnt mention which version of rhythmbox and ubuntu version you were using.

Possibly your version of the lyrics plugin will not work with this old patch version.

[B]Ubuntu = Ubuntu 12.04 (Precise Pangolin) LTS
Rhythmbox ... it was 12.04's default, right? I never do any changes.[/B]
[FONT=Times New Roman]**** Sorry I unable to A this Q, cos I'm not bring my lappie with me.***[/FONT]

---

### Post by davidmohammed on 2012-07-18
I similarly could not get the lyrics plugin to work in 12.04.  I gave up trying in the end.

Instead I used another lyric plugin - there is lyric plugin for rhythmbox 2.9x you can install from [github]("https://github.com/dmo60/lLyrics")

Alternatively if you are using 12.04 - I've packaged this in my [PPA]("https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins").  I've also written this up in a [Q&A format]("http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins") if you want a guide to install.

Hope this helps.

---

