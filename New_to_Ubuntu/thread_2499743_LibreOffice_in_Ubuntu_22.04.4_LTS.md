---
title: "LibreOffice in Ubuntu 22.04.4 LTS"
date: 2024-08-08
forum: New to Ubuntu
---

### Post by jbl85 on 2024-08-08
Still a beginner with Ubuntu, and one question I have is why can you not remove the ancient version of LibreOffice that comes with 22.04.4 LTS and install the latest and then maintain the latest version of the Office Suite?

I have removed LibreOffice via the Ubuntu Software App, then I install the latest version of LibreOffice by way of the following commands:

apt update
apt upgrade
apt install libreoffice

After a rather long process, the installation finishes.

Go to the "Show applications" widget in the lower left part of the screen, click on LibreOffice Writer, for example, and it is still at version 7.3.  What am I missing?

Thanks in advance.

---

### Post by deadflowr on 2024-08-08
That is the latest version for that version of Ubuntu.
Ubuntu freezes the versions for most packages at the Ubuntu release time.

If you want a newer version you'll need to either grab from LibreOffice or install it from flatpak, snap or a ppa.

---

