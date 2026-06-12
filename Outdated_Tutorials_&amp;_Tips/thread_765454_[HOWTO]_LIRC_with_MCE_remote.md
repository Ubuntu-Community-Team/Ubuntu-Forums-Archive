---
title: "[HOWTO] LIRC with MCE remote"
date: 2008-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by jpm493 on 2008-04-24
I had alot of trouble setting lirc up, and i figure someday another person will. This is what worked for me.

note my system:
Ubuntu 7.10 
Philips USB Media Center Edition Remote -shipped with my Dell Inspiron 530, 4/5/08

First off, connect your IR device 

1.  Goto lirc homepage <[http://www.lirc.org/]("http://www.lirc.org/")> and get the most recent version (as of 4/24/08, it is  lirc-0.8.2.tar.bz2)
2.  Extract files to Desktop
3.  In terminal: cd ~/Desktop/lirc*
4.  In terminal: ./setup.sh 
[INDENT]If given a note dialog not found, In terminal: sudo apt-get install dialog
a.)  Choose the appropriate remote from Driver Configuration
b.)  Choose Save Configuration and Run Configure
[/INDENT]
5.  Back in Terminal:  sudo make and then sudo make install
[INDENT]Lirc should now recognize that a remote is present.
Lets test this. In terminal: mode2 
Try pressing any button on the remote, the output should be a hex number
Note, irw does not function yet[/INDENT]
6.  Open Synaptic Package Manager and search for lirc.  Mark install.  Choose the appropriate remote
7.  Restart your computer
8.  Now lets test lirc again.  In terminal: irw
[INDENT]Note, output may be 'Connection Refused'.  In this case
a.)  In terminal:  cd /dev
b.)  In terminal:  sudo lircd restart
c.)  Try irw again
The output should show recognition of the signal transmitted, the correct button pushed, the duration the button was held, and the remote used[/INDENT]
9.  Lirc should now be setup.  However, to my knowledge, programs will not accept remote control commands until the ~/.lircrc file has been created.  

.lircrc is the control file that programs like vlc and mythtv use to translate the buttons lirc reads, to program control.

It has this syntax:
begin
prog = ...
remote = ...
button = ...
repeat = ...
delay = ...
config = ...
mode = ...
flags = ...
end

one example is:

begin
prog = vlc
button = play
config = key-play-pause
end

button corresponds to the name of the remote's button listed within lircd.conf
config corresponds to the program's control

i manually created a .lircrc for use in VLC. My setup is Ubuntu 7.10, Windows MCE remote.
Found here: [http://jpm493.googlepages.com/lircrc.txt](http://jpm493.googlepages.com/lircrc.txt)
if directly used, rename to .lircrc and move to ~/

vlc config commands can be found by running "vlc --help --advanced"



hope all this helps.  time to enjoy your movies and music...
:popcorn:

- j

---

