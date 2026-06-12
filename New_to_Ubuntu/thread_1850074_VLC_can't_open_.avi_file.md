---
title: "VLC can't open *.avi file"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by Osmodivs on 2011-09-25
I thought VLC was cool, but not anymore, since it CAN'T open a simple .avi file: 
```

[0x2ca0be0] avi demux error: avi module discarded (invalid file)
```Worst, Totem can open it, but I can't open .srt or .*** files for subtitles, I tried Kaffeine and it doesen't support subs either, Xine just crashes when I try to open a .srt file, Mplayer... well, that's a terminal based player, I am not that geeky. 
Thanks a lot LINUX, now I'll eat my popcorn "movieless"... :popcorn:

---

### Post by oldos2er on 2011-09-25
Post moved to its own thread, title changed.

---

### Post by Captain Smiley Pants on 2011-09-25
First*, if you haven't already, go here to make sure you have the correct codecs needed to play your video type:

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

Don't worry, I've been using Medibuntu as a repository for years, these guys are legit.

After that, try installing this:

**ubuntu-restricted-extras**

If it's already installed, do a complete removal and install it again. This will pick up on a few things, like Flash, but should also specifically pick up on the codecs needed for your video player.

If you need to play some purchased DVDs, you'll want to go through with this as well:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

*make sure you are legally able to do this in your country, blah blah blah

EDIT: And yea, I don't really use subtitles myself but I'll do a Google and see what I come up with.

EDIT2: Have you tried this? [http://linuxandfriends.com/2009/08/23/how-to-display-subtitles-for-movies-in-totem-player/](http://linuxandfriends.com/2009/08/23/how-to-display-subtitles-for-movies-in-totem-player/) If you could post a little more of what's been done thus far besides error messages, that'd be cool too.

---

### Post by pjd99 on 2011-09-25
> **Captain Smiley Pants said:**
> First*, if you haven't already, go here to make sure you have the correct codecs needed to play your video type:

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

Don't worry, I've been using Medibuntu as a repository for years, these guys are legit.

After that, try installing this:

**ubuntu-restricted-extras**

If it's already installed, do a complete removal and install it again. This will pick up on a few things, like Flash, but should also specifically pick up on the codecs needed for your video player.

If you need to play some purchased DVDs, you'll want to go through with this as well:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

*make sure you are legally able to do this in your country, blah blah blah

EDIT: And yea, I don't really use subtitles myself but I'll do a Google and see what I come up with.
While this is always useful, it will have no impact on VLC's ability to play video files (cept dvd's) as it contains its own set of decoders (based on ffmpeg i think). Also, the problem is with the avi, and avi is not a codec, it's a container.

Install mediainfo (i think it's in the medibuntu repos) and see what it says about the file. VLC is saying it's not properly constructed/not an .avi file.

---

### Post by Captain Smiley Pants on 2011-09-25
> **pjd99 said:**
> While this is always useful, it will have no impact on VLC's ability to play video files (cept dvd's) as it contains its own set of decoders (based on ffmpeg i think). Also, the problem is with the avi, and avi is not a codec, it's a container.

Install mediainfo (i think it's in the medibuntu repos) and see what it says about the file. VLC is saying it's not properly constructed/not an .avi file.

Bah, forgot about that too. Brain fart.

---

### Post by coffeecat on 2011-09-25
> **pjd99 said:**
> Install mediainfo (i think it's in the medibuntu repos) and see what it says about the file.

That's very useful - thanks. I'd not heard of it before and did a bit of digging. I don't see it in medibuntu or the Ubuntu repos, but I found this:

[http://mediainfo.sourceforge.net/en](http://mediainfo.sourceforge.net/en)

Which leads to this:

[http://mediainfo.sourceforge.net/en/Download](http://mediainfo.sourceforge.net/en/Download)

And this:

[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

I'll be interested to see if the OP has a bad AVI file.

---

### Post by pjd99 on 2011-09-25
That's right, I installed it from a PPA... I just noticed that it seems to be lacking features it used to have. Probably a Natty issue, as there's no menus anymore.

---

### Post by andrew.46 on 2011-09-25
> **Osmodivs said:**
> Mplayer... well, that's a terminal based player, I am not that geeky.

MPlayer has a few graphical frontends, perhaps try SMPlayer:

```
sudo apt-get install smplayer
```

---

### Post by pjd99 on 2011-09-26
> **andrew.46 said:**
> MPlayer has a few graphical frontends, perhaps try SMPlayer:

```
sudo apt-get install smplayer
```

+1 for mplayer. Very few files refuse to work with this marvellous piece of software.

I'll give a shout out to gmplayer (mplayer-gui in the repos), that's my favourite gui for it. Never could get used to the others...

---

### Post by andrew.46 on 2011-09-26
> **pjd99 said:**
> I'll give a shout out to gmplayer (mplayer-gui in the repos), that's my favourite gui for it. Never could get used to the others...

Mind you there is a new kid on the block that is taking up where SMPlayer left off and that is UMPlayer. A very capable gui for the commandline player which I did not mention before as it is not yet in the Ubuntu repositories :(.

---

