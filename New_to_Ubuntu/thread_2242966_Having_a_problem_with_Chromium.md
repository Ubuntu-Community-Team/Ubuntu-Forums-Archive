---
title: "Having a problem with Chromium"
date: 2014-09-05
forum: New to Ubuntu
---

### Post by Knightmare060 on 2014-09-05
Hello I'm new to using ubuntu and I'm having a bitt of a problem because Chromium keeps closing right after I open it.

I tried from terminal and this is what I got
[HTML]chromium-browser
[12679:12679:0905/150049:ERROR:desktop_window_tree_host_x11.cc(1497)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[12679:12731:0905/150049:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
[12679:12709:0905/150050:FATAL:url_request.cc(709)] Trying to send secure referrer for insecure load
Aborted (core dumped)[/HTML]

So...help?

---

### Post by pfeiffep on 2014-09-05
I'm  using Ubuntu 14.04.1 with Chromium [COLOR=#303942][FONT=Ubuntu]36.0.1985.125 which was installed via software center with no problems. 

The error that you reported appears to originate from a test version.  

I suggest completely removing Chromium and re-installing.[/FONT][/COLOR]

---

### Post by Knightmare060 on 2014-09-05
I tried that and it's still the same thing :(

---

### Post by Rob Sayer on 2014-09-07
Did you use 

```
sudo apt-get remove
```

or

```
sudo apt-get purge
```

?  Because only the latter will *completely* remove it.

If you have a beta version installed rather than the tested one from the ubuntu repos you must have added a 3rd party ppa to do it.  You'd have to remove that from your software sources list or else when you reinstall it'll just install the same version you had before.  I recommend synaptic package manager for this.  I haven't used software center for ages.

Actually if there's one piece of advice I'd give noobs it'd be don't use 3rd party untested ppa's unless you really can't avoid it.

I had problems with chromium in 14.04 but that was in Lubuntu, which I found so buggy that frankly I think it's a stain on ubuntu that they support it.  Chrome works fine.  Frankly unless you're a FOSS zealot I don't see the point of Chromium over Chrome.  It's just not as well supported in Linux as chrome is.

---

### Post by craig10x on 2014-09-07
Chrome would be the better choice...i would just uninstall chromium and download the .deb file from google chrome website...aside from being much better supported then chromium as was previously mentioned, it also has the pepperflash plug in (which gives you the latest flash version) as well as a neat built in pdf reader and also adds a ppa to your software updater so that as soon as a new version becomes available, you get it with your usual ubuntu updates...

---

### Post by Dennis N on 2014-09-07
> it also has the pepperflash plug in (which gives you the latest flash version) as well as a neat built in pdf reader
Well, lets be fair..Chromium uses the pepperflash plugin also, and has the same built in PDF reader (looking at ver. 37) included.

---

### Post by craig10x on 2014-09-07
Yes, that is true... you can ADD on pepperflash to chromium and it does now come with the pdf reader (finally...lol)  but still, Chrome is better supported and does give you quicker upgrades to the newest versions...and those two features are pre-installed by default...nothing at all to add...also, i seem to notice people having more problems with installing chromium...it seems pretty rare that i read someone on the ubuntu forums having problem installing chrome...

---

### Post by andrew102 on 2014-09-08
Solution

```
sudo apt-get remove chromium
```
```
sudo apt-mark hold chromium
```

```
sudo apt-get update
```
```
sudo apt-get install firefox
```

problem solved

---

### Post by Steve_Guy on 2014-09-08
have to agree with andrew102 - Chrome has continually crashed my system (for reasons I have yet to establish - will go through logs at some point when I have the time).  Not so with FF.

---

### Post by craig10x on 2014-09-08
Firefox is installed on ubuntu by default so why would he need to install it again? (or were you just making a joke there...lol)

Chrome has never crashed on my system, perhaps you are having some other problems that cause that...
Anyway, again, i would suggest he uninstall chromium and try doing the install from the google chrome website and see how it goes :D

---

### Post by vasa1 on 2014-09-08
And why is
**sudo apt-get remove chromium**
followed by 
**sudo apt-mark hold chromium**? What is apt-mark for in *this* context?

---

### Post by vasa1 on 2014-09-08
> 
... This even applies if you have friends that confirm your anecdotes.  "Anyone else's <browser name> behaving terribly lately?" is pretty much guaranteed to get affirmative responses no matter which browser you name.  Then people will talk about how they switched browsers and life got much better.  But a day later there will be a thread that flips the names of those two browsers around and you'll still see tons of posts in it. ...
from [https://plus.google.com/+PeterKasting/posts/fNU31MWqYrX](https://plus.google.com/+PeterKasting/posts/fNU31MWqYrX)

---

### Post by andrew102 on 2014-09-19
Everyone my post was meant as a joke.

Still I do an apt-mark hold on chromium so I don't have to bother downloading it. I much prefer to use Firefox.

---

### Post by nineteen-73 on 2014-09-19
> **andrew102 said:**
> Everyone my post was meant as a joke.

Still I do an apt-mark hold on chromium so I don't have to bother downloading it. I much prefer to use Firefox.

Why do you prefer Firefox over Chrome?

---

### Post by andrew102 on 2014-09-23
> **nineteen-73 said:**
> Why do you prefer Firefox over Chrome?

Well here's a list:

[LIST]
[*]I can actually use Firefox, eg: I haven't found the equivalent of about:config in chrome (if somebody knows please tell !)
[*]Add-ons
[*]Malware (this is more to do with Windows) - I haven't experienced anywhere near as many instances of browser highjacking (for example) in recent months/years until Chrome came along, also said about:config above makes it easier to rectify malicious changes.
[*]Security wise Firefox has a stong backing behind it and updates are released quite frequently.
[*]Mozilla seemed to have rectified the high memory usage from some time ago. Unfortunately Chrome still uses quite an amount of RAM.
[*]Having used chrome briefly it does seem marginally faster than firefox but that isn't enough to get me to join the bandwagon.
[/LIST]

While I'm at it could anyone tell me if Chrome defaults to google's DNS servers?? I'd like to know. (I remember I had to change something to get local addresses to resolve from the address bar instead of doing a google search)

---

### Post by andrew102 on 2014-09-23
> **andrew102 said:**
> Well here's a list:
[LIST]
[*]Security wise Firefox has a stong backing behind it and updates are released quite frequently.
[/LIST]


Actually this probably isn't any different to Google/Chrome...

---

### Post by pfeiffep on 2014-09-24
> **andrew102 said:**
> Well here's a list:

[LIST]
[*]I can actually use Firefox, eg: I haven't found the equivalent of about:config in chrome (if somebody knows please tell !)
[/LIST]

The chrome / chromium equivalent is about:flags

---

### Post by Mike_Walsh on 2014-09-25
> **craig10x said:**
> Chrome would be the better choice...i would just uninstall chromium and download the .deb file from google chrome website...aside from being much better supported then chromium as was previously mentioned, it also has the pepperflash plug in (which gives you the latest flash version) as well as a neat built in pdf reader and also adds a ppa to your software updater so that as soon as a new version becomes available, you get it with your usual ubuntu updates...

That's interesting you say that, Craig. My Chromium is currently on exactly the same version as my Chrome; 37.0.2062.120.

A few months ago, Chromium was lagging several versions behind Chrome; but now (at least in my case), Canonical and the Chromium devs appear to be much more 'on the ball' with regard to keeping Chromium updated as quickly as possible in the repos. All credit to them.

Maybe some of the mirrors around the globe are being updated more regularly than others; just a thought. Certainly, we seem to get updates VERY quickly here in the UK. I don't know what the situation's like on your side of "the Pond"...

Regards,

Mike.

---

### Post by craig10x on 2014-09-25
mike: sounds like it's much better now regarding getting the newer versions of chromium as they use to lag way behind chrome's updates...glad to hear that ;)
still, overall, i just find it easier to install chrome since it already has the pepperflash and pdf reader in it (although i heard that the pdf reader was finally added to chromium)...

It's not like is any harder to install then grabbing chromium from the software center, as all one has to do is open firefox, go to Chrome's site and download the deb, and when it finished downloading just hit the default "Open to Software Center", the software center pops up with it and you hit "install"....done :D

---

### Post by Mike_Walsh on 2014-09-25
The interesting thing is, in some of my distros, I can install Chrome; but if I look in the Software Centre for 'installed software'.....it doesn't show.

So if it doesn't show....where is it? I can't find it by looking in /etc, either; it doesn't show up ANYWHERE. Chromium shows, but there is NO trace of Chrome. I suppose if I needed to remove it for any reason, I'd need to do so via the terminal.

That, and removing the ppa...

Regards,

Mike.

---

### Post by vasa1 on 2014-09-25
> **Mike_Walsh said:**
> The interesting thing is, in some of my distros, I can install Chrome; but if I look in the Software Centre for 'installed software'.....it doesn't show.

So if it doesn't show....where is it? I can't find it by looking in /etc, either; it doesn't show up ANYWHERE. ...
```
[07:39 PM] ~ $ whereis google-chrome
google-chrome: /usr/bin/google-chrome /usr/bin/X11/google-chrome /usr/share/man/man1/google-chrome.1
[07:39 PM] ~ $ 
```That works for me.

```
which google-chrome
```also works.

---

### Post by Mike_Walsh on 2014-09-25
Well, **that **worked.

First one returned "Command not found".

But the second one returned:-

```
/usr/bin/google-chrome stable
```

So that's answered that! But I still am curious as to why it's not listed along with the installed software.....or is that to do with the external ppa Chrome installs?


Regards,

Mike.

---

### Post by vasa1 on 2014-09-25
> **Mike_Walsh said:**
> Well, **that **worked.

First one returned "Command not found".

But the second one returned:-

```
/usr/bin/google-chrome stable
```

So that's answered that! But I still am curious as to why it's not listed along with the installed software.....or is that to do with the external ppa Chrome installs?


Regards,

Mike.
It would be nice to know the distro on which the first command doesn't work. I'd think that "whereis" is one of those pretty standard things. Re. the ppa, once dpkg gets involved there shouldn't be any different treatment of debs belonging to ppas whether from launchpad or elsewhere. AFAICT.

What happens when you run```
dpkg --get-selections | grep "chrome"
```

---

### Post by craig10x on 2014-09-25
@mike: yes, that's true...i can never find it (after it is installed) in the software center...however, it does appear (and can be removed) on synaptic package manager, after it's installed....in fact, in package manager you would see that not only is the installed stable version shown but also the beta and the development version as well, so they can also be installed from there as well (after removing stable of course)...and it appears in the dash, of course...which is where i bring it up the first time and then lock it to the unity launcher...

---

### Post by vasa1 on 2014-09-25
> **craig10x said:**
> @mike: yes, that's true...i can never find it (after it is installed) in the software center... 
Hmmm... I wonder if that's a feature of the Software Center? I wonder if Xubuntu users also see the same thing or it's something limited to Unity (even though both use the same software center). I wonder if someone installs any other ppa, whether that software wouldn't show up as well.

---

### Post by Mike_Walsh on 2014-09-25
Hi, vasa.

Now, then; the command returns this:-

```
google-chrome-stable                install
xserver-xorg-video-openchrome            install
```

And the distro is Ubuntu 14.04.

My spelling mistake on the other one! If I enter the other command, this is what I get:-

```
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ whereis google-chrome
google-chrome: /usr/bin/google-chrome /usr/bin/X11/google-chrome /usr/share/man/man1/google-chrome.1
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 

```

Astonishing what adding a space in the wrong place will do... ;)

Actually, to answer your other point, I can tell you. I've got the Xfce desktop installed on here as well; at login, 'Ubuntu' & "Xfce session" both run Ubuntu; 'Xubuntu session', of course, gives me Xubuntu.....and it's exactly the same there, too. Doesn't show up in the Software Centre.

I also have the noobslabs ppa installed, for Unity Tweak Tools; that doesn't show in the Software Centre, even though it's in the repos anyway. Curious, isn't it?

But I think we're getting 'off-topic' here again..!


Regards,

Mike.

---

### Post by vasa1 on 2014-09-25
> **Mike_Walsh said:**
> ...
But I think we're getting 'off-topic' here again..!
...
Subject for another thread, why do you keep such a long prompt: **paul@paul-EK335AA-ABU-SR1619UK-GB540:~$** ?

---

### Post by andrew102 on 2014-09-25
> **pfeiffep said:**
> the chrome / chromium equivalent is about:flags

thanks !

---

