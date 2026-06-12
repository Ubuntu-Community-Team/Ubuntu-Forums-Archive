---
title: "ALSA:  calling snd_pcm_hw_params_set_rate_near exit app"
date: 2012-10-28
forum: Programming Talk
---

### Post by miodas007 on 2012-10-28
Hi,
i try run examples from
[http://equalarea.com/paul/alsa-audio.html](http://equalarea.com/paul/alsa-audio.html)

Any examples don't work for me. When method snd_pcm_hw_params_set_rate_near is called program exits.

Simple example:
fprintf (stderr, "TEST STRING 1");
```

if(snd_pcm_hw_params_set_rate_near (capture_handle, hw_params, 44100, 0) < 0) 
fprintf (stderr, "TEST STRING 2");
else fprintf (stderr, "TEST STRING 3");
fprintf (stderr, "TEST STRING 4");

```print only > TEST STRING 1have idea why ?

---

