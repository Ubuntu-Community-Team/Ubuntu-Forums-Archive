---
title: "Rhythmbox + MPC/musepack"
date: 2005-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by RaymondQE on 2005-05-29
This is my feeble attempt to get MPC support to work on my Hoary system. No guarantees that it will work.

Below are two debian files I created with the checkinstall program, so it they aren't completely debianized.  Download the two files from the address below:

[http://www.tc.umn.edu/~ouch0004/](http://www.tc.umn.edu/~ouch0004/)

Run the commands outlined below.

```
sudo dpkg -i libmusepack_1.1-1_i386.deb
sudo dpkg -i gstreamer0.8-musepack_0.8.8-1_i386.deb
gst-register-0.8
```

Open up rhythmbox and see if it works.

UPDATE:

Updated the deb files to work with libmpcdec 1.2 instead of libmusepack 1.1.

new files are located at:

[http://www.tc.umn.edu/~ouch0004/libmpcdec/](http://www.tc.umn.edu/~ouch0004/libmpcdec/)

Procedure:

1. Remove any of the previous installed musepack files

```
sudo dpkg -r libmusepack_1.1-1_i386.deb
sudo dpkg -r gstreamer0.8-musepack_0.8.8-1_i386.deb
```

2, install new files

```
sudo dpkg -i libmpcdec_1.2-1_i386.deb
sudo dpkg -i gstreamer0.8-musepack_0.8.8-2_i386.deb
gst-register-0.8
```


-- remember to remove and replace these files when the official debs are released.

---

### Post by foxy123 on 2005-05-30
works perfectly with amaroK. Thanks a lot for the files!

---

### Post by royg1234 on 2005-05-31
RaymondQE, you just made my day.  Good work!!!

---

### Post by budge on 2005-06-01
Great stuff. Thanks . :) 
Got loads of mpc files and couldn't figure out how to get it going under linux.
Efforts much apprieciated.
 \\:D/

Is there a way of getting this to work with all the media players, xmms, beep, etc?

---

### Post by knockey on 2005-06-01
Fantastic! Thank you very much, indeed!  :grin:

---

### Post by MikePB on 2005-06-01
Hi, I tried this and amoroK still won't play mpc files. as much as I like XMMS, I don;t like it's tag reading, and, imo anyway, amoroK does that TONS better.

---

### Post by jadugarr on 2005-06-01
[QUOTE=RaymondQE]This is my feeble attempt to get MPC support to work on my Hoary system. No guarantees that it will work.

Below are two debian files I created with the checkinstall program, so it they aren't completely debianized.  Download the two files from the address below:

[http://www.tc.umn.edu/~ouch0004/](http://www.tc.umn.edu/~ouch0004/)

Run the commands outlined below.

```
sudo dpkg -i libmusepack_1.1-1_i386.deb
sudo dpkg -i gstreamer0.8-musepack_0.8.8-1_i386.deb
gst-register-0.8
```

Open up rhythmbox and see if it works.

UPDATE:

Updated the deb files to work with libmpcdec 1.2 instead of libmusepack 1.1.

new files are located at:

[http://www.tc.umn.edu/~ouch0004/libmpcdec/](http://www.tc.umn.edu/~ouch0004/libmpcdec/)

Procedure:

1. Remove any of the previous installed musepack files

```
sudo dpkg -r libmusepack_1.1-1_i386.deb
sudo dpkg -r gstreamer0.8-musepack_0.8.8-1_i386.deb
```

2, install new files

```
sudo dpkg -i libmpcdec_1.2-1_i386.deb
sudo dpkg -i gstreamer0.8-musepack_0.8.8-2_i386.deb
gst-register-0.8
```


-- remember to remove and replace these files when the official debs are released.[/QUOTE]
 Thanks man, this saved me from re-ripping several cds to ogg like i have already done with most of my collection.  Great guide.

---

### Post by foxy123 on 2005-06-02
[QUOTE=MikePB]Hi, I tried this and amoroK still won't play mpc files. as much as I like XMMS, I don;t like it's tag reading, and, imo anyway, amoroK does that TONS better.[/QUOTE]
did you make sure that amaroK uses gstreamer engine... also do not forget to register a newly installed plugin...

---

