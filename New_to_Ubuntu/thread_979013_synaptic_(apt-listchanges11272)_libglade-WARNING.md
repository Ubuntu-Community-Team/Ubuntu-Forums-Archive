---
title: "synaptic (apt-listchanges:11272): libglade-WARNING **"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by ericrdrayer on 2008-11-11
I get this everytime i try to install anything from synaptic
the system seems to work well. 8.04 lts Kubuntu rt 64bit 
I believe that I have honked up the mysql install.
I am using blender 248... works well yafaray too.
I have an ati radeon 9000 (diablotek).
I looked but could not find related stuff.searched on apt, synaptic,and various key words that are below.
I installed fglrx-controlpanel
synaptic has it green(marked as installed )
I have been unable to find it.
I started all this inorder to be sure that I was taking advantage
of the diablotek.
I installed alien but its graphics are garbled.
it does not crash the OS.
there are a number of other games with 3d interfaces which behave similarly.

I would like to know what is causing this error in synaptic.
I would like to know if my card is fully utilized.
I would like know if there is a way to test the 3D acceleration.

Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
Parsing Found/Fixed information... Done

(apt-listchanges:11272): libglade-WARNING **: could not find glade file 'apt-listchanges/apt-listchanges.glade'
Selecting previously deselected package fglrx-control.
(Reading database ... 402075 files and directories currently installed.)
Unpacking fglrx-control (from .../fglrx-control_1%3a8-3+2.6.24.14-21.51_amd64.deb) ...
Selecting previously deselected package mesa-swx11-source.
Unpacking mesa-swx11-source (from .../mesa-swx11-source_7.0.3~rc2-1ubuntu3_all.deb) ...
Selecting previously deselected package mesademos.
Unpacking mesademos (from .../mesademos_6.2.1-1_all.deb) ...
Setting up mtop (0.6.6-1.2) ...
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
dpkg: error processing mtop (--configure):
 subprocess post-installation script returned error exit status 1
Setting up fglrx-control (1:8-3+2.6.24.14-21.51) ...
Setting up mesa-swx11-source (7.0.3~rc2-1ubuntu3) ...
Setting up mesademos (6.2.1-1) ...
Errors were encountered while processing:
 mtop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mtop (0.6.6-1.2) ...
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
dpkg: error processing mtop (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mtop

---

