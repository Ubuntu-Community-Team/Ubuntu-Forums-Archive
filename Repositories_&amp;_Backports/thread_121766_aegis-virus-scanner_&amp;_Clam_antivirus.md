---
title: "aegis-virus-scanner &amp; Clam antivirus"
date: 2006-01-25
forum: Repositories &amp; Backports
---

### Post by STN on 2006-01-25
I installed aegis and clam virus scan. Installation was easy. But to run those virus scanner is a different story. Although I managed to run aegis-virus-scanner, I got this error message when i tried to update virus definition or something:
(gnome-terminal:8512): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:8512): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

I have no idea what happen. As for Clam Antivirus, I just don't have a clue on how to run the scanner.

Oh yea. One more thing. I stalled wpasupplicant as well. But it like i said, installation is one thing configuring is another. So i'd be so glad to hear about those issues coz most of the newbies got into the same problems.

---

### Post by public_void on 2006-01-26
Are you trying to run two scanners? If so why any? Viruses for Linux are very rare, I think there only been 40, most of those where created in a lab and never released. Viruses are platform specific so a Windows virus can't effect a Linux box much, if at all. IMO if you're using p2p software and sharing files will Windows, then get anti-virus software. Not to protect you, but so you don't pass infected files to Windows users. If you got the AV from the repositories, then remove them, its much easier if you don't have to worry about them at all.

---

### Post by hugo491 on 2006-02-28
I have used clam antivirus and aegis-virus-scanner, and from my personal experience, Clam AV is better. I know what you mean about Aegis not wanting to update (did you try running the program as root?). Also, running clam anti virus is easy since there is a GUI for it. Installing **clamtk** from the repositories gives you a graphical interface for use with clam AV. (if you do not see it in your menu after installation, run **clamtk** from a terminal window; only root can update so running **sudo clamtk** will solve that problem.) Clam anti-virus has detected about 12% more viruses than aegis in my experience. (I know there are few Linux viruses but I have tested clam and aegis by bombarding the system with viruses on a non-essential computer.) If you are looking into further protection, I suggest the **firestarter** firewall. Hope I was of some assistance!

---

