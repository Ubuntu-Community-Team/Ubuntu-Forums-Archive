---
title: "Multi-Part .avi Files"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by no-1-uno on 2008-07-23
What would y'all suggest I use for joining multi-part avi files I downloaded of a movie?

---

### Post by Joeb454 on 2008-07-23
Moved to it's own thread - it was a separate question from login sounds ;)

---

### Post by LaRoza on 2008-07-23
> **no-1-uno said:**
> What would y'all suggest I use for joining multi-part avi files I downloaded of a movie?

What movie? Is this legal?

---

### Post by Joeb454 on 2008-07-23
Actually I've just read that (overdrank pointed it out to me - thanks)

---

### Post by LaRoza on 2008-07-23
> **Joeb454 said:**
> Actually I've just read that (overdrank pointed it out to me - thanks)

He is now invisible?

---

### Post by Joeb454 on 2008-07-23
overdrank or no-1-uno?

---

### Post by no-1-uno on 2008-07-23
I am here just away from the puter for awhile, will check in from time to time.

Oh and it is a home movie my Uncle made of the grandbabies.

---

### Post by no-1-uno on 2008-07-23
I am here just away from the puter for awhile, will check in from time to time.

Oh and it is a home movie my Uncle made of the grandbabies.

---

### Post by mali2297 on 2008-07-23
Do you know how the files are split?

Is each of them viewable by itself?

---

### Post by northern lights on 2008-07-23
"mencoder" will do.

Documentation can be found [here]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide").

---

### Post by sisco311 on 2008-07-23
avimerge
```
sudo apt-get install transcode
```

---

### Post by jtniehof on 2008-07-23
[Avidemux]("http://fixounet.free.fr/avidemux/") will do the job...just open the first, then "append" the next (in the File menu). (You need to have multiverse enabled to install avidemux in Ubuntu.)

---

### Post by halitech on 2008-07-23
open a terminal
```
cat filename1.avi filename2.avi > completedfilename.avi
```

I believe will do it as well and pretty fast as well.

---

### Post by ice60 on 2008-07-23
i do what halitech said, i just checked my bash history and i joined an avi file back together like this -

if these are the names of the files to join -

cool_movie.avi.001 cool_movie.avi.002 cool_movie.avi.003 cool_movie.avi.004

```
cat cool_movie.avi.00[1-4]>cool_movie.avi
```

---

