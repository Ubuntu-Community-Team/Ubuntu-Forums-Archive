---
title: "Problems downloading Firefox"
date: 2020-04-03
forum: New to Ubuntu
---

### Post by acid-burn2 on 2020-04-03
I'm new here and new to Linux in general. I have an Acer chromebook and just set it to dev mode and downloaded Crouton and Ubuntu 16.04. The default browser Netsurf, is very difficult to execute tasks through, i.e. can't click on buttons in the window. I tried downloading both Chromium and Firefox through Netsurf and through a terminal, but it keeps saying that I have unmet dependency. Has anyone else had issues like this? I'm starting to think something was corrupted when I downloaded either Crouton or Ubuntu?

---

### Post by NM5TF on 2020-04-04
can we assume that you followed a procedure similar to this  [https://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](https://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/)

did you get any errors during the install ??

have you updated your package list from a terminal??

```
sudo apt-get update
```

when you tried installing Firefox, did you do this from a terminal ??

```
sudo apt-get install firefox
```

what were the error messages ??

tommy

---

### Post by bestucan on 2020-04-04
1. download firefox at its official website.
2. extract it.
3. open the extracted folder in terminal.
4. use commander "firefox" to open.

---

### Post by CelticWarrior on 2020-04-04
> **bestucan said:**
> 1. download firefox at its official website.
2. extract it.
3. open the extracted folder in terminal.
4. use commander "firefox" to open.

DON'T do this. Please ignore for the moment and reply to post #2.

---

### Post by acid-burn2 on 2020-04-04
I downloaded Ubuntu per the "how to geek" posting stated above. I didn't receive any errors throughout both crouton and Ubuntu downloading . I immediately updated. I tried to download Firefox through the terminal and also through the NetSurf browser that came with the download. I was able to click the download "64-bit Linux" button, but when I went to the terminal to download Firefox, it gives me a message saying I have unmet dependencies and I may have held broken packages.

---

### Post by acid-burn2 on 2020-04-04
Update...I uninstalled everything and put the computer back in Chrome OS. Then started fresh, not sure what was missing the first time, but it worked the second time.

---

### Post by NM5TF on 2020-04-05
if you would have used apt-get install firefox, it would have taken care of all the dependencies
for you....

 please go to your 1st post and use Thread Tools to mark your post SOLVED so others may find it useful

---

