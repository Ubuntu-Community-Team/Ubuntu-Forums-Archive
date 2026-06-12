---
title: "Installing OOo 3 in Ubuntu"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by SteelCore on 2008-10-13
Is there any problem in installing OOo 3 in 7.10 or 8.04 from the .deb installer downloaded form the OOo site?
What would happen to the 2.4 copy already installed within Ubuntu?

Thanks

---

### Post by HellNoire on 2008-10-13
2.4 should be overwritten, at least, that was the case for The Gimp via GetDeb

---

### Post by jamillikan on 2008-10-13
On Gutsy, I downloaded the deb.tar.gz for OpenOffice 3.0, specifically OOo_3.0.0rc4_20080930_LinuxIntel_install_en-US_deb.tar.gz and unpacked it.

Launch a terminal and cd into the above-mentioned folder.

cd DEBS [ENTER]

sudo dpkg -i *.deb [ENTER]

(Wait until it finishes)

cd desktop-integration [ENTER]

sudo dpkg -i *.deb [ENTER]


Close the terminal when finished.   The new Open Office 3.0 is installed.
I've experienced no issues so far with this RC.  Enjoy.

---

### Post by krul on 2008-10-13
> **jamillikan said:**
> On Gutsy, I downloaded the deb.tar.gz for OpenOffice 3.0, specifically OOo_3.0.0rc4_20080930_LinuxIntel_install_en-US_deb.tar.gz and unpacked it.

Launch a terminal and cd into the above-mentioned folder.

cd DEBS [ENTER]

sudo dpkg -i *.deb [ENTER]

(Wait until it finishes)

cd desktop-integration [ENTER]

sudo dpkg -i *.deb [ENTER]


Close the terminal when finished.   The new Open Office 3.0 is installed.
I've experienced no issues so far with this RC.  Enjoy.

This worked for me almost with the OO 3.0 Final version. For the last step I had first to remove some old OO 2.4 stuff (sudo apt-get remove openoffice.org-core).

---

### Post by OutOfReach on 2008-10-13
As far as I know, OOo 3 doesn't overwrite 2.4 (I could be wrong), because OOo 3 installs it self in /opt/

---

### Post by kneewax on 2008-10-14
> **krul said:**
> This worked for me almost with the OO 3.0 Final version. For the last step I had first to remove some old OO 2.4 stuff (sudo apt-get remove openoffice.org-core).

Thanks for this, the desktop-integration was giving me hassle - as soon as I did the remove of OOo2 core it was happy.  Fantastic.  Thanks.

---

### Post by Shippou on 2008-10-22
Hello...

I recently updated to OOo3.. But then it crashes when I open files.

Any suggestions?

---

