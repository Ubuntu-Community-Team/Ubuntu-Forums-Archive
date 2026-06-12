---
title: "update manager won't connect to internet"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by Jasplice77 on 2012-02-19
Hi there!

I have new updates and I want to download them but whenever I try it comes up with

Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_17.0.963.54-r121622_i386.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_17.0.963.54-r121622_i386.deb) 404  Not Found [IP: 74.125.227.43 80]

I have no idea what this means so some help would be appreciated!
Also, the wifi light is on and I am on firefox right now so the wifi is working, just not for update manager.

Thanks!

---

### Post by Frogs Hair on 2012-02-19
Hello and Welcome
 
Is this for a PPA ?

---

### Post by Jasplice77 on 2012-02-19
What's a PPA?

---

### Post by Jasplice77 on 2012-02-19
Okay I just googled that term and I have no idea if it is or not... sorry

---

### Post by Frogs Hair on 2012-02-19
How did you install Chrome ? The site for the Chrome .deb package was down earlier but is up again now ,so you may want to try the update again . The first time I tried the site I got a 404 not found error and now it works .If that fails run the following command in the terminal and post the output in code tags by using the # symbol in the reply box tool bar .

Sorry forgot the command . It is posted below. Thanks Wildmanne !

---

### Post by wildmanne39 on 2012-02-19
Hi, you must have added that PPA to your repository because you wanted to install chrome from an outside source but it is not on the server or the server is down open synaptic click on settings repositories, other software and uncheck the ppa that says chrome, then reload the packages and run:
```
sudo apt-get update 
```
in the terminal by hitting ctrl+alt+t and copy and paste the command into it and watch for errors.

---

### Post by Jasplice77 on 2012-02-19
Thanks guys!

---

### Post by wildmanne39 on 2012-02-19
Hi, your welcome! if your problem is solved please use thread tools at the top of the page to mark thread as solved.
Thanks

---

### Post by rpaskudniak on 2012-02-20
> **wildmanne39 said:**
> Hi, you must have added that PPA to your repository because you wanted to install chrome from an outside source but it is not on the server or the server is down open synaptic click on settings repositories, other software and uncheck the ppa that says chrome, then reload the packages and run:
```
sudo apt-get update 
```
in the terminal by hitting ctrl+alt+t and copy and paste the command into it and watch for errors.

Yo there!  That's Wild, Man!  (OK, it's a safe bet that someone has said that to you before. :D )

Now I don't know from PPA and I don't use chrome - still a FireFox curmudgeon. But I was having the same issue with Update manager; it even showed up as I was upgrading to 11.10.  But your cure in Terminal worked for me as well.  Only now, instead of downloading 208MB it's downloading 237MB.  It's still going...

Right now, success is a reasonable bet, if not necessarily ranchworthy.  (Love to tweak the nose of the spell-checker! =]:\)>  My rendition of a grinning devil.)

Kudos and a Three-Musketeers bar to you, Wildmann!

---

### Post by wildmanne39 on 2012-02-20
Hi rpaskudniak, your welcome!
Enjoy

---

