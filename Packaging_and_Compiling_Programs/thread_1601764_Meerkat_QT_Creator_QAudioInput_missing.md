---
title: "Meerkat: QT Creator: QAudioInput missing"
date: 2010-10-20
forum: Packaging and Compiling Programs
---

### Post by imbjr on 2010-10-20
I'm trying to compile qtv4lcapture and have run into a problem with QAudioInput: it's missing!

I thought the following would fix things:

[http://www.qtforum.org/article/33163/qaudioinput-missing.html#post106784](http://www.qtforum.org/article/33163/qaudioinput-missing.html#post106784)

but no - and besides, the pro file already has the required line in it. 

Then I installed the Phonon dev package. Again no. I look in /usr/include/phonon and see nothing that would indicate the required source code is installed.

Have I missed another dev-package I need to install, or is the code truly missing?

---

### Post by SevenMachines on 2010-10-20
You could try qtmobility-dev maybe
> $ apt-file search QAudioInput
qtmobility-dev: /usr/include/QtMultimediaKit/QAudioInput

---

### Post by imbjr on 2010-10-21
> **SevenMachines said:**
> You could try qtmobility-dev maybe

Good call. I'd have never have thought to have done that, or even know that the required package was qtmobility-dev - that does not seem obvious to me.

Anyhoo, I managed to get past the problem by taking out the microphone code - I didn't need it anyway.

Ultimately, the code did not work too! I tried a Java API instead that indicated that it could not support the data it was receiving.  I wonder if this is the old problem of having to prefix the call to the webcam app with:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so web-cam-app

UPDATE: No, still a black screen. No indication of error and a mp4 is being produced.

---

### Post by SevenMachines on 2010-10-21
apt-file is handy for finding the package with the file you're looking for, just remember to run 'apt-file update' occasionally to update the listing.
You can also search packages.ubuntu.com too

---

