---
title: "rosegarden jack not running"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by hanneshannes on 2008-07-06
hey,
I have installed Ubuntu studio.
when I Start Rosegarden the following messege appears:

Failed to connect to JACK audio server.
Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.
If you want to be able to play or record audio files or use plugins, you should exit Rosegarden and start the JACK server before running Rosegarden again.

afterwards in terminal I wrote:
sudo apt-get install jack

Reading package lists... Done
Building dependency tree       
Reading state information... Done
jack is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

this is the messege I get.

the result is I can not export my .rg to mp3 or any other format.

do you have any tipp how I could get my jack running?


I am absolutely new.
 I want to create music,
With rosegarden this seems to work well, but than I can not export the music.
If you have other tipps which point in a totally other direction (intall other program ...etc please let me know)


for example I tried this page : [http://www.hamienet.com/midi2mp3](http://www.hamienet.com/midi2mp3)
but that doesnt really work. maybe it works only with .midi istead of .rg (rosegarden)

thank you very much

---

