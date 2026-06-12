---
title: "Does anyone have a good expreance with ies4linux"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-05-16
I need to use some websites that just don't work with normal browsers and find myself having to use a windows box to do that which is a pain. 

I've tried a number of different browsers FF, opera, konqueror and can't get past the login.

ies4linux starts up very slowly and gets stuck quicker than I can access the sites I need.

Help!

---

### Post by hyper_ch on 2008-05-16
normally it's enough to change the useragent to MSIE... have you tried that with FF?

---

### Post by niceguy123 on 2008-05-16
> **hyper_ch said:**
> normally it's enough to change the useragent to MSIE... have you tried that with FF?

Thanks for the quick response. Yes, I installed an agent switcher add on in FF yesterday, but saw no change.

---

### Post by hyper_ch on 2008-05-16
you don't just have to install it, you also have to use it then to change the useragent... did you do that also?

---

### Post by niceguy123 on 2008-05-16
> **hyper_ch said:**
> you don't just have to install it, you also have to use it then to change the useragent... did you do that also?

Yes, sorry that's what I meant. I installed it and changed useragent but still could use the sites.

---

### Post by hyper_ch on 2008-05-16
hmmm, then it might be that it requiers some .net stuff or so... not sure if you can do this in linux.... BUT you could use vmware/vbox to install a virtual windows with a native MSIE then... If you have more than 500 MB ram and (preferrably 1 GB ram, 1 Ghz + processor) then you could setup a win xp and run it in virtual mode and use MSIE there.

---

### Post by shifty_powers on 2008-05-16
the first few times i tried to use it, it was buggy and didn't work very well.

now though it works pretty damn well.

try using [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux) to install it ;)

---

### Post by niceguy123 on 2008-05-16
> **shifty_powers said:**
> the first few times i tried to use it, it was buggy and didn't work very well.

now though it works pretty damn well.

try using [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux) to install it ;)

Well what did you do to get over the buggyness? 

Thanks for the link. I when though all of that yesterday. If I do it again with out uninstalling wine and ies4linux, will it replace the current installation or what?

> hmmm, then it might be that it requiers some .net stuff or so... not sure if you can do this in linux.... BUT you could use vmware/vbox to install a virtual windows with a native MSIE then... If you have more than 500 MB ram and (preferrably 1 GB ram, 1 Ghz + processor) then you could setup a win xp and run it in virtual mode and use MSIE there.

This sounds like a lot for me, I don't know if I'd want to get into all of this adventure.

---

### Post by shifty_powers on 2008-05-16
tbh, i think it was after i had some updates. it just started working properly. had to uninstall and reinstall though.

heh, sorry that probably isn't a huge amount of help but it is true.

uninstall it, and delete the ./ies4linux folder from your home directory and then try to reinstall it.

---

### Post by niceguy123 on 2008-05-16
I uninstalled and install again. I'm not sure why it works so slow and gets stuck.I just tried again after restarting my computer and not running any other applications aside for ies4linux and it still gets stuck.

---

### Post by hyper_ch on 2008-05-16
then I'd recommend either using dualboot for those sites, or another computer with windows or install virtualbox or vmware to run a virtual windows on top of your ubuntu.

---

