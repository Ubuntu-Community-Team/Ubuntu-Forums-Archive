---
title: "lost alsamixer command"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by aef54 on 2012-07-19
Yesterday I had some sound problems, but I managed to solve them. However  I have forgotten the  terminal command I used to solve it. 

The problem was that the sound for certain low tones was  distorted and rough. 

This is what I did:

- Pressed Alt +F2 and went to *ubuntu-bug audio*
- There I selected: [I]Green Line out, Rear (built-in Audio - HDA Intel)
[/I]- Then I could select what the problem was, I selected* Bad Quality.*

Then it gave me suggestion that I should run a command in the terminal. It looked something like:

*alsamixer -bla something bla bla*

Then I got some kind of control panel. There I turned down the main audio (and I turned up my speakers at the same time). Then the Audio problem was gone.

Now I try to find that specific alsamixer command again, but I cannot find it.  Do you guys know what that alsamixer command was to get into the control panel?

---

### Post by jmfal on 2012-07-19
Welcome to Ubuntu

Open a terminal and enter >>>> history

It will show a list of commands that you have used.
You can copy/paste a command back into the terminal.

Could you post that command, I would like to see what that does.

---

### Post by aef54 on 2012-07-19
Thanks! command was:

$ alsamixer -D hw:intel

I'm not sure what it does exactly, but apparently i t opens the sound control panel for a certain device.

---

### Post by jmfal on 2012-07-19
Appreciate the reply

Mark  thread solved using forum tool above

---

