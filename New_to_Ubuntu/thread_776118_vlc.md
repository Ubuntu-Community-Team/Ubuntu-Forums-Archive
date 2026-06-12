---
title: "vlc"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by kattou22 on 2008-04-30
hi, 
i finally was able to install vlc but i dont know how to make my link open vlc to play in it. it is a asx. I am using gutsy. file and open network stream and then i put in url of asx file. :(

---

### Post by nineowls on 2008-04-30
i suppose you opened file > network stream
did you select http and paste your URL in?

---

### Post by kattou22 on 2008-04-30
yup. i even changed the way ase file was managed by opening vlc. ..   it does  make vlc start but nothing plays. its silent!

---

### Post by nineowls on 2008-05-02
> **kattou22 said:**
> nothing plays. its silent!
can u share the link--i'll try it on my vlc

---

### Post by Fatal Equinox on 2008-05-02
So dragging the link into an already open vlc player doesn't work?

---

### Post by kattou22 on 2008-05-05
[www.12stepradio.com](www.12stepradio.com) you have to clik on the link called listen in or something like that.  :)

Sorry about the delay, i had to think hard before telling everyone the link!!

---

### Post by wolfen69 on 2008-05-05
it works for me directly from my browser. i just clicked "listen now". try this: ```
sudo apt-get remove --purge totem-mozilla 
```
then
```
sudo apt-get install mozilla-mplayer
``` i bet it will work for you. mozilla-mplayer seems to work much, much better than totem.

---

### Post by kattou22 on 2008-05-05
Hi, i just did that, but it seems that it did not remove totem as totem is still installed. And in my applications i dont see mozilla-mplayer anywhere. Yet in console it did install 
Any ideas

---

### Post by wolfen69 on 2008-05-05
you wont see mozilla-mplayer. it gets integrated into firefox. check your link again and click "listen now". wait for it to buffer. also, you did not remove totem, just the totem plugin for firefox.

---

### Post by kwacka on 2008-05-05
VLC (my favourite player) doesn't play this stream for me either, although it does play .asf files. 

I can confirm that the mplayer plugin does play this stream.

---

### Post by kattou22 on 2008-05-05
Oki, i rebooted thinking maybe something did not go right,  It seems to continue opening with totem and says no plugin or something like that.  

:(

---

### Post by wolfen69 on 2008-05-05
then just remove totem.
```
sudo apt-get remove --purge totem
```
in my opinion, totem shouldnt even be installed by default anyway. there are much better media players out there.

---

### Post by kattou22 on 2008-05-05
Hi again. 
I completly removed totem, but it was still starting when i clik on a link. So i completely removed it using sudo apt-get autoremove totem.

Now it stars with VLC.  so i managed to open mplayer, (it is now in my application menu) but when i open url . this is the error i get. :
 couldnt resolve name for AF_INET6: [www.12stepradio.com](www.12stepradio.com)

Some how i feel i am gettting close to listening to my radio but still need a bit of help :)

---

### Post by kattou22 on 2008-05-06
Oki, i managed to make it work but only through console by typing

mplayer -playlist [http://www.12stepradio.com/audio/12sr.asx](http://www.12stepradio.com/audio/12sr.asx)

if i try through the ubuntu desktop it dont work, it tells me an error, 
At least i know that the stream works through mplayer.  But is there a way to make it work in graphic mode

---

### Post by wolfen69 on 2008-05-06
open firefox and go to edit>preferences>applications. there you will be able to change some default settings.

---

### Post by kattou22 on 2008-05-09
Hey, This problem is solved.  
While opening in terminal, i realized that it kept saying
Playing [http://azul.streamguys.com/12stepradio?SAMI=http://www.12stepradio.com/audio/12sr.smi](http://azul.streamguys.com/12stepradio?SAMI=http://www.12stepradio.com/audio/12sr.smi).

So i tried this Url in Mplayer  instead of dragging my link into the window or using the asx link.   :)  it works wonderfully now. 

Thanks for all ppl help

---

