---
title: "Question on gdm / plymouth integration"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by website.reader3 on 2011-09-28
As of this morning, on my amd64 oneiric system, gdm cannot install due to conflicts with plymouth, specifically the mountall command which is depended upon by other commands, so plymouth effectively cannot be removed.

I have lost the gdm x-server effectively.

Yesterday an update removed gdm when it took place.

Also, the server_dists_oneiric_universe_binary-amd64_Packages index file has a broken hash sum, so using the traditional Software Updates also seems to be failing, while running under the lightdm X-windows server.

Any idea when this all might get fixed?  Or is this uniquely happening to my system as an anomaly?

---

### Post by garvinrick4 on 2011-09-28
You cannot remove "plymouth" it carry's a lot of essential packages with it when done.
If you do not want to see plymouth you can select not to see a splash screen in plymouth
themes by choosing I believe text theme and installing and update initramfs.
```
sudo apt-get install synaptic
```Now open and install plymouth-theme packages you want. 
then below.
```
sudo update-alternatives --config default.plymouth 
```Choose your theme by number then:
```
sudo update-initramfs -u
```Lightdm is now the choice in oneiric. On an upgrade that still has gdm you can reconfigure
to choose lightdm.
```
sudo dpkg-reconfigure lightdm
```To restart lightdm from tty
```
sudo /etc/init.d/lightdm restart
```Post the error when trying to update your system.

---

