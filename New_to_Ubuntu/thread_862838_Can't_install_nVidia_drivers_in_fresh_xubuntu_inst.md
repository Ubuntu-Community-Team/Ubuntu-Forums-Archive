---
title: "Can't install nVidia drivers in fresh xubuntu install"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by tstack77 on 2008-07-17
I try to enable/download restricted drivers and get this:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

Is the site down or am I doing something wrong?

---

### Post by RomeReactor on 2008-07-17
Hi. Try reloading the package information in Synaptic, then try to install the driver again; otherwise, your system might be having difficulty connecting to that particular repository. You can change which repository to access: in Synaptic, go to 'Edit->Repositories' and on the first tab (Ubuntu Software) there's a dropdown menu labeled 'Download from'. Select 'Other', then press 'Select Best Server'. After that, reload the package information and try installing the driver again.

EDIT: The driver your system is looking for ends in **13-18.41_i386.deb**, but the current version is **13-19.45_i386.deb**, so it looks like you just need to update the package information. You can also get the package [here]("http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb"). Ubuntu has a [page for packages]("http://packages.ubuntu.com/") that is very useful.

---

