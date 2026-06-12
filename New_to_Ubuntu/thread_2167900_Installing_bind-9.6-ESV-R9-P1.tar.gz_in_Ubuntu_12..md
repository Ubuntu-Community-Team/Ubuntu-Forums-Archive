---
title: "Installing bind-9.6-ESV-R9-P1.tar.gz in Ubuntu 12.04 LTS"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by karanbpathak on 2013-08-15
[COLOR=#000000][FONT=Arial]I wanted to install bind in Ubutnu 12.04 LTS,since i downloaded it in form of tar.gz so How to install bind-9.6-ESV-R9-P1.tar.gz in Ubuntu 12.04 LTS,assuming i want to install in home directory. I also want to learn these type install,please help[/FONT][/COLOR]

---

### Post by GwL3eNC on 2013-08-15
Hi,

if you want to install software from source it is extrem importand to read the README file. There you can 
find any information how to build the sources. These are the first two steps, copied from the README. 

To build, just

        ./configure
        make

You have to do that in the terminal and in the folder containing the sources. It is possible that you
must install build-essential before. sudo apt-get install build-essential.

Further you can find in the README (the last step of three step building)

"make install" will install "named" and the various BIND 9 libraries.
    By default, installation is into /usr/local, but this can be changed
    with the "--prefix" option when running "configure".

Try it. To see additional configure options, run "configure --help".

---

