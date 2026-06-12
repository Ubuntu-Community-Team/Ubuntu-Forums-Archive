---
title: "question for UK 11.10 users"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-09-30
watching bbc iplayer, full screen, cpu usage at about 50%.

watch 4OD, itv player or five OD, cpu usage at about 75%.

same in firefox & chromium.

just me ?

can anyone solve / explain ?

---

### Post by grahammechanical on 2011-09-30
Here are my not very scientific results. 18:00 - 18:30 30th September 2011
> 
Firefox
BBC - not downloading
ITV - 70%
Channel 4 - 70%
Channel 5 - 50%

Chromium
BBC - 50%
ITV - 50%
Channel 4 - 70%
Channel 5 - 50%


All on full screen and 2.4 Ghz dual core CPU with the load being swithced between cores and both working at the same level.

Now say, can you run the same test on 11.04? 

Regards.

---

### Post by flipper T on 2011-09-30
thanks for response

don't have 11.04 to test on

i have 2.5 ghz dual core processor, like you the load is equally shared.

interesting that you too are seeing that 4OD is making your cpu warm up.

obviously i never watch itv or 5, being a cultured individual.

:)

i guess my underlying question is : are these figures ok / normal ?

---

### Post by terry_gardener on 2011-09-30
i think it is normal. 

my opinion on the usage is flash, with sites like iplayer etc they are using higher screen resolution video and therefore on linux flash doesn't use hardware acceleration by default, therefore the video processing is getting done by the cpu and not the gpu.

---

### Post by flipper T on 2011-09-30
interesting then that the best quality picture (bbc iplayer) uses the least resources.

ps you mention that "linux flash doesn't use hardware acceleration by default", does this mean that i can / should enable it ? if so, how ?

i have a "decent" nvidia card

---

### Post by terry_gardener on 2011-09-30
> **flipper T said:**
> interesting then that the best quality picture (bbc iplayer) uses the least resources.

ps you mention that "linux flash doesn't use hardware acceleration by default", does this mean that i can / should enable it ? if so, how ?

i have a "decent" nvidia card

everytime i have tried to enable video acceleration it been very buggy. 

but if you want to try, in the address bar type 

```
about:config
```

then in the search bar type layer. find layers.acceleration.force.enabled and change the value to true. 

restart firefox. 

to check if it has enabled. 

type url ```
about:support
```

at the bottom you will see GPU Accelerated Windows 0/1 means disabled and 1/1 means enabled.

---

### Post by flipper T on 2011-09-30
just before you posted i tried "about:flags" in chromium and enabled: 

"Override software rendering list

Overrides the built-in software rendering list and enables GPU-acceleration on unsupported system configurations."

initial impressions are that cpu usage on iplayer & 4OD are reduced by about 10%.

these are after a few minutes use, will repost later

ps i have edited OP, put wrong figs in

---

### Post by flipper T on 2011-09-30
ok, minimal effect on bbc iplayer, but 4OD down to 60%

---

