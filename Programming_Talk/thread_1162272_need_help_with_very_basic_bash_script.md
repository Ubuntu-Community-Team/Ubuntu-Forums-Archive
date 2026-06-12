---
title: "need help with very basic bash script"
date: 2009-05-17
forum: Programming Talk
---

### Post by Woody1987 on 2009-05-17
Im trying to write a bash script that will download the source code for a program, in this example it is banshee. The script will then download the build dependencies and then configure and make, lastly install.

The script so far:
> #!/bin/bash
cd /tmp
apt-get source <help>
sudo apt-get build-dep <help>
cd <help>
./configure CFLAGS="-march=core2 -O2 -pipe" CHOST="x86_64-pc-linux-gnu" MAKEOPTS="j5" -prefix=/usr
make
sudo checkinstall -D make install
sudo dpkg -i <help>.deb

Where <help> is shown is where i need the help. What i want to be able to do is pass an argument to the script i.e. banshee so that <help> will read banshee or any other program i desire. This will work partly, but on lines 5 and 10 (cd <help> sudo dpkg -i <help>.deb) this wont work as this will be not just the program name but also the version.

This is what the script needs to look like:

> #!/bin/bash
cd /tmp
apt-get source banshee
sudo apt-get build-dep banshee
cd banshee-1.4.3
./configure CFLAGS="-march=core2 -O2 -pipe" CHOST="x86_64-pc-linux-gnu" MAKEOPTS="j5" -prefix=/usr
make
sudo checkinstall -D make install
sudo dpkg -i banshee-1.4.3_amd64.deb

This would be fine if the only program i wanted to compile was banshee, but i want to be able to pass any program into the script and for it to compile.

---

### Post by pokerbirch on 2009-05-17
To get user input, use the **read** command. Obviously the user would have to enter the correct file name but it should work ok. This is NOT tested!

```

#!/bin/bash
echo "Please enter the app name and press [ENTER]"
read app_name
cd /tmp
apt-get source $app_name
sudo apt-get build-dep $app_name
cd $app_name
./configure CFLAGS="-march=core2 -O2 -pipe" CHOST="x86_64-pc-linux-gnu" MAKEOPTS="j5" -prefix=/usr
make
sudo checkinstall -D make install
sudo dpkg -i "$app_name.deb"

```

---

### Post by Woody1987 on 2009-05-17
Thanks, but i was thinking more like pass as an argument instead of prompting for user input, 

e.g. ./script banshee
./script vlc
./script deluge
etc
etc

---

### Post by Woody1987 on 2009-05-17
Some research has lead me to

> #!/bin/bash

cd /tmp
apt-get source $1
sudo apt-get build-dep $1
cd $1
./configure CFLAGS="-march=core2 -O2 -pipe" CHOST="x86_64-pc-linux-gnu" MAKEOPTS="j5" -prefix=/usr
make
sudo checkinstall -D make install
sudo dpkg -i "$1.deb"

exit 0

This works except i then need to be able to cd into the program directory but the folder isnt called the same as the program, it has the version number in it.

---

### Post by Woody1987 on 2009-05-17
fixed it a little more for the installing the deb

> #!/bin/bash

cd /tmp
apt-get source $1
sudo apt-get build-dep $1
cd $1-1.4.3
./configure CFLAGS="-march=core2 -O2 -pipe" CHOST="x86_64-pc-linux-gnu" MAKEOPTS="j5" -prefix=/usr
make
sudo checkinstall -D -y make install
sudo dpkg -i "*.deb"

exit 0

just need to be able to cd now.

---

### Post by Woody1987 on 2009-05-17
Solved!

> #!/bin/bash

cd /tmp
apt-get source $1
sudo apt-get -y build-dep $1
cd $1*
./configure CFLAGS="-march=core2 -O2 -pipe" CHOST="x86_64-pc-linux-gnu" MAKEOPTS="j5" -prefix=/usr
make
sudo checkinstall -D -y make install
sudo dpkg -i "*.deb"
sudo rm -r /tmp/$1*

exit 0

---

