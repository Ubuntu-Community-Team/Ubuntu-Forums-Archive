---
title: "Samba installed but no Samba Shares?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-10-12
Hello all,

I now have 2 Kubuntu PC's a Windows XP PC and my old notebook running Xubuntu on my home network. I still am very new at this Linux O.S. and networking.  When I first installed Kubuntu I was trying to transfer files from the Windows XP box. A friend of mine told me to load SAMBA, I did and it loaded under Network, Samba Shares and it let me see my complete Windows XP C: drive.  I transfered the needed files over to the Kubuntu box no problem.  I just installed Ubuntu Server edition as a Lamp and also included Samba with the install the same way I loaded the 2 Kubuntu systems. After installing I then loaded the Xubuntu desktop as the GUI on my old notebook.  Why is Samba Shares not showing up under the Xubuntu applications network folder? I looked in my Xubuntu Synaptic Package Manager and the Samba, Samba-Common and the Samba-doc are loaded.  On the Kubuntu systems I can see my Xubuntu notebook I know there is a connection.  I need the Xubuntu notebook to see my Windows XP system but can not find Samba shares?

Can someone please point me in the right direction. All help will be appreciated.

James in GA,USA

---

### Post by jemate18 on 2008-10-12
> **JKHinton CPBD said:**
> Hello all,

I now have 2 Kubuntu PC's a Windows XP PC and my old notebook running Xubuntu on my home network. I still am very new at this Linux O.S. and networking.  When I first installed Kubuntu I was trying to transfer files from the Windows XP box. A friend of mine told me to load SAMBA, I did and it loaded under Network, Samba Shares and it let me see my complete Windows XP C: drive.  I transfered the needed files over to the Kubuntu box no problem.  I just installed Ubuntu Server edition as a Lamp and also included Samba with the install the same way I loaded the 2 Kubuntu systems. After installing I then loaded the Xubuntu desktop as the GUI on my old notebook.  Why is Samba Shares not showing up under the Xubuntu applications network folder? I looked in my Xubuntu Synaptic Package Manager and the Samba, Samba-Common and the Samba-doc are loaded.  On the Kubuntu systems I can see my Xubuntu notebook I know there is a connection.  I need the Xubuntu notebook to see my Windows XP system but can not find Samba shares?

Can someone please point me in the right direction. All help will be appreciated.

James in GA,USA

type
```
dpkg --get-selections | grep samba

```

if there is an entry of samba, then it is installed

---

### Post by bodhi.zazen on 2008-10-12
For some reason samba shares do not always show up, ant there is often a bit of a delay between when you bring a server on line  to when it is visible on the network.

You may need to manually connect.

See also :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by JKHinton CPBD on 2008-10-17
Hello bodhi.zazen and Jemate18 sorry about being so long to get back with you Thank you both for your responses.  I am still having trouble with the Sambi shares.  I can reach the Xubuntu notebook from my Windows XP system and both of the Kubuntu systems but I can not see any of the systems from Xubuntu. Also when I try to write my web development files from XP to a folder on the xubuntu box I get a can not write permissions error. I have tried going to the xubuntu file manager going to the folder that I am trying to copy files to and clicking properties then permissions tab all the dialog boxes are greyed out how do I open these to the pull down selections to change to a read write file?

---

