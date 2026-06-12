---
title: "server help..."
date: 2008-05-15
forum: New to Ubuntu
---

### Post by boe-bots on 2008-05-15
I downloaded rosegarden and i started it up, and then it told me i needed to start up my JACK server. what is a JACK server and how do i start it up?

thanks

---

### Post by Xiong Chiamiov on 2008-05-15
JACK is an audio server.  Most people use ALSA instead, I believe.  Do you get sound in other applications?

BTW, when you say "server help", do you mean that you're running Ubuntu Server?

---

### Post by boe-bots on 2008-05-15
i'm running hardy 8.04.

i just tried rythmbox and i got sound.....so i'd say yes.

---

### Post by Xiong Chiamiov on 2008-05-15
I installed rosegarden for the heck of it, and it did the same for me.  There are [quite]("http://ubuntuforums.org/showthread.php?t=488315") a few [threads]("http://ubuntuforums.org/showthread.php?t=150876&highlight=jack+rosegarden") [around]("http://ubuntuforums.org/search.php?searchid=41252596"), so you may want to try looking through them.  Let us know how it goes.

---

### Post by boe-bots on 2008-05-15
okay! i've made some progress!!

i went to my terminal and put in:

sudo apt-get install jackd jackeq jack-rack jamin qjackctl


then after i installed it(through the terminal), i started rosegarden back up and the JACK sever popup was gone.

BUT now another window has come at startup(of rosegarden) saying that my general audio import was not avalible......what does that mean/what do i do?

thanks

---

### Post by boe-bots on 2008-05-15
whoops! it also said:

 "To fix this, you should install the following additional programs: sox OR sndfile-resample"


my package manager couldnt find it when i searched.......

---

### Post by spiderbatdad on 2008-05-15
I use rosegarden quite a bit for transposing midis into sheet music. It runs with no errors, so not sure why you are having these problems. Two things of note in my case. I installed rosegarden via synaptic package manager, and I use Hardy on the previous kernel used by Gutsy: 2.6.22-14-generic

You might consider changing the title of your thread to: Rosegarden help.
You might also post in the Multimedia Production forum.

---

