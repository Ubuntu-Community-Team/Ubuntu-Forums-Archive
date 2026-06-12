---
title: "Gstreamer, play audio without gmainloop"
date: 2014-10-29
forum: Programming Talk
---

### Post by jhay2 on 2014-10-29
hi , 

is there any good example on how to play audio using only the buffer and play it using own loop with gstreamer ?

i saw some tutorials on playing audio but on the tutorial , audio play inside GMainLoop  and when i put the GMainLoop inside on my own loop example 

while(true){
GMainLoop *loop=[COLOR=#000000][FONT=Consolas]g_main_loop_new (NULL, FALSE);[/FONT][/COLOR]

...
..
}


the program crashed , (segmentation fault)

it seems that GMainLoop works on its own loop, and crash if it will put to another loop 


i also try to use thread 

but same results ,



any ideas ? how can i play sound using gstreamer without using GMainloop ? 


c++ language , Thank you :)

---

