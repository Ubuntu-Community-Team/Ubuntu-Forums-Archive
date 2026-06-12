---
title: "Need help installing printer driver tar.gz"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by freedomispopular on 2012-02-07
I'm trying to install the drivers for my printer, located [here]("http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux"). First of all, which, file should I be downloading. Second, what terminal commands should I be using. I've tried all three printer driver tar.gz's, and I've searched all over and it seems like installing from tar.gz's SHOULD be simple, but nothing is working. I've tried ./configure, make, and autogen.sh, and all of them give me errors. Am I doing something wrong, or are these not even compatible with 11.10?

---

### Post by Linux Dutchman on 2012-02-07
I see you want to try to install a Conan printer driver. Check here and especially at the bottom. There you see how to add a PPA to your Software sources which add a repositorie for Canon drivers: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers)

---

### Post by HiImTye on 2012-02-07
from that page you linked, choose the ones 'for debian' and then all you need to do is double click them and they will open in the software center and do the rest for you

..or you can use the ppa in that other link

one thing to keep in mind is that you need to use scangear (through GIMP) to scan rather than the scanning software that comes with Ubuntu

---

