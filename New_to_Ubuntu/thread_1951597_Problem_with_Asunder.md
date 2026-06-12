---
title: "Problem with Asunder"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by nifty542 on 2012-04-02
Hi, all
I was worried I might have a broken system, so I reinstalled and upgraded to 12.04. I have used Asunder for a while, with no problems.
Now, it is reporting "lame' was not found in your path. Asunder requires it to create MP3 files. All MP3 functionality is disabled."
I have checked in Synaptic and it reports that I have libmp3lame installed.
I have a DVD drive and a DVDRW drive. I changed the path for my DVD drive to dev/sr0. It is correct according to the disc utility.
Obviously, I am doing something wrong, but can you friends enlighten me?

Many thanks, in advance of you lovely people

Regards

Nifty

---

### Post by dniMretsaM on 2012-04-02
This might help:
```
sudo apt-get install lame
```

Or
```
sudo apt-get install libmp3lame0-dev
```

---

### Post by nifty542 on 2012-04-03
Hi

Many thanks for the  reply. I tried the first solution and it worked!

Thank you.

Regards

Nifty

---

### Post by dniMretsaM on 2012-04-03
Glad you got it working. Mark as solved, please.

---

