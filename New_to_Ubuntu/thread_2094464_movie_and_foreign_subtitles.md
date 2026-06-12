---
title: "movie and foreign subtitles"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by briar rabbit on 2012-12-13
Hello,

I have ubuntu 10.04.

I used to could play DVD's that would show subtitles only for the foreign language like you would see it in the theatres.  Now the mplayer I have always used no longer shows those subtitles.  Can someone help me to fix that?

Also, I have acidrip which I like, it is very simple :-).  The problem with acidrip is I can not download the foreign subtitles which is the part of the movie spoken in a foreign language.

I have looked for an answer here on the forums but, could not find anything.

Any help is appreciated.

---

### Post by TOMBSTONEV2 on 2012-12-14
From what I gather, when another language is spoken in the movies you are watching the subtitles are not appearing.

Certain DVD's have copy protection, programs that copy the DVD to your hard drive have to decrypt the DVD's copy protection to do so. Sometimes the programs used to copy DVD's misidentify the subtitles as part of the copy protection.

It seems to me that Acidrip is removing the subtitles with the copy protection. This happens in many other DVD ripping programs as well.

---

### Post by SeijiSensei on 2012-12-14
Handbrake will rip DVDs to the Matroska or MP4 container and preserve the subtitles.  I recommend using the version that John Stebbins maintains in his [PPA]("https://launchpad.net/~stebbins/+archive/handbrake-releases").

The current version of SMPlayer seems to handle subtitled DVDs correctly, at least the [one]("http://www.imdb.com/title/tt1156240/") I just threw at it for testing.  SMPlayer is in the standard repositories.

---

### Post by DuckHook on 2012-12-15
...ehrm, I am forced to note that these forums do not approve of requests dealing with "download [of] the foreign subtitles". If you meant ripping the subtitles from DVDs that you already own, then I apologize for any possible misunderstanding.

---

### Post by andrew.46 on 2012-12-20
> **DuckHook said:**
> ...ehrm, I am forced to note that these forums do not approve of requests dealing with "download [of] the foreign subtitles". If you meant ripping the subtitles from DVDs that you already own, then I apologize for any possible misunderstanding.

SMPlayer has the ability to download subtitles from OpenSubtitles.org, quite a handy feature btw, which as far as I know is not illegal in any shape or form. I have been wrong before of course.....

---

### Post by SeijiSensei on 2012-12-20
> **andrew.46 said:**
> SMPlayer has the ability to download subtitles from OpenSubtitles.org, quite a handy feature btw, which as far as I know is not illegal in any shape or form. I have been wrong before of course.....

Here you go, Andrew.

From the OpenSubtitles.org [Disclaimer]("http://www.opensubtitles.org/en/disclaimer")

> OpenSubtitles.org ("this website") offers direct downloads off our own server. These files are NOT illegal warez downloads, we only offer files that we believe we are free to redistribute. If any doubt occurs about the legality of any of our file downloads we will take them off right away after contacting us. We do not offer any kind of video/movie (avi, divx, xvid...) files or audio (mp3, wma, waw) files - we mainly provide movie's subtitles translated by users. Commercial use prohibited.

We make no gaurantees whatsoever, whether or not files/applications downloaded from our server works and/or contains virusses (but if it comes to our attention that any such thing is the case, we will, of course, cease to offer the file in question for download).

In the weird way that copyright law works, the rights to any "fansubs" distributed with an infringing copy are themselves still separately copyrighted and belong to the author(s). So in theory it is possible that some of the subtitle files at OpenSubtitles.org might be infringing were their authors to assert their rights.  I don't really see that happening.

---

### Post by andrew.46 on 2012-12-21
Intellectual rights do my head in sometimes :(. I spend some time extracting subtitles with the following rather slow process:

[http://www.andrews-corner.org/fist.html#subtitles](http://www.andrews-corner.org/fist.html#subtitles)

and I wonder if the copyright police would disapprove of these if I distributed them! Sigh.....

---

### Post by mc4man on 2012-12-21
> **andrew.46 said:**
> 
and I wonder if the copyright police would disapprove of these if I distributed them! Sigh.....
you never know but in such & related dvd matters it seems that right/wrong, legal/illegal comes done to whether any money is being made & more importantly 'is there any money to be had?'

---

### Post by monkeybrain2012 on 2012-12-21
> **DuckHook said:**
> ...ehrm, I am forced to note that these forums do not approve of requests dealing with "download [of] the foreign subtitles". If you meant ripping the subtitles from DVDs that you already own, then I apologize for any possible misunderstanding.

Oh please, if you are watching commercial dvds on Linux you may already break the law according to the copyright cartel (libdvdcss2). Do I really care?

@OP

+1 to handbrake. Choose MKV format then you can even have multiple subtitles (and audio tracks if the dvd has more than one)

---

### Post by andrew.46 on 2012-12-21
> **mc4man said:**
> you never know but in such & related dvd matters it seems that right/wrong, legal/illegal comes done to whether any money is being made & more importantly 'is there any money to be had?'

I could be sitting on a goldmine :)

---

### Post by DuckHook on 2012-12-21
> **monkeybrain2012 said:**
> Oh please, if you are watching commercial dvds on Linux you may already break the law according to the copyright cartel (libdvdcss2). Do I really care?

Actually, I'm on your side and in complete agreement with you. Have droned on endlessly among friends and family about the stupidity and futility of U.S. copyright law. Just trying to adhere to the code of conduct and protect the forum, is all. But perhaps I'll leave such alerts to the forum staff from now on.

---

