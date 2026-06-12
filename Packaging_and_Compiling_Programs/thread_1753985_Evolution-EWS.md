---
title: "Evolution-EWS"
date: 2011-05-09
forum: Packaging and Compiling Programs
---

### Post by turbozmike on 2011-05-09
Newbie disclaimer

Ive been trying to build the evolution-ews package on 11.04
I managed to get it setup using

git clone git://git.gnome.org/evolution-ews

The following packages were required.
sudo-atp-get install git checkinstall libedata-cal1.2-dev libecal1.2-dev libebackend1.2-dev libedataserverui1.2-dev libedataserver1.2-dev evolution-data-server-dev libgtk2.0-dev  libedata-book1.2-dev evolution-dev gnome-common  gtk-doc-tools libntrack-gobject-dev

I used checkinstall to install and create a deb file
I was pretty excited that I managed to actually get it to work at all but when I launch evolution via terminal I get:

 (evolution:4787): DEBUG: Loading Exchange EWS Plugin 


 Construct the listener
(evolution:4787): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'

(evolution:4787): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'
^CSegmentation fault
mike@mike-VirtualBox:~/Downloads/evo/evolution-ews$

---

### Post by compuguy1088 on 2011-05-11
I am very much interested in getting a deb of evolution-ews. This would allow me to actually use my BPOS exchange account with evolution! :guitar:

---

### Post by vbinsider on 2011-07-14
I managed to successfully compile and run evolution-ews under Natty. I checked the code out of the Git repository and configured with ```
./configure --prefix=/usr
```

After the compilation I installed the library with ```
sudo make install
```

At the next start Evolution presented another account type named "Exchange Web Services". I had to fiddle a bit with the EWS URLs because my Exchange account is a managed one, but after all my e-mails showed up.

But there are still some issues with evolution-ews: At least for me, only e-mail works. No calendar entries and no address book. Evolution reads the configured address books but fails to download the entries.

---

### Post by Chrysostomos on 2011-10-10
> **vbinsider said:**
> I managed to successfully compile and run evolution-ews under Natty. I checked the code out of the Git repository and configured with ```
./configure --prefix=/usr
```After the compilation I installed the library with ```
sudo make install
```At the next start Evolution presented another account type named "Exchange Web Services". I had to fiddle a bit with the EWS URLs because my Exchange account is a managed one, but after all my e-mails showed up.

But there are still some issues with evolution-ews: At least for me, only e-mail works. No calendar entries and no address book. Evolution reads the configured address books but fails to download the entries.
Is this still the case? If it does only email it is not useful for me.

---

