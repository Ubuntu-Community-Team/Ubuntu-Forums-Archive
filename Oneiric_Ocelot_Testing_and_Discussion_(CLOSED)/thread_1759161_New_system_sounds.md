---
title: "New system sounds?"
date: 2011-05-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by WIN7GT on 2011-05-15
System sounds in Ubuntu wasn't ever changed, from what I know. The current startup sound is not comfortable and is a bit sudden and sharp. I have a small experience in music creating, but I am full of enthusiasm and new ideas. It will be a honor for me to create sounds as evolution of current sounds or from scratch. So, what do you think?

---

### Post by benjamimgois on 2011-05-15
> **WIN7GT said:**
> System sounds in Ubuntu wasn't ever changed, from what I know. The current startup sound is not comfortable and is a bit sudden and sharp. I have a small experience in music creating, but I am full of enthusiasm and new ideas. It will be a honor for me to create sounds as evolution of current sounds or from scratch. So, what do you think?

I would be very good. The current system sound still based on human idea. We really need a light oriented sound theme.

---

### Post by teachop on 2011-05-15
I have thought for years, the default setting for all sounds should be OFF.  If you want them, then they can be enabled. (kindof a pet peve there)

---

### Post by donniezazen on 2011-05-16
First thing i do to a new install.

> sudo rm /usr/share/sounds/ubuntu/stereo/system-ready.ogg

---

### Post by WIN7GT on 2011-05-16
Well, here is a two sounds I created by now: [http://ompldr.org/vOHB2Zg](http://ompldr.org/vOHB2Zg)

---

### Post by lucazade on 2011-05-16
It's a nice idea..
Take a look at this request in Canonical Design blog:
[http://design.canonical.com/2010/08/ubuntu-needs-a-new-sound-theme/](http://design.canonical.com/2010/08/ubuntu-needs-a-new-sound-theme/)

---

### Post by CreativeReach on 2011-05-16
A new sound theme would be great!

---

### Post by Merk42 on 2011-05-16
Was this brought up at UDS? If not, it probably won't happen... again.

---

### Post by andrek on 2011-05-16
Yup. It hasn't change at all since at least 6.06 (2006!). This has to be changed.

---

### Post by linuxuser12345 on 2011-05-16
I think we need a log off sound!

---

### Post by NCLI on 2011-05-17
I think it was proposed for the natty cycle, but postponed due to lack of time. Maybe they'll get around to it this cycle xD

---

### Post by ranch hand on 2011-05-17
Does anyone know where the configuration file is that points a particular event at a particular sound?  Like where the sound for login is actually defined.

Have wondered, mildly, for years now.

---

### Post by Mr. Picklesworth on 2011-05-17
> **ranch hand said:**
> Does anyone know where the configuration file is that points a particular event at a particular sound?  Like where the sound for login is actually defined.

Have wondered, mildly, for years now.

Yep, look under /usr/share/sounds. There are a few sounds there that _aren't_ related to the sound theme system, but look for an index.theme file and you'll be on the right track. It's very similar to how icon themes work (and you can stick your own themes in ~/.local/share/sounds). The system is specified over here:
[http://www.freedesktop.org/wiki/Specifications/sound-theme-spec](http://www.freedesktop.org/wiki/Specifications/sound-theme-spec)

The Ubuntu sound theme (since it predates this specification) isn't the best example. There's a package in the repository called sound-theme-freedesktop, which is a very up to date sound theme with lots of (very tasteful) event sounds. Once you install it you can select it from Sound Preferences.

---

### Post by ranch hand on 2011-05-17
> **Mr. Picklesworth said:**
> Yep, look under /usr/share/sounds. There are a few sounds there that _aren't_ related to the sound theme system, but look for an index.theme file and you'll be on the right track. It's very similar to how icon themes work (and you can stick your own themes in ~/.local/share/sounds). The system is specified over here:
[http://www.freedesktop.org/wiki/Specifications/sound-theme-spec](http://www.freedesktop.org/wiki/Specifications/sound-theme-spec)

The Ubuntu sound theme (since it predates this specification) isn't the best example. There's a package in the repository called sound-theme-freedesktop, which is a very up to date sound theme with lots of (very tasteful) event sounds. Once you install it you can select it from Sound Preferences.
Thank you very much.  Have to get my brain checked, there it was in /usr/share/sounds/freedesktop/stero.  Never really paid good attention attention I guess.

I will have to look at the package you mention too.

I usually have sounds turned off  as they distract and irritate me.  There are times, though, when I kind of like to have them.  I find a lot of people like them and so I turn them on before showing the system off to folks.  If they don't like them then I can show them how easy it is to turn it off.

Now I can show how they can put in their own if they so desire.

Thanks again.

---

### Post by Mr. Picklesworth on 2011-05-18
> **ranch hand said:**
> Thank you very much.  Have to get my brain checked, there it was in /usr/share/sounds/freedesktop/stero.  Never really paid good attention attention I guess.

I will have to look at the package you mention too.

I usually have sounds turned off  as they distract and irritate me.  There are times, though, when I kind of like to have them.  I find a lot of people like them and so I turn them on before showing the system off to folks.  If they don't like them then I can show them how easy it is to turn it off.

Now I can show how they can put in their own if they so desire.

Thanks again.

You're welcome!

Unfortunately, there aren't many themes to choose from. Back when Mark S said he wanted to get community contributions for the new sound theme (and then everyone seemed to forget about it) I was hoping we would see some proper sound themes (with appropriate packaging!) start to emerge. Alas, though people made some pretty nice sounds, nothing really came of it. This is something that needs a bit of advocacy (and maybe a little more software).

I was just tempted to make a tutorial blog post myself, but the trouble is I'm decidedly not a sound person :)

---

### Post by ranch hand on 2011-05-18
The themes may not be available but sound files are easy to get in several different formats.  The package "soundconverter", if installed will easily change anything your have gstreamer support for to any other supported format.

This means that if you want sounds you can have pretty much anything you want.

If you are a "sound man" editing programs can grab things out of just about any sound file and turn them into what you want.  My son can do that kind of thing.  I can't.

---

### Post by Johnsie on 2011-05-18
The login sound stutters on alot of old computers I've used Ubuntu on. Hardly a great first impression. It would be nice to update with with something fresh, but there also needs to be a way to make it play properly.

---

### Post by ewaynec on 2011-05-18
Maybe we could get the Rolling Stones to let us use "Start It Up"

---

### Post by WIN7GT on 2011-05-20
So, here I am, with updated sounds. [http://cl.ly/1i1G1Z2t3v2s0G070d3x](http://cl.ly/1i1G1Z2t3v2s0G070d3x)
Check out and tell me what you think :)

---

### Post by Squonk07 on 2011-05-20
Frankly I've always thought that silence was the most welcome sound my computer could make. On the other hand, I freely admit that my opinion isn't the only one out there. At any rate I agree that it's time to update the system sounds. We left the old Kumbaya image behind from Lucid onward (thankfully!); it's time to ditch the sounds as well. I would elect to keep the startup sound for tradition's sake (and because it kind of sounds like light breaking through the clouds, which fits) but update the rest.

---

