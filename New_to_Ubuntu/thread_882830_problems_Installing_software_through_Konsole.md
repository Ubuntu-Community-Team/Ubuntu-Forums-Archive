---
title: "problems Installing software through Konsole"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Tower33 on 2008-08-07
Hey

Not sure if this is the right place for this let me know if it's not.

Just started using Ubuntu as i need it for my Honors project at uni. 
I need to install edinburgh speech tools, festival and festvox. I've been on other( forums for this and they informed that speech tools needs to be installed then festival then festvox. so I'm trying to do that but speech tools does not seem to install properly. Adivce given was that the GCC 4.2 might be conflicting and i should use GCC 4.1 instead, how do i go about doing this?

I installed GCC 4.1 but i'm not sure if thats what is being used.

all the files come packed in .tar.gz file which I unpacked using tar command.

heres the output when i run .configure

loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for ar... ar
checking whether byte ordering is bigendian... no
checking for tputs in -ltermcap... no
checking for tputs in -lncurses... no
updating cache ./config.cache
creating ./config.status
creating config/config

i then run make comand and at the end it comes up with these errors
/usr/bin/ld: cannot find -lcurses
collect2: ld returned 1 exit status
make[1]: *** [ch_lab] Error 1
make: *** [main] Error 2

any help will be much appreciated :)

---

### Post by jimv on 2008-08-07
That program is in the Ubuntu repositories.  You can install it with your favorite package manager instead of building it.  I like apt-get

You can run this command in the konsole to get the programs:
```

sudo apt-get install speech-tools festival festvox-kallpc16k
```

---

### Post by Tower33 on 2008-08-07
that seemed to have worked thanks for that :)

---

