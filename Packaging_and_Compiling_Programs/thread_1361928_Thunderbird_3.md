---
title: "Thunderbird 3"
date: 2009-12-22
forum: Packaging and Compiling Programs
---

### Post by michael37 on 2009-12-22
Thunderbird 3 and its associated extensions are in dire situation in  Ubuntu.  Lucid still provides only Thunderbird 2; nearly 2 weeks after TB3 release.  The only credible way to run TB3 is using Ubuntuzilla, but that relies on Mozilla builds, non-Ubuntuized packages and 32-bit code only.  64-bit support is non-existent.  Extensions are miss more than a hit.  Ubuntu-specific extensions simply don't work with Mozilla builds.

So far, fta is the only person supporting T-bird 3 using the mozilla-daily-builds, but the latter being daily builds are unstable.  It doesn't help with extensions, esp those which are architecture sensitive (32-bit vs 64-bit). 

I am recruiting here to start a PPA team which will provide Thunderbird 3 release debs and port/package important extensions, esp those architecture sensitive or Ubuntu-only.  So far, my to-do extension list includes lightning-extension and thunderbird-traybiff.

---

### Post by tad1073 on 2009-12-22
Never mind, didn't read all the post

[]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

---

### Post by wilee-nilee on 2009-12-22
Using the PPA version and have never found a PPA yet that was unstable but that is just my experience.

---

### Post by michael37 on 2009-12-22
> **wilee-nilee said:**
> Using the PPA version and have never found a PPA yet that was unstable but that is just my experience.

Are you using any extensions?  If yes, how come daily PPA changes have never broken them?

---

### Post by wilee-nilee on 2009-12-22
I don't use any addons.

As of now expecting Lucid to already have T3 as part of synaptic is a bit premature, there isn't even a upgrade from Hardy yet.

As is apparent with the lack of responses with this thread, you will probably have to do all the work yourself, in creating a new PPA.

Personally to me Thunderbird is just a email fetcher it doesn't matter to me whether it is T2 or T3, as long as it does the fetching.

I would assume that the T3 download from Mozilla would have the addons working continuously, I think a little patience is needed for any Ubuntu-centric changes and inclusion is needed.

---

### Post by michael37 on 2009-12-23
> **wilee-nilee said:**
> I don't use any addons.

As of now expecting Lucid to already have T3 as part of synaptic is a bit premature, there isn't even a upgrade from Hardy yet.

As is apparent with the lack of responses with this thread, you will probably have to do all the work yourself, in creating a new PPA.

Personally to me Thunderbird is just a email fetcher it doesn't matter to me whether it is T2 or T3, as long as it does the fetching.

I would assume that the T3 download from Mozilla would have the addons working continuously, I think a little patience is needed for any Ubuntu-centric changes and inclusion is needed.

I'll give it a week or two to see if there is more interest.  I think TB3 will truly outperform user expectations.  Email fetcher is OK (so was Firefox before Tabs), but I'm sure you will find new uses with Tab and Search.  I've been using it for about 6 months now, and I just can't go back anymore.

Tab and Search (Image source: [http://en-us.www.mozillamessaging.com/en-US/thunderbird/features/](http://en-us.www.mozillamessaging.com/en-US/thunderbird/features/)). 
[IMG]http://en-us.www.mozillamessaging.com/img/thunderbird/features/screenshot-tabs-search.jpg[/IMG]

Here is a picture with Calendar integrated with Tabs -- that's how I use it.  Courtesy of [this wonderful review]("http://ascher.ca/blog/2008/12/09/thunderbird-3-beta-1-a-platform-for-innovation-shapes-up/").
[IMG]http://farm4.static.flickr.com/3115/3094292059_b099806f0b.jpg[/IMG]

---

### Post by michael37 on 2009-12-23
I am closing the thread since it has been already handled (as of yesterday).

Beta packaging of Thunderbird release is now available.

[https://bugs.launchpad.net/baltix/+bug/314668](https://bugs.launchpad.net/baltix/+bug/314668)

---

