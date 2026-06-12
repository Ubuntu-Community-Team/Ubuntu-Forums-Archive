---
title: "Ubuntu Studio"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by iUnify on 2013-06-11
I installed Ubuntu Studio 12.04 LTS... I had the same issues as  when I installed Ubuntu.  I can install 12.04 LTS but not 12.10 or  13.04.  With Ubuntu I was able to upgrae to .10 and 13 but with Studio I  am stuck at 12.04 LTS, upgrades claim to succede but fail on restart...  my screen just turns on and off and wont load linux.

Also, I  notice a few changes I am unhappy with in Studio, but, for the extra  benefits its worthwhile.  I was thinking some may be solvable though....

I  am not a fan of the workspace switcher on the top menu to the far  right.  I see I can narrow it down to 1 or 2 but I wanted to get rid of  that all together from the menu if possible.  And, no (unity I believe  it is called) application menu.... in settings it says 'right click  desktop for app menu' but thats a no go for me, doesnt work.  installed  and reinstalled unity from software center.

I can't Ctrl+Alt+T to open terminal in Studio which I was unhappy with.

Lastly,  I see I can hide my desktop icons... I like that... but, I have no clue  how to then find my recycle bin and also the drives, for example when I  insert a USB device and for example the HDD appears on the app menu in  Ubuntu, I can then right click that to safely remove or I can open it to  view the files... how do I do this without desktop icons in Studio?

I  hope I don't come off as a complainer!  I am ever so grateful for  advice I recently received on the forum, my last post....think once I get my feet wet I'll be much more satisfied  with this version of Ubuntu, just wanna work out the kinks.  :)

Thanks so much again!

---

### Post by iUnify on 2013-06-11
Also, if anyone knows how to integrate Rhythmbox with the Volume Control in Studio as it is in Ubuntu.  I am not sure if I was clear that I am using 12.04 LTS.

---

### Post by iUnify on 2013-06-11
I can not get the JACK running... as was suggested to me on my last post about Audacity.  This is what I am getting....

[HTML]marco@Marco:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse,marco
marco@Marco:~$ sudo usermod -a -G audio marco
[sudo] password for marco: 
marco@Marco:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse,marco
marco@Marco:~$ audacity
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4541
^A^[[D

[/HTML]

---

