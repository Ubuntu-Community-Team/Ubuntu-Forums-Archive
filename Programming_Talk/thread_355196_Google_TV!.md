---
title: "Google TV!"
date: 2007-02-06
forum: Programming Talk
---

### Post by raid517 on 2007-02-06
Hi OK this is something that is born out of my own frustration at the big companies dragging their heels on providing a cheap reliable and universal IPTV service.

In any case we have all heard the hype about Google supposedly one day possibly offering a Google IPTV type service - but Google themselves have generally shown little interest in this.

This has meant that people like me have had to improvise to cobble together some crude IPTV type services of their own.

Currently I use TVersity (which is a windows only application right now, due to the requirement of compatibility with certain Windows Media formats used by several mobile devices). I would like an equivalent for Ubuntu - but at this current time, no such equivalent exists.

Nonetheless TVersity is a very interesting application. Among several things that it does, it can stream/transcode virtually any media type to any UPNP capable device - so that for example this means that your entire music, video and image collection can be streamed to your phone, your MP3 player, your Xbox, your PlayStation, your laptop and so on.

Overall UPNP is a very powerful, though misunderstood and wrongly neglected protocol which affords a great deal of power to a users fingertips. With a reliable UPNP server enabled, you can walk virtually into any scenario and have all of the media in that environment available immediately with zero additional configuration by the user whatsoever.

In any case, sadly even TVersity has it's limitations. It can't for example save a locally encoded copy of a transcoded stream, so that you could perhaps save that copy load it on an MP4 type PMP media player and take it out when it is loaded on your player in order to watch it later.

Moreover Tversity can not serve up full blown Internet TV channels - only individual streams.

To demonstrate what I mean, here is a selection of my own customised and favorite Google video feeds:

[http://video.google.co.uk/videofeed?type=search&q=genre%3Acomedy+duration%3Along+is%3Afree&so=0&num=20&output=rss](http://video.google.co.uk/videofeed?type=search&q=genre%3Acomedy+duration%3Along+is%3Afree&so=0&num=20&output=rss)

[http://video.google.com/videofeed?type=search&q=-jesus+-lord+-saviour+-christ+documentary+duration%3Along&so=0&num=20&output=rss](http://video.google.com/videofeed?type=search&q=-jesus+-lord+-saviour+-christ+documentary+duration%3Along&so=0&num=20&output=rss)

[http://video.google.co.uk/videosearch?so=0&q=type%3Amusic_video+is%3Afree+duration%3Amedium&start=0](http://video.google.co.uk/videosearch?so=0&q=type%3Amusic_video+is%3Afree+duration%3Amedium&start=0)

[http://video.google.co.uk/videofeed?type=search&q=type%3Asports+OR+genre%3Asports&so=0&num=20&output=rss](http://video.google.co.uk/videofeed?type=search&q=type%3Asports+OR+genre%3Asports&so=0&num=20&output=rss)

These essentially constitute 4 unique channels and are almost infinitely configurable using Google's video search API. For example you could equally have a feed that only showed videos that were 20 minutes long, in specific format (the available feed selections are .avi .mp4 and .flv) discussed only the subject of cats and excluded a certain breed of cat. e.g.:

[http://video.google.co.uk/videofeed?type=search&q=cats+duration%3Along+-persian&so=0&num=20&output=rss](http://video.google.co.uk/videofeed?type=search&q=cats+duration%3Along+-persian&so=0&num=20&output=rss)

There are many other search operators you can use (see a short description of the main ones here: [http://labnol.blogspot.com/2006/09/google-video-search-operators-how-to.html](http://labnol.blogspot.com/2006/09/google-video-search-operators-how-to.html)) but essentially you can pretty much construct your own individual TV channels based on your own specific preferences.

And herein lies the bones of an idea. In the case of TVersity it will happily list the individual streams available in each .rss feed and if needed, depending on the device you are using (which it can automatically detect)  it can play back/transcode these streams to your UPNP compatible device in a suitable/compatible format. But (and this is a very significant point) it can't play/stream each individual stream in a continuous way. That is to say it can't play all of the streams in a feed 'back to back', or one after the other - in a similar way to the way a normal TV works. In other words once it has finished playing back a specific stream, it will stop and the user will have to manually select the next stream and hit play on his device to begin playing this next new stream.

Not a big issue you might think. But having spoken to several people in the past about these topics, one thing I have heard them say is that they like the differences between the Internet and normal TV - and that if they are watching TV they want this to be a largely passive pursuit - unlike in the case of their computers and the Internet which is often a very interactive and time consuming activity.

So the question is, what if you could have an application like TVersity, which could serve up these streams to compatible UPNP type devices and which were comprised of 'channels' or 'feeds' that were able to conform very tightly to one's own specific set of criteria - but which was also capable of playing back the individual videos contained in these feeds in a continuous 'back to back way? (Although a shuffle feature might be useful too, so that the programming/content was a little randomised - and wasn't always too predictable). Essentially if you did this, you would have created GoogleTV without the need for any intervention or involvement of Google management or developers whatsoever.

We all long for Google TV (and other services like it) so why not do it? Why not just make it happen?

Unfortunately my problem is that I am not a programmer and that I wouldn't know where to start with something like this. So this is basically just a suggestion which I hope someone else here will see and will take up. The other problem of course is that Tversity is Windows only - and here is the ball breaker in my own view, because bizarrely, even though it uses several open source components to do what it does, the software itself is not open source.

So really I think that we need a better and equivalent answer that can be used on Ubuntu and on the Linux platform in general.

You guys however are programmers - and if you want Linux to remain relevant, I think it is important that the Linux platform doesn't get left behind by the impending IPTV revolution. 

So please, please can some whizzbang top gun programmer out there try to think of a way to make this happen?

This is an opportunity I think to steal a march on other platforms. Think of it if you will, where one day you have an iPTV capability where you get to choose exactly the kind of programming you want, to filter, add and remove content based on a specific set of criteria, to include content only on a specific subject - starring a specific actor and excluding another, or in an exact format/duration. All of this could be possible with a little thought and a little innovation.

I would therefore be very interested to hear what you guys here thought of this idea?

---

### Post by Shay Stephens on 2007-02-07
Have you looked at the democracy player?  Is that close to what you are thinking?

---

### Post by raid517 on 2007-02-07
It's close - but still a very long way away from what I want. It's really just an .rss feed aggregator and media player.

It can't handle custom Google .rss search strings, it has no transcoding or UPNP capability - it is buggy and slow as hell most of the time and the developers rarely respond to development requests.

So all in all not ideal.

---

