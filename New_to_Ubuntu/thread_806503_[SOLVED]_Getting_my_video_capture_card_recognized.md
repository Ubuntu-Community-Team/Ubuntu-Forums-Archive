---
title: "[SOLVED] Getting my video capture card recognized"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by thomand52 on 2008-05-25
I'm a noob to ubuntu and am trying to get Hardy to recognize my 150 PVr card.

---

### Post by wolfen69 on 2008-05-25
your card is recognized already. ubuntu sees it. read on to watch tv.

I have a Hauppauge pvr150 card running on my hardy box, and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```

it will record whatever channel you are on. then ctrl-c to stop.

---

### Post by thomand52 on 2008-05-26
Thanks for your help.
Now I've got it displaying but it won't change channels.
Any suggestions would help.
I've tried typing the changes in the terminal, but it still stays on ch4.

---

### Post by thomand52 on 2008-05-26
I removed my webcam and reinstalled my card and it's working now.

---

### Post by saedelaere on 2008-06-03
Hi,

[here]("http://ubuntuforums.org/showthread.php?t=763698") you may find an alternative frontend :)

Regards

Saedelaere

---

