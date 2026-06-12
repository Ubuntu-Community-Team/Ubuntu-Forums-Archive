---
title: "canon lbp2900 ubuntu 11.10 64-bit"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by krishnan t s k on 2011-12-23
hi all
i was unable to install my printer(canon lbp2900) in ubuntu 11.10 so i ran the wubi  installer in one of my computers to determine the cause.....wubi  installed the amd64 version of ubuntu 11.10 in my computer and i once  again followed the steps provided in   [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)  this time pausing and observing every little step..... after fiddling  around for 2 days, i seem to have made some progress..... i have been  able to add my printer and get the two numbers that i should get for the  ccpd status
however, the captstatusui shows the error message Check the Device Path of /etc/ccpd.conf and upon typing 
lsmod | grep usblp it outputs as follows
usblp                  18239  0
now it says in the link mentioned above that in case it outputs nothing,then we should load the module and restart ccpd
but in my case, there is an output..... i even tried changing the device uri by replacing ccp with parallel but with no success
what should i do now?
Answer needed desperately!!!!!!! 
thanks in advance :smile: :smile:

---

### Post by krishnan t s k on 2011-12-23
ok after several trials and reruns, i got my canon laserjet printer working i.e. it was able to print a test page successfully :D :D
this is now officially SOLVED :) :)

---

### Post by Elfy on 2011-12-23
Might be nice to post what you did to get it working for anyone searching for an answer. That is after all what you came here for :)

---

### Post by krishnan t s k on 2011-12-23
This is for 64-bit users ONLY
For all those poor souls struggling with canon laserjet installation problem, i may have something for you.... it worked for me but i cant guarantee that it will work for you too!!!! try it at your own risk and if something goes wrong, dont blame me
what i did was simple
first step follow ubuntu 11.10 install from the link [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)
in case you get error saying bad device uri you can take a look at this link [http://kgrz.posterous.com/canon-lbp2...-bit-installat](http://kgrz.posterous.com/canon-lbp2...-bit-installat)
in case during rpm conversion to deb you get a warning saying that scripts are not included, add --scripts at the end of

sudo alien *.rpm
note:follow steps till start printer driver service for now

the next step is adding the printer. Here i recommend the gui actions instead of the terminal.... 
the procedure to do so is given in the first link only
having done it, start the terminal and edit /etc/ccpd.conf....replace printer name LBP2900 with the CAPT printer that you added in the previous step
save and close the text file
next, restart the ccpd service and look at the ccpd status....you will probably see one number or no number at all... dont panic here
now follow the steps given in starting or stopping on usb add or remove....here too you will probably see only one number at the end....again dont panic
here you have to again edit /etc/ccpd.conf....this time, below the CAPT printer, ypu will see another printer with the name canon LBP2900
the device uri of the printer will be /dev/usblp0.... add a / after usb save and exit...
now restart the ccpd deamon and check the status.... you will see 2 numbers or (as in my case) 3 numbers
now go to printing, right click the CAPT printer choose properties and print the test page... it should now be successful

the next step is to restart the computer and check the ccpd status.... again it will display only one number.... fear not... just restart the ccpd deamon and voila!!! your printer is back running at its best :):)
users of oneiric should know that at each restart the ccpd deamon must also be restarted.... its a kernel bug which should hopefully be fixed in the next release
in case of any doubts or hiccups in the process, just post your problems....i'm still a novice but i'll see what i can do :):)
cheers and have a good day :)

---

