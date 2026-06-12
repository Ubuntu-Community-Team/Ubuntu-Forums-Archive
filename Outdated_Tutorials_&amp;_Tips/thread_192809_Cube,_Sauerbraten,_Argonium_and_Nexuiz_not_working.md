---
title: "Cube, Sauerbraten, Argonium and Nexuiz not working in Dapper? Simple solutions..."
date: 2006-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by whatrucrazy on 2006-06-09
after upgrading to dapper form breezy i was annoyed to notice that on re-installing or dowloading almost none of my FPS games worked, these included Cube, Sauerbraten, Nexuiz and Argonium.
turns out that in my case the solutions were simple:

for the first three games the error message was (from memory) "SDL parachute deployed..." (or something). all that was required was to run apt-get and install libsdl-mixer1.2.

to do this type: sudo apt-get install libsdl-mixer1.2

[this may require adding this repository to your sources.list file first (at /etc/apt/sources.list - type: sudo gedit /etc/apt/sources.list then add the line below to the file)

deb [http://packages.filefind.net/](http://packages.filefind.net/) ubuntu-dapper dotnet p2p

then run apt-get update by typing: sudo apt-get update.
note: this may not be necesary, it wasn't running when i first updated and now i can't remember... just try it if the install doesn''t work.] 

and for Argonium the solution was even simpler. the error message was this:

*Added packfile ./data/pak0.pak (4 files) using /home/mukunda/.argonium/data/ for writing execing default.cfg couldn't exec config.cfg Console initialized. ------- sound initialization ------- sound sampling rate: 11025 ------------------------------------ ------- Loading refresh.so ------- LoadLibrary("./refresh.so") ref_gl version: GL 1.0 ./libGL.so: cannot open shared object file: No such file or directory ref_gl::R_Init() - could not load "libGL.so" CDAudio_Init: No CD in player. CD Audio Initialized ------- Loading runtimei386.so ------- ==== InitGame ==== ------- Server Initialization ------- 0 entities inhibited 0 teams with 0 entities ------------------------------------- ====== Argonium Initialized ====== 0.0.0.0:0: client_connect  ShellMap Segmentation fault*

the solution for me was to go to the folder you have saved Argonium in, go into the /data folder and open the default.cfg file for editing (type: sudo gedit   [wherever the argonium file is]/Argonium/data/default.cgf)

about 3/4 of the way down is a line that says: set gl_driver "libGL.so"
change the line to say: set gl_driver "libGL.so.1"

now it should all run.
open your terminal, type: cd /(wherever the argonium folder is)/argonium
then to start the game type: ./argonium
(this start process is the same for sauerbraten too, go to its folder and type: ./sauerbraten. Both cube and Nexuiz can be installed though, so desktop launchers can easily be created, or you can just type "cube" from anywhere in the terminal.) 

FPS fun it up! (and start running argonium servers!)

---

