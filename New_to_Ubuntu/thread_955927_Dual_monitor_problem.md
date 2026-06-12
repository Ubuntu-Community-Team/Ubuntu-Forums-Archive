---
title: "Dual monitor problem"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by jon555 on 2008-10-22
Under screen resolution clone is unchecked, but in reality second monitor shows the same as first. I can change settings, monitor placement, but after saving and closing nothing happens. When I open screen resolution again, it's like before changing.
2 monitors 19 & 17 inch
Radeon 9250 card - not recognized - shows as  radeon (fglrx)
driver ati - ATI mach8, 32, 64 ............
 HELP

---

### Post by robalcorn on 2008-10-22
Don't know if this will help. I use Nvidia not ati but have you downloaded the ati-catalyst from add/remove and run it as root to save the changes?

---

### Post by Blackdragon1400 on 2008-10-22
Also make sure when you run the resolution/settings manager that you run it with the "gksudo" command, so that it is allowed to save that changes to your Xorg file. See if that helps

I use Nvidia so i dont know the exact command for that program srry.

---

### Post by jon555 on 2008-10-22
Catalist doestnt work because my card is nor correctly recogized and it cant be because there is no driver any more. 7.10 had it ok but 8.4 lostit.
And what was comand to open screen resolution from comandline.

---

### Post by Blackdragon1400 on 2008-10-22
When I installed the driver for my card (Nvidia 9800gtx) it came with the Nvidia settings program, wich lets me change all of my settings like setting up the dual monitors. I belive the ATI driver should come with somthing like that too. 

You might be able to find it on the synaptic package manager. I tried to find it, but i had no luck

---

### Post by jon555 on 2008-10-22
Ati have not jet made  driver
btw what is console command for screen resolution

---

### Post by earthpigg on 2008-10-22
> **jon555 said:**
> Ati have not jet made  driver
btw what is console command for screen resolution

```
sudo gedit /etc/x11/xorg.conf
```

somewhere in there, i think. on a windows box at work atm so i can't confirm.

> after saving and closing nothing happens. When I open screen resolution again, it's like before changing.

you never really answered the other guy... you gotta run that as root. ie: cant start by clicking on the icon in the menu. 

to find out the command you need to run
-right click on the menu, click 'edit'.
-navigate to the menu icon, whatever it is... right click and look at what command that icon executes.
-run that with 'gksudo' in front.

now you should be able to actually save changes you make.

---

### Post by jon555 on 2008-10-22
sudo gedit /etc/x11/xorg.conf    shows blank page
I tried 
gksu gnome-display-properties
and
gksudo gnome-display-properties
but when I chane something in setting ir reality nothing happens.
I also tried to change gksu displayconfig-gtk settings, but option for big desktop is grey, can't set it.

in one other post was this 
If changing the clone screens checkbox in the gui for the screen resolution it will give
Code:

(gnome-display-properties:8379): display-properties-WARNING **: Creating revert dialog
and another wey similar post
Ok,

I have an ATI Radeon 9250 Pro with two 19" Samsung SyncMaster 940bw's attached (one VGA, one DVI).

After installing 8.04 both monitors were displaying in approx 1024x768 (cloned) and I wanted to get them both into their native res of 1440x900 and working as dual monitors (ie a 2880x900 desktop).
After much playing around with my xorg.conf I got the screens in the right res by using the radeon driver, the layout correct so that my main monitor is the DVI and the mouse moves from DVI to VGA via the left edge.
However the displays are still both displaying the same images, but with only one mouse cursor!!

Any help would be appreciated
So it's a wide problem, and no working solutions  for now.

My next video card certainly won't be ATI.

---

### Post by jon555 on 2008-10-23
This is still open - solution needed.

---

### Post by earthpigg on 2008-10-23
i made a noob mistake, and i apologize. 

```
sudo gedit /etc/X11/xorg.conf
```

capital letter "X".

---

### Post by markbuntu on 2008-10-23
The 9250 is no longer supported by ati, and neither is every other card before the 9500 series. This is because these cards are fully supported by the open source "radeon" and "ati" drivers.

Monitor configurations are a user preference so you need to save your session when you change them to make them persistent. You can edit your xorg.conf file for more global changes. There is a wiki around somewhere about doing that.

---

### Post by jon555 on 2008-10-24
Markubuntu - then why, when these cards are fully supported by the open source "radeon" and "ati" drivers my comp can't make ubuntu animations happen smoothly.  I really don't get it - all worked great on 7.10, but on 8.4 it doesn't.

---

### Post by jon555 on 2008-10-24
what line in xorg.conf is responsible for cloned / not cloned displays. I want wide horisontal desktop.

---

### Post by markbuntu on 2008-10-24
> **jon555 said:**
> Markubuntu - then why, when these cards are fully supported by the open source "radeon" and "ati" drivers my comp can't make ubuntu animations happen smoothly.  I really don't get it - all worked great on 7.10, but on 8.4 it doesn't.

It is most probable that the open source driver you are using is an older one. You can go to radeon.org to find the newer ones.

---

### Post by drtre on 2008-10-24
dont know if this helps but have u tried to enable it in 
System> Administration> Hardware Drivers ?

---

### Post by jon555 on 2008-10-24
At Ati - radeon is no newer driver
And under System> Administration> Hardware Drivers I see not a single driver.

---

