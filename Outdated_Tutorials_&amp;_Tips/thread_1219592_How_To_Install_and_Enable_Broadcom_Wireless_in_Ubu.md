---
title: "How To: Install and Enable Broadcom Wireless in Ubuntu Jaunty"
date: 2009-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Caytin on 2009-07-21
After a few days of playing around on the net I found a not too complicated way on installing and enabling the Broadcom Wireless Cards in Ubuntu Jaunty.  As I have already typed this is in its entirety on my blog I will post the link to my blog and copy/paste what the post says.

Link: [http://caytin.wordpress.com/2009/07/21/how-to-broadcom-wireless-in-ubuntu-jaunty-jackalope/](http://caytin.wordpress.com/2009/07/21/how-to-broadcom-wireless-in-ubuntu-jaunty-jackalope/)

You will need to do the restricted driver tutorial I have on my blog first:
[http://caytin.wordpress.com/2009/07/21/how-to-why-restricted-drivers-dont-show-up-on-a-fresh-install-of-ubuntu/](http://caytin.wordpress.com/2009/07/21/how-to-why-restricted-drivers-dont-show-up-on-a-fresh-install-of-ubuntu/)


I just posted a how to on getting restricted drivers to be seen in Jaunty, please read that first as the Broadcom Wireless Driver is a restricted driver.

How to install the driver:

Easy:

1.  Connect your computer to the intenet using the wired LAN connection.  I.E. Plug in you network cable to the computer in question to connect to the intenet.

2.  Go to System > Administration > Hardware Drivers.  Enter your password.

3.  If you see “Broadcom…. wireless driver”, select it and click activate near the bottom of the window.  It should be right above the close button.  It should activate the driver, and the circle next to the “Broadcom… wireless driver” should be green.

4.  Disconnect the wire connect from your computer.  (Unhook the network cable from the computer.)

5.  Right click on the wireless strength bars at the top left of your screen.  If you see a wireless network click on that, enter the passkey if necessary, and that is it.

BUT, if you don’t see a wireless network available and you know that there is one, we have a few more steps to take.

The Hard Way (If the Easy Way didn’t work):

1.  Do the steps in the Restricted Driver How To and The Easy Way.

2.  We need to install B43-fwcutter.  To do this we go to System > Administration > Synaptic Package Manager.  Enter your password.

3.  Go to Edit > Search, and search for fwcutter.  You should see b43-fwcutter in the Package window.

4.  Left click the box right before the name.  If it is grey, click mark for installation.  If it is green with a star, click mark for upgrade.  If it is green, do not click anything.

5.  Click Apply at the top of the window if you clicked mark for installation/upgrade.  Then follow the prompts to install/upgrade.  Close out of the Synaptic Package Manager.

6.  Go back to System > Administration > Hardware Drivers.  Enter your password if prompted.  You should now see the “Broadcom… wireless driver”.  Activate it.

7.  Right click the wireless signal strength icon to see if you see a wireless network.  If you do, congratulations you are finished.  If not, lets move on to the terminal.

8.  Open the terminal by going Applications > Accessories > Terminal.

9.  Type in:  sudo modprobe -r b43 b44 ssb wl ,and hit enter.

10. Type in:  sudo modprobe ieee80211_crypt_tkip ,and hit enter.

11.  Type in:  sudo modprobe wl ,and hit enter.

12.  Type in:  sudo modprobe b44  ,and hit enter.

13.  Type in:  sudo /etc/init.d/networking restart, and hit enter.

14.  Now right click the wireless signal strength icon and you should see a wireless network at this point.  Click on the network shown and connect.

This fix goes away when you restart because the wireless card deactivates itself.  You do not need to re-install the driver again, but you do need to at some code to rc.local file so that it reactivates on start up.

Code to Add to rc.local file:

1.  Go to terminal if you don’t still have it up and running from activating your wireless card.

2.  Type in:  gksudo gedit/etc/rc.local  or  sudo gedit/etc/rc.local

3.  That should open up a text editor with the file rc.local opened.  You should see some blue text with #’s in front of it and an exit 0.  You are going to add the following code to the file right before the “exit 0&#8243; at the end.

#Activate Broadcom Wireless Card

modprobe -r b43 b44 ssb wl
modprobe ieee80211_crypt_tkip
modprobe wl
modprobe b44
/etc/init.d/networking restart

Look familiar?  It should, it is the commands you just entered to activate it by hand in the terminal.  This file runs at start-up and will run the commands for you right after Ubuntu has finished loading.

4.  Click save and exit out of the program.

5.  Type exit in the terminal and hit enter.  This will exit out of the terminal.

Notes:

Sometimes it takes a few seconds to a minute for the rc.local file to run the commands, be patient.

If the Network Manager asks you for a passphrase after you entered the network’s passkey, make it easy on yourself, put the same password for that as your user login.

The info pages I got the basic information from are located at:

[http://tenthblog.com/ubuntu/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/](http://tenthblog.com/ubuntu/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/)

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

They are both for older versions and bcm43xx-fwcutter has been renamed to b43-fwcutter, hence why I made a new tutorial.

Hope this helps!

---

### Post by wily6 on 2009-09-11
past step 8 those commands in the terminal don't work

'FATAL: Module wl not found.'

been trying to get wireless foreverrrrrrrrrrr =[

---

