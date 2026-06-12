---
title: "instal OpenFOAM"
date: 2013-12-03
forum: New to Ubuntu
---

### Post by paumaryu on 2013-12-03
[SOLVED]
Hi,
I am trying to instal OpenFOAM 2.0.1. in Ubuntu 12.04 but it seems impossible. When I write in the terminal:

sudo apt-get install openfoam201

it doesn't work, it tells me:

E: Unable to locate package openfoam201

Anybody can help me? I don't know what is wrong. I attach the screenshot of the terminal.
Thanks you so much.

---

### Post by jdeca57 on 2013-12-03
What's wrong with the suggestion on their site? [http://www.openfoam.org/download/ubuntu.php](http://www.openfoam.org/download/ubuntu.php)

---

### Post by Dennis N on 2013-12-03
You could download the two .deb files directly without adding a repository. On the download page, look where is says:

> The .deb files for different versions of Ubuntu supplied can be downloaded directly from the following locations:

Just select the lines that fits your version of Ubuntu and paste into the address window of Firefox to download.

After downloading, install the .deb files with gdebi package installer.

---

### Post by paumaryu on 2013-12-03
ok, thanks!
i was trying to install an old version and that's not possible.

---

