---
title: "Using TCRC Tibetan Fonts In Ubuntu"
date: 2010-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by tenzinmonlam on 2010-05-10
This HOWTO is to help all the people who want to use the TCRC Tibetan fonts in Debian / Ubuntu based distro. I have tested this on Gnome (Ubuntu 9.10,10.4,10.10,11.04, Mint 9, 10, 11), XFCE (Xbuntu 9.10, 10.4), LXDE (Lubuntu 10.4,10.10,11.04 & Mint LXDE 9,10) and CrunchBang Linux 9.4, it works like charm.


Ubuntu (Gnome based systems) Steps:


1 - Download tcrc & other tibetan packages from the link below and extract it.

  Click here to download [http://goo.gl/CdyRb]("http://goo.gl/CdyRb")

Alternative download location: [http://goo.gl/9XyUf]("http://goo.gl/9XyUf")

2. Open a terminal, after that go to the directory where you have extracted the tcrclinux_vs6_modified zip file and run the script:

  - cd Download/tcrclinux_vs6_modified &#9166;
  
  - sh ubuntu_setup.sh &#9166;   


3. Last Step "Add TCRC Keyboard Layout".

  - Click On 
            > System
                    > Preferences
                                 > Keyboard 


  - Select the layout option on the Keyboard Preferences window.

[IMG]http://img36.imageshack.us/img36/3558/screenshotkeyboardprefe.png[/IMG]
  

  - Now click on the "Add" button, after that select Bhutan from the country field and click on add.


Now your system is ready use the TCRC Tibetan fonts. Please note that you will get a icon on the top panel indicating which typeface you are using. You just have to click on Keyboard Typeface Layout switcher to switch from English to TCRC Tibetan Layout.


###############################################################################################



Xubuntu (XFCE based systems) Steps:


1. Do the 1st and 2ed step.

2. Last Step "Add Keyboard Switching Applet & TCRC Keyboard Layout".

 - Right click on the top panel and click on "Add New Item". 
 - Search the "Keybaord   Layouts" and click on the add button.
 - Now, click on the add button, it will open the "Add Layouts" window. 
 - On the "Add Layouts" window, search / look for the "TCRC Bodyig".
 - Click on "TCRC Bodyig" and click on OK button. 
 - Close the Keybaord Layouts Window.
 

It is done, click on the Keyboard Switching Applet to change the keyboard layout and enjoy.


##############################################################################################

Lubuntu & Linux Mint 9-10 LXDE (LXDE Based system)

LXDE's keyboard layout switching tool doesn't seems to work, to solve this we only have to edit some files.

Linux Mint 9:

You need to add two lines in the /usr/lib/X11/xorg.conf.d/05-evdev.conf file to solve this issue on the Linux Mint 9.
 
1. Do the 1st and 2ed step.
2. Open and edit the 05-evdev.conf file by following the steps below:

- Press Alt+F2 & type: gksu leafpad /usr/lib/X11/xorg.conf.d/05-evdev.conf &#9166;
    
    Section "InputClass"
    Identifier "evdev keyboard catchall"
    MatchIsKeyboard "on"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    EndSection

to

    Section "InputClass"
    Identifier "evdev keyboard catchall"
    MatchIsKeyboard "on"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
[COLOR="Red"]    Option "XkbLayout" "us,bt"
    Option "XKbOptions" "grp:alt_shift_toggle"[/COLOR]
    EndSection

Reboot and you are done.

Linux Mint 10 LXDE:

On the Mint 10, you need to edit the autostart file.

1. Open and edit the autostart file by following the steps below:

- Press Alt+F2 & type: gksu leafpad /etc/xdg/lxsession/Mint/autostart

2. At the end of the autostart file, just paste line below and save it.

- @setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,bt

Now reboot and you shold be able to switch the keyboard lay out using the alt_shift or you can add keyboard layout switching tool by right click the bottom panel and adding the keyboard layout switching tool.. If you face any issue switching the layout, just reboot. It will fix by it self..


#######################################################################################

CrunchBang Linux Steps:


1. Do the 1st and 2ed step.

2. Edit the auto-start.sh file to add the TCRC Keyboard Layout.

  - Press Windows Button + Space bar
  - Click on Preferences > Openbox Config > Edit autostart.sh (Screenshot[4] )
  - At the end of the file, copy and paste the test below and make sure it is same as below: 

# Enable keyboard switching between us & tibetan keyboard layout
setxkbmap -option grp:switch,grp:alt_shift_toggle us,bt &
(sleep 10s && fbxkb) &

3. Close the autostart.sh file, logout and login back.

We are finished and you will get a keyboard layout switcher applet beside the network manager applet. You can click on that to switch from TCRC Tibetan Keyboard Layout to US Keyboard layout. As we have manually added the TCRC Tibetan Keyboard Layout, so there is no icon image and you will get [??] when ever you click on keyboard layout switcher applet to switch the layout.

To remedy that, you can add your own image. Browse to the /usr/share/fbxkb/images/ folder and paste any small png file. I use this [IMG]http://dl.dropbox.com/u/1523443/bt.png[/IMG]. All set on this solid distro.

---

### Post by bapoumba on 2010-05-11
Approved to T&T.

---

### Post by marstehr on 2011-05-29
Good news:
Within Ubuntu 11.04 the way through the terminal might not be necessary:
Download Tibetan from the Ubuntu Software Center. Then follow instructions by tenzinmonlam from Step 3 to the end:
(Click on 'System Settings' and the 'Control Center' window will open; there click 'Hardware'; then 'Keyboard'; there 'Layouts' click 'Add'; choose the country 'Bhutan' and 'TCRC Bodyig' should show up.)

Down News:
Unfortunately the installation through the Software Center does not always work for all letter combinations, in that case you need to follow the instructions above from tenzinmonlam.

---

### Post by tenzinmonlam on 2012-07-13
***Please use the link below for the updated post************

[http://buddhatux.blogspot.in/2012/07/use-tcrc-input-method-on-linux.html]("http://buddhatux.blogspot.in/2012/07/use-tcrc-input-method-on-linux.html")

---

