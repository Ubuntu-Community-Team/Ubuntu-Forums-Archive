---
title: "Deluge confusion"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by mayur.shetye on 2012-02-03
Hi! I have a question about Deluge and Google has confused me. :P 
I just want to make deluge start downloading the torrents which are added on startup(like utorrent).I googled about this and came across the init script.Also,in all the posts I read I found that the init script is used to start the daemon so that deluge could be accessed using the web UI.I don't intend to access deluge using the web UI.So,here's the question
i)Do I need to use the init script to just start my downloads automatically on startup?
ii)Is there a simpler way or perhaps another torrent client which can perform this task?  

P.S I tried the init script and it doesnt work.

---

### Post by Cas07 on 2012-02-07
If you are simply using Deluge on your desktop then just add deluge to Startup Applications.

---

### Post by ikt on 2012-02-07
What happens if you try

Cog in the top right > Startup Applications > 

then add deluge?

---

### Post by mayur.shetye on 2012-02-08
Hi! The problem is solved.I unistalled deluge completely using synaptic and reinstalled it along with delugged(daemon). Then I used the init script given on the deluge website and evrything works fine :).Its actually the deluge daemon which needs to be started up during login. Thank you for your help :)

---

