---
title: "raid 1 8.04"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by mspIggy on 2008-07-03
hello - 

absolutely new to installing anything like this onto a web server - but i need it!

i found a nice hp dl360 g4 with 2x 80gb sata drives

i need to install server edition 8.04 64bit for AMD and Intel Computers...

i have spent a considerable amount of time reading and researching freeBSD, Debian and Ubuntu and have decided to choose this

i need to install on this server with raid 1 and completely baffled - i have searched everywhere and see no guides to help me with this task 

from thsi url [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

"Your search query "8.04 raid 1" didn't return any results"

how in the world do i install this?

is there a person/group here that can sort of 'hold my hand' as it were... and guide me thru this process?

i would be very grateful

many thanks

mspIggy

---

### Post by bluepowder7 on 2008-07-03
has your search for "ubuntu server guide" given anything useful?

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by mspIggy on 2008-07-03
WOW --> very helpful - this will make my july 4th much more enjoyable!

thank you...

i have spent the evening on the debian website

question 

how in the world can ubuntu OS load with one cd rom and debian is 23 cd rom volume?

what makes up the difference here?

what am 'i' missing?

what are the main differences between ubuntu and debian

like i said - complete rookie :)

also --> to download these packages for mysql 5.0.21 and php 5.26 can i simply plug my server into an rj45 jack in my office www 4 plug network box? or does this contraption (dl360) need to be plugged into the switch port at my 'data-center' where it will eventually be co-located (already have one running with a worthelss unnamed os)

thank you

---

### Post by bluepowder7 on 2008-07-03
23 cd's?  ouch!  that has GOT to include every app and library known to man.  that's a LOT of stuff.  with ubuntu, 1 cd does the install, and any other app you need beyond the defaults is downloaded from a remote server and installed.

as to hooking it up - yeah, if you have a spare network jack at work you should be able to drag your heavy-**** server over, plug it in (though, might need to enable DHCP on the server box - probably on by default anyways), and you SHOULD be connected to the outside world.

to check if you're connected, type **ping google.com** in terminal, and it should spit out the results, with the time value at the end of each line being something like 90ms or 140ms.  hit Ctrl-C to stop the pinging after you get a few lines.

you can connect anywhere to download and install apps.  and after you're done, you can bugger off and physically set up the machine in a completely different city, though you may need to set up the DHCP / static IP stuff for the new location.  personally, i have my home server on a static IP.  heck, all my machines at home are on static IP since they're connected to a switch before going to a router (that way, if the router explodes and isn't able to handle DHCP, my machines don't care since they're all set up with static addresses)

---

### Post by mspIggy on 2008-07-04
ok---

heerree we go --

i will read and re- read both links for install...

'roll up the sleeves' as it were and get to work

many thanks


PS>> found this -- if this helps any others :)
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)
:)

---

### Post by mspIggy on 2008-07-04
how big is the root file system in the 8.04 server 64 bit version ??

i guess i need ot know this as i will install this for a raid 1 setup...

---

### Post by mspIggy on 2008-07-04
ok - making progress

got raid 1 set up finally

now i am at point hwere i am setting up server dns in file etc/network/interfaces

i made my settings saved the file..

then restarted the network etc/network/interfaces

an error came up

something about etc/postfix/main.cf - nosuch file or directory -- the dir is on the server  but no file called main.cf there is however one called master.cf?

what is this all about? 

is this a problem?

i downloaded the amd64 server disk on monday from chicago

---

