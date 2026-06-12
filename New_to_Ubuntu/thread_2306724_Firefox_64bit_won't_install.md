---
title: "Firefox 64bit won't install"
date: 2015-12-18
forum: New to Ubuntu
---

### Post by chris-burmajster on 2015-12-18
Hello Friends,

Why won't Firefox 64bit install? I download it from the website and it opens in Archive Manager. Then it's stuck! What should I do next?

Chris

---

### Post by howefield on 2015-12-18
What have you downloaded, is it a tar.bz2 file ?

Extract it and run the firefox application that you'll find inside the extracted Firefox folder.

---

### Post by QIII on 2015-12-18
Install it from the repos, perhaps?

I'm not that familiar with the Software Center, so I can't advise much on that other than to say to search for "Firefox"

Other options:

Install synaptic and install Firefox from there via the GUI:

```
sudo apt-get install synaptic
```

or just install it via the terminal

```
sudo apt-get install firefox
```

It is generally best to install software from the Canonical repositories if it is available because the software has been packaged and tested so that it is installed as Ubuntu "expects" it to be.

---

### Post by chris-burmajster on 2015-12-18
Thank you for the replies. Yes, it's a tar.bz2 file. I can extract it but I don't know which icon to press to start the installation. Using Synaptic just gives you the 32 bit Firefox - there is no 64 bit version.

---

### Post by howefield on 2015-12-18
The highlighted one in the screenshot... inside the extracted Firefox folder you will see a firefox icon, double click on it.

---

### Post by chris-burmajster on 2015-12-18
Thank you, howefield!

---

### Post by howefield on 2015-12-18
You're welcome.

Caveat : I'd echo what QIII said about sticking to the official repositories.

Also I'm curious, if you type about:buildconfig into the address bar of the default Firefox (the one installed along with your system) - what does it say under "target" ?

---

### Post by monkeybrain20122 on 2015-12-19
?? Firefox is already installed by default for Ubuntu. You shouldn't have to do anything.

---

