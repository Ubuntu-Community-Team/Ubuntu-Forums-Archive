---
title: "Computer boots to a black screen"
date: 2015-04-29
forum: New to Ubuntu
---

### Post by joomla1 on 2015-04-29
I'm on Kubuntu 15.04, upgraded recently from the previous version.
Last night I was watching a tv show on vlc, when the power flickered and went out. I was using a laptop but didn't have the battery in it at the time. I disconnected the laptop then and turned it on the next morning.
At that point I was able to get to a login screen but logging into plasma, after a series of black flashes, just took me back to the login screen the first time and then stayed black the second time. The second time logging in, all the font would be visibly smaller.
Attempting to login to failsafe always brought me back to the login screen. With the visibly smaller font as before, but this I could do as many times as I felt like...

I read somewhere else in a thread made in 2012 that reinstalling kubuntu-desktop and plasma-desktop could fix it. Though he did a purge and then installed again and I just did:
sudo apt-get install --reinstall plasma-desktop kubuntu-desktop

Now I don't even get the login screen it just boots to black.
I tried logging into safe mode, running sudo touch /forcefsck to force a check at boot time, trying the dpkg option from the recovery menu and nothing works.
I'm still able to run commands since I can use ctrl+alt+f1 to get a terminal.
I've retrieved the .xsessions-errors file from my home folder and posted to pastebin.
[URL="http://pastebin.com/1XbqHWhq"]
http://pastebin.com/1XbqHWhq[/URL]

Please help!

---

