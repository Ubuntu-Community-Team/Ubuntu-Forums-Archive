---
title: "setup"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by cactusjack351 on 2008-04-29
I have a HP laptop at work,1gb ram 80gb hd,installed ubuntu from a disc they sent me.can not connect to web at work.would like to watch dvd`s on it,but cannot.
is there any way to download a dvdplayer program on a thum drive,take it to work and install it.I have a pc at home but it is xp.I know 0 about putting in code or that stuff,I am really trying to learn.Thanks in advance

---

### Post by pedro_orange on 2008-04-29
If you can get your internet working you can do a:

```
sudo apt-get install ubuntu-restricted-extras
```

Which will install DVD / MP3 codecs. Flash Player. Java Runtime Env. etc

Whats up with your network conns?

Can you see it in an lspci command?

---

### Post by hermes0710 on 2008-04-29
Linux dvd players: totem, kaffeine, mplayer.

If you want to install these (if they are not already) go to "System">"Administration">"Synaptic Package Manager" and then search for these packages and tick them to be installed.

---

### Post by pro003 on 2008-04-29
cannot do that without internet connection...


```
sudo apt-get install ubuntu-restricted-extras
```


what connection you have?

---

### Post by Michael.Godawski on 2008-04-29
WE can help you with the setting up of an internet connection but we need to know few things. Open the terminal and run these commands, then post the output here.
After this command you have to enter your login password. It will not be displayed, just type it in and hit enter:
```
sudo lshw -C network
```


```
lspci
```

---

### Post by daengbo on 2008-04-29
I get the feeling that he's not allowed to use the net with this computer, not that it doesn't work. He's asking about DVD players, not the connection problem.

---

### Post by daengbo on 2008-04-29
OK,
Since you don't have a net connection, we want to download as few packages as possible. Mplayer and VLC are out for this reason. We'll try Xine and see how it goes

Download the following packages:
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gxine/gxine_0.5.901-1ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gxine/gxine_0.5.901-1ubuntu2_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.11.1-1ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.11.1-1ubuntu3_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxinerama/libxinerama1_1.0.2-1build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxinerama/libxinerama1_1.0.2-1build1_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.11.1-1ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.11.1-1ubuntu3_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/x/xine-lib/libxine1-plugins_1.1.11.1-1ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/x/xine-lib/libxine1-plugins_1.1.11.1-1ubuntu3_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.11.1-1ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.11.1-1ubuntu3_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.11.1-1ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.11.1-1ubuntu3_amd64.deb)
I think that's all you need.

You will need to install these (probably in the reverse order that Igave them to you). Do this by double-clicking on the file.

I hope that all works out for you. The Ubuntu method of software installation doesn't work so well without network accessibility.

---

### Post by pro003 on 2008-04-29
i would recommend him to get his laptop on internet somehow and do these updates things, as well install mplayer and codecs to play movies / dvd's ... or the other way is to get an apton-cd...

not quite sure how to do these things without internet connection...

anyway how do you manage to post here...without internet?:confused:

---

### Post by hermes0710 on 2008-04-29
> **pro003 said:**
> i would recommend him to get his laptop on internet somehow and do these updates things, as well install mplayer and codecs to play movies / dvd's ... or the other way is to get an apton-cd...

me too

---

