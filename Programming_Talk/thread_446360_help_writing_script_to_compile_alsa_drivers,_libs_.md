---
title: "help writing script to compile alsa drivers, libs and utils"
date: 2007-05-16
forum: Programming Talk
---

### Post by syxbit on 2007-05-16
It's becoming a pain, but as of Feisty, my sound is broken, and I need to compile alsa to fix it.
every time an updated kernel is pushed out, it breaks my sound again.
i wanted to write a script to do this (and to learn more about scripting)
could someone help me out.

this is what i do manually



```

#install necessary build tools
Install necessary build tools
sudo apt-get install build-essential linux-headers-generic libncurses5 libncurses5-dev libasound2 libasound2-dev

cd alsa-driver-1.0.14rc4
./configure --with-oss=yes --with-cards=hda-intel
make
sudo make install

cd ../alsa-lib-1.0.14rc4
./configure
make
sudo make install

cd ../alsa-utils-1.0.14rc4
./configure
make
sudo make install

sudo alsaconf
---pick intel  soundcard

sudo /etc/init.d/alsasound reload
```

any help would be greatly appreciated

---

### Post by gradedcheese on 2007-05-18
Well, there's not much to it:

```

#!/bin/sh

# put your same sequence of commands here

```

Save this as alsa_install.sh or something and make it executable:

```

chmod a+x alsa_install.sh

```

Instead of running alsaconf, just overwrite the alsa config file with a saved copy.

---

### Post by FuturePast on 2007-05-18
That's basically it, though I would remove all the sudos and then just run
$ sudo alsa_install.sh

---

### Post by syxbit on 2007-05-25
this is what i have so far
```

#!/bin/sh
sudo apt-get install build-essential linux-headers-generic libncurses5 libncurses5-dev libasound2 libasound2-dev
cd driver
./configure --with-oss=yes --with-cards=hda-intel
make
make install

cd ../lib
./configure
make
make install

cd ../utils
./configure
make
make install

cd ../
#sudo alsaconf- instead, i'm copying the file that alsaconf seems to modify
cp sound /etc/modprobe.d/sound
sudo /etc/init.d/alsasound reload

```

i'm not sure it's running properly, as before it finished it says "cannot cd to this directory"
any ideas?

---

### Post by jyba on 2007-05-25
Your first cd command is 'cd driver'. This assumes that there's a directory called 'driver' in whatever directory is current when you run the script. After that, all your cd commands are relative to that initial directory. If you're getting the error message 'No such file or directory' then that suggests that somewhere along the chain of cd's you've directed it to a non-existant directory.

Put "#! /bin/bash -x" at the beginning of your script and the "-x" option will give you some good feedback on precisely where your script is going wrong.

---

### Post by syxbit on 2007-05-25
i have DIR's "driver" "utils" "lib" all in the same directory that the script is in.
so I don't need to "cd .." to get back out?
each time i "cd" it'll assume the original starting directory?

---

