---
title: "brasero doesn't work"
date: 2015-09-08
forum: New to Ubuntu
---

### Post by Daniel_Sierra on 2015-09-08
Hi, I'm really newby in ubuntu. I've tried to burn a dvd in brasero and it says to me this:

Please install the following manually and try again:
mplex (GStreamer plugin)
vcdimager (application).

I've gone to gstreamer web page and it says I should find it in my distribution's package repository. I'm not sure what to do, can anyone help me please?

thank you for your atention

---

### Post by coffeecat on 2015-09-08
There was a flurry of similar questions with the same error message in about 2010 with a now-fixed bug (as far as I can make out) in the now-obsolete 10.04 version of Ubuntu. Before we go any further - which version of Ubuntu are you using? If you are using 10.04, you need to be running a supported and current version.

---

### Post by Daniel_Sierra on 2015-09-09
Hi, thanks for the answer. I'm using ubuntu 15.04 so I think that's not the problem.

---

### Post by MartyBuntu on 2015-09-09
Honestly, I would just install K3B...and accept all the KDE libs that come with it. It's not that painful and K3B is one of my favourite burning applications of all time.

---

### Post by Geoffrey_Arndt on 2015-09-09
And did you install Brasero from either the Ubuntu Software Center OR by using the Synaptic Package Manager with only the official Ubuntu repositories active?

    Whenever I read about new users of Linux (no matter what distro) . . going to a web site to download and install an application, I cringe.    Because with rare exceptions (like installing the Chrome Browser from Google) . . . that practice of going to other websites to get software for Ubuntu is a "non-starter" . . . in other words, not recommended.

---

### Post by coffeecat on 2015-09-09
Well... Brasero comes in a default installation of Ubuntu. I doubt whether the OP will have needed to have installed it.

@Daniel_Sierra, I'm fairly sure the packages you need are gstreamer0.10-plugins-bad-multiverse and vcdimager, both of which you can find and install using the Software Centre. But rather than fiddling about with individual packages, you might want to install the metapackage ubuntu-restricted-extras, which will bring in a whole load of useful restricted stuff including most of the multimedia libraries that you will need. That will definitely bring in gstreamer0.10-plugins-bad-multiverse, but I'm not sure about vcdimager. If you install ubuntu-restricted-extras, check in Software Centre afterwards to make sure vcdimager has been installed. And if you do install ubuntu-restricted-extras, watch out for a EULA for the Microsoft Core Fonts. If you don't agree to that, the fonts don't get installed, which include useful things like Times New Roman, Arial and Verdana.

---

### Post by Geoffrey_Arndt on 2015-09-09
Good post coffeecat.    I once had a doxie (dachshund) who like dipping his nose into an old beer stein with a dreg or two at the bottom.   Was tipsy a couple times till I pulled him off the juice.

Anyway, the restricted-extras thing is always good to do.    One aspect of that update is kinda tricky, in that the MS-fonts eula often pops-up in a window that is "hidden" behind the installer window (USC or Synaptic), so I like to shrink the installer window so I can see the eula window and then agree to it (otherwise I've seen the install hang -up and once it didn't even finish).

G

---

### Post by Daniel_Sierra on 2015-09-10
Hi. Thanks for the answers, I've found all the pakages on the software center. Brasero works and become to burn, but then stop and say that is imposible to link plugin pads. This are the last lines of the error log

BraseroVob called brasero_job_get_audio_output
BraseroVob called brasero_job_tag_lookup
BraseroVob called brasero_job_tag_lookup
BraseroVob Setting ratio 16:9
BraseroVob Error while linking pads
BraseroVob can't create object : Impossible to link plugin pads 

BraseroVob stopping
Session error : Impossible to link plugin pads (brasero_burn_record brasero-burn.c:2856)

I think I'll try with k3b

---

### Post by Geoffrey_Arndt on 2015-09-10
also, best to set at slow burn speeds (4x or 8x) . . doesn't take much longer but fewer errors.

---

