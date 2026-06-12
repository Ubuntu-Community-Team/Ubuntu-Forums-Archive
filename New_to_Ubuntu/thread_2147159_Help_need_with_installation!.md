---
title: "Help need with installation!"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by Banshee159 on 2013-05-21
Hello guys.
I am a newbie.

I needed help with installation OS some programs. When i type in the codes of downloading a particular program in the terminal(Ubuntu 12.04.2 Precise pangolin) i get some error stating that "Could not get a lock on some var STUFF". After a reboot an error box popped up stating that it is impossible to install or remove any program and to fix it i needed to do some STUFF about "synaptic" and also a code to fix it was there in the error. I entered the code in the terminal but still an error stated that could not get a lock on var. I tried downloading synaptic manager program from the software center but it does not download. What should i do?

---

### Post by c2tarun on 2013-05-21
there are some quick fixes:

Try running:
> sudo apt-get update
above will refresh your repository list.

If still you are facing this issue, you can remove the lock on that file by following command:
> sudo fuser -kvi /location/to/file

---

### Post by sync on 2013-05-21
Just to check, since you didn't post what commands you're using, are you beginning your commands with "sudo"?  Installs need to be run with superuser permissions.

---

### Post by mastablasta on 2013-05-21
better write exactly what you typed/copied (commands) and what you got and also what you are trying to do.

---

### Post by nerdtron on 2013-05-21
What is the error you are receiving? If you are receiving error from the terminal such as the "Could not lock ..." can you copy/paste the error here?
Also, please post here the commands you entered for us to better understand your situation.

---

