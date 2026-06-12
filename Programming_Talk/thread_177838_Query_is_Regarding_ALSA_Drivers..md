---
title: "Query is Regarding ALSA Drivers."
date: 2006-05-17
forum: Programming Talk
---

### Post by Tarun Mehta on 2006-05-17
Hi All,

I am trying to understand the ALSA code for the pcm.c in test for the ALSA library 1.0.10.

I am facing some problems regarding the assigning of the pointer (*writei) in the Transfer method - write only. In 

static int write_loop(snd_pcm_t *handle,
		      signed short *samples,
		      snd_pcm_channel_area_t *areas)

snd_pcm_writei(handle, ptr, cptr) function is being called where writei is a pointer to some function. 

Here snd_pcm_writei(handle, ptr, cptr) in turn returns 
_snd_pcm_writei(pcm, buffer, size);

which further returns returns

pcm->fast_ops->writei(pcm->fast_op_arg, buffer, size);



But I am getting hard time to find out the point where writei is being assinged the value of some function.


Please help me out of this!!!!

---

### Post by mvniekerk on 2008-12-12
After 2 years this might seem random, but did you come right?
I'm also having a bit of a challenge figuring out where the code jumps to. So if you came to any knowledge, please let me know!

---

