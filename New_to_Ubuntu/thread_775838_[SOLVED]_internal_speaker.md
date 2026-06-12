---
title: "[SOLVED] internal speaker"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by person8451 on 2008-04-30
I think this is an OS problem but not really sure.

I have an old Compaq 510d sff that has an internal speaker.  When I ran XP, if I plugged in external speakers, the sound would come only from those.  With Ubuntu, (8.04, but it did it with 7.10 also), the internal speaker still produces sound with the external speakers plugged in--that is, both the internal and external speakers produce sound.

This is not a big deal, just annoying because the internal speaker sounds awful and I can't adjust the volume without going into the menu (as opposed to just turning the knob as I was used to doing).  

I have fiddled with the various volume controls, but anything that turns down the internal speaker seems to also turn down the external ones.  

If I have to I can get in there and disconnect the internal speaker, but I thought perhaps someone here might have an idea.

---

### Post by kshtjsnghl on 2008-04-30
Hey this might help you

 Do one thing go to volume controls>edit>preferences
 and then check on all the given options and then in the playback section you will get a sound control named pcm2   (it might be different in your case) at least in my pc this is the option. 
Changin the volume in that control might help you get rid of the sound of your internal speakers,

PS. If pcm2 doesnt work try some other switch.

---

### Post by quixotic-cynic on 2008-04-30
If you search around this issue has arisen before - mainly with laptops... IIRC some people have met with success by using some of the methods listed on [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) & [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto).

That said, on my Toshiba laptop it remains unsolved and is slowly driving me nuts. ;)

---

### Post by person8451 on 2008-04-30
Switches!  That was it.  There's one in there that says "Line jack sense", and once I checked that box the internal speaker hushed up.

Thanks kshtjsnghl (hope I spelled that right  lol)

---

