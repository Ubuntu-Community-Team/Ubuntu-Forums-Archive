---
title: "Speech to Text"
date: 2010-08-27
forum: Programming Talk
---

### Post by Vistz on 2010-08-27
I'm interested in creating a speech-to-text program. One of its functions will be to type out the words I say. Another will be to "control" your computer, i.e. open applications, browse the web. Is there a specific language that I can use that will make this project go smoothly?

---

### Post by worksofcraft on 2010-08-27
That is an awesome project and will be really useful for people with certain disabilities.

Alas as far as I know it is **extremely** complicated and processor intensive:

You need to capture your audio and do Fourier transform on it. That convets it into frequency domain and then you need to normalize that and present it to trained neural networks for phoneme recognition.

After that you still have to convert phonetic spelling (with mistakes) into proper spelling and just hope all the while that they were speaking English :shock:

Oh and did I mention... it all has to happen in real-time as the person speaks. IDK perhaps someone has devised an easy way.

Your best bet might be to hunt around for an existing and preferably open source project and contribute to that. I only recently heard of code.google.com but it might be the sort of thing they have there?!

---

