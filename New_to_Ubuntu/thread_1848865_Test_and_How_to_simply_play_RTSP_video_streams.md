---
title: "Test and How to simply play RTSP video streams ?"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-23
Hello, 

```
 cat rt2x | while read i ; do echo "$i" ; ffplay "$i" ; done
```

is not working :(

(From xterm please)

with rt2x contains
```
TV Channels:
rtsp://3gp-tv2.unwire.dk/livestreaming/tv2/tv2news/tv2news_108k.sdp
rtsp://202.146.92.43/Live/FTV/Astro_FTV.sdp
rtsp://stream.roktv.com/rtpencoder/v2_music.sdp
rtsp://stream.roktv.com/rtpencoder/studio411.sdp
rtsp://stream.the.sk/live/joj/joj-hm.3gp
rtsp://stream.the.sk/live/aztv/aztv-hm.3gp
rtsp://stream.the.sk/live/musicbox/musicbox-hm.3gp


AdventureFree.TV
rtsp://video3.multicasttech.com/AFTVAdventure3GPP296.sdp

CartoonsFree.TV
rtsp://video2.multicasttech.com/AFTVCartoons3GPP296.sdp

ClassicsFree.TV
rtsp://video3.multicasttech.com/AFTVClassics3GPP296.sdp

ComedyFree.TV
rtsp://video3.multicasttech.com/AFTVComedy3GPP296.sdp

CrimeFree.TV
rtsp://video2.multicasttech.com/AFTVCrime3GPP296.sdp

HalloweenFree.TV<
rtsp://video3.multicasttech.com/AFTVHalloween3GPP296.sdp

HorrorFree.TV
rtsp://video2.multicasttech.com/AFTVHorror3GPP296.sdp

IndyMovies.TV
rtsp://video2.multicasttech.com/AFTVIndyMovies3GPP296.sdp

MysteryFree.TV
rtsp://video2.multicasttech.com/AFTVMystery3GPP296.sdp

SciFiFree.TV
rtsp://video2.multicasttech.com/AFTVSciFi3GPP296.sdp

WesternsFree.TV
rtsp://video2.multicasttech.com/AFTVWesterns3GPP296.sdp

EspanaFree.TV
rtsp://video3.multicasttech.com/EspanaFree3GPP296.sdp

Radio:

WKSU (NPR)
rtsp://mobile.wksu.org/wksu.sdp

rtsp://lyssna-mp4.sr.se/live/mobile/SR-P1.sdp
rtsp://lyssna-mp4.sr.se/live/mobile/SR-P3.sdp
rtsp://lyssna-mp4.sr.se/live/mobile/SR-P3Star.sdp
rtsp://lyssna-mp4.sr.se/live/mobile/SR-P3Rockster.sdp
rtsp://lyssna-mp4.sr.se/live/mobile/SR-P3Svea.sdp
rtsp://lyssna-mp4.sr.se/live/mobile/SR-DinGata.sdp
rtsp://lyssna-mp4.sr.se/live/mobile/SR-P3Street.sdp
rtsp://lyssna-mp4.sr.se/live/mobile/SR-Metropol.sdp
rtsp://lyssna-mp4.sr.se/live/mobile/SR-P4.sdp
rtsp://stream.zoovision.com/zvradio.sdp
rtsp://stream.zoovision.com/fkrzv.sdp
```

thank you

---

### Post by honeybear on 2011-09-23
does it work for you? 

And if we use : openRTSP instead of ffplay?

```
apt-get install livemedia-utils 
```
contains openRTSP

this one, I know it works...  rtsp://dmzosx001.dpa.act.gov.au/medium
or this one: 
rtsp://184.72.239.149/vod/mp4:BigBuckBunny_175k.mov

---

