---
title: "trouble installing oracle 11g"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by viswanathan on 2008-10-15
well rather than following any of those tutorials i just unzipped the files to my home document and changed to database folder and  ran ./runinstaller well i get this error 

1 . OUI-10035:You dont have permission to write to the inventory location 
OR
2. OUI-10033 : THE inventory location /us01/app/orainventory set by the previous session is not valid do you want to create new inventory ? 

if i give yes and continues the next step it fails saying i dont have permissions any idea guys

---

### Post by Nepherte on 2008-10-15
you will have to run the installer with root privliges. Place sudo in front of the command:
```
sudo ./runinstaller
```

---

### Post by rosanbio on 2009-11-10
Atleast as of now oracle 11g is not compatible with Ubuntu:mad:, Hmm, i have seen some workarounds for Ubuntu 8;););) but not really sure will it work with 9.10[-X.
Best would be as Oracle Enterprise Linux available for free cheak it out with a virtual machine, if ur purpose is academics:popcorn:..

---

