---
title: "Remastering Linux: Highly specialized distro creation"
date: 2008-07-30
forum: Programming Talk
---

### Post by Dukie91191 on 2008-07-30
I've tried to put this in the forum where it would fit best, if this is not it, I apologize.

Hi all, I have what may sound like a strange question.
I have built an script that will only run in Linux, however, it will be deployed in a Windows environment. I must use Linux because of the native driver support, among other things. Now, I had the idea of going about this by remastering a Live Linux CD, including all the things I would need. This would be a very specialized OS with only the bare essentials +support for Serial to USB, Minicom or a similar program, Expect/Tcl support. 
I will recap at this point. I need to create a Live CD that will run a script. This is all it needs to do. I also need the user to have no option to install or format their Hard Disk (accidents happen, this disk will be going to people with limited Computer Literacy) 
Is it possible to do this in Ubuntu? is there a way to have only this script run, not even a GUI boot? 
This whole idea is just in the planning phase, and I'm mainly looking for a good starting off point. If theres any information I've failed to include, let me know and I will provide it to the best of my ability.

Thanks in advance for your help, and thanks for this forum.

-Dukie

---

### Post by stevescripts on 2008-07-30
Dukie91191 -

see my website [http://www.stevescripts.com](http://www.stevescripts.com)  - click on the Starpacks link.

Many folks in the tcl community develop on linux and deploy on windows - my website
just scratches the surface.  It is not a big job to d/load and package up the necessary windows libs and executables into a starpack.

Again, feel free to e-mail me directly.

Steve

---

