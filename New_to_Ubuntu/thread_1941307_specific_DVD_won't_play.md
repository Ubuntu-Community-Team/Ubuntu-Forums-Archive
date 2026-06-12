---
title: "specific DVD won't play"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by bielsa on 2012-03-15
hello,
I can't play the DVD 'Tinker, Tailor, Soldier, Spy' using Ubuntu.  It causes both movieplayer and VLC to crash.  I've got the codecs and restricted stuff installed, can play all other DVDs.  And I've tried 3 different copies from LoveFilm so it's not a faulty disc...

any ideas? do some specific DVDs have anti-Ubuntu software on them?

thanks

---

### Post by bielsa on 2012-03-15
It's the new one by the way, so a very recent release

---

### Post by arminwessel on 2012-03-15
HI!

I had this problem recently.

Download the css codec for encrypted dvds.

I terminal type:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```


and restart computer.

More info:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Hope it helped.

---

### Post by bielsa on 2012-03-15
I've already got libdvdread4 installed, thanks.  It's only this specific title that isn't working, I can play DVDs generally

---

### Post by winh8r on 2012-03-15
Check to see if it will play in a "normal" DVD player connected to a TV.

And try it in someone elses computer too running windows if possible.

---

### Post by bielsa on 2012-03-15
I don't have another DVD player, or run windows.

As I mentioned, though, this is the 3rd different copy I've been sent, so its very unlikely that they've all just been damaged discs.

I'm specifically wondering whether there are some DVDs that have extra layers of ubuntu unfriendliness, beyond the encoding that most DVDs have

---

### Post by donkyhotay on 2012-03-15
If you don't have another DVD player or computer then go to a friend or family members house and try the disc in their player or computer.

---

