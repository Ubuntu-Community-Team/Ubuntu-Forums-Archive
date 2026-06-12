---
title: "Intrepid T61 issues, suspend resume mouse help..."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by neurostu on 2008-11-07
I just installed Intrepid on my T61 and I'm really happy but there are a few problems.

I had to create a file: /etc/hal/fdi/policy/mouse-wheel.fdi
```

<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>

```

This worked great but when I suspend then resume the laptop the scroll doesn't kick in right away it takes a few minutes and sometimes doesn't come back at all...

---

