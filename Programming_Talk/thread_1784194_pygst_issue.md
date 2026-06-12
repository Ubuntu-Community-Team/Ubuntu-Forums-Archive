---
title: "pygst issue"
date: 2011-06-16
forum: Programming Talk
---

### Post by Hairy_Palms on 2011-06-16
ive got a problem with a simple music player im currently making in python, it seems theres some sort of timing problem with gstreamer commands, so that if i call
```

self.player.set_property("uri", "file://" + filepath)
self.player.set_state(gst.STATE_PLAYING)
print((self.player.query_duration(gst.FORMAT_TIME, None)[0]))

```
it gives the following error
```
print(self.player.query_duration(gst.FORMAT_TIME, None)[0])
gst.QueryError: query failed
```

however if i call from a Gtkbutton after the song has started playing the same print statement
```
print((self.player.query_duration(gst.FORMAT_TIME, None)[0]))
```
then it works fine and prints 515320453514 which is the correct song length.

if anyone can point out what im doing wrong id be grateful :)

---

