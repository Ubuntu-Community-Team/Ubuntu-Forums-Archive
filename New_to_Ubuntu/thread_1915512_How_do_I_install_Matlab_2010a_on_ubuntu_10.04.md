---
title: "How do I install Matlab 2010a on ubuntu 10.04?"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by agentfortyseven on 2012-01-26
Hello everyone,
I recently got a unix version of matlab 2010a from a friend. Apparently there is nothing wrong with the matlab's .iso file. But I have no idea how to install it. Can anyone here please help me out. 
Thanks.

---

### Post by tkabir11 on 2012-01-26
Try following the steps [_HERE_]("http://kittipatkampa.wordpress.com/2012/01/13/install-matlab-r2010a-on-ubuntu-10-04/") and see if it works.

---

### Post by agentfortyseven on 2012-01-26
> **tkabir11 said:**
> Try following the steps [_HERE_]("http://kittipatkampa.wordpress.com/2012/01/13/install-matlab-r2010a-on-ubuntu-10-04/") and see if it works.

Hey thanks for the reply. I tried following the instructions from the link you gave. But after mounting the .iso and running 
sudo sh install I get the following reply
sh: Can't open install. What do I do now?
Thanks.

---

### Post by tkabir11 on 2012-01-27
> **agentfortyseven said:**
> Hey thanks for the reply. I tried following the instructions from the link you gave. But after mounting the .iso and running 
sudo sh install I get the following reply
sh: Can't open install. What do I do now?
Thanks.

Are you running sudo sh from the directory where the installation files are??

---

### Post by agentfortyseven on 2012-01-27
> **tkabir11 said:**
> Are you running sudo sh from the directory where the installation files are??

how do I do that? I just tried executing that command from the terminal. Am I wrong? The .iso file is in a folder in the home directory.

---

### Post by tkabir11 on 2012-01-27
> **agentfortyseven said:**
> how do I do that? I just tried executing that command from the terminal. Am I wrong? The .iso file is in a folder in the home directory.

Sorry- that guide is quite concise- should've explained a bit more. I haven't actually installed anything from iso files in Ubuntu yet- otherwise I couldve explained this all myself :p 
If you haven't done so- first you have to copy the installation files from the iso to somewhere in your home directory. After that, follow [THIS]("https://help.ubuntu.com/community/MATLAB/R2010a") guide which is much better at explaining what you actually need to do.
Let me know if you have any problems.

---

### Post by agentfortyseven on 2012-01-27
> **tkabir11 said:**
> Sorry- that guide is quite concise- should've explained a bit more. I haven't actually installed anything from iso files in Ubuntu yet- otherwise I couldve explained this all myself :p 
If you haven't done so- first you have to copy the installation files from the iso to somewhere in your home directory. After that, follow [THIS]("https://help.ubuntu.com/community/MATLAB/R2010a") guide which is much better at explaining what you actually need to do.
Let me know if you have any problems.

On the link that you've provided it says:
"The assumption is that MATLAB install files are in /media/MATHWORKS_R2010A".
Can you please tell me about this location "/media/MATHWORKS_R2010A."
And when I ran the following command "sudo sh "/media/MATHWORKS_R2010A/install" I got the following reply "sh: Can't open /media/MATHWORKS_R2010A/install" even though I mounted the .iso file.

---

### Post by cariboo on 2012-01-27
We don't support installing pirated software. Thread Closed.

---

