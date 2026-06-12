---
title: "Volume keeps changing"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by schmidtbag on 2008-08-22
Every time I boot up the computer, my volume keeps resetting back to its default.  I'm getting really tired of changing everything every time Ubuntu starts up, how do I get it to stop doing this?

I did look up this question ahead of time but found no results.

---

### Post by elmoosecapitan on 2008-08-22
Can you elaborate on what is resetting back to default?

cheers

---

### Post by schmidtbag on 2008-08-22
Just all of the volume channels like master, PCM, line-in, mic, everything.  Some are muted, some are slightly lower than I want them to be, some are muted and all the way down.  Its just annoying because they're set the same values every time I boot up.

---

### Post by elmoosecapitan on 2008-08-22
Oh, sound volume! Your post makes so much more sense now. : )

---

### Post by schmidtbag on 2008-08-22
so do you know how to solve it?  i don't ever remember it doing this before.  i recently added a different sound card (and disabled the integrated) if that makes a difference

---

### Post by Majorix on 2008-08-22
To me it sounds like your alsa daemon is not set to start everytime with your computer.

I don't remember how to do it in Ubuntu, but someone here may point it out.

After setting the daemon, you have to set your volumes ONCE for the daemon to memorize.

---

### Post by schmidtbag on 2008-08-23
well, how would you do it in your distro?

---

