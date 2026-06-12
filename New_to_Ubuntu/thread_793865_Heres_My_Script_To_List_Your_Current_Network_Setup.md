---
title: "Heres My Script To List Your Current Network Setup &amp; Check Connectivity"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by nicedude on 2008-05-14
This is a simple script for English Ubuntu installs that will run a ifconfig, iwconfig, lists the current routing table & finally pings google & yahoo to test your network connection. It will send all the information from these commands to a file named "My Current Network Setup.txt" which will be created on your desktop. This script does not use any commands that require SUDO so you can run it even if you don't have admin rights. It only takes about 5 seconds or so for it to run and create the output file so give it that before trying to open the text file it makes. This cannot do anything to mess up your system so feel free to try it as there is zero risk in doing so :-)

This should come in handy for newbies to see what is going on with their network setup, as well as for experienced users to list the results of any changes they make quickly and with no effort.

To run this just go to its properties and make sure it is set to be executable and then either type its name in a command line or double clicking  on it then selecting run should work as well with Ubuntu ( it does for me anyway ). This also is a nice addition to your nautilus scripts directory.

For any who don't know I would recommend everyone using Ubuntu with Nautilus to install the Nautilus scripts addon. You can then add scripts to your nautilus directory located -> /home/"user name"/.gnome2/nautilus-scripts by default. Once you have some scripts in there you can use them with a right click and looking in the sub menu "scripts". I am finding this to be one of the best features of nautilus by far.

Thought since I took the time to make it for my use I would share with the community and post it here.

If you use another language ubuntu then you will need to change all the ~/Desktop references to what your desktop is called or just ~/ to send output to your home folder. you can do that in gedit by using the replace command and replace all ~/Desktop locations with what yours is called or ~/ (For your home folder), for English installed newcomers sending it right to the desktop seems like the logical location though.

---

