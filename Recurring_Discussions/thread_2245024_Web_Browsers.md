---
title: "Web Browsers"
date: 2014-09-20
forum: Recurring Discussions
---

### Post by nineteen-73 on 2014-09-20
Which browser, Firefox or Chrome, do you use on Ubuntu and why? What advantages and disadvantages do you think one has over the other? Do you use both browsers for certain features?  I'm not looking to choose one browser over another  per se. But browsers behave and interpret things differently from one another and I would like to understand their nuances under Linux.   I've been a Windows user all my life, so with my limited experience with an old iBook G4 PPA (Mac OS X 10.5.8) and recently installed Ubuntu 14.04 LTS on my HP G7-2325DX, I've observed that these web browsers behave differently, especially with Flash, Java, and HTML 5. So because of my inexperience with Linux, I don't want to mash lines in the Terminal, installing this, that, and the other,  to get my browser(s) to function properly. I would like some pointers and advice as to what commands work for which browsers to watch Netflix, YouTube, and online  flash games, etc.   Lastly, does anyone use Tor? If so, can it be configured to run on both Firefox and Chrome?  Thanks for your time and input.

---

### Post by Frogs Hair on 2014-09-20
Perhaps you should indicate specific problems you are having . I don't have any experience with flash games, but Firefox suits my needs for video except when MS Silvelight is required which rarely happens anymore . Browsers behave differently with different hardware so only  comparisons with the same or similar hardware would be of value. I use  an HTML 5 un-block extension for Youtube and the change from flash to HTML 5 continues to be a slow one. 

 [http://liliputing.com/2014/09/native-support-netflix-coming-ubuntu.html](http://liliputing.com/2014/09/native-support-netflix-coming-ubuntu.html)

---

### Post by nineteen-73 on 2014-09-20
> **Frogs Hair said:**
> Perhaps you should indicate specific problems you are having .[http://liliputing.com/2014/09/native-support-netflix-coming-ubuntu.html](http://liliputing.com/2014/09/native-support-netflix-coming-ubuntu.html)     I've done the following with FireFox closed: ```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update 
sudo apt-get install --install-recommends pipelight-multi 
sudo pipelight-plugin --update 
sudo pipelight-plugin --enable silverlight 
```
Afterward when I log into Netflix via FF, I am unable to stream movies.

---

### Post by nineteen-73 on 2014-09-20
Curious. My response above didn't format properly. It all came out on a single line. Why?

---

### Post by QIII on 2014-09-20
To get Netflix to work, you will need to add a User Agent Switcher to Firefox to get Netflix to think you are running Windows.

---

### Post by nineteen-73 on 2014-09-20
> **QIII said:**
> To get Netflix to work, you will need to add a User Agent Switcher to Firefox to get Netflix to think you are running Windows.  Will do!

---

### Post by rosswmcgee on 2014-09-20
Opera 

Because it has a wonderful speed dial and also it is an email client. It is a one stop shop.

---

### Post by nineteen-73 on 2014-09-20
I had no luck with User Agent Switcher, but User Agent Overrider did. But now Netflix works properly.

---

### Post by sammiev on 2014-09-20
I use FF with everything but Netflix. ( but having done it a few years )

I use Google Chrome with [this]("http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins") for Netflix.

---

### Post by carrington2 on 2014-09-20
I like chrome browser. Because it has good opportunity to add any extension. So for this reason i did like it.

---

### Post by kira-yamato-2008 on 2014-09-20
> **carrington2 said:**
> I like chrome browser. Because it has good opportunity to add any extension. So for this reason i did like it.

The problem with Chrome is it gets more and more resource demanding, in my experience, the longer you use it with out exiting the program. More importantly Chrome has a slew of security holes, partially extending to it's lack of checking SSL certificates. All in all I'm much more comfortable with FireFox for those reasons, especially with extentions like NoScript, AdBlock Plus, Flash Block, and Certificate Patrol.

---

### Post by Elfy on 2014-09-21
*Thread moved to **Recurring Discussions**.*

---

### Post by olliemonster on 2014-09-21
I prefer to use firefox whenever possible mainly because of the slew of better add ons and also cause i don't want google to get more info about than they already have however when i find a html video i tend to switch to chrome because google have impented h264 better than firefox.

---

### Post by cesarvilla9421 on 2014-12-09
I proved opera developer and it's great, i really liked it.. But it doesn't work well on ubuntu.. Between Chrome and Firefox.. I have to say firefox is better.

---

### Post by pfeiffep on 2014-12-10
I use Firefox which I just switched to from Chromium. I believe Firefox is a bit more secure.

---

### Post by Camilia on 2015-03-02
> **nineteen-73 said:**
> I had no luck with User Agent Switcher, but User Agent Overrider did. But now Netflix works properly.
From where do you download User Agent Overrider? I tried ubuntu software center and synaptic manager and was not able to find it.

---

### Post by deadflowr on 2015-03-02
> **Camilia said:**
> From where do you download User Agent Overrider? I tried ubuntu software center and synaptic manager and was not able to find it.
Depending on browser, either chrome webstore (for chrome) or mozilla/firefox
firefox is easier, just go to the menu item add-ons, and then use it's function to search for it.
(Tools >> Addons >> use search bar "user agent overrider")

---

### Post by Camilia on 2015-03-02
> **deadflowr said:**
> Depending on browser, either chrome webstore (for chrome) or mozilla/firefox
firefox is easier, just go to the menu item add-ons, and then use it's function to search for it.
(Tools >> Addons >> use search bar "user agent overrider")
Found it. Now to use it do you choose options for windows?

---

### Post by deadflowr on 2015-03-02
> **Camilia said:**
> Found it. Now to use it do you choose options for windows?
If you want to use it with pipelight for netflix, it is best to use the settings that the pipelight devs have recommended.
[http://pipelight.net/cms/installation-user-agent.html](http://pipelight.net/cms/installation-user-agent.html)

otherwise, dealer's choice.
(you being the dealer)

---

### Post by pfeiffep on 2015-03-02
I found a site that specifically states that FireFox is the most secure browser wrt certificat revocation. Test it yourself [here]("https://www.grc.com/x/ne.dll?rh1dkyd2")

---

### Post by sammiev on 2015-03-02
> **pfeiffep said:**
> I found a site that specifically states that FireFox is the most secure browser wrt certificat revocation. Test it yourself [here]("https://www.grc.com/x/ne.dll?rh1dkyd2")

I use GRC often, great site.

---

