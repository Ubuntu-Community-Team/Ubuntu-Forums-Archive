---
title: "My GNOME 3.28.2 Is Missing Monitor Brightness Control"
date: 2019-10-02
forum: New to Ubuntu
---

### Post by michael-bielesky on 2019-10-02
Dear All,

I recently installed Ubuntu 18.04 that came with GNOME 3.28.2 as the GUI. I have desktop PC with an AMD® Ryzen 5 2400g processor; graphics: AMD® Raven; 64-bit; 250 GB SSD. Weirdly there is no brightness control anywhere to be found neither in the Launcher nor in the Screen Display Settings. I'm currently controlling the brightness through the following command:

  $ xrandr --output "my-monitor-name" --brightness "number_from_0_to_1"

 From what I've seen there should be a slider control below the volume control in the Launcher. Ubuntu seems to be up to date and the Livepatch is ON. I would appreciate your help with this matter very much!

Sincerely,
Michael

---

### Post by deadflowr on 2019-10-02
External monitor?

---

### Post by michael-bielesky on 2019-10-03
Yes, an LG monitor connected via HDMI.

Mike

---

### Post by deadflowr on 2019-10-03
Yeah, external monitors rarely, if ever, get the brightness controls in System settings.
On non-laptops I've never seen them.
You might look at this
[https://launchpad.net/~apandada1/+archive/ubuntu/brightness-controller]("https://launchpad.net/~apandada1/+archive/ubuntu/brightness-controller")
Should still work.

---

### Post by Autodave on 2019-10-03
Your brightness control should be in the menu of the monitor.

---

### Post by michael-bielesky on 2019-10-03
Hi,

It's been so long since I'd worked  on a desktop PC that I found it weird not to be able to control brightness through the operating system. Deadflowr, thanks for the link I'm going to look into this!

Mike

---

### Post by Holger_Gehrke on 2019-10-04
Another tool that might be helpful is ddccontrol and it's GUI gddccontrol. It uses DDC/CI (Display Data Channel/Command Interface), a protocol that gives access to most of the controls in the OSD-menu of a display. While xrandr and tools based on it change the image that gets send to the display to control brightness, color balance and the like, ddccontrol actually changes the settings of the display.

Holger

---

### Post by michael-bielesky on 2019-10-05
Thanks Holger_Gehrke, I'll also look into this.

Mike

---

