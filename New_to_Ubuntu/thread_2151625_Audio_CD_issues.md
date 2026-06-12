---
title: "Audio CD issues"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by frodo5632 on 2013-06-05
I am new to Kubuntu, I am running 13.04, and have had to dig for everything to get it working properly, no dvd playback, no netflix, having to open terminals to do the simplest things that would not work until command line stuff was entered to get whatever device permission to do whatever. I am tired of having to input passwords evertime a fly farts. I have been in computer since Concurrent CPM was the big thing, and I have never seen more paranoid computer users in my life. 

I am wondering why the default installed media player won't play audio cds, and the default installed cd burning software won't write them correctly? When I insert an audio cd it will open Amarok but will not play the disc...  I have been able to play them with media player for Gnome, but the KDE stuff won't? Also when trying to burn cds the software says it's burning but it just writes a bunch of directories with 0 length files in them...  It would seem to me that if something don't work it shouldn't be included as default software...  

How do I get the default software to work?

---

### Post by Feathers McGraw on 2013-06-05
Hi Frodo5632

I had the same problem to begin with. *buntu doesn't come with proprietary codecs etc. by default, so e.g. whereas VLC on Windows will run pretty much everything straight away, VLC in Ubuntu requires you to install the codecs manually.

I think the point is that you have to make a conscious choice to install non-FOSS software instead of anyone slipping something in under the radar.

Fortunately, you get them all from [Medibuntu]("http://www.medibuntu.org/repository.php")

There's an install guide on the page but here's the code for convenience:

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

And then to play encrypted DVDs:

```
sudo apt-get install libdvdcss2
```

To install codecs for a 32 bit version:
```
sudo apt-get install w32codecs
```
or for a 64 bit version:
```
sudo apt-get install w64codecs
```

Hope that helps,

Feathers

---

