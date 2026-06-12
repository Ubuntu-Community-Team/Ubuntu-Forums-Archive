---
title: "Netflix-Desktop"
date: 2016-09-13
forum: New to Ubuntu
---

### Post by dzyn2 on 2016-09-13
I want to get the netflix-deskstop app on my PC seeing on how I do not use Chrome and do not want to so I typed this into the terminal.

[INDENT]sudo apt-add-repository ppa:ehoover/compholio
 sudo apt-get update
 sudo apt-get install netflix-desktop

What came up was this


E: Unable to locate package netflix-desktop


How can I get the Netflix application on my PC?





[/INDENT]

---

### Post by deadflowr on 2016-09-13
The netflix-desktop app hasn't been in the ehoover/compolio ppa since 12.10 or there abouts.
Instead remove that ppa, and add the pipelight-stable ppa
```
sudo apt-add-repository -r ppa:ehoover/compholio
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install netflix-desktop
```

Hope it helps

---

### Post by cwmoser on 2016-09-14
Tried the above, but get "E: Unable to locate package netflix-desktop"

---

### Post by howefield on 2016-09-14
> **cwmoser said:**
> Tried the above, but get "E: Unable to locate package netflix-desktop"

Are you running Ubuntu 16.04 ?

There is no netflix-desktop package available for 16.04 in that repository.

---

### Post by deadflowr on 2016-09-14
^^Yeah, I forgot, for xenial install pipelight-multi,
then follow the advice from pipelight on setting up firefox:
[http://pipelight.net/cms/installation.html#section_2]("http://pipelight.net/cms/installation.html#section_2")

I think you should be able to choose either the silverlight plugin or the widevine plugin to run netflix.
Two things you may need to do would be
1)create the pipelight mozilla-plugins:
```
sudo pipelight-plugin --create-mozilla-plugins
```
and 
2)set a user agent switcher:
[http://pipelight.net/cms/installation-user-agent.html]("http://pipelight.net/cms/installation-user-agent.html")

Also as a sidenote, this will most likely be moot in only a few weeks time as firefox is looking to include the widevine plugin in firefox for the firefox 49.
this will allow netflix to run without any user intervention at all.
Or at least that is the theory.
More here on that: [http://www.omgubuntu.co.uk/2016/08/firefox-49-linux-netflix-google-widevine-cdm]("http://www.omgubuntu.co.uk/2016/08/firefox-49-linux-netflix-google-widevine-cdm")

---

### Post by dzyn2 on 2016-09-14
I did all that on 16.04 and still unable to find netflix desktop :(

---

### Post by SeijiSensei on 2016-09-14
Let us repeat, there is no netflix-desktop app for 16.04.  You can use Firefox with the Pipelight add-on and the Silverlight plugin as deadflowr explained.

The other option is to upgrade to a recent beta of Firefox and activate the Widevine plugin.  I'm using FF 49.0b8 from [https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next).

Or you can just use Chrome.

---

### Post by cheroka4 on 2016-09-16
> **SeijiSensei said:**
> 
Or you can just use Chrome.
 
Yes, this did the trick for me, just works like a charm. You can (should?) even create an app like icon if in Chrome you use More Tools -> Add to desktop

---

### Post by pqwoerituytrueiwoq on 2016-09-17
i don't use netflix but it should work in firefox
[http://www.omgubuntu.co.uk/2016/08/firefox-49-linux-netflix-google-widevine-cdm](http://www.omgubuntu.co.uk/2016/08/firefox-49-linux-netflix-google-widevine-cdm)

---

