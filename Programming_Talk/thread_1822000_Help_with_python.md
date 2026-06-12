---
title: "Help with python"
date: 2011-08-09
forum: Programming Talk
---

### Post by 7cardcha on 2011-08-09
I was wondering how with python to "broadcast" data over an open port so another python app could pick it op over that port how would I go about both ideas?

---

### Post by karlson on 2011-08-09
> **7cardcha said:**
> I was wondering how with python to "broadcast" data over an open port so another python app could pick it op over that port how would I go about both ideas?

Not sure what you mean, but have you considered multicast using Python?

---

### Post by Tony Flury on 2011-08-10
Do you really mean "broadcast" - i.e. a single "transmitter" and multiple receivers - and the "signal" sent only once by the transmitter - if so the only way to do that is to do a multi-cast - your receiver will need to join a multi-cast group and wait for traffic to reach them.

If you have a limited number of "Receivers" and the "transmitter" can know who they are ahead of time (i.e. the hostnames or IP addresses) then you might find that opening a few point to point sockets and transmitting the data to each receiver would be easier (multi-cast can be a pain to set up from what i understand).

You could even do a design where by the "receivers" dynamically register with the "transmitter" and then go with the point to point solution - it all depends on the structure of your application, where the transmitter is (i.e. same host all the time) etc.

Either way in Python you need to look at the relevant sockets library.

---

### Post by unknownPoster on 2011-08-10
MPI may also be an appropriate solution.

---

### Post by StephenF on 2011-08-10
Depending on what you want to achieve DBus might be the answer.

---

