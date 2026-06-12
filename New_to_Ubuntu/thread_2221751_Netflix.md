---
title: "Netflix"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by asmolinski on 2014-05-03
I am having trouble install the Netflix Desktop app. Once I have it installed once I go in it tells me to download silverlight, but I already have silverlight enabled.
To install I ran the following commands:

sudo add-apt-repository ppa: pipelight/stable
sudo apt-get update
sudo apt-get install pipelight-multi
sudo pipelight-plugin --enable silverlight
sudo apt-get install netflix-desktop wine-compholio

I am running 14.04 64-bit

---

### Post by monkeybrain20122 on 2014-05-03
Well if you have pipelight you don't need netflix-desktop (which is deprecated anyway, developers moved on to pipelight) Please look at the official, up to date guide
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update

```

To enable silverlight, close all browsers
```
pipelight-plugin --enable silverlight
```

You don't need 'sudo' to enable it for just yourself.

For netflix you need user agent overrider  and set to Firefox/Windows
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)

---

### Post by ian-weisser on 2014-05-03
One overlooked step for ext3 and ext4 filesystems is to install the *attr* package.
Silverlight requires it to store DRM data.
It was the hiccup I ran into.

(Source: [Pipelight FAQ]("https://answers.launchpad.net/pipelight/+faq/2485") #3)

---

### Post by monkeybrain20122 on 2014-05-03
> **ian-weisser said:**
> One overlooked step for ext3 and ext4 filesystems is to install the *attr* package.
Silverlight requires it to store DRM data.

Huh?? netflix is working perfectly here and attr is not even installed.

---

### Post by sammiev on 2014-05-03
> **monkeybrain20122 said:**
> Well if you have pipelight you don't need netflix-desktop (which is deprecated anyway, developers moved on to pipelight) Please look at the official, up to date guide
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update

```

To enable silverlight, close all browsers
```
pipelight-plugin --enable silverlight
```

You don't need 'sudo' to enable it for just yourself.

For netflix you need user agent overrider  and set to Firefox/Windows
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)

This is all that is needed. Been working good here for sometime now.

---

### Post by don-handymanreality on 2014-05-03
Just a thought;

I hope you realize that pipelight installs only i386 packages and not AMD64. In my experience i386 packages make my 64 Bit Ubuntu installations unstable.

Pipelight installation page
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

Run at your own risk...lol.

---

### Post by monkeybrain20122 on 2014-05-03
> **don-handymanreality said:**
> Just a thought;

I hope you realize that pipelight installs only i386 packages and not AMD64. In my experience i386 packages make my 64 Bit Ubuntu installations unstable.

Pipelight installation page
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

Run at your own risk...lol.

I don't see any problem installing i386 packages in 64 bit os, never experienced any problem (I run 64 bit Ubuntu as well). Plenty of things installs i386 libs, google-earth, skype, wine...

---

### Post by asmolinski on 2014-05-03
I ran the commands that[COLOR=#000000] monkeybrain20122 told me to run, and it still won't run. Could be because I am running 64-bit?[/COLOR]

---

### Post by sammiev on 2014-05-03
> **asmolinski said:**
> I ran the commands that[COLOR=#000000] monkeybrain20122 told me to run, and it still won't run. Could be because I am running 64-bit?[/COLOR]

I'm running 64-bit as well with no problems.

Are you also using User Agent Overrider?

---

### Post by monkeybrain20122 on 2014-05-04
> **asmolinski said:**
> I ran the commands that[COLOR=#000000] monkeybrain20122 told me to run, and it still won't run. Could be because I am running 64-bit?[/COLOR]

What won't run? silverlight or netflix?

Try the bubble test to make sure that silverlight is working [http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html)
If it doesn't work, it may be because of your previous failed installation. In that case do the following

1. close all your browsers
2. run
```
pipelight-plugin --disable silverlight
```
3. Open the file manager to your home directory, press ctrl+h or in the menu choose "show hidden files", then delete the folder .wine-pipelight
4. Run 
```
 pipelight-plugin --enable silverlight
```
5. launch firefox and go to the bubble test again, the silverlight installer should kick in, let it do its work, it may take a minute.

Edited: you should get rid of netflix-desktop
```
sudo apt-get remove netflix-desktop
```

---

### Post by asmolinski on 2014-05-04
I removed the desktop app. Tried the bubbetest, it worked. I tried disabling and removing the hidden directory, then re enabling it. Opened firefox, it ran some silverlight installers, then I did the bubbletest it work. Netflix still won't work. When I get into netflix and try and watch something this is the page that I get. [ATTACH=CONFIG]252824[/ATTACH]

---

### Post by monkeybrain20122 on 2014-05-04
That is because you haven't installed the user agent overrider addon as I told you in my first post, or you have installed it but haven't set it to firefox/windows.  Netflix checks for OS if it is not Windows or Mac it won't play. These people are idiots, you are a paying customer no matter what OS you use. Since  pipelight is courtesy of the community they don't have to pay for support or maintenance why exclude customers they get for free?

---

### Post by asmolinski on 2014-05-04
Installing the user agent overrider worked. Thanks a bunch for your help!

---

