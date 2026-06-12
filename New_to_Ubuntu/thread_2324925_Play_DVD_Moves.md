---
title: "Play DVD Moves"
date: 2016-05-17
forum: New to Ubuntu
---

### Post by Norman_L_Bliss on 2016-05-17
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Calibri]How do I play DVD moves on Ubuntu 16.04 LTS [/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT]

---

### Post by oldos2er on 2016-05-17
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss)

---

### Post by rg-pigl on 2016-05-17
1/ Use synaptic to install "libdvd-pkg" from link above.  Then search synaptic to ensure all of the following are installed:  "libdvdcss2" , "libdvdnav4" , "libdvdread4" , "ubuntu-restricted-extras" , "regionset".  
2/ If the dvd still will not play, use regionset to set your region. Note: you need to insert a "readable" dvd into your drive, else regionset will not work. Search the net for the number for your region: eg USA is #1.
3/ The above work only for readable dvd. Not all dvd will be readable. In my case, original China dvd is not readable in Ubuntu 16.04, and so far I cannot find anyone to help me with a solution. FYI, a Macbook purchased in China, loaded with Chinese o/s and apps, will have no troubles to play an original China dvd. Thus the dvd problem is specific to Ubuntu, and should be addressed by Canonical.

---

