---
title: "Cannot update firefox 3 beta 4 to 3.0 final version"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by parkerfutbol3 on 2008-06-30
OK, this is becoming very frusterating as 3.04b is not nearly as stable as the final version. In fact I have become so annoyed with it that I am posting this from Opera! 

It seems ridiculous to me even, but after exausting every option I can think of here I am... I have not used linux in a couple weeks so when I came back to my machine this morning it had several updates ready, one of them was Firefox 3.0 as expected. So I installed all updates and all was well until I tried to go check my email and the title at the top of firefox was still "Yahoo! - Mozilla Firefox 3 Beta 4." After I scratched my head I went into synaptic, uninstalled firefox then tried reinstalling it and still the same. I tried a few other things and after "uninstalling" it again to my surprise i was still able to use firefox. i went ahead and installed firefox 2 and completely removed 3.0. this seemed to work as i was now using firefox 2. then after i went to install 3.0 fresh and from the start it opened up as firefox 3 beta 4 still! i am completely clueless as to how this is happening so if someone with better knowledge of either the linux filestructure or firefox could help it would be very much appreciated

---

### Post by rxtx on 2008-06-30
Are you grabbing the version number from "about" or the main title bar?

---

### Post by parkerfutbol3 on 2008-06-30
> **rxtx said:**
> Are you grabbing the version number from "about" or the main title bar?

Both say 3.04b

---

### Post by rxtx on 2008-06-30
Odd.

Sorry for what maybe be stupid suggestions, but have you tried to run apt-get with purge on firefox and then the update arguement before installing anew?

```
sudo apt-get remove --purge firefox
sudo apt-get update
sudo apt-get install firefox-3.0
```

---

### Post by billgoldberg on 2008-06-30
Just use the update manager to upgrade your system.

It will be installed that way.

---

### Post by parkerfutbol3 on 2008-06-30
No I have not! No questions are stupid for me as I am not incredibly experienced with Linux. Lets give that a try...


Ok, the purge seemed to work as did the update but the last command did this:
```
jake@jake-desktop:~$ sudo apt-get firefox-3.0
E: Invalid operation firefox-3.0
```
I tried updating again and nothing, then I opened up firefox from Applications>Internet>Firefox Web Browser and it took me like usual to Firefox 3.04b

---

### Post by parkerfutbol3 on 2008-06-30
> **billgoldberg said:**
> Just use the update manager to upgrade your system.

It will be installed that way.

That was originally the way I intended to install it, but it did not appear to make any changes.

---

### Post by rxtx on 2008-06-30
> **parkerfutbol3 said:**
> No I have not! No questions are stupid for me as I am not incredibly experienced with Linux. Lets give that a try...


Ok, the purge seemed to work as did the update but the last command did this:
```
jake@jake-desktop:~$ sudo apt-get firefox-3.0
E: Invalid operation firefox-3.0
```
I tried updating again and nothing, then I opened up firefox from Applications>Internet>Firefox Web Browser and it took me like usual to Firefox 3.04b

Hey there. I just removed it myself with the above method and started anew. Then reinstalled. Typing "firefox" at the command prompt after the purge gives me nothing.

Sorry for the mis-type. The last line should read.

```
sudo apt-get install firefox-3.0
```

Try the purge and remove, update then that line one more time. Sorry!

---

### Post by parkerfutbol3 on 2008-06-30
Although I had tried it before, I decided to download the package from the firefox download page for grins. After extracting I double clicked on "firefox" and it opened... 3.0... no beta... i dont know what the difference was this time but to be frank I dont care ha. I think I can handle it from here. Thank you all for your suggestions and trying to help me out with my problem which was most likely user based :)

---

### Post by billgoldberg on 2008-06-30
> **parkerfutbol3 said:**
> Although I had tried it before, I decided to download the package from the firefox download page for grins. After extracting I double clicked on "firefox" and it opened... 3.0... no beta... i dont know what the difference was this time but to be frank I dont care ha. I think I can handle it from here. Thank you all for your suggestions and trying to help me out with my problem which was most likely user based :)

The difference is that this firefox 3 isn't actually installed on your system. 

So you can't use the update manager to receive updates, ...

If you didn't get the package from the update, it could be that some repositories aren't enabled.

I **strongly** suggest you enable all the ones in "system -> administration -> synaptic package manager", then "setting -> repositories".

In the first tab, select them all, in the second, dito (you won't need the source repositories).

Then reload synaptic and the update manager should appear with updates a few moments later.

Install the updates and you will be good.

---

### Post by kansasnoob on 2008-06-30
This always confuses me, but I'm a nOOB:confused:

I started with Hardy when it was still an RC, but kept Gutsy to fall back on if something broke. Even back in Gutsy I'd figured out that which repos and 'updates" were enabled had a huge effect on the stability of my system.

So I always keep Software Sources set like this:

[ATTACH]75838[/ATTACH]

And repos set like this:

[ATTACH]75840[/ATTACH]

[ATTACH]75841[/ATTACH]

Anyway I've had no trouble with the stability and functionality of FF3 beyond about 2 to 3 weeks since Hardy's final release.

I'm either doing something right or I'm just lucky:confused:

Now, this is not meant as criticism or sarcasm, I'm a noob and I just wonder how I could get so lucky?

---

### Post by kansasnoob on 2008-06-30
Oops first attachment didn't work:

[ATTACH]75842[/ATTACH]

---

### Post by stchman on 2008-06-30
Nowhere was FF3 b4 installed with ANY Ubuntu distro.  FF3 b5 was installed by default in Hardy, but it has been updated to FF3.

How did you install FF3 b4?

---

