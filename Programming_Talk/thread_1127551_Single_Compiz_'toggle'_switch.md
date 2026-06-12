---
title: "Single Compiz 'toggle' switch"
date: 2009-04-16
forum: Programming Talk
---

### Post by CLomax on 2009-04-16
At the moment I have two buttons on my panel which I made myself to toggle between Compiz and Metacity like so:
[IMG]http://img89.imageshack.us/img89/5907/screeny.jpg[/IMG]

Now, however, I would like only one button. Would you happen to know how I would test if Compiz or Metacity is on or not?

I've looked through *gconf-editor-> /apps/metacity* and */apps/compiz* but can't see anything useful.

My script so far (small and simple ;)):
```
#!/bin/bash
#
# Tests whether Metacity is turned on:
#  > Turns on Compiz if true
#  > Turns on Metacity if false
#  7bH475h0xr4345fgGh53jbrgHhf3h@googlemail.com
#                       - ~G-74gghcz-O9 (JG3tJnmai8)

compon=gconftool-2 -g '/apps/metacity/general/compositing_manager'
[COLOR="Red"]# I am aware that the above tests for the Metacity compositing feature.
# It needs to be replaced with a test for Compiz or Metacity.[/COLOR]

if [ $compon=0 ]; then
   metacity --replace
   else
   compiz --replace
fi

exit 0
```

---

### Post by ajgreeny on 2009-04-16
This may not be a reason to stop you trying to do what you are but are you aware that there is already an script application available called Compiz-Switch from [Forlong]("http://forlong.blogage.de/entries/pages/Compiz-Switch"), which does exactly what you are trying to do.  Have a look at that script and it should help you find the answer to your question, or even persuade you it's not worth continuing.

---

### Post by CLomax on 2009-04-16
> **ajgreeny said:**
> This may not be a reason to stop you trying to do what you are but are you aware that there is already an script application available called Compiz-Switch from [Forlong]("http://forlong.blogage.de/entries/pages/Compiz-Switch"), which does exactly what you are trying to do.  Have a look at that script and it should help you find the answer to your question, or even persuade you it's not worth continuing.

Thank you very much for the link. It helped me figure out an answer quite quickly. :)

---

