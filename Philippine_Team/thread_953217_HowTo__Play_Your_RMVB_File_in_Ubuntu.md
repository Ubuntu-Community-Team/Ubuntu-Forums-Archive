---
title: "HowTo : Play Your RMVB File in Ubuntu"
date: 2008-10-19
forum: Philippine Team
---

### Post by ysNoi on 2008-10-19
Guys, I just want to share this to all. :)

I've been configuring my rmvb fiLes to play in Ubuntu...So after searching from some threads, I found this documentation here and able to figure it out fine....!

My Source Here : [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

My Steps heRe : 8.04

1.> ***In your Terminal: Add Medibuntu to your sources.list***

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

***Then, add the GPG Key:***

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu.

2.> GoTo : ***System --> Administration --> Software Sources*** See Image Below :

[IMG]http://i249.photobucket.com/albums/gg226/ysnoi_lacroxste/Ubuntu/Screenshot.png[/IMG]

***Close --> Reload***

3.> GoTo : ***System --> Administration --> Synaptic Package Manager***
Click search and type ***Medibuntu***. There, mark ***mplayer and W32codecs*** for installation.

4.> Now, right click your rmvb file and open it with "Movie Player". It should work. Your doNe...

Hope it works for you too....Goodluck..! :guitar::guitar:

---

### Post by jepong on 2008-10-20
weird thing with RMVB is that (my favorite) VLC can't play it... mplayer is the way to go! :)

---

### Post by sethvath on 2008-10-20
the rm codec is not provided with vlc

---

