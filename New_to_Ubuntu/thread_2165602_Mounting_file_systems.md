---
title: "Mounting file systems"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-08-05
Hello Everyone
                       My computer automatically mounts hdd and usb sticks with no mounting commands input by me. I can plug in a usb stick anytime and it gets mounted. This is contrary to what I read in a few  books I have. Is this normal operationn for linux


Thanks

---

### Post by Tom 6 on 2013-08-05
Hi :)
'Normal' is a relative term.  Different systems are set up different ways.  

Mine (13.04) seems to automount things too.  I vaguely remember having to do all that myself so perhaps this is fairly new behaviour?  I like it though :)  Saves me a step :)  

When i plug in a Cd with music or movies on then i get a  pop-up box offering me choices of what i want to do with the device;  browse, play whatever.  For a blank cd the pop-up offers to open some Cd writer.  if i plug in a Usb-stick then it generally appears as a drive listed down the left hand side (both in the taskbar/launcher and in the side-panel of any file-browsers i have open.  

I'm fairly sure this is nothing to worry about.  it's usually easy enough to unmount.  

I have noticed that extra partitions on my hard-drives don't get automounted.  My Windows partition for example.  Again that is perfect for me.  

Have you tried looking in your fstab to see what is listed in there?  
sudo gedit /etc/fstab
I would back-up before messing around with that one though!
sudo cp /etc/fstab /etc/fstab-2013-08-05
(i tend to use the date in reverse order rather than just call it fstab-backup so that i know which backup was made when)

Regards from 
Tom :)

[edit] corrected soem tpyos

---

### Post by deadflowr on 2013-08-05
It's because Ubuntu includes the group "plugdev" in the first users list of groups.
This allows that user to mount without a need to enter root(sudo).

If you add a new "normal"(standard) user, they shouldn't belong to the plugdev group and will need extra privileges to mount.

---

### Post by emerson1979 on 2013-08-05
I think I found the answer. Some distros have an automount feature, which automatically mount a filesystem when detected.

---

### Post by Tom 6 on 2013-08-05
Hi :)
I think deadflwr deserves the kudos points for this.  His answer sounds perfect to me.  

Just to clarify, his answer is saying that it's only your main user that it happens for.  If you create extra users, such as for family or close friends, (or colleagues if you are doing this at work) then they wont find things auto-mount unless you edit their groups (which is a bit of an obscure thing to find how to do).  
Regards from 
Tom :)

---

### Post by emerson1979 on 2013-08-05
thanks that clarifies his reply

Thanks

---

### Post by deadflowr on 2013-08-05
If you look over this from AskUbuntu
[http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu-12-10](http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu-12-10)
It has a nice list of the default groups and what they are.(Look in the section 2a)

---

### Post by Tom 6 on 2013-08-06
Hi :)
I dunno the next bit.  Can questions be marked as solved?
Regards from 
Tom :)

---

### Post by Paqman on 2013-08-06
You should have a "solved" option in the Thread Tools at the top of the thread.

---

