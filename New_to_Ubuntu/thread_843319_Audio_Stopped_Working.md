---
title: "Audio Stopped Working"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by s.fox on 2008-06-28
Hi.  

I don't know why, but for some reason i an no longer getting any audio output. I have checked the volume control panel and its definitely  not on mute.  I have also checked my speakers and the volume is also on.  My speakers just plug straight into the speaker socket.  They are not USB.  can anybody please help me fix this?  i haven't a clue what to do.

thanks in advance.

---

### Post by s.fox on 2008-06-28
Well i now know what caused it.  It seems that i have got to have the speakers plugged in when i boot up and that i can't plug them in later.  Very strange.  Does anybody know any other solution to this?  

Thanks

---

### Post by prshah on 2008-06-28
> **Ash R said:**
> Well i now know what caused it.  It seems that i have got to have the speakers plugged in when i boot up and that i can't plug them in later.  Very strange.  Does anybody know any other solution to this?  

Are you on a laptop? Are you using SPDIF/Optical audio out, or regular RCA 3.5mm jack? What sound card? To check```
lspci | grep -i audio
```

---

### Post by s.fox on 2008-06-28
I am not using a laptop,  just a normal desktop machine.

Here is the output from terminal-

```
ashley@ashley-desktop:~$ lspci | grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
ashley@ashley-desktop:~$ 

```

Forgot to mention that its a regular RCA 3.5mm jack

---

### Post by prshah on 2008-06-28
> **Ash R said:**
> 
  just a normal desktop machine.

```

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

```

its a regular RCA 3.5mm jack

This is a guess: Since that's a 5.1 capable sound device, I'd say that it reconfigures itself depending on whether a 2.x speaker or a 5.1 speaker set is plugged in. Are you using the front ports?

Try this; boot without the speakers plugged in; then play any music; then, while the music is playing, try all the suitable ports until you get any sound or run out of ports.

If any ports other than those you regularly use work, you may have to reconfigure the sound subsystem; it's not difficult, but first post back with the results of the above (small) test.

---

### Post by s.fox on 2008-06-28
Thanks for the help.

You won't believe it but it now works  as if nothing was wrong in the first place. :confused: 

Something I did notice which may or not be nothing unusual is that the webcam i have plugged in turns itself on for a split second when i connect the speakers to the power socket.  Is this something to worry about?

once again thanks for your time.

---

### Post by prshah on 2008-06-28
> **Ash R said:**
> 
Something I did notice which may or not be nothing unusual is that the webcam i have plugged in turns itself on for a split second when i connect the speakers to the power socket.  Is this something to worry about?



Yes, MOST DEFINITELY. (OK not _definitely_ but if I was in your place I would definitely check the electrical connections)

Either you may have a open earth connection (ie, the "big" top pin in a 3 pin plug is either not connected or not working) or you may have line/neutral reversed in your socket. Both require a competent electrician to take a look. 

Here's a quick, relatively safe test you can perform yourself to check the earth connection; get a "tester" screwdriver, which is a special screw driver with a bulb and resistor coils in it. 

Turn on your computer, and, near the back, in an UNPAINTED area (Because the painted area generally acts as an insulator), touch the tester to the case, and keep your finger on the top of the tester where you will find a metal plate/disc. If the bulb within the tester glows, you have electrical leakage which is very dangerous for you as well as the computer. It means earth is open and can lead to a nasty shock.

Note that you perform this at your own risk. There is generally no risk in using a tester but if you happen to use an old/defective one...

And of course I may be wrong in which case I apologize for disturbing your mental peace, but as I said, if I was in your place...

---

### Post by s.fox on 2008-06-28
Thankfully one of my friends is a fully trained electrician.  I shall have a word with him about this set of power sockets. Really don't fancy risking shocking myself , especially for a test.  

Thanks for highlighting this possible problem to me.  Until i get this looked at i will use a different set of sockets just to be on the safe side.

---

