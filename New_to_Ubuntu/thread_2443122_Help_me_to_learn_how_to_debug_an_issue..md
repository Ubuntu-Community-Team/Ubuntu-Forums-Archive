---
title: "Help me to learn how to debug an issue."
date: 2020-05-11
forum: New to Ubuntu
---

### Post by cwmoser on 2020-05-11
I have this issue:
Libreoffice opens and runs properly when I used the Marco Window manager.
(This is selected this way:  MATE Tweak -> Windows -> Window manager)

BUT, Libreoffice will not open if i have Compiz as the Window manager.

So, how do I debug issues like this using the log files, etc?

---

### Post by daniewicz on 2020-05-11
First thing I would do is run libreoffice from the command line (terminal) and see what errors come up on the screen.

---

### Post by cwmoser on 2020-05-12
Fooling around some more with this issue, I Googled and noted others have this problem.

I ran libreoffice --safe-mode and a couple of modules failed to load.
I googled the error for a suggestion, but no success.

I tried rm ~/.config/libreoffice and purging libreoffice then reinstalling.
Some posts stated their fix was to downgrade to Libreoffice 6.1.
Eventually after trying several suggestions, Libreoffice would not even run in Marco, and Ubuntu seemed sluggish.

Last thing I tried was to go to the install and select reinstall which stated that it would repair problems without deleting data.
That seems to have fixed the issue and I'm not going to run with Compiz as the Window Manager but instead use Marco.

---

