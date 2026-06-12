---
title: "Netgear issue"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by rem1100 on 2011-11-05
I am just getting started with Ubuntu. Having issue getting Netgear WG311v3 wireless card to work with Ubuntu. Have found document that contains instructions on how to repair, downloaded what I need to to USB but I cannot figure out how or where to start a console. Feel like I am missing something simple.

---

### Post by dFlyer on 2011-11-05
If your using 11.10 a control alt t will start a terminal. You can click on the dash icon and type terminal and click on terminal or you can press control-alt F1 will also take you to a terminal which you will have to log in to with your user name and password.

---

### Post by rem1100 on 2011-11-05
Did that and terminal started, need to find document again and follow instructions.
Thanks for a quick reply, will post later if successful.
Jeff

---

### Post by rem1100 on 2011-11-05
OK I typed in lspci and recieved a list of controllers, the Marvell is on this list, typed in grep Marvell hit enter and curser moved to next line and nothing else. Do I need to have the live CD in the drive or does 11.10 (version I have installed) work differently than the version in the document?
Jeff

---

### Post by rem1100 on 2011-11-06
Have tried to install ndiswrapper off both startup disk and flash drive to try to get netgear WG311v3 to work. Will not install from either, install button is gray. Have also tried from terminal, only get error message. Ubuntu 11.10 installed earlier today.
Thanks in advance,
Jeff

---

### Post by cariboo on 2011-11-06
Have you check to see if your device is detected properly, and the proper driver installed? I see from your other thread, that you know how to open a terminal, so do so, and type the following command:

```
sudo lshw -C network
```

and paste the output in your next post.

To copy and paste text from a terminal, just highlight the text, then use the middle mouse button to paste the highlighted text. IF you are on a laptop, tho middle click, press both touchpad buttons at once. 

If either of the above methods don't work for you, the regular right-click context menu work too.

---

### Post by anewguy on 2011-11-06
I've got that adapter in use with 2 other desktops - same version, etc..  The simplest way to get it working:

If you can hard-wire a connection between your computer and a router:

- open software center
- put ndisgtk in the search string
- select and install it -> this will be default also install ndiswrapper common and ndiswrapper utilities so you don't have to install anything else
- close out from software center
- go to COMMON SECTION below

If you can't hard-wire a connection between your computer and a router:

- start Ubuntu normally
- put the installation CD in the drive -> just cancel when the message comes up about a software source being founr
- using the navigator (with Uiwnity, start at the "Home Folder" button), open the CD for browsing.
- navigate to the /pool/main/n/ndiswrapper folder
- double-click on the ndiswrapper-common to begin it's installation and wait for it to finish
- double-click on the ndiswrapper-utilities to begin it's installation and wait for it to finish
- navigate to the /pool/main/n/ndisgtk folder
- double-click on ndisgtk to begin it's installation and wait for it to finish
- this has installed ndiswrapper, it's utilities (required) and ndisgtk (the graphical interface)

COMMON SECTION
--------------

- copy the Windows XP .inf and .sys files for the driver to a folder.  These drivers can be downloaded directly from Netgear, should also be on the installation CD that came with the adapter, or if needed I could attach them here for you.

- click on the "Dash Home" (topmost button) on the Unity menu
- put windows in the search string
- select windows wireless drivers
- select add/new
- point it to your .inf file for your driver and ok it
- wait a few seconds and your wireless should start scanning.


Dave ;)

---

### Post by rem1100 on 2011-11-08
I got as far as adding the driver, when I click Install New Driver ( I assume that it means the same as add new) I can open the home file as far as The WG311v3_1_0.zip in the select inf file window, will not install a .zip file. I can open The previously mentioned file all the way to viewing the .inf and .sys files but I have found no way to select or install them. I believe I am missing something, just do not know what it is. The wireless adapter does function as I have set this machine up to dual boot and it functions properly in XP. Also was not able to get ndisgdk through a wired connection off internet (connection fine was on Ubuntu site through it) but was able to download that and ndiswrapper from CD. Appreciate all the help I have recieved so far. 
Jeff

---

### Post by anewguy on 2011-11-08
The file with the drivers is a "zip" file - it is a compressed file of an entire folder tree.  In order to use files from it they must be extracted first.  Follow the below and it will hopefully get you there:


When you "open" the zip file, you are opening it in the archive manager - see screen 1.

If you double-click on the folder shown you will now get 2 folders to choose from - see screen 2.

Now double-click on the Drivers folder and you will be shown 4 folders.  See screen 3. 

Now double-click on the Windows XP folder.  You will see 4 files - see screen 4.

Highlight all 4 files shown, then click on Extract.  On the window that opens, click on Desktop in the left pane, then click Extract.  This will put those 4 files on your desktop.

Now open Windows Wireless Drivers again, select new/add (whatever the verbage is) and point it to the .inf file on your desktop and click the ok/yes/accept (whatever the verbage is).  This should install the driver.

Dave ;)

---

### Post by rem1100 on 2011-11-09
With your help I am 1 step closer. Got .imf file installed. Was able to get Google search page to come up but clicking on any of the Ubuntu search links or typing in a search yeilded a internet connection error message. The LED light on the Netgear card is flashing also. Rebooted to make sure that XP connected, it did. Rebooted again back to Ubuntu but could not get the search page to come up or the LED light on Netgear to come on until I uninstalled then reinstalled the .inf file for the driver. Noticed immediately after installing file the LED light is on solid for a few seconds then starts flashing. Can connect through the router with a wired connection using Ubuntu/Firefox. At this point I believe I have an issue with the firewall in the router as XP uses Internet Explorer and Ubuntu uses Firefox. Will attempt to remedy later today, ran out of time last night.
Jeff

---

### Post by rem1100 on 2011-11-09
IT WORKS!!!!  The last issue that needed to be addressed was that I had to go to system settings and pick out our wireless network, firewall in router not the problem. Thanks to all who helped me with this especially you Dave.  Your experience with this particular issue and willingness to walk me through this was invaluable.
Thanks again
Jeff

---

### Post by anewguy on 2011-11-10
Hey, you're welcome!  The whole idea of this forum is just to help people.  Now that you've seen how to solve your problem, if you see it come up again from another user, you too will be able to play it forward!

Dave ;)

---

