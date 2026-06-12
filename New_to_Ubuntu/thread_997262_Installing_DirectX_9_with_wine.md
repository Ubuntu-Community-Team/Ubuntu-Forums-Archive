---
title: "Installing DirectX 9 with wine"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Bauro on 2008-11-29
hi all..

I have searched the forum for a guide on how to install directX 9 with wine, but either im reading it wrong, or the post is outdated.. 

can any of you guys give me a detailed walkthrough please :)?

---

### Post by binbash on 2008-11-29
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

you can install via winetricks.

---

### Post by Bauro on 2008-11-29
i have installed cabextract and downloaded the "winetricks" from [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks). as the guide says. but then what? 

i have a file on my desktop but i dont know what to do with it.. nothing happens when i click it..

And the guide doesn't help from there.. i cant understand what it is he is writing.. (im foreign so i dont understand all english - especially in Linux-language :()

---

### Post by almahtar on 2008-11-29
Open a terminal (Applications->accessories->terminal) and type
```

cd Desktop
sh winetricks directx9

```

---

### Post by linuxguymarshall on 2008-11-29
I thought installing DX alongside Wine was bad.

---

### Post by Bauro on 2008-11-29
thanks for the help - both of you :)

---

### Post by Bauro on 2008-11-29
Ok i was a bit fast to close the thread before.. i still have a couple of questions. - i know its a bit complicated but here we go:

i want to play "Call of Juarez" on Steam, with wine >.<.. 

First question: is it even possible?
Second question: If so, then how?

I have:
Ubuntu 8.10
The newest wine
Winetricks (from the link i wrote in previous reply)
and i have DirectX 9 installed (Did the commands wroten above).

---

### Post by linuxguymarshall on 2008-11-29
First go download steam.  You can download the installer from their site or use PlayOnLinux to install it. Right click the installer.msi file if you downloaded it and open with Wine. Set it up and you are good to go

---

### Post by kamitsukai on 2008-11-29
Best bet is [PlayOnLinux]("http://www.playonlinux.com/en/")

---

### Post by Duck2006 on 2008-11-29
You may find what you want here.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)





Edit kamitsukai got there first.

---

### Post by Marshal0505 on 2008-11-29
> **Bauro said:**
> Ok i was a bit fast to close the thread before.. i still have a couple of questions. - i know its a bit complicated but here we go:

i want to play "Call of Juarez" on Steam, with wine >.<.. 

First question: is it even possible?
Second question: If so, then how?

I have:
Ubuntu 8.10
The newest wine
Winetricks (from the link i wrote in previous reply)
and i have DirectX 9 installed (Did the commands wroten above).

If you need to know stuff about wine and app 'X' first go to their site and check the appDB. 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8280](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8280)

According to this link it runs but there are problems.

---

### Post by Bauro on 2008-11-30
I get this error when launching call of juarez from steam:

Failed to initialize rendering service. Check if your graphic card supports DirectX 9.0c.


I have DirectX 9.0c installed and my graphic card is 7600 Nvidia.

---

### Post by Doctor Drive on 2010-02-16
I've installed DirectX9 using winetricks, looks like everything's fine

log:
```

doctor@Doctor:~/apps$ ./winetricks d3dx9
Extracting cabinet: /home/doctor/.winetrickscache/directx_aug2009_redist.exe
  extracting /home/doctor/.wine/drive_c/winetrickstmp/apr2005_d3dx9_25_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/apr2006_d3dx9_30_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/apr2007_d3dx9_33_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/aug2005_d3dx9_27_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/aug2007_d3dx9_35_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/aug2008_d3dx9_39_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/aug2009_d3dx9_42_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/dec2005_d3dx9_28_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/dec2006_d3dx9_32_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/feb2005_d3dx9_24_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/feb2006_d3dx9_29_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/jun2005_d3dx9_26_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/jun2007_d3dx9_34_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/jun2008_d3dx9_38_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/mar2008_d3dx9_37_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/mar2009_d3dx9_41_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/nov2007_d3dx9_36_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/nov2008_d3dx9_40_x86.cab
  extracting /home/doctor/.wine/drive_c/winetrickstmp/oct2006_d3dx9_31_x86.cab

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/apr2005_d3dx9_25_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/apr2005_d3dx9_25_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_25.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/apr2006_d3dx9_30_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/apr2006_d3dx9_30_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_30.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/apr2007_d3dx9_33_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/apr2007_d3dx9_33_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_33.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/aug2005_d3dx9_27_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/aug2005_d3dx9_27_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_27.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/aug2007_d3dx9_35_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/aug2007_d3dx9_35_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_35.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/aug2008_d3dx9_39_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/aug2008_d3dx9_39_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_39.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/aug2009_d3dx9_42_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/aug2009_d3dx9_42_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_42.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/dec2005_d3dx9_28_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/dec2005_d3dx9_28_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_28.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/dec2006_d3dx9_32_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/dec2006_d3dx9_32_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_32.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/feb2005_d3dx9_24_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/feb2005_d3dx9_24_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_24.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/feb2006_d3dx9_29_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/feb2006_d3dx9_29_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_29.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/jun2005_d3dx9_26_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/jun2005_d3dx9_26_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_26.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/jun2007_d3dx9_34_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/jun2007_d3dx9_34_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_34.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/jun2008_d3dx9_38_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/jun2008_d3dx9_38_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_38.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/mar2008_d3dx9_37_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/mar2008_d3dx9_37_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_37.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/mar2009_d3dx9_41_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/mar2009_d3dx9_41_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_41.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/nov2007_d3dx9_36_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/nov2007_d3dx9_36_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_36.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/nov2008_d3dx9_40_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/nov2008_d3dx9_40_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_40.dll

All done, no errors.
/home/doctor/.wine/drive_c/winetrickstmp/oct2006_d3dx9_31_x86.cab: WARNING; possible 5960 extra bytes at end of file.
Extracting cabinet: /home/doctor/.wine/drive_c/winetrickstmp/oct2006_d3dx9_31_x86.cab
  extracting /home/doctor/.wine/drive_c/windows/system32/d3dx9_31.dll

All done, no errors.
Using native override for following DLLs: d3dx9_24 d3dx9_25 d3dx9_26 d3dx9_27 d3dx9_28 d3dx9_29 d3dx9_30
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using native override for following DLLs: d3dx9_31 d3dx9_32 d3dx9_33 d3dx9_34 d3dx9_35 d3dx9_36 d3dx9_37
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using native override for following DLLs: d3dx9_38 d3dx9_39 d3dx9_40 d3dx9_41 d3dx9_42
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Install of d3dx9 done
winetricks done.

```


But dxdiag.exe wouldn't launch.
```

$ wine dxdiag.exe
$

```

---

