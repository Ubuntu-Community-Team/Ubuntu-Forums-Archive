---
title: "sound, only sometimes on start up"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by rwarwarwa on 2008-05-21
Hi there,

Usually when I start up my computer the sound doesn't work. I have to resart it a few times to get sound. 

I have a sound blaster sound card and it was working fine for the first four months I had ubuntu up and running. 

thanks,

rwa

---

### Post by bluefrog on 2008-05-21
Perhaps your card is about to die then.

---

### Post by prshah on 2008-05-21
> **rwarwarwa said:**
> 
Usually when I start up my computer the sound doesn't work. I have to resart it a few times to get sound. 


Post outputs of commands lspci and dmesg, both when you have sound and when you don't.

Please attach the outputs as files, not as quoted text within the post.

---

### Post by aeiah on 2008-05-21
do you have a soundblaster card and onboard sound? when it doesnt work, does the sound get outputted through the onboard sound? that happens to me. i make sure an asoundconf command gets issued on startup so it defaults to the correct card.

```

asoundconf list

asoundconf set-default-card <cardname>

```

---

### Post by rwarwarwa on 2008-05-23
Hi there,

Here are the results.

thanks,

RWA

---

### Post by dastasha on 2008-05-23
Disabling my on board sound card through bios worked for me

---

### Post by rwarwarwa on 2008-05-23
Thanks for the suggestions. I am working on them. Will get to the computer again soon. The dmesg will be posted soon. 

rwa

---

### Post by daimyo505 on 2008-05-23
Hello everyone, I've been having the exact same problem. I have been searching for the same problem for some time but couldn't find the exact same problem.

I went into BIOS and disabled the on-board sound chip and my sound starts on start up. I could then see the difference in the lspci file with and without sound.

Thanks for your help :)

---

