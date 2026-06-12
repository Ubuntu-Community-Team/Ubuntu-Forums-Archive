---
title: "Uninstall COMODO?"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by shane.oneill65 on 2013-11-13
Hi guys, I just downloaded COMODO anti-virus but I want rid of it. I have Ubuntu 12.04. I tried searching for it to do a quick uninstall but linux doesnt seem to want to make my life easy for me. Can anyone walk me through exactly what to do to uninstall the program? The download looks like this "cav-linux 1.1.268025-1".
I am completely lost as to what to do so any help would be greatly appreciated, thanks :)

---

### Post by Frogs Hair on 2013-11-13
Hello and Welcome

You can remove the package from the software-center . I checked the Comodo site and they supply a  .deb package which would have been installed with the software-center unless you used another application or installed from another package type.

Open the software center and search for Comodo , select remove , and enter your password.  

Terminal: ```
sudo apt-get remove package-name 
```

---

