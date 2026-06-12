---
title: "Software Centre and other updates not working"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by Abhinav_Nain on 2014-08-09
I am completely new to ubuntu. Maybe the reason why I am posting it here. ;)

Okay, so i started a video and I get and error of missing codecs. Ubuntu looks for updates, finds them, tries to download them, most of them finish but some of them are always stuck at 0%. Even tried changing servers. A problem is up with software centre too. I cannot install anything. Downloads are stuck at Updating cache. Please help me out.:?

Grateful to ur help. Thanks! ):P

---

### Post by Jesse_Campton on 2014-08-09
Well, lets start with what version of Ubuntu are you using? If you are using Ubuntu 14.04 and you are missing codecs. Open a terminal by pressing and holding Ctrl+Alt+t, then copy and paste into terminal,```
sudo apt-get update && [COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install ubuntu-restricted-extras[/FONT][/COLOR]
``` Press enter, type password if your asked, then enter again. Then type the next command (rinse & repeat). ```
sudo apt-get update && [COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install libavcodec-extra[/FONT][/COLOR]
``` & ```
sudo apt-get update && [COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install icedtea-7-plugin openjdk-7-jre[/FONT][/COLOR]
``` .. For DVD Playback: ```
sudo apt-get update && [COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install libdvdread4[/FONT][/COLOR]
``` & ```
&#8203;sudo apt-get update && [COLOR=#000000][FONT=UbuntuBeta Mono]sudo /usr/share/doc/libdvdread4/install-css.sh[/FONT][/COLOR]
```.

Also: just a FYI (google is your friend) simple questions along with adding the word Ubuntu to the beginning or end of your question will yield amazing results =) "Google Search: Missing video codecs Ubuntu 14.04" 
Something else to look into is [http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html).

---

