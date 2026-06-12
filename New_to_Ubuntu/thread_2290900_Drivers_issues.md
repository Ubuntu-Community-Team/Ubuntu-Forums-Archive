---
title: "Drivers issues"
date: 2015-08-16
forum: New to Ubuntu
---

### Post by sab7 on 2015-08-16
Hi all, I have burnt a Lubuntu 64bit CD and I launched the live version of this OS. The only problem I have with that is that I have issues installing the drivers of my printer and the drivers of my webcam.
My printer vendor (Brother) officially supports Linux by distributing a .gz archive and by giving instructions. When I move the installing archive to the desktop (/home/lubuntu/Desktop), I follow the instructions by writing "sudo gunzip etcetc.gz" but according to the terminal, there is no such file or directory. Is it because the Lubuntu version I'm running is Live?
Another problem is that my webcam (Logitech C170) is not recognized by the system. According to information the internet, it should be automatically recognized.
Thank you so much for the help :)

---

### Post by dino99 on 2015-08-16
with all the needed drivers (and mostly all packages) the first place to glance at is the 'ubuntu archive' where you might find everything you need. 
As ubuntu packaging have some tweaks, the third package source is never the first choice.

That said, install 'synaptic' then search'brother' you will get a list of brother drivers
If you have doubt about the choice to do, then use your browser to search about" ubuntu+hardware model+ driver" (adapt as you need); most of the time there is at least a thread explaining the stuff (wiki/howto/forum)

---

### Post by sab7 on 2015-08-16
Sorry, I forgot to write this other information.
I went on this page
[http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=dcp350c_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=dcp350c_all&os=128)
Under the title "Printer Drivers" there are 3 links:
- Driver Install Tool (it is an archive, and I can't install it because the terminal tell me that there is no such file or directory).
- LPR Printer Driver - deb package - I can't install it because it says "i386 wrong architecture". Why? I run the 64bit version of Lubuntu and a 32 bit driver doesn't work?
- CUPSwrapper Printer Driver - deb package - I can't install it due to the same reason above.

What if I burnt a 32bit CD of Lubuntu (I don't care about the limitation of the RAM).
Anyway, I am not an expert, I do not understand the 3 terms above. In your opinion, will the LPR and CUPS things let me print with my printer?
Thank you so much.

---

### Post by dino99 on 2015-08-16
follow the explainations of post #2 above
about 64/32 install , ubuntu have made the necessary setting (called multiarch) so no need to download from external source, nor burning ....

---

### Post by sab7 on 2015-08-16
I finally installed the drivers of my printer.
Now it can prints but it can't scan..

I finally installed the drivers of the webcam too.

---

