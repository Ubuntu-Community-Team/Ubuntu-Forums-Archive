---
title: "[SOLVED] Dell D600 and Touchpad"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by MrWES on 2008-11-21
I need some pointers on how to calibrate my touchpad on a Dell D600. I'm running Ibex 8.10 and I have to make several swipes just to get across the screen. Is there some additional settings I can add to xconf.org to correct this?

Thanks,
Bill

---

### Post by MrWES on 2008-11-21
> **MrWES said:**
> I need some pointers on how to calibrate my touchpad on a Dell D600. I'm running Ibex 8.10 and I have to make several swipes just to get across the screen. Is there some additional settings I can add to xconf.org to correct this?

Thanks,
Bill


I did some research and I ended up editing the following file:

```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

And entering the following:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.LeftEdge" type="string">120</merge>
   <merge key="input.x11_options.RightEdge" type="string">830</merge>
   <merge key="input.x11_options.TopEdge" type="string">120</merge>
   <merge key="input.x11_options.BottomEdge" type="string">650</merge>
   <merge key="input.x11_options.FingerLow" type="string">14</merge>
   <merge key="input.x11_options.FingerHigh" type="string">15</merge>
   <merge key="input.x11_options.MaxTapTime" type="string">180</merge>
   <merge key="input.x11_options.MaxTapMove" type="string">110</merge>
   <merge key="input.x11_options.ClickTime" type="string">0</merge>
   <merge key="input.x11_options.EmulateMidButtonTime" type="string">75</merge>
   <merge key="input.x11_options.VertScrollDelta" type="string">10</merge>
   <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
   <merge key="input.x11_options.MinSpeed" type="string">0.45</merge>
   <merge key="input.x11_options.MaxSpeed" type="string">0.95</merge>
   <merge key="input.x11_options.AccelFactor" type="string">0.06</merge>
   <merge key="input.x11_options.EdgeMotionMinSpeed" type="string">200</merge>
   <merge key="input.x11_options.EdgeMotionMaxSpeed" type="string">200</merge>
   <merge key="input.x11_options.UpDownScrolling" type="string">1</merge>
   <merge key="input.x11_options.CircularScrolling" type="string">0</merge>
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
  </match>
 </device>
</deviceinfo>
```

Save and reboot. Man what a difference! I can now navigate from side to side on the screen without lifting a finger. Very nice.

Bill

---

