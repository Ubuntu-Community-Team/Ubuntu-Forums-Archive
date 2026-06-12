---
title: "Google Chrome for Linux! (You won't find it in Software Center)"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by Aryan_Gaikwad on 2014-01-25
To get Chrome for Ubuntu,


First install Chrome from from the link -


For Ubuntu, Fedora, Debian and openSUSE - [http://bit.ly/ChromeForLinux](http://bit.ly/ChromeForLinux)
For other platforms - [http://bit.ly/ChromeOther](http://bit.ly/ChromeOther)

After installations, extract it to a folder and open it.


Software center will open with Chrome. If it doesn't then click on the drop-down arrow beside "All Softwares" and now you'll find Google over there. 

Click on it and install your chrome from there (the software you already have usually has a tick on it). 


After installation, you can either run it from GUI by searching Google™ Chrome or launch it from Terminal using the command google-chrome-stable 

Hope it Helps :)

---

### Post by deadflowr on 2014-01-25
Or simply run a search for chrome.
Most search engines will list google chrome as the first result.

The chrome store is really good at setting which distro you have.
The harder part is which arch you have.


On another hand, if you want to run an open-source non googlized version, chromium is in the Ubuntu repos.

---

### Post by Bashing-om on 2014-01-25
Or the terminal way !

Add google repository to your sources, that is, create a new file under /etc/apt/sources.list.d with the following cotents:
deb [http://dl.google.com/linux/chrome/deb/ stable main](http://dl.google.com/linux/chrome/deb/ stable main)
Get repository key:
 download the key and then use apt to install it.
```

wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -

```
Update your sources:
```

sudo apt-get update

```
And install the package:
```

sudo apt-get install google-chrome-stable

```

And ya got it direct from the source !

[INDENT][INDENT]piece of cake
[/INDENT][/INDENT]

---

### Post by avdiel1946 on 2014-01-27
I found Chromium on my 13.10 distro. Same thing as Chrome. When I got in I signed into my Chrome account and everything updated.

---

### Post by deadflowr on 2014-01-27
> **avdiel1946 said:**
> I found Chromium on my 13.10 distro. Same thing as Chrome. When I got in I signed into my Chrome account and everything updated.

Not really.
Though it is what chrome is based on.

It doesn't have pepperflash by default, though there is a ppa for it.
As well as an newly added package in the development release trusty repository .
There are a couple of other things chrome has that aren't in the chromium browser, as well.
I think the pdf viewer is one.
Google also adds some of it's own things to chrome.

---

### Post by FiremanEd on 2014-01-27
> deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main

This should be deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

---

### Post by monkeybrain20122 on 2014-01-27
Just download the .deb from google and install it and it will automatically add the repository to your sources list (or rpm for Fedora, Suse etc, for arch it is in AUR) You don't have to manually add any repo.

---

### Post by Bashing-om on 2014-01-27
@ FiremanEd; Thanks for the correction.

Agreed and my posting edited.

[INDENT]source check, verified
[/INDENT]

---

