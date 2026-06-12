---
title: "HOWTO: Further regain the Firefox logo"
date: 2005-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Jormundgand on 2005-06-04
If you're like me, you love the Firefox logo and want it to be everywhere it should by rights be. So you're not happy to leave the About box as it is. You want that logo fixed.

I'm providing the Firefox about logos. Also included is instructions for replacing them in the browser:

1) Download the three images below to your home directory
2) $ cp /usr/lib/mozilla-firefox/chrome/browser.jar ~
3) $ unzip browser.jar
4) $ rm content/browser/about*.png
5) $ cp *.png content/browser/
6) $ zip -r browser.jar content
7) $ sudo rm /usr/lib/mozilla-firefox/chrome/browser.jar
8) $ sudo cp ~/browser.jar /usr/lib/mozilla-firefox/chrome
9) Restart Mozilla Firefox

When I come up with a similar sequence for Thunderbird, I'll post that too. You might even make this into a small bash script like was done for the logos.

---

### Post by statsministern on 2005-06-04
That worked great thanx!

---

### Post by Jormundgand on 2005-06-04
I've gone through the same process with Thunderbird.

1) Download the file below
2) $ cp /usr/share/mozilla-thunderbird/chrome/messenger.jar ~
3) $ cp /usr/share/mozilla-thunderbird/chrome/en-US.jar ~
4) $ unzip thunderbird.zip
5) $ unzip messenger.jar
6) $ unzip en-US.jar
7) $ rm content/messenger/about*.png
8) $ rm locale/messenger/h*.png
9) $ rm locale/messenger/thunderbird-watermark.png
10) $ rm locale/messenger/start.html
11) $ cp about*.png content/messenger/
12) $ cp *.png locale/messenger/
13) $ cp start.html locale/messenger/
14) $ zip -r messenger.jar content/
15) $ zip -r en-US.jar locale/
16) $ sudo rm /usr/share/mozilla-thunderbird/chrome/messenger.jar
17) $ sudo rm /usr/share/mozilla-thunderbird/chrome/en-US.jar
18) $ sudo cp *.jar /usr/share/mozilla-thunderbird/chrome/
19) Restart Mozilla Thunderbird

---

### Post by Poul on 2005-06-04
Wonderful howto - thats what i've been waiting for. 

Ps Now i am waiting for quick script.

---

