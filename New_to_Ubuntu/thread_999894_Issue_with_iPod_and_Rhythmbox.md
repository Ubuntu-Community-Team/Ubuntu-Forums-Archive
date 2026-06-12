---
title: "Issue with iPod and Rhythmbox"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by damonjablons on 2008-12-02
Hola Amigos,

Whenever I try to add music to my iPod in Rhythmbox, the program pretends to do the transfer and even will show the music as existing on the ipod when I browse the ipod.  However, it is not on the ipod :(.  If I unmount and remount the ipod, it doesn't exist on the ipod anymore, and if i eject the ipod, it's not in the ipod's music library.

I decided to reinstall rhythmbox and it still does the same thing.  I don't really like the interface of GTKPod so I'd rather use Rhythmbox.

I ran rhythmbox from terminal, and here was the output when I tried to transfer some m4a files a friend sent me:

```
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/x-tar decoder|decoder-application/x-tar
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/x-gzip decoder|decoder-application/x-gzip
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.

** (rhythmbox:7631): CRITICAL **: itdb_track_free: assertion `track' failed

** (rhythmbox:7631): CRITICAL **: itdb_track_free: assertion `track' failed

```

thanks in advance for the help.

-d!

---

### Post by damonjablons on 2008-12-02
Now with added Seg Fault!

```
(rhythmbox:15782): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

```

---

### Post by kernelhaxor on 2008-12-02
I don't have a fix for that issue but if I could suggest, I would recommend Amarok which works very well with my Ipod .. both video and audio files

---

