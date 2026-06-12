---
title: "[SOLVED] mpd pulse audio startup problems"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by whitethorn on 2008-11-05
When I log in and try to play something on mpd it doesn't work.  I looked in the error log and got the following.



> Nov 06 01:48 : Cannot connect to server in PulseAudio output "My MPD PulseAudio Output" (attempt 1): Connection refused

Nov 06 01:48 : problems opening audio device while playing "****.mp3"





When I restart mpd using



```
sudo /etc/init.d/mpd restart
```



I can then play music -> works perfectly.  



I'm guessing the reason is that mpd gets started before pulseaudio.  Mpd gets started before the xserver (one of the reasons I chose to use mpd a year ago when pulse wasn't implemented yet) and pulseaudio gets loaded when I log in.  So mpd doesn't have a connection to pulse.  Is there a way to get mpd to get restarted when I log in or only start after pulse?  I'm thinking a small script of which I can then add to my session? I just don't know how to give the script/command root priviledges (so I won't be asked for my password).

---

### Post by Nepherte on 2008-11-06
Take a look at this: [http://mpd.wikia.com/wiki/PulseAudio#An_alternate_solution_for_fixing_access_rights](http://mpd.wikia.com/wiki/PulseAudio#An_alternate_solution_for_fixing_access_rights)

---

