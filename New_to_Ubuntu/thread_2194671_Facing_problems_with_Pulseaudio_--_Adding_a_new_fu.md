---
title: "Facing problems with Pulseaudio -- Adding a new function to the introspect.c"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by sathish1000 on 2013-12-19
Hi,

   I am trying to add a new function "pa_context_set_sink_input_paused" to the pulseaudio introspect.c file. I was able to able and successfully compile pulseaudio too..

 gcc pa_listclients_pause.c -o pa_listclients_pause -L /home/sathish/Desktop/pulseaudio-4.0/build/src/.libs/ -lpulse
/tmp/ccueP47b.o: In function `pa_get_devicelist':
pa_listclients_pause.c:(.text+0x6cb): undefined reference to `pa_context_set_sink_input_paused'
collect2: error: ld returned 1 exit status

   But when I try to run a program using this new function, it returns me "undefined reference".

   I tried to run the nm command and check whether the new function is present in libpulse.so

   The function returns me it has found it..

   nm -A *.so | grep "pa_context_set_sink_input_paused"
   libpulse.so:0001d4a0 t pa_context_set_sink_input_paused

   I am not able to comprehend what is happening. Can you help me with this ??

   Thanks,
   Sathish

---

### Post by sathish1000 on 2013-12-19
Hi,

   I am trying to add a new function "pa_context_set_sink_input_paused" to the pulseaudio introspect.c file. I was able to able and successfully compile pulseaudio too..

 gcc pa_listclients_pause.c -o pa_listclients_pause -L /home/sathish/Desktop/pulseaudio-4.0/build/src/.libs/ -lpulse
/tmp/ccueP47b.o: In function `pa_get_devicelist':
pa_listclients_pause.c:(.text+0x6cb): undefined reference to `pa_context_set_sink_input_paused'
collect2: error: ld returned 1 exit status

   But when I try to run a program using this new function, it returns me "undefined reference".

   I tried to run the nm command and check whether the new function is present in libpulse.so

   The function returns me it has found it..

   nm -A *.so | grep "pa_context_set_sink_input_paused"
   libpulse.so:0001d4a0 t pa_context_set_sink_input_paused

   I am not able to comprehend what is happening. Can you help me with this ??

   Thanks,
   Sathish

---

### Post by squakie on 2013-12-19
Don't create duplicate posts - you already posted this a short time ago with a different title.

---

### Post by QIII on 2013-12-19
Threads merged.

Please do not create duplicate threads.  It causes confusion and duplicates effort on the part of those who would help you.

---

