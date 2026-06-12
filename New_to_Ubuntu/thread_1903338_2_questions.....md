---
title: "2 questions...."
date: 2012-01-02
forum: New to Ubuntu
---

### Post by missJ on 2012-01-02
I'm very new to the whole Ubuntu experience, and I'm loving it so far!!  Just need a bit of help...

1) I just bought a new Sony Experia mini pro... how can I sync my laptop (ubuntu 10.04 LTS) to my android, to get most out of both of them??

2) I've downloaded Spotify for linux (through vine), but I can't get the sound right. I get the message that there i s something wrong with my soundcard. I've followed the online download-instructions, but still doesn't seem to work... 

Can anyone help me?? ](*,)

 missJ

---

### Post by SingingBush on 2012-01-02
There is a native Linux version of Spotify, I would recommend using that instead of having to use Wine. 


Add this line to your list of repositories by editin your **/etc/apt/sources.list** and adding the following:
```

deb http://repository.spotify.com stable non-free

```

Then do the following:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
sudo apt-get update
sudo apt-get install spotify-client-qt

```

---

### Post by bruno9779 on 2012-01-02
On this post here there are instructions to have spotify free accounts to work.

[http://ubuntuforums.org/showthread.php?t=1892199](http://ubuntuforums.org/showthread.php?t=1892199)

I advise you to split your 2 questions in 2 threads with more descriptive titles.

I don't own an android telephone, but my wife does. She installed ubuntu-one from the app-market and syncs to ubuntu with that.

---

### Post by missJ on 2012-01-02
> **SingingBush said:**
> There is a native Linux version of Spotify, I would recommend using that instead of having to use Wine. 


Add this line to your list of repositories by editin your **/etc/apt/sources.list** and adding the following:
```

deb http://repository.spotify.com stable non-free

```Then do the following:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
sudo apt-get update
sudo apt-get install spotify-client-qt

```


THIS WORKED PERFECTLY!!! THANK YOU!!!! :guitar:

---

### Post by audiomick on 2012-01-02
> **missJ said:**
> 
1) I just bought a new Sony Experia mini pro... how can I sync my laptop (ubuntu 10.04 LTS) to my android, to get most out of both of them??

What do you want to sync? Ubuntu one can do files and contacts, as far as I now, but it is still a bit of a work in progress, I think.

If you want to sync calender entries, you might want to look at syncevolution and funambol. I set that up a few weeks back, and it seems to work ok. I am not actually happy about having to use a web based server to do this, but it seems, after some searching, that direct syncing between my phone (symbian S60) and a Linux computer is not so easy.

So:
Wiki page on syncevolution. There is a link to their home page on there. You'll need to look around there for information relevant to you phone.
[http://en.wikipedia.org/wiki/SyncEvolution](http://en.wikipedia.org/wiki/SyncEvolution)

Funambol:
[https://my.funambol.com/c/portal/layout?p_l_id=default](https://my.funambol.com/c/portal/layout?p_l_id=default)
I must add that this is one of those really annoying portals that doesn't let you see anything until you have registered.

---

### Post by missJ on 2012-01-02
> **bruno9779 said:**
> On this post here there are instructions to have spotify free accounts to work.

[http://ubuntuforums.org/showthread.php?t=1892199](http://ubuntuforums.org/showthread.php?t=1892199)

I advise you to split your 2 questions in 2 threads with more descriptive titles.

I don't own an android telephone, but my wife does. She installed ubuntu-one from the app-market and syncs to ubuntu with that.


Just installed ubuntu-one on both devices. It works!! This makes my life much easier! Thank you so much for all your help!!=D>

---

