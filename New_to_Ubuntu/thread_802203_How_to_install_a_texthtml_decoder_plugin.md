---
title: "How to install a text/html decoder plugin"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by sashag on 2008-05-21
Hi!

I tried to listen to a radio station here in Canada, and when I typed in
the URL of the radio station through the Ubuntu music player, I got a popup
that said that the text/html decoder was not installed. How do I go about doing that? Thanks!

---

### Post by Monicker on 2008-05-21
I don't recall seeing that particular message before myself.  Would it be possible for you to give the url of the radio station?

---

### Post by sashag on 2008-05-21
Hi!

Yes, here's the URL of the radio station:

[http://www.650cisl.com](http://www.650cisl.com)

Hope that helps! Thanks.

---

### Post by shifty_powers on 2008-05-21
it apparently uses flash.

what vresion of flash do you have installed in firefox?

---

### Post by shifty_powers on 2008-05-21
oh and it worked for me...

---

### Post by phubert28 on 2010-06-03
I am running Firefox 3.6 under 64 bit Ubuntu 10.4


I have just run into the same problem trying to play my voicemail online with Comcast Digital Voice.

It searches for a package with the plugin and cannot find one.

---

### Post by phubert28 on 2010-06-03
It turns out (another thread) the SOLUTION is simply to go to Synaptic and install

gecko-mediaplayer

and restart your browser.

Works fine.

Just emailed Comcast (for what good it will do) and am online with their chat trying to communicate there as well.

---

### Post by rworloma on 2010-06-29
Read this guide [Liberian Geek]("http://www.liberiangeek.net/2010/06/listen-to-internet-radiomusic-in-ubuntu-10-04-lucid-lynx/")

---

### Post by zbeekman on 2010-07-27
This is great and all, and fixes it for firefox, but google chrome is still broken.  Any one have any thoughts?

Here are all the plugins chrome is using:
[http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png](http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png)

These are what firefox is using:
[http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png](http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png)

Does anyone know exactly which firefox plugin is getting this working?  Also, how do I add that to google chrome?

---

### Post by phubert28 on 2010-07-27
The Liberian Geek reference is interesting... what the heck is "gksu " ??

:-)

As to plugins for Chromium, I really couldn't say. I ONLY use Chromium if I run into a site problem with Firefox. I'm one of those 'brand loyal' guys.

---

### Post by zbeekman on 2010-07-27
Note: chromium != google-chrome.  Google for google chrome and you'll see google-chrome is now out of beta for ubuntu.  It is real fast, and stable too.

---

### Post by phubert28 on 2010-07-27
mmmm... what's the difference between Chromium and Google chrome?

I didn't realize there was a distinction.

So where does one get Google Chrome for 64 bit Ubuntu???

---

### Post by Lucre on 2010-09-23
The difference between Chromium and Chrome is that Chromium is the open source project behind Chrome.  I'm not someone who knows a lot about what he's talking about, but in my (limited) experience, they're pretty much identical, functionally.  I don't know if there's a .deb, but [here]("http://groups.google.com/group/chromium-dev/browse_thread/thread/701cd2dadcc639d3")'s something about Chromium for 64 bit.

EDIT: I have a hunch that link won't actually be much help...  I'll keep an eye out.  I don't know enough about PPAs to tell you for certain, but the first FAQ [here]("https://launchpad.net/~chromium-daily/+archive/ppa") seems to suggest that you can just install the PPA and get the 64 bit version.

---

### Post by slkamath on 2011-01-03
Hi,

In my chrome browser it's not working.

How to solve the problem?

Regards

Lokesh.

> **phubert28 said:**
> The Liberian Geek reference is interesting... what the heck is "gksu " ??

:-)

As to plugins for Chromium, I really couldn't say. I ONLY use Chromium if I run into a site problem with Firefox. I'm one of those 'brand loyal' guys.

---

### Post by Terryaaa on 2011-04-08
> **phubert28 said:**
> It turns out (another thread) the SOLUTION is simply to go to Synaptic and install

gecko-mediaplayer

and restart your browser.

Works fine.

Just emailed Comcast (for what good it will do) and am online with their chat trying to communicate there as well.

Nope! That doesn,t work either. did total reboot. Now have "gecko" and all its dependancies installed. But still do not have "text/HTML decoder" plugin.

---

### Post by sallykwitt on 2011-06-25
Thank you!  I got it working now on Chromium.  This forum is so great.

---

### Post by mbendaniel on 2012-03-15
This worked for me.

> **phubert28 said:**
> It turns out (another thread) the SOLUTION is simply to go to Synaptic and install

gecko-mediaplayer

and restart your browser.

Works fine.

Just emailed Comcast (for what good it will do) and am online with their chat trying to communicate there as well.

---

