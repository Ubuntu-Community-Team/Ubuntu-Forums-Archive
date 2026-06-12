---
title: "Envyng"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-05-31
Why doesn't ENVYNG automatically install the driver for my ATI card?? What can I do before running ENVYNG to make it install the proper drivers as promised?

Each time after running Envy fglrxinfo give me MESA ans not ATI as vendor. Plus my resolution is all wrong and very difficult to get back. I must completely remove fglrx to return to my precious 1280x1024 resolution.

lspci -n | grep 0300:

01:00.0 0300: 1002:5e4b

lspci | grep VGA:

01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]

---

### Post by shifty_powers on 2008-05-31
does the restricted driver manager not work?

---

### Post by peakshysteria on 2008-05-31
It's actually much worse. The quality is to poor to watch video. So I had hoped to get EnvyNG to make it for me since a manual install still is too difficult for me to make it all the way through the howto. So from three options (The hardware manager, Manual install and Envy) I've only got ENVYNG as a good last way to make it. Only it doesn't work in my end at all.

---

### Post by peakshysteria on 2008-05-31
It's actually much worse. The quality is to poor to watch video. So I had hoped to get EnvyNG to make it for me since a manual install still is too difficult for me to make it all the way through the howto. So from three options (The hardware manager, [Manual install]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.5.29") and Envy) I've only got ENVYNG as a good last way to make it. Only it doesn't work in my end at all. Please advice pre-installation mesure so I can make EnvyNG solve this driver issue. Canyone one at least tell us why ENvy works for some and not for others?

---

