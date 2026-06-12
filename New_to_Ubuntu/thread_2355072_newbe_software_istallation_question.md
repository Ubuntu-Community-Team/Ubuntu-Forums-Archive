---
title: "newbe software istallation question"
date: 2017-03-09
forum: New to Ubuntu
---

### Post by alexkoganov on 2017-03-09
hi guys
i am new to ubuntu and as future pen tester i am want Linux to be my best friend :) ,but what is going with the installation methods ?
here's 2 example:

1) wireshark.
after the very first installation i tried to run it and its said that i dont have permissions???
what permissions do i need? why its so easier on windows?
after a little  research i am found some nice installation guide over here that goes like this:
   sudo groupadd wireshark
sudo usermod -a -G wireshark YOUR_USER_NAME
sudo chgrp wireshark /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcapn
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
sudo getcap /usr/bin/dumpcap

what every line say?

there is a guide somewhere to understand how is works on Linux a what those directories means?

2)pycharm.
i followed this on youtube
[https://www.youtube.com/watch?v=R4hQkcjDbDw](https://www.youtube.com/watch?v=R4hQkcjDbDw).
to run it i need to execute a ./ on pycharm.sh file.
again,why windows is more simple??
and why when i am closing the terminal it kills the program??
i want a regular installation and desktop icon to lunch it immediately without complex commands :\.

p.s

as i said i am a future pen tester so if u guys have a good resource for
mastering the terminal from scratch i'll be glad to hear about one.

tnx a alot

---

### Post by QIII on 2017-03-09
You will get no help here in learning pen testing as we do not allow such discussions.

---

### Post by alexkoganov on 2017-03-09
why
i am taking a university course for it in a couple of months ?
can i got at least answers to my 2 questions?

tnx

---

### Post by howefield on 2017-03-09
Here are some links for you.

[Forums Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules")
[Forums Posting Tips]("https://ubuntuforums.org/showthread.php?t=2158945")
[Linux Command Line Learning Resources]("https://ubuntuforums.org/showthread.php?t=2015424")

Thread closed.

---

