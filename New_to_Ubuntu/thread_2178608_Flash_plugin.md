---
title: "Flash plugin"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by rami5 on 2013-10-04
Hi
I installed Ubuntu yesterday.
Durring the installation, i chose NOT to install third party pluging ( dont remember the names, but it was for Flash and MP3 i think ).

OK, so today when i try to watch YouTube videos ( Firefox ), i get prompted to install Flasgh Plugin... But i can watch videos just fine on YouTube without the plugins.

Whats going on here?
Do i need the Firefox flash plugin at all?
Why was i asked to Flash ( well... flash sumthin' ) plugin at installation?
Do i need a flash plugin at all?

---

### Post by grahammechanical on 2013-10-04
Who is prompting you to install the flash plugin? Ubuntu or the web site? Ubuntu is open source and based on Linux/Debian. The Debian developers do not believe in using any proprietary software at all. But without proprietary codecs certain audio and video formats will not run on Linux. Would you be happy with that? Or would you demand your money back?

The Ubuntu developers give us an option to install third party software during the installation. Some distributions install third party software as standard but not Ubuntu. The Ubuntu developers accept the philosophy of the Debian developers but also make it easy for those of us who do not see any ethical reason for not using free to download and free to use proprietary software if it makes for an improved user experience.

We can install third party software after installation if we choose to. In the Ubuntu Software Centre we will find Ubuntu Restricted Extras. That will bring in some codecs and we may need to accept the licensing terms of the copyright owners. We can even install the Adobe Flash Plugin. But notice, we are only installing the installer to the plugin. We are not installing Adobe Flash, The installer does that.

If you were to use Chromium then you would find that you may not be able to run those videos. But installing the Flash Plugin installer will fix it even though we are using Chromium and not Firefox. If we want to we can install something called Pepper flash player for Chromium. I think that is open source code.

Is there anything else that you demand to know, What is going on here?

Regards.

---

### Post by rami5 on 2013-10-04
The installation asked me if i wanted to install third party software ( flash + mp3 related ).
Also Firefox ( preinstalled with Ubuntu ) prompts me for Flash plugin on various sites.

As i have not accepted any of the above mentiond, i am a bit stumped as to why i am able to view the content on theese pages in the first place.
Why is this?

Pleace forgive me, but as to your last question
"Is there anything else that you demand to know, What is going on here?"
Im not sure what you mean or how to answer that.
What is going on with what? :P

---

### Post by ajgreeny on 2013-10-04
Some sites including youtube are now using html5 for what were flash videos; that is why youtube (and some other webpages) work OK.

Unfortunately not all websites use html5 and it is those which will not play without flash being installed.

Install the appropriate **restricted-extras** package from software-centre and you will get most of what you need in one go.

---

### Post by philinux on 2013-10-04
> **rami5 said:**
> Hi
I installed Ubuntu yesterday.
Durring the installation, i chose NOT to install third party pluging ( dont remember the names, but it was for Flash and MP3 i think ).

OK, so today when i try to watch YouTube videos ( Firefox ), i get prompted to install Flasgh Plugin... But i can watch videos just fine on YouTube without the plugins.

Whats going on here?
Do i need the Firefox flash plugin at all?
Why was i asked to Flash ( well... flash sumthin' ) plugin at installation?
Do i need a flash plugin at all?

As ajgreeny says install the package ubuntu-restricted-extras from the software center or if you're comfortable with the terminal then:- assuming it was Ubuntu you installed and not say kubuntu or xubuntu.

```
sudo apt-get install ubuntu-restricted-extras
```

Lots of sites still use flash.

---

### Post by rami5 on 2013-10-04
Aha, that explains it perfectly!
Thank you all for explaining this to me, i understand now :)

And yes i am using Ubuntu.
I did find the Terminal App, but i think ill just stick with clicking for nw :)
Untill i encounter a situation where i really 'need' Flash, i think ill just skipp it for now.

Again, thanks a bunch!
( ill try to figure out how to mark this thread as solved now )

---

### Post by craig10x on 2013-10-04
rami5: by the way...wanted to let you know that although ubuntu restricted extras does install flash plug in, it is rather old (about 2 years in fact) and only gets security updates....not ubuntu's fault....adobe decided no longer to make new versions available for linux....but there is a way around that...if you would like the current and up to date adobe flash plug in you can get it if you switch to google chrome web browser (not chromium which doesn't have it but the official one from google's site)...

Reason being is that Adobe has a deal with google to provide the latest flash cross platform (including the linux version) for Chrome's pepperflash which comes with the browser...so by using Chrome you would automatically always have current and up to date flash!

You should install ubuntu restricted extras anyway because it provides all the codecs (and the old flash) so it is good to have....i never have ubuntu pre-install it (that checkbox option you saw on the installer) but instead i always install it from the software center AFTER i install a new ubuntu...

---

### Post by rami5 on 2013-10-04
Why stop support for linux?
What Linux ever done to them :)

So one might assume that Flash, in general, is on its way out then

---

### Post by philinux on 2013-10-04
> **rami5 said:**
> Why stop support for linux?
What Linux ever done to them :)

So one might assume that Flash, in general, is on its way out then

A lot of people would say yes and the sooner the better. Ubuntu firefox will still get Adobe flash security updates.  Can't remember how long for but it is years not months. 

Html5 is taking a long time to get adopted across the web.

If you use tje forum search or web search all the historic info is out there.

---

