---
title: "Installing samba"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by PhilHodges on 2008-06-11
Brand new Ubuntu boy here-I'm using 7.10 and want to share desktop folders.I tried to share the folder and got the box up saying that I needed to install services (smb, NFS). I clicked on "Install services" several times but nothing happened so I downloaded samba 3.30 and extracted it to a folder on the desktop.
I tried sudo apt-get install samba in a terminal and got told  the package wasn't available but I have samba-common!?* 
What's that and what do I do now?
Some step-by-step small word instructions would be very welcome.
Thanks in advance.
Regards,
Phil 
PS. I've been all over the place looking for a direct answer and now my head really hurts.

---

### Post by heinig on 2008-06-11
this video may help you to setup samba...

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by kk0sse54 on 2008-06-11
Just go into the Synaptic package manager and install Samba and all it's dependencies from there.

---

### Post by PhilHodges on 2008-06-12
Thanks for the replies folks.
I looked at the video but it assumes that samba is already installed and takes you from there.
I tried the synaptics manager but it only showed the samba-common package which is already installed and didn't have the samba package itself.
Where does synaptics look for packages and can I point it to the one I downloaded which is now on my desktop?
Regards,
Phil

---

### Post by vamsibethapudy on 2008-06-12
try ubuntu screencasts- [http://screencasts.ubuntu.com/node?page=2](http://screencasts.ubuntu.com/node?page=2)
i remember the video showing the installing samba.sorry if i am wrong.search for it .
synaptic does not show packages in your desktop.(i guess)
it just shows the packages in the repos listed in the software souces menu.
it also shows the packages installed from ur desktop.
isn't samba listed in the Add or Remove Packages list ?? check it.

---

### Post by PhilHodges on 2008-06-12
Thanks vamsibethapudy.
Looked at the video but it only starts at modifying stuff once samba is installed.
Whatever I try I just don't seem to be able to install it.
Samba doesn't appear in synaptic or add/remove.
"Install services" in file sharing doesn't work, neither does the apt-get install command. 
I seem to have hit a brick wall with no way around it.
Bummer.
If anyone out there knows of a different way please let me know before I go completely crazy.
Computers shouldn't be this way. Pass me the abacus please.
Regards,
Phil

---

### Post by philinux on 2008-06-12
Samba is in the Main repo so you should have that enabled I think by default. Check your software sources.

---

### Post by vamsibethapudy on 2008-06-12
I really dont know why you cant see samba in your repos.
Try to change the repos in software sources to some other server near you.
I guess it will work out.

---

### Post by PhilHodges on 2008-06-13
Would you believe it?!!?
Came in this morning, fired it all up, tried synaptic manager again and this time it found samba!!! (Don't tell me it's copying Windows ie. it doesn't work but it will after a re-boot.)
Didn't ask why, just went ahead and loaded it before it did a runner again.
I can share things now. Wonderful.
Thanks for all your replies folks.
Regards,
Phil

---

