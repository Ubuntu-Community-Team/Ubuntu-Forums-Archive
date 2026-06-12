---
title: "Playing DVD's in Totem without having PulseAudio installed"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by mdavis1231 on 2013-03-09
Does anyone else have a problem playing DVD's in Totem without having PulseAudio installed?  This worked fine in Ubuntu 10.04 LTS, but in 12.04 LTS, I get the error:

[IMG]http://i1223.photobucket.com/albums/dd512/mdavis1231/Screenshotfrom2013-03-09213413_zpsc6654969.png[/IMG]

I have it to where I can turn PulseAudio on when I want to play a DVD, and off again when I'm finished, but I would rather not have to do this, and I don't really want to switch to VLC, which works perfectly without PulseAudio installed.

---

### Post by BlinkinCat on 2013-03-09
Hi, 

Perhaps these links will help,

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://launchpad.net/ubuntu/precise/+package/gstreamer-tools](https://launchpad.net/ubuntu/precise/+package/gstreamer-tools)

Cheers - :P

---

### Post by mdavis1231 on 2013-03-10
Thanks so much for your response.  I do already have both ubuntu-restricted-extras and gstreamer-tools 0.10.36-1ubuntu1 installed, so I am able to play DVD's in Totem.  However, I have to turn on PulseAudio first.  I have created shortcuts with icons for turning PulseAudio on and off in the Applications menu.  However, I'm trying to figure out what it is that's stopping Totem from playing DVD's without PulseAudio turned on in 12.04 LTS, whereas in 10.04 LTS Totem didn't seem to need PulseAudio at all.  ](*,) Thanks![URL="https://launchpad.net/ubuntu/precise/i386/gstreamer-tools/0.10.36-1ubuntu1"] 
[/URL]

---

### Post by 3rdalbum on 2013-03-10
If you rip out sections of your operating system, you kinda have to expect that it will cause breakage.

I can't get Totem to play encrypted DVDs, even with Pulseaudio on - I just use VLC. Sorry it's not a solution to the precise problem, but I think most would agree that you should just use VLC regardless of whether you have Pulseaudio or not.

---

### Post by mdavis1231 on 2013-03-10
I'm sort of coming to that conclusion.  VLC plays DVD's just fine, even if I were to completely purge PulseAudio.  It's unfortunate...I really like Totem.  I'm not sure why Ubuntu seems to be going backward on some things with each release instead of going forward.  The best Ubuntu that I've used so far has been 8.04 LTS.  It just worked.  Now it seems with each release/LTS release, you have to find tons of work-a-rounds.  Thanks for the advice!

---

### Post by 3rdalbum on 2013-03-10
> **mdavis1231 said:**
> I'm not sure why Ubuntu seems to be going backward on some things with each release instead of going forward.  The best Ubuntu that I've used so far has been 8.04 LTS.  It just worked.

You're welcome for the advice.

I think you're looking at 8.04 with rose-tinted spectacles. It was the first version of Ubuntu to ship with Pulseaudio, and it was so horrible pretty much everybody was forced to disable it. PA wasn't baked in, though.

---

### Post by mdavis1231 on 2013-08-09
Thanks everyone for your replies.  I've figured out how to use pavucontrol (after all these years) so it's no longer necessary for me to remove PulseAudio from my Ubuntu. :oops:

---

