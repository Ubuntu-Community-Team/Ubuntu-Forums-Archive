---
title: "I can't get my LexMark z25 to print"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by gardengxc on 2012-03-18
I'm using ubuntu 11.10 with gnome clasic. I plugged in my printer. It installed the drivers and set it up automatically. But now when I try to print something nothing happens. I check in system setting/printers. The printer is unlocked and on but when I click print nothing is added to jobs. Even when I click print test page.

For more info the printer is USB.

Uninstalling and re installing son't work.

OK and now I setup my Brother-MFC-J825DW as a networked printer but it does the same thing. Further it says "IP Address localhost" even tho it's on 192.168.1.30

---

### Post by kurt18947 on 2012-03-18
I can't help with Lexmark but what does your Brother say when you right-click the printer icon then properties > settings.  There's a "Device URI:" line.  Contents of that line will vary but it defaults to usb:// something even if there's no USB cable present.  Click the 'change' button and it may offer alternatives.  I've had very good luck with using something like this entered manually.  In order for this to work I first assign static I.P. addresses to printers.  This may be a little archaic but it works reliably for me :smile:
[ATTACH]214520[/ATTACH]

---

### Post by gardengxc on 2012-03-18
Rightclick what printer icon?

OK I see what you mean now. I had to have unity up to get there.

Didn't do anything but when I try to print under unity I get the following error,

"There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

---

### Post by gardengxc on 2012-03-18
I note that it says text-only printer so I tryed to install the drivers.

```
gerry@gerry-desktop:~$ cd LEX
gerry@gerry-desktop:~/LEX$ sudo sh lexmarkz35-1.0-1.gz.sh
[sudo] password for *****: 
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 4213096598 3952909298
```

---

### Post by kurt18947 on 2012-03-18
> **gardengxc said:**
> Rightclick what printer icon?

OK I see what you mean now. I had to have unity up to get there

Didn't do anything but when I try to print under unity I get the following error,

"There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

"I had to have unity up to get there"
Not necessarily.  From Gnome-shell or Gnome-classic you can open a terminal and type this:
```
system-config-printer
```That will bring up the gnome 2 style printer configuration app.  If you want to put a launcher on the desktop to make this or any app available from the desktop, you can try this:
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```A window labeled 'Create Launcher' will open.  It's fairly straight forward from there.  Who *said *you can't put desktop launchers on gnome 3 desktops? :p.  The source where I found this said it was also necessary to add this:
```
sudo apt-get install --no-install-recommends gnome-panel
```I didn't do this but I also have gnome-session-fallback installed which likely installs gnome-panel.

---

