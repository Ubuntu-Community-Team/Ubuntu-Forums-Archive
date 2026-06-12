---
title: "not sure how web apps is supposed to work"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by Allen McBride on 2015-01-12
I'm using 14.10 with Unity. When I go to a popular web page in Firefox, I get a popup asking, "Would you like to install [this website]?" I always say yes, but nothing ever happens that I can tell.

From what I've read, this is a "Web Apps" thing, and maybe I'm supposed to get a new icon in the launcher, and/or a new directory in /usr/share/unity-webapps/userscripts? I'm not seeing either of those things.

I see some complaints about Web Apps being broken in 14.04, but I can't tell whether that's been fixed or whether it's even related to the problem I'm having. I might just not know how to use the Web Apps feature.

---

### Post by DuckHook on 2015-01-12
...well, two things:

You might want to refrain from saying "yes" from now on. I never do, for security reasons. The biggest vector for malware these days is the browser and most people do not come close to practicing good security habits when surfing. My own browser is locked down tighter than a drum and I will not allow anything to install on it unless I know *exactly* what it is (and by exactly, I mean in extensive technical detail) and am absolutely positively sure that it won't do anything to my system other than what it's supposed to do. 99% of the time, I won't permit it even then. If you would like to know more about security, the following are good intros for beginners.

Basic Security:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

My own previous rant on the subject is this one:

[http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795](http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795)

As to your question proper:

Without further info, it is impossible to know what this "popular" website is trying to install. It could be a script, a web app, or a tracking cookie, all of which gives me the willies just thinking about it (see above).

If it's a Silverlight script, for example, this is made for the Windows world and Linux won't run it. Since your Linux browser is not configured to run Silverlight, it would just ignore it. If it's a piece of malware like a keylogger, then you can hardly expect it to continue advertising its presence with a button.

If I'm alarming you, then it's not through any desire to be perverse on my part. I'm just describing the way the real web works.

---

### Post by Allen McBride on 2015-01-12
Thanks. When I say "popular", I mean, for example, Reddit, Tumblr, Twitter, any major Google site, Facebook, etc. Also launchpad.net, to name a less-popular site. The pop-up has an Ubuntu logo on it, and I never saw it before switching to Ubuntu. So I appreciate your anti-malware message, but I still think this is an Ubuntu/Unity feature. (In fact, I think it is the feature advertised at the following site, which is aimed at web developers and not users: [https://developer.ubuntu.com/en/web/](https://developer.ubuntu.com/en/web/))

The exact message is, "Would you like to install [name of website], for extra features and more access?"

EDIT: Sorry, I re-read my original message and now I realize why you thought I was referring to one particular website. I should have said, "When I go to any of several popular web pages..."

---

### Post by ian-weisser on 2015-01-12
> **Allen McBride said:**
> maybe I'm supposed to get a new icon in the launcher,

In the dash, not the launcher.

---

### Post by DuckHook on 2015-01-12
Ah. In these cases (and *only* these cases), they are indeed webapps and they install automatically into your system as a "customized" browser&#8213;sometimes so customized as to look like a stand-alone app and be unrecognizable as a browser extension. They may not declare their presense and only be seen when you bring up the Dash where&#8213;surprise!&#8213;you suddenly find an "app" there that wasn't there before. I'm afraid that I'm of limited help here since I won't install these things no matter who they're from, and so don't have enough experience with the technology to be of use to you.

Perhaps other more knowledgeable members might jump in.

---

### Post by Allen McBride on 2015-01-12
Thanks to you both. They don't install to the dash either when I click "yes", and I get asked again when going to the same site in a fresh session. However, when I search for them in the dash, I see them (not yet installed) among others under "more suggestions". When I've tried to install a couple of them that way, I get an application that, when run, gives me a blank window with a toolbar that has a back arrow, a globe icon, and that's it. So there seems to be something wrong with Web Apps in my Ubuntu installation. Perhaps Firefox or something interacting with Firefox detects this problem and silently refuses to install the webapp (at least when I'm not demanding it explicitly). But it's not a big deal. I'm happy to go the sour-grapes route and figure that if they're anything like the stand-alone app versions of websites on my Android phone, I'm not missing out on much :-).

---

### Post by DuckHook on 2015-01-12
[This]("http://discourse.ubuntu.com/t/theres-a-ubuntu-browser-in-trusty/1594") thread might help. Apparently, Ubuntu has implemented a new browser called *Oxide* as an *integrated* app in Unity (I was wondering what that new generic 'Browser" was that suddenly appeared in all flavours of 14.04). This browser is designed to act as the foundation for all webapps, thus replacing browsers like FF and Chrome/ium because those can come and go at the whim of the user. Trouble is that *Oxide* is apparently broken for a lot of webapps and is not really ready for prime time.

Whatever you do, don't uninstall *Oxide*. Because it is meant to form an integral part of webapp functionality, it is "baked in" to Unity and force uninstalling it will break Unity.

All above is hearsay from linked thread above and may already be superseded by subsequent developments.

---

### Post by deadflowr on 2015-01-12
For what it's worth:
All web apps are install locally to the user's home directory, and not system wide, which is why you'll never be prompted for your sudo/admin password.
You can find the launcher within the users hidden folder > .local/share/applications folder.

Here's the web-apps launchpad page, which currently has a list of available web-apps listed for various sites
[https://launchpad.net/webapps](https://launchpad.net/webapps)

---

### Post by Allen McBride on 2015-01-13
Thanks DuckHook and deadflowr! This is helpful. Deadflowr, for me there's nothing in that directory, but at least I know what's supposed to be going on (and that such a directory exists). And it's good to know where the official webpage for this is, as well as its proper name (Oxide).

---

### Post by deadflowr on 2015-01-13
> **Allen McBride said:**
> Thanks DuckHook and deadflowr! This is helpful. Deadflowr, for me there's nothing in that directory, but at least I know what's supposed to be going on (and that such a directory exists). And it's good to know where the official webpage for this is, as well as its proper name (Oxide).

Indeed, seems like something's different.
On an older 14.04 install I have launchers for launchpad, and other webapps inside my local/share/applications folder.
But on a new install I do not, they seem to be more integrated with the overall system.
I haven't installed any newer ones on the old system, so my thinking is they are just leftovers perhaps. Odd.
No matter, when they install the install under the name unity-webapps-fillinthenameofthehere. So if you want to remove them just run a quick
```
sudo apt-get remove unity-webapps-whateverthenameforthewebbappsis
```
Well, at least I'm learning something new.

---

