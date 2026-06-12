---
title: "unable to connect from Modem"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-09-04
up to last night everything went fine with my USB modem . now also its working fine with Ubuntu 11.04 . i have 11.10 in another partition . last night i shutdown fine . now if i am trying to connect it in Xubuntu 11.10 , it not connecting but connecting in 11.04 . it sounds no problem with the modem .

> i have checked the APN in 11.10
> re-created the connection for modem , but not worked 

i don't know how to resolve this issue . please help me to out of this . 

   thanks in advance .

---

### Post by richlyn9 on 2011-09-04
looks similar to [http://ubuntuforums.org/showthread.php?t=1838583](http://ubuntuforums.org/showthread.php?t=1838583)

---

### Post by vpharry on 2011-09-05
> **raja.genupula said:**
> up to last night everything went fine with my USB modem . now also its working fine with Ubuntu 11.04 . i have 11.10 in another partition . last night i shutdown fine . now if i am trying to connect it in Xubuntu 11.10 , it not connecting but connecting in 11.04 . it sounds no problem with the modem .

> i have checked the APN in 11.10
> re-created the connection for modem , but not worked 

i don't know how to resolve this issue . please help me to out of this . 

   thanks in advance .
Even I hav d same problem. Its a bug. Wait for it to be resolved. In the meanwhile you can use Gnome PPP for connecting to the internet

---

### Post by raja.genupula on 2011-09-05
> **richlyn9 said:**
> looks similar to [http://ubuntuforums.org/showthread.php?t=1838583](http://ubuntuforums.org/showthread.php?t=1838583)



the link you have given to me looking as have solution  for my issue . i am gonna try it when i get back to my room . thanks for pick up my thread . 

@vpharry thanks for pickup , yeah i am also thinking like that .

---

### Post by raja.genupula on 2011-09-05
well i had tried that link . i didnt get any thing . is there any other way to connect to internet .

---

### Post by raja.genupula on 2011-09-07
c'mon guys please , i need help .

---

### Post by cariboo on 2011-09-07
Did you remove network-manager_0.9.0-0ubuntu2, and install network-manager_0.9.0-0ubuntu1?

---

### Post by raja.genupula on 2011-09-08
i had look at the synaptic for the version you told me but i didnt get anything from there 

can you help me with this ?

---

### Post by lucazade on 2011-09-08
try to see if you have old network-manager packages in cache

```
ls /var/cache/apt/archives | grep network-manager

```

if found you can try to install them manually..
move these old nm packages to a clean folder and
sudo dpkg -i *.deb

---

### Post by raja.genupula on 2011-09-13
@lucazade,@cariboo907,@vpharry,@richlyn9

thank you very much 
i had solved my issue now . 
i did as you said @lucazade,@cariboo907 . thanks.

---

