---
title: "laptop not shutting down"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-09-10
I have a Dell Vostro 3570 and the Beta installed. I have noticed shutting down from the menu doesn't seem to work instantly so I have to issue a "sudo halt" in the command which forces a shutdown, however it seems to get stuck at the Ubuntu screen and doesn't power off the laptop. Any ideas?

---

### Post by flipper T on 2011-09-10
go to a console, ctrl alt 1
log in
enter: sudo shutdown -h now
watch the output as the computer shuts down
it should show you what processes are being killed prior to shutdown

ps im having same problem. from terminal, hangs
from console, kills modem-manager and shutsdown.
don't know why there should be a difference

---

### Post by jerrylamos on 2011-09-10
> **sonicb00m said:**
> I have a Dell Vostro 3570 and the Beta installed. I have noticed shutting down from the menu doesn't seem to work instantly so I have to issue a "sudo halt" in the command which forces a shutdown, however it seems to get stuck at the Ubuntu screen and doesn't power off the laptop. Any ideas?

Intermittent with me on all three Compaq Presario 3.33 gHz and on Acer notebook and Acer netbook.

Sometimes they will shut down, maybe slowly, sometimes hang with the "Ubuntu" ..... screen and I power off manually or even on the Compaq flip off the terminal strip.

?

Jerry

---

### Post by flipper T on 2011-09-10
if you do a quick search you will find that this is an ongoing issue, so not strictly related to 11.10 at all.

perhaps this thread is in wrong forum & might receive more response in "general help".

don't get me wrong, i'd love an answer too

:)

---

### Post by sonicb00m on 2011-09-10
Hehe i find posting in "general help" and expecting an answer has odds similar to that of winning the lottery :D

---

### Post by flipper T on 2011-09-10
have you tried what i suggested in post no.2 ?

---

### Post by ventrical on 2011-09-10
> **flipper T said:**
> if you do a quick search you will find that this is an ongoing issue, so not strictly related to 11.10 at all.

perhaps this thread is in wrong forum & might receive more response in "general help".

don't get me wrong, i'd love an answer too

:)

  I have had this happen with Lucid on slower machines - usually lower speed Celerons. I have rarely had a shutdown hang on my Acer or Dell with Oneiric.

---

### Post by sonicb00m on 2011-09-11
> **flipper T said:**
> have you tried what i suggested in post no.2 ?

Yes but the the times I have tried it the laptop has shutdown as usual, haha.

I will post the results when I get something.

---

