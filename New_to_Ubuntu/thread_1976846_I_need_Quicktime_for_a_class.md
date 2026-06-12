---
title: "I need Quicktime for a class"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by Yogini on 2012-05-09
I am taking a summer course in pathophysiology and the online classroom requires quicktime to play mp4 files. In the past I have had no problem playing any media with VLC player but the files in the classroom will not open and keep brining up an error 'location not found'. The tech support at the school just say 'oh you have to have quicktime go buy windows' so I'm turning here for help. From searching this forum I have installed m-player and gecko through the software center but I am still not able to play the files I need to. I am kind of new to linux and don't know much about my own computer:confused: so I would appreciate any help I can get. Thanks a bunch folks!

---

### Post by Enigmapond on 2012-05-09
Have you installed ubuntu-restricted-extras? If not, do. This should install all codecs needed.

---

### Post by lucubrate on 2012-05-09
I found medibuntu helpful. Deals with that side of things

---

### Post by Yogini on 2012-05-09
> **Enigmapond said:**
> Have you installed ubuntu-restricted-extras? If not, do. This should install all codecs needed.
Yes I have resstricted-extras installed.

---

### Post by Yogini on 2012-05-09
> **lucubrate said:**
> I found medibuntu helpful. Deals with that side of things
When I type in medibuntu in the software center nothing is found...

---

### Post by mastablasta on 2012-05-09
you need to add their repositories i believe.

---

### Post by Enigmapond on 2012-05-09
Try just installing libquicktime and then don't use vlc...install umplayer which is a front end for mplayer. That you get from the medibuntu repo:

[http://www.ubuntuupdates.org/ppa/medibuntu_non_free](http://www.ubuntuupdates.org/ppa/medibuntu_non_free)

---

### Post by iMurshaq on 2012-05-09
You could install QuickTime with Wine.

---

### Post by Mark Phelps on 2012-05-09
> **iMurshaq said:**
> You could install QuickTime with Wine.

That's totally unnecessary -- and the ratings in WineHQ site for the Quicktime Player are all Bronze and Garbage -- meaning that installing will essentially be a waste of your time.

---

### Post by ubuntu27 on 2012-05-09
Here is [Medibuntu's Homepage]("http://www.medibuntu.org/").

Do the following to install medibuntu:

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

```
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```


And now you are ready to install medibuntu packages.

Perhaps try [re]installing **MPlayer** from the [Medibuntu repository]("http://www.medibuntu.org/repository.php").

And install some codecs such as **w64codecs** (for 64 bit Ubuntu) or **w32codecs** (for 32 bit ubuntu)

---

### Post by Yogini on 2012-05-09
> **ubuntu27 said:**
> Here is [Medibuntu's Homepage]("http://www.medibuntu.org/").

Do the following to install medibuntu:

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``````
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```
And now you are ready to install medibuntu packages.

Perhaps try [re]installing **MPlayer** from the [Medibuntu repository]("http://www.medibuntu.org/repository.php").

And install some codecs such as **w64codecs** (for 64 bit Ubuntu) or **w32codecs** (for 32 bit ubuntu)


Thanks for the informaiton I tried doing both of those in terminal but still can not play the mp4's how/where whould i get the codecs? Do I need to restart my computer after installing medibuntu? How do I know it has installed?
Thanks

---

### Post by ubuntu27 on 2012-05-09
> **Yogini said:**
> Thanks for the information I tried doing both of those in terminal but still can not play the mp4's how/where would i get the codecs? Do I need to restart my computer after installing medibuntu? How do I know it has installed?
Thanks

The medibuntu is a 3rd party [repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") where extra extra codecs and apps are available.

Try:

```
sudo apt-get install non-free-codecs mplayer mplayer-gui libdvdcss2
```

By the way, is the video that you want to play **streamed**, meaning are you trying to watch it embedded on a web-browser (like youtube)? Or do you download the video and play it locally?

If you are trying to stream, next time right click on the video link, and check "Save link as..." (phrase will be different depending on browser), and save it locally. And try to play it with different players such as VLC, mplayer, etc.

---

### Post by Yogini on 2012-05-09
You are awesome. I love this forum! Thanks:):KS

---

### Post by ubuntu27 on 2012-05-09
> **Yogini said:**
> You are awesome. I love this forum! Thanks:):KS

Did it work? What did you do to make it work?

---

