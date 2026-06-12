---
title: "Media Server"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by mujrim on 2008-07-30
I would like to set up a media server so I can stream MP3s and videos to my PS3, X360, and other laptops.  I tried MediaTomb, but I didn't really like its interface.  I used to use TVersity when this was running XP, I liked that more.  But then I only used that because back in the day PS3 wouldn't play DivX natively, but now that it does, I don't think I need anything as resource heavy as TVersity was.
Are there any other similar programs?

---

### Post by ace007 on 2008-07-30
I installed "ushare" from the repos and use it regularly to stream video to my Xbox360.  ushare is buggy though, music streaming doesn't really work.  It does work with Xbox360 out of the box for me, and I believe it has a PS3 profile as well.  I start the UPnP server with:  

```

ushare -x -c /path/to/media

```
I think this would start a PS3 profile, (no real clue)
```

ushare -d -c /path/to/media

```

I hear fuppes is good as well, but after hours of tinkering I couldn't get it to work the way I wanted it to.

---

### Post by Kobalt on 2008-07-30
I know [Twonky]("http://www.twonkyvision.com") works really well with PS3 and the likes, but unfortunately it isn't free (though it's available for all platforms)...

---

### Post by tonez2600 on 2008-07-30
There is also fuppes which supports the PS3 out of the box, and with some tweaking will work for the 360. But as stated before, it can be a pain to get it working the way you want it to.

---

