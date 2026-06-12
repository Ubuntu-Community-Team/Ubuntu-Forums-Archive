---
title: "Synaptic and Update Manager not working in Newly Installed Hardy"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by swarup on 2008-05-06
I installed Hardy on my laptop, and everything in it works fine. Now I am installing Hardy on my desktop, and for some reason although the computer is online, but when I start up Synaptic Package Manager and do a search, it does not yield any packages. The same thing is happening in Add/Remove Programs, and the same thing is happening in Update Manager. Update Manager starts looking for updates and sees 24, but can only get to the 15th and then the progress bar gets stuck. But the computer is online. If I open Firefox, I can browse to any web page. So what is going on?

(Note--I checked in "software repositories", and all the boxes are checked for the various repos, and the "Download from" window is set to "Server for United States", which always works fine for me.)

---

### Post by bapoumba on 2008-05-06
I've had downtimes recently. May be check later, or try from the main servers.

We can have a look at your sources.list file. Please open a terminal and paste the output to;
```
cat /etc/apt/sources.list
```

---

### Post by swarup on 2008-05-06
You know something? I went into Software Sources again just now and went into the "Download From" window and had it check for the best mirror for me. It did the check just fine, and found a site in the US that it said was the best one for me. I selected that, and now everything is working just fine--Synaptic, Update Manager, Add-Remove--all are working normally. I don't know why the usual default selection for the US didn't work for me. It always has in the past. Anyhow, this thread is solved and I'll mark it as such. Thanks for your offer to help. :)

Edit: Hey, how do you mark a thread as [SOLVED] these days? In the old forum format, it used to be listed under "thread tools". But it isn't there any more. So where has it gone to?

---

### Post by bapoumba on 2008-05-06
You're welcome, glad to see you got it to work :)
> **swarup said:**
> 
Edit: Hey, how do you mark a thread as [SOLVED] these days? In the old forum format, it used to be listed under "thread tools". But it isn't there any more. So where has it gone to?
It should be back soon, u-g is working on it :)

---

### Post by chiisu on 2008-05-07
I was having a similar problem.  I re-installed Hardy and when I tried to update it, it didn't do anything.  Lo and behold, I went to "Software Sources" and selected "Best Server", and it chose a much faster server, and now the updates are running along smoothly.  I can't believe I didn't figure this out sooner, or that Ubuntu doesn't do this by default.

---

