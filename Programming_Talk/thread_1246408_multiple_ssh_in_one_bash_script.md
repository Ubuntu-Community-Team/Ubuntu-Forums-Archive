---
title: "multiple ssh in one bash script"
date: 2009-08-21
forum: Programming Talk
---

### Post by StreetSmart on 2009-08-21
I've got two asterisk servers that I run tcpdump on in order to sip trace.

Currently I use this command to capture the packets.

ssh root@astbox01 'tcpdump -w - -p -n -s 0 udp' > capture01.cap

Problem is, I have to open up two terminal windows and run my script twice, one for box01 and the other for box02

When I am done the test call, i ctrl+C to exit.

What I want to do is simultaneously run this command on both boxes, with a way to quit both at the same time.

It would be great if I could hard code the passwords into the script as well but this is not necessary. The password is the same for both boxes.

Thank you to all for taking time out of your day to help others.

---

### Post by pcman312 on 2009-08-21
Will this work:

```
#!/bin/bash
tcpdump (box1) &
tcpdump (box2) 
```

Running the two processes in the background through the bash script?

I haven't ever tried that, so I don't know if it'll work. Personally, I'd try it on another long-running but benign process first. (ls -R / > filename would do it ;))

Edit: Though I'm not sure how it would react to ctrl+c so you should definitely test that.

---

