---
title: "show desktop button problems"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by hey_ram on 2008-10-18
hi!

i am facing some problems with my show desktop button.

when i press the button, all the open windows are minimised and the desktop shows up. however, on pressing the same button again, the applications that have been minimised just disappear!!!

and i cannot find them on any of the other workspaces...

i tried to run the following command:

ps aux | grep firefox 

and the output i get to the command is as follows:

 ps aux | grep firefox
xyz    4839  0.0  0.1   3004   752 pts/0    R+   11:49   0:00 grep firefox
xyz    7460  0.6 26.9 277884 136480 ?       Sl   Oct14  38:05 /usr/lib/firefox-3.0.3/firefox --sm-client-id 117f000101000122397581600000073130009 --screen 0

what does the above mean??

PS: i do not know if this is of any help but i had tried to install and run PekWm recently. i then deleted it and cleaned up the system using the following commands:

sudo dpkg -r pekwm
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean...

also, when i try to run firefox again, it just runs with a fresh set of windows, and not the windows i had opened earlier. 

please tell me if there is a way to solve this problem...
there were a lot of windows that were open in firefox and i would hate to lose them all!!!:(

---

### Post by hey_ram on 2008-10-18
hi!

i solved the problem...
just restarted the system..

but i would still like to know what went wrong..
maybe the sessions manager just gave up after i had uninstalled pekwm??

awaiting answers.:)

---

