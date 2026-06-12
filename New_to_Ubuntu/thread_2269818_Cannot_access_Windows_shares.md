---
title: "Cannot access Windows shares"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by herb5 on 2015-03-18
Hello everyone, I'm new, and lost. I've spent hours reading the forums and can't find the answer I'm looking for.
I can not connect to windows 7 machine, I can see it on the network folder, but cannot access any shared folders.
If this as been asked before, could someone please give a link to get there? I don't want to upset anyone or ask
to many questions. I've got everthing working on my Ubuntu machine but that. Thank you in advance.

---

### Post by Geoffrey_Arndt on 2015-03-18
Here is a youtube video showing the steps . . . both windows and ubuntu need a couple adjustments/tweaks to set this up.

Disclaimers:  the windows version used in video is 8.1, but the same steps should available in win7.   Also, I don't have a local network - my data is shared via a wireless network that has access to memory cards (SD) plugged into a wireless printer - and the default samba client already available in ubuntu will access whatever files I've added to the SD through a windows login, or if adding files via a ubuntu login (on any or all pc's in the wireless network).

ALso, another even simpler way to share files (not apps, files only) is through a service like dropbox or spideroak.   The same data is then available from all devices, including tablets, phones, etc.

[https://www.youtube.com/watch?v=7PzKzh5jsw8](https://www.youtube.com/watch?v=7PzKzh5jsw8)

---

### Post by v3.xx on 2015-03-18
> I don't want to ask to many questions.

Thats what we do here, look for answers to everything :D

I think your talking about samba.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=samba&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=samba&sa=Search&cof=FORID:9)

I do not use it myself, I have the cloud going on and for local access I just share a data partition.

---

### Post by herb5 on 2015-03-18
Thanks for the reply's. I have tried everything to get this to work. I give up. I'm tired. Thanks again.

---

### Post by sudodus on 2015-03-18
It might be easier to make an SSH server in Ubuntu, and then connect from Windows with for example Filezilla or WinSCP.

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

