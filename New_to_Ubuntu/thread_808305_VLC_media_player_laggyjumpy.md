---
title: "VLC media player laggy/jumpy"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by spacemanps on 2008-05-26
well i have been having some weird problems with my vlc media player... it tends to be a little jumpy and not smooth at all. I was reading some where that i have to maybe change the output module but i dont know which one to pick. I have opened vlc and changed it to each one and then closed it and reopeded the movie under each one and i am still getting the non smooth play pack....


 attatched is a screen shot of a list of the output modules i have on vlc. please help

---

### Post by Inxsible on 2008-05-26
Simply re-opening the movie file won't do. You have to restart  VLC. I am not sure if that's what you did or not.

Also, do you have all the necessary codecs installed ?

---

### Post by spacemanps on 2008-05-27
im trying to play avi"s and wmv"s, i am pretty sure i have the right codecs but im not sure. They are just jumpy. 

And i do go to file quit when i change the codec...

---

### Post by Inxsible on 2008-05-27
> **spacemanps said:**
> ..... i am pretty sure i have the right codecs but im not sure. ....So are you sure or NOT ?? ;-)

Go to Applications>>Add/Remove. Search for "gstreamer" without quotes and install all the options that you get. See if that improves the lag

---

### Post by sdennie on 2008-05-27
I think vlc has all it's codes builtin.  Have you tried changing the sound output module from pulseaudio to alsa?

---

