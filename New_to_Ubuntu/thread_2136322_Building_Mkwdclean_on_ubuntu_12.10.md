---
title: "Building Mkwdclean on ubuntu 12.10 ?"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by benlebowski on 2013-04-17
Hi, 

I'm creating a new thread as I was not aware I could not reply to an old thread, sorry overdrank for wasting some of your time ;)

I succeeded building mkwclean on my hp laptop with ubuntu 12.10, thanks to this thread : [http://ubuntuforums.org/showthread.php?t=1813594](http://ubuntuforums.org/showthread.php?t=1813594) and using vhook reply : 

```

sudo apt-get install build-essential checkinstall
./configure
make -C mkclean
sudo checkinstall -y

```

I know have mkclean, but I need mkwdclean.

However, I don't know how to compile mkwdclean which is used to modify mkw with old WD HD. This tool seems to be present in the package made available by matroska and that I used to compile mkclean : 

[http://www.matroska.org/downloads/mkclean.html](http://www.matroska.org/downloads/mkclean.html)

> This a command line tool to clean and optimize Matroska files that have already been muxed. It reorders the file for faster offline/online playback with the Cues at the front. Also comes with mkWDclean to modify files in a way they can play in broken players.

Thanks for your help

---

