---
title: "how to split partition in ubuntu?"
date: 2016-11-07
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2016-11-07
when i installing ubuntu first time by deleting windows, I created swap of 8GB because of 4GB RAM I use, and 75 GB for home. 

after the complete installation of ubuntu, 65GB is in use. 

so am thinking to split 30GB from the 65GB and to install another ubuntu for education purposes. ?

how can I perform it.

---

### Post by Quarkrad on 2016-11-07
When you say education, is this for you to 'play' with ubuntu and educate yourself on the inner workings?  If so - have you considered, instead of a new partition, installing Virtualbox and having a guest Ubuntu installation?  If things get messed up you can easily start again and again. (Have a ubuntu guest (call it the master install) and then 'clone' that install for testing/playing.  If it all goes horribly wrong just delete the cloned version and create another from the the master).

---

### Post by weirdygeekpsych on 2016-11-07
well, to learn ethical hacking :) so I thought to make dual boot ? any suggestions

---

### Post by ens-0 on 2016-11-07
Like Quarkrad said, it'd be easier and less risky to set up a virtual machine(VM) and use that 30G for its hard drive. On the VM you could install Ubuntu or one of the more security focused distros like Kali or Arch Linux.  
If 
you're dead set on setting up a new partition, you should first backup your data. Then, boot into a livecd and use gparted. This should be helpful [Link](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

---

### Post by ajgreeny on 2016-11-07
What do you mean by "ethical hacking"?

We frown on threads about hacking in most cases in this forum so thread closed for staff discussion.

---

