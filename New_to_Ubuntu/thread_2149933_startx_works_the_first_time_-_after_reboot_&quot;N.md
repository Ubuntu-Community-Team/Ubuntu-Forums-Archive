---
title: "startx works the first time - after reboot &quot;NO PROTOCOL SPECIFIED&quot;"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by sakuraba on 2013-05-30
Hello.

Im running ubuntu server 12.04.02

I wanted a minimal x setup so I did

apt-get install xorg
apt-get install openbox
apt-get install firefox

now the first time I run startx....Its brilliant. Very minimal windows manager...I can use firefox...xterm -fn 10x20 is awesome....everything I need.

However......after a reboot......I run startx...

All I get is a black screen.....and when I alt-ctrl-F2 back to the terminal i ran startx from I get "NO PROTOCOL SPECIFIED.."
over and over again maybe 100 times before I get an error message...

after maybe 3-4 minutes of "no protocol speficied" i get as follows:

xinit: giving up
xinit unable to connect to X server: resource temporarily unavailable
waiting for x server to shutdown ddxSigGiveup: Closing log
Server terminated success

xinit server serror
xauth: error in locking authority file /home/myusername/.Xauthority

Now I can fix this easily.....

rm ~/.Xauthority*

and then I can run startx no problems...

Whats going on????

Can I fix this permenently?

---

### Post by sakuraba on 2013-05-30
can anyone help with this problem?

---

