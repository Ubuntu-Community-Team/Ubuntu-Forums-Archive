---
title: "intel ich5 soundcard and ultramixer problems"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by tactix on 2008-07-08
ive just moved over to linux on my dell optiplex gx270 so be gentle with me 

ive installed ultramixer (as its the only thing i miss from windows ) 

but unfortunately the program shows no audio device in the applications settings so at the moment im trying to get my head around alsa and oss as ultramixer only seems to support oss my sound card works with all other sound apps so i dont know what im gonna do to solve it 

ive tried aoss /home/tactix/UltraMixer/UltraMixer.sh in the shell wich launched the app but still with the same error  

ive tried all the different settings in the system preferences sound settings but to no avail 

any help would be great cheers 

dont know if this info helps 

tactix@hal:~/alsa-driver-1.0.14$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ZabiGG on 2008-07-08
Hi,

I'm sorry to say I don't know anything about ultramixer... but I've compiled a list of sound troubleshooting how-tos [here]("http://ubuntuforums.org/showpost.php?p=5129245&postcount=2"), and since you've had no answers yet, that might be a start to help you out.

You might also google the ultramixer developer's site. Maybe there's a FAQ or a guide there that addresses your issues.

Sorry I couldn't help out more :(

Z.

---

### Post by tactix on 2008-07-09
thanks bud i think its just down to the program only supporting oss 

and i cant be bothered trying to layer wrap the alsa audio so ive just installed traktor dj software under wine for anybody out there that wants to run traktor the only version ive found that installs and runs straight away is TDS253Demo_Win_Setup.exe

---

