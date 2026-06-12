---
title: "Skype help"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by CB2RN on 2008-07-10
Hardy 8.04 on Gateway M 1625

I've downloaded Skype and have it setup, but I have no sound. I bought a headset (microphone and headphone jack hook up) and still no sound. Both jacks work with other apps, so I don't know what the problem is. I fooled around with the settings in options to no avail. Please advise.

BTW- Does anyone know if Ekiga will work on Mac, or at least a compatible app for Mac? I don't have to have Skype, I just need VOIP to talk to my wife who uses a Mac.
Thanks

---

### Post by Dave Otter on 2008-07-10
Open Skype

        There should be Blue icon -bottom left

          click  Options

           click sound devices
         
           choose the one that works

---

### Post by CB2RN on 2008-07-10
Sounds on but microphone is still no good. Any ideas?

---

### Post by ameanjoe on 2008-07-11
I also just downloaded Skype from Mediabuntu. I noticed that the version number was 2.0.0.68. When I went to the Skype site the latest version is 2.0.0.72. I'm wondering if that could be part of the microphone not working, or maybe it is Ekiga being loaded and setup???
My headphones work fine on my laptop which is running Win XP and I've heard rumors that Skype doesn't work well with Ubuntu. I have a support request in to Skype, but haven't heard back yet, but I'm considering blowing Skype off my computer and doing a fresh download from Skype. 
Maybe someone on the forum has had some experience with this problem.
Mahalo, meanjoe

---

### Post by Dave Otter on 2008-07-13
Go to volume control i.e right click loudspeaker icon on tool bar.
     click edit
      click preferences
      check microphone capture
 This works for me

---

### Post by ameanjoe on 2008-07-14
Dave Otter,
That's great, except that there isn't a "Tool Bar" in my Skype window.
Should I totally, completely delete Skype and start over?
Thanks for the response, ameanjoe

---

### Post by Dave Otter on 2008-07-14
Should be the icon as mentioned at top of screen not specifically the Skype screen

---

### Post by ameanjoe on 2008-07-14
Dave Otter,
It took a bit to figure out what you were talking about. The volume control for the mixer...What a concept....Well, I tried following your directions and the end result was nada...
Maybe you could try explaining your method again, a bit more clearly???
I don't mean to sound abusive. I'm just getting tired of mucking around with no net result...
ameanjoe

---

### Post by Dave Otter on 2008-07-16
This is what connected my microphone.

    Open mixer volume control
     Click edit
       ..   preferences
            tick microphone and microphone capture

  ensure microphone is not muted in Volume control
  

Alternatively open Terminal
  type in alsamixer

   ensure microphone not muted and set at sufficient volume

  possibly enable mic boost
If it does not work then I am afraid I have no other suggestions

---

### Post by whitethorn on 2008-07-16
Hi, do you know if you're using pulseaudio as your sound device?  You can check it under System -> Preferences -> Sound.  If your using pulseaudio the problem is skype doesn't work with it.

You have to edit the start command to add, 

pasuspender skype

Pasuspender turns off pulse audio for the one application.  The only problem with this is, that while skype is running you won't be able to use your sound with other applications.

Hopefully this helps, another way to get it to run, is to change your sound device to Alsa.

---

