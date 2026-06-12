---
title: "Problem with gmagick extension installation"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by Leepoff on 2013-11-26
Hello all,

I've spent the past couple days trying to figure out why I can't get my install of gmagick for PHP(5.4.22) working on my lucid server. I have a local lucid VM where I have ran the same commands and everything is working great, but on my remote VPS I get the error in my Apache error log file:

/usr/lib/php5/20100525/gmagick.so: undefined symbol: DrawClearException in Unknown on line 0

Actions I've taken to install gmagick:

[LIST]
[*]sudo apt-get install graphicsmagick 
[*]sudo apt-get install libgraphicsmagick1-dev 
[*]sudo pecl install "channel://pecl.php.net/gmagick-1.1.5RC1" 
[*]Placed extension=gmagick.so in my php.ini file 
[/LIST]

I'm not sure if I have an older library on my VPS that hasn't been updated? I've tried several times to uninstall graphicsmagick and gmagick, run apt-get update and apt-get upgrade but no dice. I would really appreciate any help or guidance to something I'm doing wrong. Would loves me some learning!!

---

