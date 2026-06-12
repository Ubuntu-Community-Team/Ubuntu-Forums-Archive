---
title: "Ajunta for Embedded Linux??"
date: 2008-06-04
forum: Programming Talk
---

### Post by raedbenz on 2008-06-04
Hi,,,
is it possible to use Ajunta for Embedded linux developing (specifically ARM processors)?? if yes how?

thanks

---

### Post by Vadi on 2008-06-04
I don't see why not, it's just a generic IDE.

---

### Post by raedbenz on 2008-06-04
> **Vadi said:**
> I don't see why not, it's just a generic IDE.
have u ever heard somebody tried that?
Do i have to specify the gcc , binutils etc.. for ARM or how?

---

### Post by Vadi on 2008-06-04
I think you just specify the architecture with the -m flag to gcc

---

### Post by raedbenz on 2008-06-04
> **Vadi said:**
> I think you just specify the architecture with the -m flag to gcc

where is this -m flag set? is it in the Preferences of Anjuta?
do u know any good tutorial for such procedure?
thanks

---

### Post by Vadi on 2008-06-04
I don't know. Look it up

---

### Post by raedbenz on 2008-06-04
> **Vadi said:**
> I don't know. Look it up

do u recommend any other IDE to be used for embedded Linux?
thanks

---

### Post by Yes on 2008-06-04
They can all be used, you just need to set the right parameters for gcc.  In Geany you would do that by going to Build -> Set Includes and Arguments.  It's probably something similar in Anjuta.

---

### Post by raedbenz on 2008-06-04
> **Yes said:**
> They can all be used, you just need to set the right parameters for gcc.  In Geany you would do that by going to Build -> Set Includes and Arguments.  It's probably something similar in Anjuta.

hi
do u recommend to use Geany?
with which embedded platform u have experienced it?

cheers

---

### Post by raedbenz on 2008-06-04
> **Yes said:**
> They can all be used, you just need to set the right parameters for gcc.  In Geany you would do that by going to Build -> Set Includes and Arguments.  It's probably something similar in Anjuta.

HI again i have installed geany and it seems very friendly thanks.
could u just tell me what are exactly the settings in the image below to be used for ARM??

[ATTACH]72970[/ATTACH]
thanks

---

