---
title: "Where to Start - the ADSL dialer project"
date: 2006-10-20
forum: Programming Talk
---

### Post by rancidbob on 2006-10-20
Hey there all,
would someone be so kind as to direct me. I am lost in this huge world of Ubuntu. I am not a complete n00b to linux, but I have not fiddled with the source code portions of linux. I have only ever programmed for fun, and now that I wanna do something serious I find myself lost.

I would like to write a front end for pppoeconf combined with a "dialer", sorta like the setup in windows, but all in the spirit of gnome. The intention is to start it in python(this will be my first REAL python app)(hopefully), and if i succeed at this then, redo it in gtk or whatever gnome is done in.

So this is where I need help. Where can I find the pppoeconf source code, preferably with enough comments so I can see how it all works.

Please point me in the right direction.
Many thanks 
RancidBob :P

---

### Post by gborzi on 2006-10-20
You can get pppoeconf source code with the following command > sudo apt-get source pppoeconf that will download (and unpack) the source code of pppoeconf in your current directory.

---

### Post by rancidbob on 2006-10-20
Thanks a ton. 
I have the package now, but what language is this all done in. Where can I find more info, like I mentioned before, maybe a nicely commented file, to help me make sense of it. I have checked out some of the files  that I assume to be the source code. Those would be the files in the po directory. At this time, I think just for english :).
Once again
Thanks a bunch.
Bob
PS: Where would be the best place for a n00b like me to start. This is something I'd like to do for me and the community, but it is so difficult to get any good direction. I have tried some other forums, but no-one ever gives n00b directions, pretty pretty please :)

---

### Post by rancidbob on 2006-10-23
I hate to be insistent, but would someone please point me in the right direction, keeping in mind that I am really new to this, with a bit of python and a bit of linux experience.
Many thanks
Bob

---

### Post by gborzi on 2006-10-23
Hello,
pppoeconf is written in bash scripting, note the initial line #!/bin/sh . As for starting scripting, I have used a the "Appunti di Informatica Libera" manual, but it's in italian, so I don't think it will be very helpful for you, unless you read italian.

---

