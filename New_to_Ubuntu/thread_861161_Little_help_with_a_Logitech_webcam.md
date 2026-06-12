---
title: "Little help with a Logitech webcam?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by tmofee on 2008-07-16
Hi all, just new to the whole Ubuntu world and scratching my head as to how to install my Logitech Quickcam Communicate Deluxe (I managed to figure out that it's 046d:0992). It says to install uvcvideo however the file is missing from the berliOS dev website. the page is there, but there's nothing to download! I'm running 8.04, the only thing I'm guessing is that this is old information and I need to do something else to get the thing running. plugged in the microphone works fine! camorama gives me "could not connect to the video device" before I can load the thing.

Any ideas, people? Please help a noob who has just started in this world of ubuntu.

Terry :)

---

### Post by Sef on 2008-07-16
Check out the [Logitech Webcams]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech") page.

Also check out [Webcams]("https://help.ubuntu.com/community/Webcam").

---

### Post by benfindlay on 2008-07-16
Take a quick look for your camera [here]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")
It will show you whether your specific camera is supported or not.

There is a good set of generic drivers available which work for lots of cameras. You can install this by typing ```
sudo apt-get install gspca-source
```

Or alternatively you can try installing the spca5xx drivers

Hope this helps!

---

### Post by tmofee on 2008-07-16
> **benfindlay said:**
> Take a quick look for your camera [here]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")
It will show you whether your specific camera is supported or not.

There is a good set of generic drivers available which work for lots of cameras. You can install this by typing ```
sudo apt-get install gspca-source
```

Or alternatively you can try installing the spca5xx drivers

Hope this helps!

Thanks, tried installing gspca, but exactly the same, or is there a second step once you've run the above command? Couldn't find package spca5xx, wouldnt come up when i typed this in terminal. does it have a new name??

---

### Post by benfindlay on 2008-07-16
Spca5xx needs to be installed manually, I believe. Take a look [here]("http://mxhaard.free.fr/download.html")

Not sure about the gspca, been a while since I tried it!

---

### Post by nascimento on 2008-07-22
Hya guys!
Just to give some light...

all packages named xxx-source, will be just waiting for you to compile them at your default source location: /usr/src/modules

remmember that, before you start compiling stuff around, you should get prepared for it.

Let's do all of that at the same time installing that gspca-source?

Do that:

> cd /usr/src/modules

You will see a directory named gspca in there... see it?
Well.. let's prepare our system! Type:

> sudo m-a a-i gspca-source

And follow every step that our sweet ubuntu prompts for you.
if you get ANY errors during that task, perraps some package is missing?

Well - i'm not going to make it easy.. ;-) go ahead and try to find a new compiled-world!

For any more complicated stuff - bug me any time!

hope was helpfull,

Daniel Nascimento

---

