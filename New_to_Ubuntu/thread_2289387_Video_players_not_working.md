---
title: "Video players not working"
date: 2015-08-03
forum: New to Ubuntu
---

### Post by rc_canon on 2015-08-03
I am new to linux and I have Ubuntu 15.04 (gnome)installed on my desktop and I have the totem video player and I also downloaded smplayer and neither player will play a movie. Both will start and bring up the play movie menu and that’s the end of it. Could anyone tell me why neither of these programs  and especially totem video player which came installed with the operating system will not work and how I can fix it.

---

### Post by monkeybrain20122 on 2015-08-03
Video players won't work without codecs. Did you install the package ubuntu-restricted-extras?

---

### Post by NathanRodriguez on 2015-08-03
Looks like codecs missing, as stated by monkeybrain20122. The movie players didn't gave any error message ?

---

### Post by rc_canon on 2015-08-03
How do you install Ubuntu restricted extras?

---

### Post by rc_canon on 2015-08-03
Yes I did receive an error message and being new to Ubuntu I do not no how to install codecs

---

### Post by monkeybrain20122 on 2015-08-03
In the terminal, type

```
sudo apt-get install ubuntu-restricted-extras
```
then type your password and hit enter when prompted

or open synaptic/software centre/whatever gui package manager for your DE and search for ubuntu-restricted-extras and install.

---

### Post by howefield on 2015-08-04
If you install ubuntu-restricted-extras via the command line as above, be aware that this will include some microsoft fonts to which you will need to accept a licence, do this by using the tab key to select the option and enter to complete. Just in case you got stuck :)

---

### Post by rc_canon on 2015-08-21
Thanks to everyone who replied to this thread. I also need to learn to function in this forum :-). The Ubuntu restricted codecs were not enough and I had to have a friend search and install additional codecs after I tried to install the restricted codecs. Anyway she installed VLC media player and the additional codecs and all is functioning well now. I am really a greenhorn at this but I really like the Ubuntu interface and like the Idea of getting away from depending on Microsoft so much. Windows 10 is a real disappointment to say the least

---

### Post by monkeybrain20122 on 2015-08-21
> **rc_canon said:**
> Thanks to everyone who replied to this thread. I also need to learn to function in this forum :-). The Ubuntu restricted codecs were not enough and I had to have a friend search and install additional codecs after I tried to install the restricted codecs. Anyway she installed VLC media player and the additional codecs and all is functioning well now. I am really a greenhorn at this but I really like the Ubuntu interface and like the Idea of getting away from depending on Microsoft so much. Windows 10 is a real disappointment to say the least

Just curious what additional codecs?

---

