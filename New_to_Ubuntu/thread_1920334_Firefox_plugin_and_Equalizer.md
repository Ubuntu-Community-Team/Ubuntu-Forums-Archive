---
title: "Firefox plugin and Equalizer?"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by cheatos on 2012-02-04
Hi,

I have two pretty different things I'm not so happy about:
First thing is, is there a plugin like in Win7 that allows you to read pdf documents directly in the browser? Every time I want to open a pdf file I get prompted wether I'd like to open it with the pdf viewer or to save it, what is, as I often read pdf documents pretty annoying...

Second question is, is there an equalizer in ubuntu, I'm pretty sure there has to be one, but I couldn't find it anywhere in the sound settings.


Thanks for your help!

---

### Post by Frogs Hair on 2012-02-04
I have no plug-in for Firefox and I am able to open pdf documents without saving them . I am using the Nightly build though .

I have been using this EQ since 9.10 .```
sudo add-apt-repository ppa:nilarimogard/webupd8 
``` ```
sudo apt-get update
``````
sudo apt-get install pulseaudio-equalizer
```

---

### Post by kostkon on 2012-02-04
> **cheatos said:**
> First thing is, is there a plugin like in Win7 that allows you to read pdf documents directly in the browser? Every time I want to open a pdf file I get prompted wether I'd like to open it with the pdf viewer or to save it, what is, as I often read pdf documents pretty annoying...
Firefox doesn't have a built-in pdf reader like Chrome has. You can either try installing mozplugger (for 11.04 or newer; use the software centre to install it), try [this extension]("https://addons.mozilla.org/en-US/firefox/addon/pdfjs/reviews/"), or install adobe reader and its browser plugin (again, use the software centre). 
> **cheatos said:**
> Second question is, is there an equalizer in ubuntu, I'm pretty sure there has to be one, but I couldn't find it anywhere in the sound settings.
Yes, there is the PulseAudio Equalizer app. It's no longer maintained, but it works just fine. Check [this article]("http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html") for instructions on how to install it and some info about it.

Hope that helps.

---

### Post by cheatos on 2012-02-04
Thank you both for your quick reply, I'll try it with the Adobe Reader plugin and go for the equalizer.
So there really is no equalizer installed?
How odd...

---

### Post by nickelbox on 2012-02-04
Try this PDF reader. I swear by it

[http://www.foxitsoftware.com/Secure_PDF_Reader/non.php](http://www.foxitsoftware.com/Secure_PDF_Reader/non.php)

I use it in Windows as my exclusive reader but in all fairness I haven't used it in Linux because up until now, I didn't know there was a Linux version until I went looking.

---

