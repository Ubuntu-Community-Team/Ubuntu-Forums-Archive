---
title: "Can't compile last VLC"
date: 2009-01-01
forum: Programming Talk
---

### Post by psychok9 on 2009-01-01
Bootstrap done.
After I've type ./configure --prefix=/usr
...this is the error from config.log:
```
configure:45594: checking for SWSCALE
configure:45602: $PKG_CONFIG --exists --print-errors "libswscale"
Package 'libswscale' requires 'libavutil = 49.6.0' but version of libavutil is 49.12.0
configure:45605: $? = 1
configure:45620: $PKG_CONFIG --exists --print-errors "libswscale"
Package 'libswscale' requires 'libavutil = 49.6.0' but version of libavutil is 49.12.0
configure:45623: $? = 1
Package 'libswscale' requires 'libavutil = 49.6.0' but version of libavutil is 49.12.0
configure:45651: result: no
configure:45654: WARNING: Could not find libswscale. Trying to enable imgresample.
```
Any help? libswscale is present.

---

