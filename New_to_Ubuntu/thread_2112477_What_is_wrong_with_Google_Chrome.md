---
title: "What is wrong with Google Chrome?"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by 577 Jersey on 2013-02-04
On youtube I got funny looking sparkles for the last two week,,now I get a message saying pluggin needed or something like that,Firefox works perfect,,any body know how to fix this so chrome will work on flashplayers?

 Thanks Tom:popcorn:

---

### Post by mackaframa85 on 2013-02-04
Please use the following command in terminal.


  rm -rf ~/.config/google-chrome/PepperFlash

This comes from google support.  Didn't want to link it for obvious reasons.....


After you do enter this restart google chrome and log out.  Once you log back in and open it should work.

---

### Post by 577 Jersey on 2013-02-04
Thanks,,
 It works again but Its still all glittery,,hmmm darn updates always messin me up lately.

---

### Post by rburkartjo on 2013-02-05
mac tks for the info fixed my chrome  been having problems for over a week. (just a note chromium never had the flash problem).

---

### Post by 577 Jersey on 2013-02-05
How did you fix it its really getting absurd?

Thanks Tom :)

---

### Post by Frogs Hair on 2013-02-05
I switched to Iron until a fix hit the forums which have seen many. I re-installed chrome last night and flash worked fine with out doing a thing. :confused::confused:

---

### Post by 577 Jersey on 2013-02-05
I guess I should try that,,I have friends that did and it did not work for them,,but I will try.

 Thanks
  Tom

---

### Post by 577 Jersey on 2013-02-06
I removed chrome and reinstaled google-chrome-stable and still get the glitter effect,,i saw two other chromes,,one was unstable,,and the other was beta,,thinking about giving those a try,,Im at wits end,,this was the cause of an update a few weeks ago,,I wish they would be more careful when sending out buggy updates.

---

### Post by Frogs Hair on 2013-02-06
I have continued to use Iron which doesn't include Pepper Flash and will switch back to Chrome if I have problems with playing media.

I installed Chrome mainly due to the lack of development for the Linux version of Flash. I haven't had a need for Pepper yet as far as I know.

---

### Post by ACubed10 on 2013-02-06
So I know chromium is in the ubuntu AppStore but...with ubuntu tweak I was able to install the normal chrome browser. What are the differences? Those official chrome browser is now set as my default browser..

---

### Post by no2498 on 2013-02-07
my wife uses windows  and no chrome
but for some reason pepper flash was installed
it turned off flash player
she had to uninstall pepper player
then get updates for flash player all is good now

john

---

### Post by helvecio on 2013-03-09
I am running 12.04 and still get the glitter on Chrome when playing YT.
Have removed the PepperFlash directory and reinstalled Chrome but still get the same annoying effect after upgrade.
Any clues?

---

### Post by Frogs Hair on 2013-03-09
See the link. [http://askubuntu.com/questions/243313/why-is-google-chrome-displaying-artifacts-in-youtube](http://askubuntu.com/questions/243313/why-is-google-chrome-displaying-artifacts-in-youtube)

---

