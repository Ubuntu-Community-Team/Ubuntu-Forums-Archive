---
title: "[SOLVED] Synaptic package manager - now you see now you don't"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-06-05
> **mikewhatever said:**
> Here you go:

[http://psychocats.net/ubuntu/firefox2hardy](http://psychocats.net/ubuntu/firefox2hardy)

I have a new problem. Firefox 2 doesn't show up in Synaptic package manager. This is really strange 'cause yesterday it did show but I couldn't download because of network connectivity.

---

### Post by adam_kimber on 2008-06-05
Just a quick question why switch to FF2? Broken add-ons? I found following that the instructions on that link meant that clicking links in other progams that was supposed to open FF did not work. There is probably a workaround, come to think of it I might have a solution if you MUST switch to FF2. 

As for synaptic. Have you tried refreshing the packages list it sometimes  get confused. If that fails, try opening a terminal and typing the following:

sudo apt-get update
sudo apt-cache search firefox

---

### Post by Duck2006 on 2008-06-05
Have you tried downloading fire fox from the web site and installing it.

[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)

---

### Post by kpkeerthi on 2008-06-05
Clean your apt cache and install from command line

```

sudo aptitude clean
aptitude search firefox-2
sudo aptitude install firefox-2

```

---

### Post by niceguy123 on 2008-06-05
Thanks guys, All of your replies were important for me. 

I figured out what my problem was, I had been trying different repositories because things were not downloading and that turned out to be because my network connection was not configured right.

Anyway, I just did a search for the quickest repository server and found a good one that has what i need.

---

