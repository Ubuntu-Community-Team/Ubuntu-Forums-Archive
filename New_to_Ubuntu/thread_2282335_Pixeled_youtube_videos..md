---
title: "Pixeled youtube videos."
date: 2015-06-13
forum: New to Ubuntu
---

### Post by ThanasisKant on 2015-06-13
Hi to ubuntu community. I have a tiny bit problem and i have followed many guides on the net but i could not solve it. The thing is yesterday i saw that all youtube videos are Pixeled- pixalated. I tried updates and everything but with no response. At last i did format but yet again nothing. What is the problem and how can i resolve it?

---

### Post by Frogs Hair on 2015-06-13
Hello and Welcome !

Can you indicate what browser you are using and perhaps upload a screen-shot ? Providing computer specs and describing what you have tried will improve your chance of getting a resolution.

---

### Post by ThanasisKant on 2015-06-13
I am using chromium. My hardware is and i5 4670k cpu, 8 gb ram and a 5500 HD radeon graphics card. the screenshot show the problem. also i provide you with info abou chrome://gpu and chrome://flash

Here are the link for the photos: [http://imgur.com/jbmY75q](http://imgur.com/jbmY75q) [http://imgur.com/Ik2sWBO](http://imgur.com/Ik2sWBO) [http://imgur.com/lGqAUFU](http://imgur.com/lGqAUFU) [http://imgur.com/Uf1FdAq](http://imgur.com/Uf1FdAq)
at the first one you have to zoome to see the problem :/

P.S tell me if you cant see the photos.

---

### Post by newb85 on 2015-06-13
I don't see a reason your hardware should be an issue.  Have you tried the same videos on a different system, to make sure that's not just the nature of the videos you're watching?

---

### Post by ThanasisKant on 2015-06-13
yep i have tried it. i also tried to watch them from mozilla and i dont a problem its perfect like it should be. the chrome is the problem :/ and i dont want to change to mozzila for many reasons thats why i want to fix it :P

---

### Post by sandyd on 2015-06-13
Possibly related to "GPU access is disabled in chrome://settings"
Could be that GPU process is crashing so now you're using software rendering which may be more pixilated

What video card do you have?

Is "Use hardware accceleration when avaliable" enabled in advanced chrome settings?

If you go to "chrome://flags/#ignore-gpu-blacklist" and make sure the highlighted option is enabled, does chrome://gpu still show access is disabled?

---

### Post by ThanasisKant on 2015-06-13
I have an HD radeon 5500. i dont have the same problem with mozilla only at chromium. And yes both the "[COLOR=#000000]Use hardware accceleration when avaliable" and "[/COLOR][COLOR=#000000]chrome://flags/#ignore-gpu-blacklist" are enabled.
As for "[/COLOR][COLOR=#000000]chrome://gpu" it remains the same.[/COLOR]

---

### Post by ibbill on 2015-06-13
Curious have you ever  used Chrome. Not chromium. Seeing as how Firefox is fine. Give it a try.

---

### Post by newb85 on 2015-06-13
I don't believe chromium uses the same pepper flash player as chrome by default, so I'd say trying chrome would be a good idea. Downloading the .deb from google's website and installing it with software center is quick and simple. Also, it will add the ppa, so you will receive the updates for chrome through apt.

---

### Post by ThanasisKant on 2015-06-13
So it works at chrome again just fine. the only problem is chromium. but ok i will stay with chrome. ( although i wonder what the problem with chromium is) i want to thank you all for your help :)

---

### Post by Adam_Kleiner on 2015-06-13
Also, for future reference, try installing ubuntu-restricted-extras
```
sudo apt-get install ubuntu-restricted-extras
```
This contains codecs, plugins, fonts, etc. that are normally not included in Ubuntu due to having proprietary licensing. It's perfectly fine to install, it just normally isn't included by default as many disagree with having ANY components that aren't 100% open-source, regardless of the loss in performance.

---

