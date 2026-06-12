---
title: "Google Earth"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by bgast1 on 2008-04-24
I have never gotten Google Earth to run on my computer. Don't know if it will run in Hardy Heron either. Haven't tried. Can someone tell me about what this application can do, how it compares to Marble (which does run on my computer).

---

### Post by rouge568 on 2008-04-24
It should run just fine, and is a very impressive program. I haven't ever used marble, but by what I've read, Google Earth is far superior, especially in terms of images. In metropolitan areas, you can zoom down far enough to see cars fairly clearly! You should have a broadband connection if you want to use it, however.

Here are the terminal commands to install it:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring
sudo apt-get install googleearth
```

Let me know if this works.
Have fun!

---

### Post by bgast1 on 2008-04-24
I guess it didn't work. I even went to Synaptic to try and install it that way, and that didn't work. If I go to Add/Remove, the only thing that I can find is Marble. I really want to try Google Earth.

---

### Post by rouge568 on 2008-04-24
Could you try installing again from the terminal and posting the output? We might be able to fix your problem.

edit: version from the google earth site works fine; this is if you want to do everything through synaptic.

---

### Post by reyfer on 2008-04-24
Go to the Google Earth site [http://earth.google.com/](http://earth.google.com/)
Download the Linux version, and install. That's what I did and it is running great.

---

### Post by rfruth on 2008-04-24
Works for me (its slow cause of my integrated video ?) - the installation docs work fine [http://earth.google.com/support/bin/answer.py?hl=en&answer=44713](http://earth.google.com/support/bin/answer.py?hl=en&answer=44713)

---

### Post by NToasteD on 2008-04-24
That worked out great.

Thanks

---

### Post by Dutchmaster on 2008-04-25
I downloaded the google earth binary (file with .bin extension). Next, I opened krusader in root mode and right clicked and chose properties. I checked the executable box. Then I clicked on the file and it installed itself.

---

### Post by bgast1 on 2008-04-25
What should I expect to see when installing through a terminal. I get the license agreement. At the bottom it says <ok> then it says that it is configuring Google Earth, but this screen stays up it seems forever. Is it supposed to do that?

---

### Post by rouge568 on 2008-04-25
Hmmm...
Have you tried installing via Dutchmaster's method?

---

### Post by bgast1 on 2008-04-25
I tried Dutchmasters method and it worked. I have Google Earth installed now and I think that it is working. One problem though is the map keeps blinking (flashing) in and out between the black screen and the map. I seems to stay up long enough to tell what I am looking at. It's just somewhat annoying.

---

### Post by Glugglug on 2008-04-25
I downloaded the bin file for linux  it was the latest version 4.3 beta but it wouldn't install . It appeared to start checking the files and then a message appears to say you need to run it as root . I logged in as root and it said it had been installed succesfully  but would not run or open . So I downloaded the 4.2 version and it installed no problem and didn't need to be run as root. I'm running Hardy by the way.

---

### Post by bgast1 on 2008-04-25
Does anyone know what I can do about Google Earth blinking in and out. I'm really not sure how to describe this, but it sure is annoying. At least I can get it up, which is a lot more than I can say for other distros and installs.

---

### Post by ozarkerbob on 2008-05-26
I have version 8.04

I installed a bin file, previously downloaded, using the proceedurefrom:

[https://help.ubuntu.com/community/GoogleEarth?highlight=(earth)|(google](https://help.ubuntu.com/community/GoogleEarth?highlight=(earth)|(google))  

I did the terminal commands and installed, EXCEPT--- I hit the start button which apparently is a no-no.  "Do not press Start as this will run it as root which is never a good idea"

so I have a program which shows up as an internet accessory.  It begins to load, stalls, and then crashes.  

I then ran the uninstall terminal commands, but because I didn't install correctly, it won't uninstall-  "no such file or directory"

call me stupid, but can anyone help?

---

### Post by jimrz on 2008-05-26
> **bgast1 said:**
> Does anyone know what I can do about Google Earth blinking in and out. I'm really not sure how to describe this, but it sure is annoying. At least I can get it up, which is a lot more than I can say for other distros and installs.

What video card do you have? which driver are you using? and are you running desktop effects?

Seems that (at least) some ATI cards, including the mobility 9600 on my laptop, cannot handle both compiz and GoogleEarth at the same time using the "fglrx" driver. When I tried that I got the same sort of results that you describe. Simple workaround = turn off desktop effects before running GoogleEarth, which works fine for me.

---

