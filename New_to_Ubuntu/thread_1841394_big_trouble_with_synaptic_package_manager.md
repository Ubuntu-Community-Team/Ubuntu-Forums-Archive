---
title: "big trouble with synaptic package manager"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by lemured on 2011-09-09
ubuntu karmic

Hi there everyone,

I'm having a big problem with my synaptic package manager :(

When 1st starting it a message tells me that there's a problem
and instructs me to use a terminal to fix it by typing:

sudo dpkg --configure -a

which I do.
SPM then opens as wished. 'Success,' I think, choose what I wish for, marked for installation, etc, it begins.
After a short while however it stops and this appears:

[http://img24.imageshack.us/img24/1836/synptc.png](http://img24.imageshack.us/img24/1836/synptc.png)

and nothing goes with SPM any longer. I cannot even close it.
More, when leaving it and then returning to it even what you can see has vanished [not that I cannot close SPM], which is why I had to grab the whole when making the screenshot, apologies for the thin layer of screenshot-window.

This happens everytime. My SPM is thus rendered completely unusable.

Upon opening the bottom line reads that 0 components are broken - which is doubtful.

I have no idea what's going on and am very sad.

Anyone has any ideas?

I'd be very grateful...

Thanks,

  lemured

---

### Post by audiomick on 2011-09-09
My best guess is that you need to figure out how to read that user agreement to the end.

 At the bottom of your terminal screen, the word [more] is visible, followed by a (blinking?) square cursor. This is not your usual cursor, but rather what you see when a process is in progress.

I suspect you have a vicious circle happening there. The command you are asked to perform

```
 sudo dpkg --configure -a

```
tells the installer to finish configuring any and all packages that have been de-compressed but not configured. Running this brings up the user agreement for the Java package, which you are expected to read to the end. You are bailing out of that before it is finished, effectively preventing it from finishing the dpkg command, causing it to exit in a state that wants the command to be run at the next start which causes it to try to configure the Java stuff which brings up the user agreement which you bail out of and are back at square one.

I don't know exactly how to get on to the next page of the agreement. I would be trying arrow keys, space bar, enter or something like that.

---

### Post by Enigmapond on 2011-09-09
Yes you need to scroll down to the bottom of that "agreement" and "Agree" then the installation will continue. That is the hold up and why you are getting the error. The Java hasn't completed installation.

---

### Post by lemured on 2011-09-09
uff, thanks, which i'd have to do before actually switching to do anything else, because as i said it vanishes when going anywhere else. i'll have to restart again and call up the process once more, will let you know here how it went.
thank you indeed, also below

---

### Post by oldos2er on 2011-09-09
Use the space bar to scroll down to the end, then Tab to select 'Ok" then Enter.

---

### Post by Old_Grey_Wolf on 2011-09-09
I am surprised synaptic package manager wasn't having other issues since Karmic 9.10 was End-of-Life about 4 months ago.

---

### Post by lemured on 2011-09-12
hi,

sorry for replying so late.

you wre absolutely right, dummy me.
scrolled down with enter, typed 'tes', everything's fine.

thank you so much :) :) !

Have a nice week,

 lemured

---

### Post by lemured on 2011-09-12
> **Enigmapond said:**
> Yes you need to scroll down to the bottom of that "agreement" and "Agree" then the installation will continue. That is the hold up and why you are getting the error. The Java hasn't completed installation.

thanks also to you, was exactly it :) :)

a good week to you as well,


 lemured

---

### Post by lemured on 2011-09-12
> **oldos2er said:**
> Use the space bar to scroll down to the end, then Tab to select 'Ok" then Enter.

also to you, thank you.
worked fine :)

used 'enter' & typed in 'yes' when asked for agreement

be well,

 lemured

---

### Post by oldos2er on 2011-09-12
Glad you got it working. Enjoy Ubuntu!

---

