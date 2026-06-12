---
title: "hmm sixth sense"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-09-16
guys actually morning i saw a thread with problem of mounting .
he is getting a error message while mounting that "unable to mount not authorized ", i google it and got nothing for that.

just now only i came back to my room and opened my box which have 11.10 in it . Now i am also getting the same error , no partition of mine mounting and all are with error message i mentioned above , i used my usb, for that also it slap me with same error . now i get back to 11.04 which is at another partition . is there any solution for it ? 

thanks in advance .

---

### Post by dino99 on 2011-09-16
fix is on the road :) with latest lightdm

---

### Post by sikander3786 on 2011-09-16
I don't have any such problem with Oneiric. Switch your download server to "Main" and try upgrading the packages.

---

### Post by raja.genupula on 2011-09-16
Hi Dino99 , thanks for quick reply .
so if i get latest lightdm , is it gonna be solve ?

---

### Post by raja.genupula on 2011-09-16
> **sikander3786 said:**
> I don't have any such problem with Oneiric. Switch your download server to "Main" and try upgrading the packages.

hey man ,thank  you very much , lemme try it .
i will let you know , what i got .

---

### Post by raja.genupula on 2011-09-16
hmm bad luck man , my server is already main . 
i think updates are not going to be a cause for this

---

### Post by sikander3786 on 2011-09-16
> **raja.genupula said:**
> hmm bad luck man , my server is already main . 
i think updates are not going to be a cause for this
What if you try mounting it from the Terminal?

```
sudo mkdir ~/Desktop/test
sudo mount /dev/sdXY ~/Desktop/test
```

Where 'sdXY' is your intended partition. You can find it by running this command:

```
sudo fdisk -l
```

---

### Post by professor76 on 2011-09-16
This issue got fixed by an updated of lightdm, If your current lightdm version is not 0.9.7 then you need to update. 

Another fix is that You can change the login manager to gdm by dpkg-reconfigure gdm  and it will work properly.

---

### Post by raja.genupula on 2011-09-16
> **sikander3786 said:**
> What if you try mounting it from the Terminal?

```
sudo mkdir ~/Desktop/test
sudo mount /dev/sdXY ~/Desktop/test
```

Where 'sdXY' is your intended partition. You can find it by running this command:

```
sudo fdisk -l
```
hi thanks for this , i like this alternative solution upto i am gonna fix it . this is showing again command are excellent are better than GUI .

---

### Post by raja.genupula on 2011-09-16
> **professor76 said:**
> This issue got fixed by an updated of lightdm, If your current lightdm version is not 0.9.7 then you need to update. 

Another fix is that You can change the login manager to gdm by dpkg-reconfigure gdm  and it will work properly.

hey man , thanks for this . 
i have checked mine and it is not 0.9.7 , so now cache update going on , i am looking for new version in that . 

mine was xubuntu not ubuntu , but i had given a try and got what i expected . it given that gdm not installed .

---

### Post by raja.genupula on 2011-09-16
HI PROFESSOR , thanks for your help man , now i did the update and got my system back to its previous state . 
but i have another issue with this update 


ok
this is a advanced answer for the users who are going to have this issue after doing update,  i had lost my grub guys ,along with lightdm latest version i had installed some more updates ,after that i made restart to apply changes, in the grub menu i do not have my 11.04  . but os-prober made me  sure that i have 11.04 .
then i had ran sudo update-grub and now everything seems fixed . 

thanks to professor76,sikander3786,dino99 for helping me on this issue . really thanks a lot guys .

---

