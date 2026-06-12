---
title: "Problem creating Audio CD with k3b"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by pkj on 2008-09-08
Hi,

Want to create audio CD for playing on my mp3 player..
When i want to attach .mp3 songs (downloaded from the net) to k3b for creating an audio cd... it gives me an error meaasge

Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.

How do i go about it

pkj

---

### Post by swoll1980 on 2008-09-08
You have to install mp3 support to burn mp3s 
```
sudo apt install gstreamer0.8-mad
```

---

### Post by tangibleorange on 2008-09-08
For ubuntu:
```
sudo apt-get install ubuntu-restricted-extras
```

For kubuntu:
```
sudo apt-get install kubuntu-restricted-extras
```

---

### Post by swoll1980 on 2008-09-08
> **tangibleorange said:**
> For ubuntu:
```
sudo apt-get install ubuntu-restricted-extras
```

For kubuntu:
```
sudo apt-get install kubuntu-restricted-extras
```

restricted extras installs more than just mp3 support. Things like win32, and dvd may not be legal where you live

---

### Post by tangibleorange on 2008-09-08
yeah but otherwise I think we need to know if he's using xine or gstreamer and so that further complicates things.

but you are correct

---

### Post by swoll1980 on 2008-09-08
> **tangibleorange said:**
> yeah but otherwise I think we need to know if he's using xine or gstreamer and so that further complicates things.

but you are correct

You could install libmad0 instead I think that would work either way. Wouldn't it?

---

### Post by tangibleorange on 2008-09-08
hehe i've no idea. I use Brasero...

---

### Post by GiveLove on 2008-12-04
Hello,

Using Ubuntu 8.10 32 bit.
I have this same problem and error message. But it applies to .wav and .flac audio files. I can add MP3 files to the project no problem. I don't ever recall having to install anything extra in the past to support .wav and .flac. 

Is there a software package to support these two audio formats within K3B that I'm not aware of that needs to be installed?
Thanks.

---

### Post by philinux on 2008-12-04
I think for k3b this package is needed

libk3b3-extracodecs

---

### Post by GiveLove on 2008-12-05
Thank you for the reply philinux.

I already have that package installed.
So I'm guessing it must be something else.

---

