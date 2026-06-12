---
title: "HOWTO: Play WMA audio files using Beep Media Player"
date: 2005-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2005-05-09
All of the commands below should be typed from a terminal.  Applications->System Tools->Terminal

If you don't have the beep media player you can get it via synaptic or:
```

sudo apt-get install beep-media-player
```

First download the beep development files:
```

sudo apt-get install beep-media-player-dev
```

Download the WMA plugin:
```
wget http://download.berlios.de/bmp-plugins/bmp-wma-0.1.1.tar.gz
```

Extract the files
```
tar -xvzf bmp-wma-0.1.1.tar.gz
```

Build and install the plugin
```

cd bmp-wma-0.1.1
```

```
./configure
```

```
make

```
```
sudo make install
```

That's it!  You can now play WMA with Beep Media Player, keep in mind that it still cannot play WMA files with DRM.

Let me repeat this, BEEP CANNOT PLAY WMA FILES WITH DRM!  It will open the file and show the title in the window but it will not play it.

---

### Post by Gandalf on 2005-05-10
it didn't work for me, BMP just disappear when i try to play any wma file

---

### Post by Darrena on 2005-05-10
[QUOTE=Gandalf]it didn't work for me, BMP just disappear when i try to play any wma file[/QUOTE]

Does it play MP3's successfully?

---

### Post by Brum on 2005-06-21
Hi very new to unbuntu.

Have followed the above steps and got as far as step 6 and typing in the ./configure command. Below is the response I get back. Can anyone give me a simple step by step guide as to what needs to be done to resolve this.

Cheers

[HTML]
********** ~/bmp-wma-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.[/HTML]

---

### Post by Druke on 2005-06-21
[QUOTE=Brum]Hi very new to unbuntu.

Have followed the above steps and got as far as step 6 and typing in the ./configure command. Below is the response I get back. Can anyone give me a simple step by step guide as to what needs to be done to resolve this.

Cheers

[HTML]
********** ~/bmp-wma-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.[/HTML][/QUOTE]


looks like you need a c/c++ compiler, get gcc

---

### Post by bored2k on 2005-06-21
sudo apt-get install build-essential

To the main poster: You could create a far deeper-better guide if you would include other plugins like OGG, FLAC, M4A, APE, Audioscrobbler (etc) support ;). I'm sure you know how..

---

### Post by Brum on 2005-06-22
Excellent! Thanks  \\:D/

---

### Post by Darrena on 2005-06-24
[QUOTE=bored2k]sudo apt-get install build-essential

To the main poster: You could create a far deeper-better guide if you would include other plugins like OGG, FLAC, M4A, APE, Audioscrobbler (etc) support ;). I'm sure you know how..[/QUOTE]

lol, well my point was only to get WMA support but maybe this weekend I will update it to be a more comprehensive guide to Beep Media Player.

---

### Post by frodon on 2005-06-24
thanks Darrena !

You can also read wma with XMMS using the xmms-wma module, after installing XMMS via synaptic you can download here the plugin (for example) : [http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)

after you do the same kind of commands :

```
tar -xjvf xmms-wma-X.X.X.bz2
```

go into the created repertory and do 

```
make
```

then 

```
sudo make install
```

now open XMMS and go to preference (Ctrl+p), in the entry  plugin verify that libwma.0 is activated and now you're ready to listen .wma files

---

### Post by angrykeyboarder on 2005-06-24
[QUOTE=frodon]thanks Darrena !

You can also read wma with XMMS using the xmms-wma module.... [/QUOTE]   Yes, but it's XMMS (w/that nasty GTK1..........)

---

### Post by Jonathan2007 on 2005-06-29
When I tried to install the bmp dev package using KPackage I got this error
```

<pt-get install --yes 'beep-media-player-dev' ;echo RESULT=$?
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beep-media-player-dev: Depends: libgtk2.0-dev but it is not going to be installed
E: Broken packages
RESULT=100

```
Anybody know what the problem could be? Thanks.

---

### Post by FLeiXiuS on 2005-06-29
[QUOTE=Jonathan2007]When I tried to install the bmp dev package using KPackage I got this error
```

<pt-get install --yes 'beep-media-player-dev' ;echo RESULT=$?
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beep-media-player-dev: Depends: libgtk2.0-dev but it is not going to be installed
E: Broken packages
RESULT=100

```
Anybody know what the problem could be? Thanks.[/QUOTE]

This should be a huge clue:-P
```
beep-media-player-dev: Depends: libgtk2.0-dev but it is not going to be installed
```

$ sudo apt-get install libgtk2.0-dev --force-yes --y

---

### Post by Jonathan2007 on 2005-06-29
Well I am not that stupid. I tried to just sudo apt-get install libgtk2.0-dev but it said it depended on something else. And when I tried to apt-get that it said that *it* depended on something else. So I thought I had hit a dead end, I will try your suggestion to force it which is what I thought needed to happen but I didn't know the exact command. Thanks. I will post back.

EDIT: Just tried it and I got this E: Command line option --force is not understood. So what now? Thanks again for your help.

---

### Post by FLeiXiuS on 2005-06-30
[QUOTE=Jonathan2007]Well I am not that stupid. I tried to just sudo apt-get install libgtk2.0-dev but it said it depended on something else. And when I tried to apt-get that it said that *it* depended on something else. So I thought I had hit a dead end, I will try your suggestion to force it which is what I thought needed to happen but I didn't know the exact command. Thanks. I will post back.

EDIT: Just tried it and I got this E: Command line option --force is not understood. So what now? Thanks again for your help.[/QUOTE]
 $ sudo apt-get install libgtk2.0-dev --force-yes --y

---

### Post by Jonathan2007 on 2005-06-30
When I try 

sudo apt-get install libgtk2.0-dev --force-yes --y

I get this 

E: Command line option --y is not understood

??

---

### Post by i3dmaster on 2005-07-01
Great! Thanks for sharing!

---

### Post by Jonathan2007 on 2005-07-01
[QUOTE=Jonathan2007]When I try 

sudo apt-get install libgtk2.0-dev --force-yes --y

I get this 

E: Command line option --y is not understood

??[/QUOTE]
No knows how to get this dev package installed? I really want BMP to be able to play wma's and I know I have the w32 codec package because Kaffeine can play the wma's fine.

---

### Post by twowheeler on 2005-07-03
Alternatively, you can convert the .rpm and avoid the build.

```
wget http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4-1.i386.rpm
sudo alien --to-deb xmms-wma-1.0.4-1.i386.rpm
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb
```

cheers.

---

### Post by empathy on 2005-07-04
Nice work Darrena! Exactly what I was searching for. Man, I love this ubuntu community - the level of commitment ot helping others is priceless.... literally.  :grin:  big ups yoself

---

### Post by Darrena on 2005-07-11
[QUOTE=empathy]Nice work Darrena! Exactly what I was searching for. Man, I love this ubuntu community - the level of commitment ot helping others is priceless.... literally.  :grin:  big ups yoself[/QUOTE]

Glad you liked it!  I am going to write a more detailed HOWTO to use Beep to play all your audio formats soon.

---

### Post by Jonathan2007 on 2005-07-28
I just did a reformat and reinstall of Kubuntu and so I resintalled BMP and followed this guide and it worked perfect. No problems like previously before. Thanks.

---

### Post by kalin_s on 2005-11-25
[QUOTE=twowheeler]Alternatively, you can convert the .rpm and avoid the build.

```
wget http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4-1.i386.rpm
sudo alien --to-deb xmms-wma-1.0.4-1.i386.rpm
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb
```

cheers.[/QUOTE]


Update:

There is already a version  for Beep Media Player, download from
[http://mcmcc.bat.ru/xmms-wma/beepmp-wma-1.0.5-1.i386.rpm](http://mcmcc.bat.ru/xmms-wma/beepmp-wma-1.0.5-1.i386.rpm)

Be sure you have Alien installed, then 
```

sudo alien --to-deb beepmp-wma-1.0.5-1.i386.rpm
sudo dpkg -i beepmp-wma_1.0.5-2_i386.deb
```

---

### Post by jrib on 2006-03-28
For Breezy Badger 5.10:

This didn't compile for me with gcc4, but worked fine with gcc3.4.

1. get gcc-3.4
```
sudo aptitude install gcc-3.4
```

2. Before ./configure, issue the following command
```
export CC=gcc-3.4
```

proceed as usual with the tutorial.

However I do strongly recommend the usage of ```
sudo checkinstall
``` as opposed to ```
sudo make install
```.  You will first have to install checkinstall with the command ```
sudo aptitude install checkinstall
```

---

### Post by DragonOrta on 2006-04-02
I just went through this and keep gettting this error at Make
> dragon64@dragon64:~/bmp-wma-0.1.1$ make
make  all-recursive
make[1]: Entering directory `/home/dragon64/bmp-wma-0.1.1'
Making all in src
make[2]: Entering directory `/home/dragon64/bmp-wma-0.1.1/src'
Making all in libffwma
make[3]: Entering directory `/home/dragon64/bmp-wma-0.1.1/src/libffwma'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-allcodecs.o -MD -MP -MF ".deps/libffwma_a-allcodecs.Tpo" -c -o libffwma_a-allcodecs.o `test -f 'allcodecs.c' || echo './'`allcodecs.c; \
then mv -f ".deps/libffwma_a-allcodecs.Tpo" ".deps/libffwma_a-allcodecs.Po"; else rm -f ".deps/libffwma_a-allcodecs.Tpo"; exit 1; fi
In file included from avcodec.h:14,
                 from allcodecs.c:21:
common.h:72: error: array type has incomplete element type
common.h:74: error: array type has incomplete element type
make[3]: *** [libffwma_a-allcodecs.o] Error 1
make[3]: Leaving directory `/home/dragon64/bmp-wma-0.1.1/src/libffwma'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dragon64/bmp-wma-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dragon64/bmp-wma-0.1.1'
make: *** [all] Error 2


---

### Post by Step on 2006-12-13
> **DragonOrta said:**
> I just went through this and keep gettting this error at Make

I had the same problem. Not able to fix it, yet...:-k


//edit:
Fixed, I managed to install the .deb by downloading it from [_HERE_]("http://packages.debian.org/unstable/sound/beep-media-player-wma")

Take the one which suits you most (mine was i386), then it will almost automatically install for you.
I used this in combination with 6.10 Edgy Eft, for your information. :)

---

### Post by vitor on 2007-01-24
I try your way step..but some trouble with packages to.. and when I try compile the error is the same of DragonOrta, some help!

```
vitor@ubuntu:~/arquivos/pacotes$ sudo dpkg -i beep-media-player-wma_1.0.5-4_i386.deb 
Password:
Selecionando pacote previamente não selecionado beep-media-player-wma.
(Lendo banco de dados ... 120975 arquivos e diretórios atualmente instalados.)
Descompactando beep-media-player-wma (de beep-media-player-wma_1.0.5-4_i386.deb) ...
dpkg: problemas de dependência impedem configuração de beep-media-player-wma:
 beep-media-player-wma depende de libavcodec0d (>= 0.cvs20060823); porém:
  O pacote libavcodec0d não está instalado.
 beep-media-player-wma depende de libavformat0d (>= 0.cvs20060823); porém:
  O pacote libavformat0d não está instalado.
 beep-media-player-wma depende de libdc1394-13; porém:
  O pacote libdc1394-13 não está instalado.
 beep-media-player-wma depende de libfontconfig1 (>= 2.4.0); porém:
  A versão de libfontconfig1 no sistema é 2.3.2-7ubuntu2.
 beep-media-player-wma depende de libpango1.0-0 (>= 1.14.8); porém:
  A versão de libpango1.0-0 no sistema é 1.14.5-0ubuntu1.
dpkg: erro processando beep-media-player-wma (--install):
 problemas de dependência - deixando desconfigurado
Erros foram encontrados durante processamento de:
 beep-media-player-wma

```

whats wrong? thanks

---

### Post by blazoner on 2007-01-25
I had most of these problems, and that  link to [http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4-1.i386.rpm](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4-1.i386.rpm) gives a 404 error.

Here's what I did to get it to work:
If you have bmp-wma installed, remove it.  It conflicts with this.

Make sure you have alien installed, then
```
wget http://mcmcc.bat.ru/xmms-wma/beepmp-wma-1.0.5-1.i386.rpm
sudo alien --to-deb beepmp-wma-1.0.5-1.i386.rpm
sudo dpkg -i beepmp-wma_1.0.5-2_i386.deb
```

Hope this helps....:)

---

### Post by QTWNeT on 2007-09-15
How to fix?

> dragon64@dragon64:~/bmp-wma-0.1.1$ make
make all-recursive
make[1]: Entering directory `/home/dragon64/bmp-wma-0.1.1'
Making all in src
make[2]: Entering directory `/home/dragon64/bmp-wma-0.1.1/src'
Making all in libffwma
make[3]: Entering directory `/home/dragon64/bmp-wma-0.1.1/src/libffwma'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2 -MT libffwma_a-allcodecs.o -MD -MP -MF ".deps/libffwma_a-allcodecs.Tpo" -c -o libffwma_a-allcodecs.o `test -f 'allcodecs.c' || echo './'`allcodecs.c; \
then mv -f ".deps/libffwma_a-allcodecs.Tpo" ".deps/libffwma_a-allcodecs.Po"; else rm -f ".deps/libffwma_a-allcodecs.Tpo"; exit 1; fi
In file included from avcodec.h:14,
from allcodecs.c:21:
common.h:72: error: array type has incomplete element type
common.h:74: error: array type has incomplete element type
make[3]: *** [libffwma_a-allcodecs.o] Error 1
make[3]: Leaving directory `/home/dragon64/bmp-wma-0.1.1/src/libffwma'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dragon64/bmp-wma-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dragon64/bmp-wma-0.1.1'
make: *** [all] Error 2

---

### Post by QTWNeT on 2007-09-15
> **Step said:**
> I had the same problem. Not able to fix it, yet...:-k


//edit:
Fixed, I managed to install the .deb by downloading it from [_HERE_]("http://packages.debian.org/unstable/sound/beep-media-player-wma")

Take the one which suits you most (mine was i386), then it will almost automatically install for you.
I used this in combination with 6.10 Edgy Eft, for your information. :)

Link not found

---

### Post by QTWNeT on 2007-09-15
Pls delete this post - Thanks

---

