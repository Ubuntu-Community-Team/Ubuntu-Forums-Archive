---
title: "sound changed now can't sudo"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by cmcanulty on 2014-01-19
I am the only user I was trying to fix the audio which I did OK but in process now I can't sudo anything I didn't change any admin things that I know of. It thinks I am not an admin

---

### Post by nAHE8Yx on 2014-01-19
the problem is? no sound?

---

### Post by Iowan on 2014-01-19
[Here]("http://www.psychocats.net/ubuntu/fixsudo") is an article about fixing **sudo**, though I don't understand how it could "break". 
Perhaps a brief description what you did to fix the audio - permissions changed, etc.
What error message do you receive?

---

### Post by cmcanulty on 2014-01-19
Thanks I think I fixed it by mounting the / from a live usb and editing groups got directions from
[http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")
will restart to be sure. My audio was running only with sudo so I removed me from sudo group by mistake instead of audio

---

