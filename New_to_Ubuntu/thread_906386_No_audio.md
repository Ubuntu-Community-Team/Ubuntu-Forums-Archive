---
title: "No audio"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by ronb94 on 2008-08-31
Hello
Before 2 weeks I had 2 logitech multimedia speakers.About week ago I changed my audio system to 2 bookshelf speakers and subwoofer. The speakers have a sound card already so I am using a RCA cable from my digital output of my onboard card to the speaker.After I changed It I cant get sound in Ubuntu I tried play with the sound preferences but I cant get it work. 
I am using 64 bit Ubuntu Hardy
Thanks

---

### Post by PriceChild on 2008-08-31
If you're having problems with sound, first ensure ALSA is selected, by double clicking on the volume control, then File -> Change Device (ALSA Mixer). If that fails, see [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) - [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) - [http://alsa.opensrc.org/DmixPlugin](http://alsa.opensrc.org/DmixPlugin)

---

### Post by Eisenwinter on 2008-08-31
type asoundconf list in terminal.

Now, did you also change the **sound card**, or simply the speakers?

How were your previous speakers connected to the computer?

What is the name of your sound card?

---

### Post by ronb94 on 2008-10-12
from asoundconf list i am getting "intel".
I tried almost every setting but still no sound.
My old speakers were connected with the green analog output. Those speakers connected from my digital output from the motherboard and to the speakers.

---

### Post by billgoldberg on 2008-10-12
> **ronb94 said:**
> from asoundconf list i am getting "intel".
I tried almost every setting but still no sound.
My old speakers were connected with the green analog output. Those speakers connected from my digital output from the motherboard and to the speakers.

Go to system -> preferences -> sound and in the devices tab, play with the settings. 

Use the test button to see what works.

---

