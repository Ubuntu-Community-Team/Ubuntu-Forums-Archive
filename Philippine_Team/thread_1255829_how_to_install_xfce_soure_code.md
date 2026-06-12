---
title: "how to install xfce soure code"
date: 2009-09-01
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-09-01
Hello, paano po ba mag install ng xfce desktop sa ubuntu? (not xubuntu)...I have downloaded the xfce source code in [www.xfce.org:(](www.xfce.org:()

---

### Post by guitar_man on 2009-09-02
pwede mo to run sa terminal para mainstall mo yung xfce..pero galing yan sa repository


> sudo aptitude install xfce4

---

### Post by loell on 2009-09-02
parang mahaba-habang usapan yan, pero kung gusto mo talaga,

tingnan mo yung README or INSTALL.TXT na mga file sa base directory, for the most complete instruction.

---

### Post by Script Warlock on 2009-09-02
pero kung apt-get install xfce4 kasama na rin to ang desktop

---

### Post by guitar_man on 2009-09-02
xfce desktop naman ang kailangan nya e..

---

### Post by ache109 on 2009-09-02
PWEDE DIN DUN SA SYNAPTIC SEARCH MO NA LAN DUN UNg XFCE DUN TAPOS DOWNLOAD MO. gANUN UNg SA hARDY KO. (PAKI DISREgARD NA LANg UNg CAPITALIZATION..)

(sIRA NANAMAN UNg KEYBOARD KO KAINIS!)

---

### Post by Lila_IT_CMU on 2009-09-02
I have downloaded the source code but there is no readme file or ./configure file

---

### Post by ragadanga63 on 2009-09-03
Installing xfce from synaptic will install plain vanilla xfce.  Installing xubuntu-desktop will install Xubuntu desktop(xfce plus ubuntu goodies).

---

### Post by itagomo on 2010-04-09
Tol, diba pag-inextract mu yun tar file, puru folders lalabas. Gawin mu punta ka sa terminal, type mo sa bawat folder:
./configure && make && make install

E2 un list kung anung folder ang uunahin mu:
Build order
1. xfce4-dev-tools
2. libxfce4util
3. xfconf
4. libxfcegui4, libxfce4menu, libexo
5. xfce4-panel
6. thunar
7. xfce4-settings, xfce4-session, xfdesktop,
xfwm4, xfce-utils, xfce4-mixer, xfprint,
xfce4-appfinder

Ang aga ng reply ko, hEHe..

---

