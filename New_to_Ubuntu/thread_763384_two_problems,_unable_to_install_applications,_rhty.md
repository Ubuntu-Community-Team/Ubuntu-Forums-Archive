---
title: "two problems, unable to install applications, rhtyhmbox errors"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by aceramicbunny on 2008-04-22
so i am running unbuntu 7 and have two problems that have gotten out of hand i am completely new to the linux experience (though a self proclaimed geek) and am loving it so far, and need help please!

1. Whenever i try to install something using the add/remove program in the address bar, i get the same error message, regardless of the program i try to install. first a popup comes up saying that the list needs to be refreshed, im asked for my password and then two download (or what i assume are download) windows pop up and go real fast. cant really get what they say, but its something like downloading package information and checking updates. It says i need a working internet connection, but here i am typing this so that is not the issue. anyway, it goes through all of that and then the list comes up again but when i try to download anything or mark it to be downloaded the same thing happens. no idea what to do.

2. Whenever i try to import a song into rhythmbox, i get an error saying that the gstreamer plugin to import the file cannot be found. so i googled gstreamer found the plugin and download it, and i get one of these tarball things. i have  no idea what to do with it, something with the terminal i know but i just dont understand.

any help is very much appreciated and a pre-emptive thanks to all!

---

### Post by PeterJS on 2008-04-22
> **aceramicbunny said:**
> so i am running unbuntu 7 and have two problems that have gotten out of hand i am completely new to the linux experience (though a self proclaimed geek) and am loving it so far, and need help please!

1. Whenever i try to install something using the add/remove program in the address bar, i get the same error message, regardless of the program i try to install. first a popup comes up saying that the list needs to be refreshed, im asked for my password and then two download (or what i assume are download) windows pop up and go real fast. cant really get what they say, but its something like downloading package information and checking updates. It says i need a working internet connection, but here i am typing this so that is not the issue. anyway, it goes through all of that and then the list comes up again but when i try to download anything or mark it to be downloaded the same thing happens. no idea what to do.

GUI error messages are notoriously bad in all operating systems. In a terminal try:
```

sudo apt-get update

```

which should produce a much better error/description.

> 
2. Whenever i try to import a song into rhythmbox, i get an error saying that the gstreamer plugin to import the file cannot be found. so i googled gstreamer found the plugin and download it, and i get one of these tarball things. i have  no idea what to do with it, something with the terminal i know but i just dont understand.

any help is very much appreciated and a pre-emptive thanks to all!

Once you've got the repos working you can ignore the tar ball and install the restricted extras package which includes a bunch of codecs including mp3.

---

### Post by Xiong Chiamiov on 2008-04-23
For future reference, if you do ever need to install anything from source (tar.gz usually), there is a guide [here]("http://monkeyblog.org/ubuntu/installing/#source").

---

