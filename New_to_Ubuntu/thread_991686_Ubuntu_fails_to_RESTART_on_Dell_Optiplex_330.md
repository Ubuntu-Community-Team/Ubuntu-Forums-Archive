---
title: "Ubuntu fails to RESTART on Dell Optiplex 330"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by babloo75 on 2008-11-24
Hi frenz,
I am facing a very strange problem on my new desktop optiplex 330. initially it used to be a problem with shutdown as well as restart, both.
but after following the advice in another forum, as below

[http://ubuntuforums.org/showthread.php?p=6069946#post6069946](http://ubuntuforums.org/showthread.php?p=6069946#post6069946)

i.e. by opening in terminal
sudo gedit /etc/init.d/alsa-utils

and then adding 
# ifconfig eth0 down

it seems to be solved partially (partially because when i give a command to shutdown, it shuts down. but when i try to restart it fails to shut down and freezes at the end of orange bar becoming black-- and then it stays there untill i switch off the ac current)

can u please help me solve this problem

---

