---
title: "offline patch management for ubuntu 11.04"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by Pradeep Badiger on 2011-12-11
Hi guys,
I am having issues with the "offline patch management" for ubuntu 11.04 I tried downloading all the patches but i have got them in the ".tar.gz" format 
Is there any tool to work with the offline patch management....if any, It would be great if you can also give the procedure to install and run it




:confused:

Thanks and regards

Pradeep

---

### Post by editheraven on 2011-12-11
patches for what? Kernel? Packages?

---

### Post by Pradeep Badiger on 2011-12-12
> **editheraven said:**
> patches for what? Kernel? Packages?
   

Hi,

      Patches for all,(kernel  and packages). Mainly I am looking for ubuntu security notices installation in ubuntu 11.04 server by offline, meanse i need to download required security notices from [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn) and I need to upgrade manually using command.
      Reason is security reason we are not opening our server to public network also some other dependencies. It is great full ,if you approached my requirement.....

Thanks and regards,

Pradeep B.

---

### Post by mcduck on 2011-12-13
To use the patches you'd also need the source codes for all the packages. (And of course complier and all the relevant header files etc.) Which would require even more downloading and make things even more complicated if you don't want to keep the machine connected to Internet.

I'd recommend just downloading the security update packages instead of the pathces. You'll save yourself froma lot of extra work and trouble that way, as you can simply download and install the packages using package managemnt isnetad of having to downlaod the source codes and pathces, then patch the sources, complie and install them manually.

---

### Post by MartijnNL on 2011-12-13
You might want to look at the apt-offline package, this might be able to help you achieve your goals. This is available in the repositories (it is for 10.10 anyway, so I assume it is for 11.04 as well). I just ran into this today when searching in Synaptic for something else.

---

