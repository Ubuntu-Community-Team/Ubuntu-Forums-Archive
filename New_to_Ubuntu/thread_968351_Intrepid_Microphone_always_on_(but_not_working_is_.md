---
title: "Intrepid: Microphone always on (but not working is skype)"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by mgm74 on 2008-11-02
Hi All!

My microphone is always on (when I tap the mic, I can hear it in the speakers). In skype however the microphone is not functioning (skype cannot hear me).

Just upgraded to Ubuntu 8.10 (had a similar problem in 8.04, but there I was able to use skype even with the echo in the speakers).

My audio card (lspci | grep audio):
02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

I tried the sound controls (System->Preferences->Sound), aslamixer and pulse audio without success. The alsamixer microphone controls cannot mute the mic (have minimal impact on the volume even when the volume is set to 0). 

In skype I tried all "Sound in" options (default device, pulse, SB Live! Value xxx) but none worked (skype did not hear me).

Has anyone got any idea on what could be the problem?

---

### Post by ubun_two on 2008-11-02
I am on Intrepid 64bit.

I am pretty much experiencing the same issue with Skype.  I managed to get the sound output to work, but input through microphone doesn't seem to work at all.  I even tried uninstalling pulse audio and using alsa only, but that didn't work.

---

### Post by lakelse on 2008-11-02
I have a similar problem in Sound Recorder.  

I've activated both Line In and Microphone in the Volume Control there, but when I go to do a new recording the only option for Input is Capture, and when I push record the timer goes through minutes in a few seconds and it doesn't matter whether I speak or not.  The sound card seems to be working-the 4 Seasons on a CD sounded fine using RhythymBox.  To answer the first obvious question one should ask a newbie, the microphone is properly plugged in and turned on.  

The microphone is on a headset, combined with the headphones, which says Cyber Accoustics on it.  I haven't kept the packaging so sorry to say can't provide more information about it.

I'm a middle aged newbie, downloaded 8.04.1 on October 28 at home, and 8.10 Desktop (X86) yesterday at the office, both set up using WUBI to cautiously try to begin migrating from Windows.  The microphone problem is at the office, using 8.10 with all recommended updates installed as of about three hours ago.  In case it helps someone answering, my level of Linux knowledge is very low, and I've only used (and only had to use) the GUI in getting set up.  

Ubuntu seems useful enough and easy enough to use that I could almost use it at home to the exclusion of Windows if it weren't for the microphone problem.  

Thanks to anyone who can help!

                                 bob c

---

### Post by lakelse on 2008-11-02
Sorry for the previous post.

My sound recorder now works. I doubt if my solution applies to the Skype users, but I just had to go to Preferences-Sound-Devices-Sound Capture (under Video Conferencing) and play with the choices until one worked.


                                    bob c

---

### Post by zorozadeh on 2008-11-05
I've got the same problem with GA-M61SME2 gigabyte main board and its onboard audio controller. The mics working well but skype cannot detect it.It seems that the problem is almost independent of model of your audiocontroller.

---

### Post by jmwyatt on 2008-12-28
This is immensely frustrating. We are a business and using Ubuntu (so far with success and satisfaction). Now with fresh installs of 8.10, Skype is not working and our communications are in chaos. (We place many international calls.) As a supporter of Ubuntu, this is disheartening... still not ready for prime time.  We just don't have the time to fiddle with settings hoping something critical to our business will work.

---

