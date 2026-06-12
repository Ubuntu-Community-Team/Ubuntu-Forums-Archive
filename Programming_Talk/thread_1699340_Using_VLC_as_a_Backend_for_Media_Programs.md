---
title: "Using VLC as a Backend for Media Programs"
date: 2011-03-03
forum: Programming Talk
---

### Post by andras artois on 2011-03-03
Would it be possible to have a music player such as Banshee or Rhythmbox use VLC instead of regular codecs?

Thanks.

---

### Post by foxmuldr on 2011-03-03
> **andras artois said:**
> Would it be possible to have a music player such as Banshee or Rhythmbox use VLC instead of regular codecs?

Thanks.

No. The codecs are aggregate in the system, able to be used by any app. VLC is an app that uses the codecs in a particular and distinct way from other apps. The VLC authors would have to write a "codec wrapper" for their decoding abilities, one which presented itself as another codec, but resulted in being a tool for use within other apps. Very unlikely to happen.

---

### Post by Reiger on 2011-03-03
Assuming that you mean would it be possible for such programs to leverage the VLC code base for codecs and assorted goodies, then the answer is most definitely yes. VLC exposes a software library for that. 

In addition, there is a VLC backend for Phonon, meaning that any application build on top of Phonon will be able to &#8220;use VLC&#8221; (or gstreamer or xine for that matter) out of the box. The applications may be entirely unaware of this since they access the VLC code through an abstraction layer.

---

### Post by andras artois on 2011-03-03
> **Reiger said:**
> Assuming that you mean would it be possible for such programs to leverage the VLC code base for codecs and assorted goodies, then the answer is most definitely yes. VLC exposes a software library for that. 

In addition, there is a VLC backend for Phonon, meaning that any application build on top of Phonon will be able to “use VLC” (or gstreamer or xine for that matter) out of the box. The applications may be entirely unaware of this since they access the VLC code through an abstraction layer.

Thanks, that was exactly what I was after.

And thanks for the replies.

---

