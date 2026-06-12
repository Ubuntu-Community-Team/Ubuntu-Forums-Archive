---
title: "Migrate hotplug script"
date: 2006-01-05
forum: Programming Talk
---

### Post by vhaarr on 2006-01-05
With the recent changes in Dapper moving away from hotplug to a pure udev system, my hotplug usb camera script stopped working (naturally), and I'm at loss what to do.

The script was runned by hotplug when I inserted my camera, and has special env variables available, like $DEVICE.

How can I make this script work without hotplug? Can udev, HAL, or something else do it for me?

I've attached the usbcam script, which was invoked by the rules in usbcam.usermap when the camera was inserted.

Thanks.

---

