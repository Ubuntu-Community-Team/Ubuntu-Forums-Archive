---
title: "Thunderbird doesn't play my custom sound file when retrieving emails"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by Houmie on 2012-05-22
Hi,

I have selected a short wav file from here [http://www.ilovewavs.com/Events/GotMail/GotMail.htm](http://www.ilovewavs.com/Events/GotMail/GotMail.htm)

But nothing even happens when I click on the Play button on Thunderbird settings. 


[IMG]http://i.imgur.com/1PIhU.png[/IMG]

Is this a bug?

Thanks

---

### Post by Sealbhach on 2012-05-22
Hi, I've just tried doing the same thing as you did, and it's the same for me, no sound. I found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/732572") which explains that Thunderbird used to rely on esound to make system sounds but now that has been superseded by the Pulseaudio sound system. 

At the end of the bug report it says that this issue is supposed to have been fixed with Thunderbird 12.01 but that's the version I'm using but still there is no sound. :confused:

.

---

