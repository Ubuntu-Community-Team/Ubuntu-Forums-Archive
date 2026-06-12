---
title: "Fingerprint login help ?? I'm new to ubuntu"
date: 2016-04-25
forum: New to Ubuntu
---

### Post by mitch20 on 2016-04-25
HI!

 i have a LENOVO t61 that i've just installed ubuntu 14.04.4 LTS on... 
all my drivers seem to be working great, top marks ubuntu! 

But my fingerprint scanners not working for logins, can anyone point me in the right direction or give me a bit of advice ? 

i like feeling like james bond when i log on my pc lol 


also yes yes i know this is a old computer but its dual core, 2.5gb ram, and i paid £30 for it and plan on using it just for browsing.

---

### Post by zerubbabel on 2016-04-25
Try installing [this]("http://www.ullrich-online.cc/fingerprint/").

---

### Post by steeldriver on 2016-04-25
At least on my T61p, all that's necessary is to install the libpam-fprintd package, either from Software Center or via the command line using

```

sudo apt-get install libpam-fprintd

```

You should then see an extra option called 'Fingerprint Login' in System Settings --> User Accounts
[ATTACH=CONFIG]268617[/ATTACH]

You should then be prompted to enroll your fingerprint(s) by swiping your finger
[ATTACH=CONFIG]268618[/ATTACH]

---

### Post by DuckHook on 2016-04-25
> **steeldriver said:**
> At least on my T61p, all that's necessary is to install the libpam-fprintd package+1

There are other packages, but they tend to break or replace PAM which can lead to nasty problems with security and upgrades. This solution works as an extension of PAM so it is the most benign. I use it on my Dell XP as well.

Please be aware that any fingerprint module will diminish your security. They are not difficult to spoof.

---

### Post by mitch20 on 2016-04-26
hiya, ive installed it, ive added my fingerprints, after i scan my finger to login it comes up saying login, i click it, the screen goes blank and its asif i never swiped my fingerprint, and i have to repeat this til it asks me to entre my password, ive tried putting different fingerprint enrolls, and it is telling me sometimes that the fingerprint i enter is wrong so its all working just not logging me in lol

---

### Post by yetimon_64 on 2016-04-26
> **DuckHook said:**
> ...
Please be aware that any fingerprint module will diminish your security. They are not difficult to spoof.
I don't mean to divert/hijack the thread or anything, but could you explain a bit about how or link to more info on that point DuckHook?

I would be keen to learn more about that as I am using a fingerprint reader on a HP machine, the driver I use had to be built from source code as the device is not generally supported. It is working OK as is (I don't have a problem as such) and am interested to find out how it could be spoofed or possibly diminish security on this set up. Hopefully any further info or links to such may also help the OP and others. Cheer, yeti.

---

### Post by mitch20 on 2016-04-26
> **steeldriver said:**
> At least on my T61p, all that's necessary is to install the libpam-fprintd package, either from Software Center or via the command line using

```

sudo apt-get install libpam-fprintd

```

You should then see an extra option called 'Fingerprint Login' in System Settings --> User Accounts
[ATTACH=CONFIG]268617[/ATTACH]

You should then be prompted to enroll your fingerprint(s) by swiping your finger
[ATTACH=CONFIG]268618[/ATTACH]


[LIST]
[*]                              [INDENT]                     hiya, ive installed it, ive added my fingerprints, after i scan my  finger to login it comes up saying login, i click it, the screen goes  blank and its asif i never swiped my fingerprint, and i have to repeat  this til it asks me to entre my password, ive tried putting different  fingerprint enrolls, and it is telling me sometimes that the fingerprint  i enter is wrong so its all working just not logging me in lol                 [/INDENT]
[/LIST]

---

### Post by DuckHook on 2016-04-26
> **yetimon_64 said:**
> I don't mean to divert/hijack the thread or anything, but could you explain a bit about how or link to more info on that point DuckHook?[https://www.blackhat.com/us-15/briefings.html#fingerprints-on-mobile-devices-abusing-and-leaking](https://www.blackhat.com/us-15/briefings.html#fingerprints-on-mobile-devices-abusing-and-leaking)
[https://www.yahoo.com/tech/iphone-hack-fools-touch-id-170652752.html](https://www.yahoo.com/tech/iphone-hack-fools-touch-id-170652752.html)
[http://www.popsci.com/how-samsung-and-htcs-fingerprint-security-was-hacked](http://www.popsci.com/how-samsung-and-htcs-fingerprint-security-was-hacked)

The biggest issue (and one that didn't occur to me when I started using it) is that, once hacked, the bad guys will have access to an immutable part of your identity that you can't change. Obviously, you can't change your finger like you can a password. Moreover, you are throwing this immutable part of your identity out there to god knows how many vendors, relying on them to safeguard it, and we should know by now that some of them have all the security savvy of Homer Simpson.

Food for thought.

Having said all of the above, I still use one instance of this technology on my laptop.

Incidentally, I think this topic is relevant to the OP's initial question insofar as it impacts his/her decision on using it.

---

### Post by QDR06VV9 on 2016-04-26
> **DuckHook said:**
> [https://www.blackhat.com/us-15/briefings.html#fingerprints-on-mobile-devices-abusing-and-leaking](https://www.blackhat.com/us-15/briefings.html#fingerprints-on-mobile-devices-abusing-and-leaking)
[https://www.yahoo.com/tech/iphone-hack-fools-touch-id-170652752.html](https://www.yahoo.com/tech/iphone-hack-fools-touch-id-170652752.html)
[http://www.popsci.com/how-samsung-and-htcs-fingerprint-security-was-hacked](http://www.popsci.com/how-samsung-and-htcs-fingerprint-security-was-hacked)

The biggest issue (and one that didn't occur to me when I started using it) is that, once hacked, the bad guys will have access to an immutable part of your identity that you can't change. Obviously, you can't change your finger like you can a password. Moreover, you are throwing this immutable part of your identity out there to god knows how many vendors, relying on them to safeguard it, and we should know by now that some of them have all the security savvy of Homer Simpson.

Food for thought.

Having said all of the above, I still use one instance of this technology on my laptop.

Incidentally, I think this topic is relevant to the OP's initial question insofar as it impacts his/her decision on using it.
+1 And glad you brought to light.
I've been dying to start a thread on this a few years back, but reluctant due to feed-back.
So cheers to you Duck Hook

---

### Post by DuckHook on 2016-04-26
> **mitch20 said:**
> ...the screen goes  blank and its asif i never swiped my fingerprint, and i have to repeat  this til it asks me to entre my password, ive tried putting different  fingerprint enrolls, and it is telling me sometimes that the fingerprint  i enter is wrong so its all working just not logging me in...Follow the instructions [here]("https://launchpad.net/~fingerprint/+archive/ubuntu/fprint"). It should be noted for readers who make it to this thread that the *fprint* project is not very active at this time. Older fingerprint readers tend to have better support, but newer readers are a hit-and-miss affair, due to lack of support from manufacturers and slow pace of development in the project.

---

### Post by yetimon_64 on 2016-04-26
> **DuckHook said:**
> [https://www.blackhat.com/us-15/briefings.html#fingerprints-on-mobile-devices-abusing-and-leaking](https://www.blackhat.com/us-15/briefings.html#fingerprints-on-mobile-devices-abusing-and-leaking)
[https://www.yahoo.com/tech/iphone-hack-fools-touch-id-170652752.html](https://www.yahoo.com/tech/iphone-hack-fools-touch-id-170652752.html)
[http://www.popsci.com/how-samsung-and-htcs-fingerprint-security-was-hacked](http://www.popsci.com/how-samsung-and-htcs-fingerprint-security-was-hacked)

...
Incidentally, I think this topic is relevant to the OP's initial question insofar as it impacts his/her decision on using it.

Thanks, interesting bit of reading there (I had to dig a bit but managed to find the articles about biometrics). Yes, I agree, very relevant. I'll now have to reset my password, long forgotten because of the "convenience" of the fingerprint reader. 

An "immutable" part of me for access to my machine and the idea of that being stolen if hacked is a bit creepy to think about :shock:. I will be changing back to my usual "nasty" 14 + character passwords (upper and lower case letters, numbers and keyboard symbols) that I have a method for regenerating every time. 

Thanks for the links, yeti.

---

