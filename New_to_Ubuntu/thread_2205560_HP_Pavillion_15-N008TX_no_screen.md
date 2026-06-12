---
title: "HP Pavillion 15-N008TX no screen"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by carlmather2001 on 2014-02-14
I recently bought a new HP Pavillion notebook, model 15-N008TX. I had some trouble getting the system to read a usb stick for ubuntu OS, so I burned a disc and installed 13.10 on the notebook.
Now I get a message:
"System is running in low graphics mode.
Screen graphics card and input device settings could not be detected correctly. You will need to configure these."
going to the next screen gives me these options;
1. "Run in low graphics mode for one session." I tried this and get a message (standby for 1 minute while display restarts) but nothing happens, even after 30 minutes.

2. "Reconfigure graphics." this option gives me 2 further choices; "1. use default config", which doesn't do anything. and then "2. use backed up config.", which I don't have.

3. "trouble shoot error." which leads to 3 options; "1. review xserver log." which I did but can't make heads or tails of it, although no obvious/outstanding error flags. then  "2. review startup errors." which is blank, so I assume no errors. and "3. edit config file." which, upon selection, absolutely nothing happens.

4. "Exit to console login." which option just leaves a blank screen.

the graphics card is AMD Radeon 'HD dedicated graphics' and after searching I found its model: HD8670M.

At present I can't view any of these messages on the notebook screen, I can only see them on a second screen (TV).

How can I get Ubuntu to recognise this card, recofigure graphics, whatever? I'm not very computer literate, so simple please.

Thanks

---

### Post by entw on 2014-02-14
I think you have two ways: 1) upgrade to 14.04, 2) try to install fglrx 14.1 beta.

Also I have [some useful link]("https://help.ubuntu.com/community/RadeonDriver") for you, but the information here is a bit outdated since 14.04 release is near.

---

### Post by carlmather2001 on 2014-04-18
Well, I waited for 14.04 and have installed it. everything seemed to go well. However, on restart I get a blank screen with a cursor in the top left corner. Nothing happens at all. Tried reinstalling, and it runs through that fine, says its all ok and to restart, which then goes back to blank screen with non-blinking cursor. 
Tried running system from stick without install, no go. 
Ran disk check, all ok.

---

### Post by carlmather2001 on 2014-04-20
Have now tried 14.04 'standard' ie not the gnome version, and I get the initial problem and error messages noted in the start of this thread. So, I guess that means that upgrading/updating to 14.04 makes absolutely no difference at all.

---

### Post by carlmather2001 on 2014-04-23
Solved, sort of. Ubuntu gnome 14.04 will not work on this computer. Standard 14.04 will so long as I 'apt-get install fglrx' after initial 14.04 installation. However that means I have to put up with unity.

---

