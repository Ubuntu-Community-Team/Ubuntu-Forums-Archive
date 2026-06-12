---
title: "Forget Wifi"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-08-18
How can  make I make Ubuntu completely forget the details of my WiFi conection.
When I boot through a live DVD and provide my wifi details, Ubuntu remembers it even after the installation is over.
I have installed Ubuntu on one of my friend's computer and I want Ubuntu not to 'carry' my wifi details to her, when I return the computer.

---

### Post by deadflowr on 2013-08-18
Look in the network icon for edit connections.
There should be a section for wireless and if you click on it a select-able entry should appear.
select it and delete.

This is per Unity, not sure about other variants.

---

### Post by 3dmatrix on 2013-08-18
> **deadflowr said:**
> Look in the network icon for edit connections.
There should be a section for wireless and if you click on it a select-able entry should appear.
select it and delete.

This is per Unity, not sure about other variants.

Well, honestly speaking i know that part. I wish to know if there is any way to make sure its just not there ?
After coming to know that the live dvd 'carries' the info to the installation it makes me a bit paranoid !
So wish to confirm if it has 'really' forgot the details.

---

### Post by kurt18947 on 2013-08-19
You installed from a live DVD to a hard drive?  If so, yes the network connection established for the install may carry over to the hard drive.  Unless the live DVD can be written to - and I don't think they can be - the live DVD cannot remember your network details.  The hard drive install can however.  AFAIK, like deadflowr says go to network connections and delete everything there.  That should do it.  If you connect other devices to your wireless network frequently, does your router support guest connections?  Many newer machines and DD-WRT do.  You could use a guest connection for 'foreign' machines then delete the guest connection info.

---

### Post by CaptainMark on 2013-08-19
Or just don't connect to the wireless whilst installing, A live cd won't remember anything from a previous session, only in the event that you boot up a live session, connect to the internet, and install from the disk (in that order all in the same session) will the network configuration be transferred to the hard drive

---

### Post by kurt18947 on 2013-08-19
> **CaptainMark said:**
> Or just don't connect to the wireless whilst installing, A live cd won't remember anything from a previous session, only in the event that you boot up a live session, connect to the internet, and install from the disk (in that order all in the same session) will the network configuration be transferred to the hard drive

Another good solution.  Wired connections have something to recommend them.

---

### Post by 3dmatrix on 2013-08-19
I know live session does not remembers anything. But when wifi is used in live session and it is installled on hdd in the same session then the wifi info is transferred to the hdd install. And that is exactly what i was talking about. I did not wish to remove the entire installation just for this little thing. I have deleted the wifi profile from the network connections but i remember i read some where that there is another better way to delete it (may be some where in the network config) but i could not locate the info now. Anyway, I have returned the comp to its user. Thanks all of you.

---

