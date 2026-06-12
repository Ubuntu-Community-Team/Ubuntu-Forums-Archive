---
title: "Ubuntu Can't Detect Wired Connection, Although Windows Still Can"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by Tinevisce on 2012-07-06
Hello all,

This is my first time using Ubuntu (installed about 15 minutes ago) and I used the wubi Windows installer to do so, meaning it's on dual boot mode along with Windows 7.

However, Ubuntu keeps saying that I am 'disconnected' from the Wired connection on my computer. I tried manually editing in IP Address, Gateway, Subnet Masks, etc; but whenever I'm clicking on 'Add' and trying to type in the digits, nothing seems to be showing up.

I am an absolute noob with this, so a little help will be much appreciated.

(I don't know if this is relevant, but I'm putting it in here in case it is. My ISP works in such a way that even if you're wired to the network; you can't access the Internet unless you log in with an ID and password. On Windows, opening a browser automatically redirects to the log in page, and you key them in, hit enter and only then can you access the Internet)

Update:
So I did manage to add relevant info manually, such as the IP Address, Subnet Mask, Gateway, etc; but the 'Save' button at the bottom is still greyed out. Am I missing something really obvious here?

---

### Post by jmfal on 2012-07-06
Welcome to Ubuntu,

Try unplugging your router/modem at the power supply for a couple of seconds, and try again.

[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)

---

### Post by wilee-nilee on 2012-07-06
A Wubi is not a true dual boot it is a file in windows.

Post what the card actually is here are two commands that may tell you what the card is.
```
lspci | grep -i wireless  

``````
lspci | grep Broadcom
```[FONT=Arial, sans-serif][SIZE=2] [/SIZE][/FONT]

---

### Post by Tinevisce on 2012-07-06
Oh, I seem to have figured it out. I restarted my machine, and tried again- this time it worked. Thank you for the suggestions, though!

---

