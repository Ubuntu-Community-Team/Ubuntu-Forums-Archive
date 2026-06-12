---
title: "[SOLVED] mpc and mpd - &amp;quot;no audio on client&amp;quot;?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by iKevin on 2008-09-01
Hi All

I am sorry for asking yet another question but I am stumped again.  

I have mpd installed and configured on my main ubuntu box.  I have also install mpc/gmpc and it runs fine on both.  However, on the client box, I can see all of my mp3's and I can select and play but there is no audio.  Gmpc shows the progress bar for the song as if it were playing.  

I generally have audio working on the client machine so I am wondering if someone where to look to for getting audio to work with mpc/gmpc.

---

### Post by vanadium on 2008-09-01
mpc is a "command" server: it will take commands from a remote client. However, it cannot stream audio: it will play back audio only on the computer where it is installed. Thus, you need to connect to an mpd running on your client machine if you want the audio be produced on your client machine.

---

### Post by iKevin on 2008-09-01
Thanks

So the mpd on the server machine communicates with the mpd on the client?  And the mpc client communicates with the mpd server on the client?

Kev

---

### Post by iKevin on 2008-09-01
Hi All

I figured out that mpd was not what I thought it was.  The clients control the daemon and the music on the server.  What I really was after was "mt-daap".  I wanted to share my music with a few other machines in the house. It is all up and running.

Thanks
Kevin

---

