---
title: "Goodix Touch Screen X Y Axis Inversion and Incorrect Orientation"
date: 2024-11-08
forum: New to Ubuntu
---

### Post by joshua-newbould on 2024-11-08
I am using Ubuntu 24.04.1 LTS on a Mini-PC with a Goodix Capacitive Touchscreen. Upon first turning the machine on, the touch input was inverted (pressing the bottom-left would click the top-right and etc.) but I have semi-fixed it by disabling Wayland and using the XInput to invert the matrix. I was then able to highlight text in the terminal and click the app menu icon – but absolutely nothing else. I cannot scroll or do anything else using the touch screen. Also, it turns out the fix was temporary as it quickly reverted back to being inverted.

The second problem I have is the orientation of the display. The device has a gyroscope to detect orientation – which Ubuntu recognises and responds to – but it keeps flipping the orientation to 90° anticlockwise from what it actually should be.

---

