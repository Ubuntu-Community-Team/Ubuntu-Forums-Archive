---
title: "Panels disappeared, really gone!  11.04"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by raequin on 2011-10-11
This is regarding a fresh install of 11.04.  I deleted the bottom panel, and added some things to the top panel.  I changed some of the effects in CCSM.  I also swapped CapsLock and Ctrl.  So, I start up the computer one time and there are no panels.  I can't open Terminal because I cannot access the menus.  So I can't do what is recommended [here]("http://helpforlinux.blogspot.com/2009/08/restore-ubuntu-panels-back-to-their.html"):

> Open the Terminal. 

Once the Terminal window opens, enter the following command at the prompt:
gconftool --recursive-unset /apps/panel

Then enter the next command:
rm -rf ~/.gconf/apps/panel

And enter one more command:
pkill gnome-panel

Therefore I followed the instructions [here]("http://shibuvarkala.blogspot.com/2009/09/howto-recover-gnome-panel-disappeared.html"):

> Boot the system upto Login Window. Press Ctrl + Alt+F1

Now You will get a Text based login screen

login with your username and password

now you will get a $ prompt.

Type the following Command

$ rm -rf .gnome .gnome2 .gconf .gconfd

Now Press Ctrl + Alt+F7 

Well, I couldn't exactly follow the instructions since it's set to auto-login, so I just did Ctrl+Alt+F1 from my home screen or whatever it's called.  This failed to restore the panels.  Furthermore, it removed some things I want, such as the aforementioned CapsLock-Ctrl switch, and more importantly, the info for my wireless network.  I can't connect to my wireless network without being able to click on the networking icon that's usually on the panel.  Now I can't get online to download any packages, as is recommended [here]("http://atentia.wordpress.com/2008/07/26/gnome-panel-disappears-after-ubuntu-update/").

I did download the shell script (I guess) posted [here]("http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/").  You guessed it, that didn't help either.  Now I feel pretty stuck.  I'd appreciate any help on this.  Thanks.

---

### Post by raequin on 2011-10-11
* bump

I don't want to be obnoxious about bumping this, yet there's really nothing I can accomplish with my laptop until the panels are restored, so it's just non-productive time, computer-wise, until that happens.  Thanks!

** edit: Wow, bumping after just two hours . . . lame.

---

### Post by decoherence on 2011-10-11
For future reference, when one of these 'how to' things people post on their blogs tell you to 'rm -rf' use 'mv' instead.

For instance, rather than

rm -rf .gnome .gnome2 .gconf .gconfd

you could've used the mv command to rename each directory and got the same result. Don't trust anything posted on a blog -- modify the commands so they aren't destructive.

Now, on to your problem. I must note that I don't use Ubuntu anymore so I can't give you specifics, but basically you need to make a custom X session (here's something from the wiki -- no idea if it still applies in 11.04 -- if not maybe someone can update it [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession))

this custom session should run a window manager and a terminal emulator. For instance metacity (if that's still in 11.04) and xterm.

From here you can try and launch gnome-panel from the command line and see what the heck it is choking on.

---

### Post by westie457 on 2011-10-11
Try this.

Open a terminal Ctrl+Alt+T copy and paste this in ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```and hit enter.

---

### Post by raequin on 2011-10-11
> Open a terminal Ctrl+Alt+T copy and paste this in
Code:
gconftool --recursive-unset /apps/panel && killall gnome-panel
and hit enter.

Result:

```
gnome-panel: no process found
```

I'll look into the customxsession later.

---

### Post by Thewhistlingwind on 2011-10-11
You can also open a tty with control-alt-f[1-12]

You can get back with control-alt-f[your tty with an x client]

You can also try:

apt-get gnome-panels 

Which should download the package from the internet if it's missing.

---

### Post by raequin on 2011-10-11
> You can also try:

apt-get gnome-panels 

Since doing the "rm -rf . . . " that's mentioned above (something I found on a blog), my network settings are gone.  I don't know how to open the network manager without the icon that's on the panel.  What I'm saying is the laptop is not connected to the internet and I don't know how to get it back on.  Well, I guess I could carry it to the router and plug it in like a cave man.

---

### Post by raequin on 2011-10-11
Panels are back.  I had to plug in an ethernet cable to get online and then

```
sudo apt-get install gnome-panel
```

plus a restart did the trick.  When it was downloading and configuring gnome-panel, I noticed a lot to do with gwibber.  Do you think the original problem (that caused panels to disappear) was due to me removing gwibber and Evolution?  I did so because I do not use those programs.  Thanks.

---

### Post by rawrmonster on 2011-10-11
just a fyi in the future if you ever need to connect to wireless with out nm-applet up you can alt+f2 and type gnome-terminal. then for wep type "sudo iwconfig <interface> essid <essid of ap>" then "sudo iwconfig <interface> key <network key>" then finally "sudo dhcpcd <interface>" and for wpa and wpa2 "sudo iwconfig <interface> essid <essid of ap> channel 7" then "sudo wpa_supplicant -B -D<wireless driver> -i<interface> -c/etc/wpa_supplicant/wpa_supplicant.conf"

---

### Post by raequin on 2011-10-11
I will go ahead and mark this as solved, though I'd like to know the answer to my last question: "Do you think the original problem (that caused panels to disappear) was due to me removing gwibber and Evolution?"

---

