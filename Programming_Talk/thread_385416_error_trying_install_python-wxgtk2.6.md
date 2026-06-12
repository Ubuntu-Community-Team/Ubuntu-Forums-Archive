---
title: "error trying install python-wxgtk2.6"
date: 2007-03-15
forum: Programming Talk
---

### Post by PLIACHAS PASCHALIS on 2007-03-15
when i try to install python-wxgtk2.6 following the advise o this post:
[http://www.ubuntuforums.org/showthread.php?t=218001&highlight=wxpython](http://www.ubuntuforums.org/showthread.php?t=218001&highlight=wxpython)
i get an error telling me that errors became while prossecing the: gtk-engines-eazel
any advise?
Thanks anyway

---

### Post by Arby on 2007-03-16
We'll be able to help you better if you show us what the specific errors are. Can you run ```
sudo apt-get install package_name_here
``` in a terminal and post the output here so we can see what's happening.

---

### Post by PLIACHAS PASCHALIS on 2007-03-16
sudo apt-get install kiki python-wxglade

i get the following which is in Greek language:
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
Reading state information... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;             
&#964;&#959; kiki &#949;&#943;&#957;&#945;&#953; &#942;&#948;&#951; &#951; &#964;&#949;&#955;&#949;&#965;&#964;&#945;&#943;&#945; &#941;&#954;&#948;&#959;&#963;&#951;.
&#964;&#959; python-wxglade &#949;&#943;&#957;&#945;&#953; &#942;&#948;&#951; &#951; &#964;&#949;&#955;&#949;&#965;&#964;&#945;&#943;&#945; &#941;&#954;&#948;&#959;&#963;&#951;.
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#960;&#959;&#965; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#940;&#952;&#951;&#954;&#945;&#957; &#945;&#965;&#964;&#972;&#956;&#945;&#964;&#945; &#954;&#945;&#953; &#948;&#949;&#957; &#967;&#961;&#949;&#953;&#940;&#950;&#959;&#957;&#964;&#945;&#953; &#960;&#953;&#945;:
  libdc1394-13 libpostproc0d libdvbpsi4 libavformat0d libxosd2 libvlc0 vlc-nox
  libdvdnav4 libiso9660-4 libavcodec0d libtar libvcdinfo0
&#935;&#961;&#951;&#963;&#956;&#959;&#960;&#959;&#953;&#942;&#963;&#964;&#949; &#964;&#959; 'apt-get autoremove' &#947;&#953;&#945; &#957;&#945; &#964;&#945; &#945;&#960;&#959;&#956;&#945;&#954;&#961;&#973;&#957;&#949;&#964;&#949;
0 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 0 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 0 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
1 &#956;&#951; &#960;&#955;&#942;&#961;&#969;&#962; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945; &#942; &#945;&#966;&#945;&#953;&#961;&#941;&#952;&#951;&#954;&#945;&#957;.
&#935;&#961;&#949;&#953;&#940;&#950;&#949;&#964;&#945;&#953; &#957;&#945; &#956;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#969;&#952;&#959;&#973;&#957; 0B &#945;&#960;&#972; &#945;&#961;&#967;&#949;&#943;&#945;.
&#924;&#949;&#964;&#940; &#964;&#951;&#957; &#945;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#952;&#945; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#951;&#952;&#959;&#973;&#957; 0B &#967;&#974;&#961;&#959;&#965; &#945;&#960;&#972; &#964;&#959; &#948;&#943;&#963;&#954;&#959;.
[B]&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; gtk-engines-eazel (0.3-5.1) ...
dpkg (&#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945;): &#945;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#949;&#954;&#964;&#941;&#955;&#949;&#963;&#951; post-installation script: Exec format error
dpkg: &#963;&#966;&#940;&#955;&#956;&#945; &#963;&#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965; gtk-engines-eazel (--configure):
 &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; post-installation script &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 2
&#928;&#961;&#959;&#941;&#954;&#965;&#968;&#945;&#957; &#963;&#966;&#940;&#955;&#956;&#945;&#964;&#945; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965;:
 gtk-engines-eazel
E: Sub-process /usr/bin/dpkg returned an error code (1)
paschalis@paschalis-desktop:~$ [/B]

i 'll try to translate the bolded message
istalling gtk-engines-eazel (0.3-5.1) ...
dpkg (subroutine):unable to run post-installation script: Exec format error
dpkg: error processing gtk-engines-eazel (--configure):
 subroutine post-installation script returned situation error 2
errors become while prossesing:
 gtk-engines-eazel
E: Sub-process /usr/bin/dpkg returned an error code (1)
paschalis@paschalis-desktop:~$

---

### Post by Arby on 2007-03-16
OK, you've found a bug in the gtk-eazel package. Specifically, [this bug]("https://launchpad.net/ubuntu/+source/eazel-engine/+bug/68668"). What version of Ubuntu do you run, according to that bug report this has been fixed in Feisty?

So it would seem the solution to your problem is to upgrade to feisty, either now or when it is released in a few weeks (April sometime). The problem is actually caused by the package containing an empty file for an install script. Apparently, the solution was to remove this file from the package. Doing that manually would be a pain and I can't help you with it because I don't know how.

Sorry, there's not much else I can do. My last shot in the dark would be to see if you can get the source code for gtk-eazel from somewhere and compile it yourself but I'm not too confident about that.

---

### Post by PLIACHAS PASCHALIS on 2007-03-16
thanks for reply. my edubuntu is set to update automatically every time there is an update.

---

