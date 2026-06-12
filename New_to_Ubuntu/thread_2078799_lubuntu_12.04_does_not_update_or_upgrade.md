---
title: "lubuntu 12.04 does not update or upgrade"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by ninos on 2012-10-31
impossible to update or upgrade

terminal message:

sudo do-release-upgrade -d

[sudo] password for emmanouil: 
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#941;&#955;&#949;&#947;&#967;&#959;&#962; &#947;&#953;&#945; &#957;&#941;&#945; &#941;&#954;&#948;&#959;&#963;&#951; &#964;&#959;&#965; Ubuntu
[=check for new version]
&#923;&#942;&#968;&#951;:1 &#933;&#960;&#959;&#947;&#961;&#945;&#966;&#942; &#949;&#961;&#947;&#945;&#955;&#949;&#943;&#959;&#965; &#945;&#957;&#945;&#946;&#940;&#952;&#956;&#953;&#963;&#951;&#962; [198 B]     
[= receive signature tool upgrade]                   
&#923;&#942;&#968;&#951;:2 &#917;&#961;&#947;&#945;&#955;&#949;&#943;&#959; &#945;&#957;&#945;&#946;&#940;&#952;&#956;&#953;&#963;&#951;&#962; [1200 kB]  
[receive 2 tool upgrade]                                       
&#934;&#972;&#961;&#964;&#969;&#963;&#951; 1200 kB &#963;&#949; 0s (0 B/s)                                                  
&#964;&#945;&#965;&#964;&#959;&#960;&#959;&#943;&#951;&#963;&#951; «quantal.tar.gz» &#941;&#957;&#945;&#957;&#964;&#953; «quantal.tar.gz.gpg» 
&#945;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; 'quantal.tar.gz'
[=decompress "quantal.tar.gz]

&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#955;&#945;&#957;&#952;&#940;&#957;&#959;&#965;&#963;&#945;&#962; &#956;&#957;&#942;&#956;&#951;&#962;   [=read swap memory]

&#904;&#955;&#949;&#947;&#967;&#959;&#962; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#954;&#941;&#964;&#969;&#957;
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; ntp (1:4.2.6.p3+dfsg-1ubuntu3.1) ...
* Starting NTP server ntpd                                                     *** glibc detected *** lockfile-create: free(): invalid next size (fast): 0x09341008 ***
*** glibc detected *** lockfile-create: malloc(): memory corruption (fast): 0x09341048 ***

---

### Post by marinara on 2012-10-31
looks like apt is crashing on the ntp package.   maybe someone can explain how to delete the package cache or something i donno

---

