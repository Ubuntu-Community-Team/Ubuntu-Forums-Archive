---
title: "Opera doesnt save settings"
date: 2016-05-10
forum: New to Ubuntu
---

### Post by gunner5 on 2016-05-10
Hello guys! Im with ubuntu 16.04 lts and i love him more and more... really happy.
So, my problem is that opera 36 doesnt save my settings, and show me a message starting... settings were not saved and kind, how can i get it work? I dont want to use ff or chrome, i dont like it.
Thx in advance!

---

### Post by QDR06VV9 on 2016-05-10
Well just checking here with Opera 37.0.2178.32 in VB (Virtual Box) 
Seems to save all my settings.
If you want to see or test I am using this link [http://www.ubuntuupdates.org/ppa/opera](http://www.ubuntuupdates.org/ppa/opera)
But Be Warned your mileage may vary from mine.
Kind Regards

---

### Post by gunner5 on 2016-05-10
I installed through deb, that make any difference? Im going to try updating.

---

### Post by QDR06VV9 on 2016-05-10
That should be ok just see if that fix's your not saving your settings.
But if that works for you then you might want to add the PPA as per the instructions there to receive the proper updates as they roll in.
Dose that make sense?;)

---

### Post by steeldriver on 2016-05-10
Perhaps it's unable to save settings because of file ownership issues. Have you ever run it using sudo?

---

### Post by gunner5 on 2016-05-11
Doesnt work, with sudo the message doesnt show but doing normal always...
I attached a running with terminal.
Thx for response.

---

### Post by steeldriver on 2016-05-11
Sorry, I wasn't suggesting that you **should** run it with sudo - my point was it's probably **because** you ran it with sudo that it can now no longer write to the configuration files (they have become owned by 'root')

You will need to find any root-owned files in your opera configuration directory e.g.

```

find $HOME \( -uid 0 -o -gid 0 \) -ls

```

and restore their proper ownership

---

### Post by QDR06VV9 on 2016-05-11
Is this in a virtual box session?
Ninjed by steeldriver:)

---

### Post by gunner5 on 2016-05-11
> **steeldriver said:**
> Sorry, I wasn't suggesting that you **should** run it with sudo - my point was it's probably **because** you ran it with sudo that it can now no longer write to the configuration files (they have become owned by 'root')

You will need to find any root-owned files in your opera configuration directory e.g.

```

find $HOME \( -uid 0 -o -gid 0 \) -ls

```

and restore their proper ownership

That worked men! Now it saves my settings. I mean with the same command, i deleted some directories like "Local Store" and other i can remember, sorry...
Problem solved, thx a lot!

---

