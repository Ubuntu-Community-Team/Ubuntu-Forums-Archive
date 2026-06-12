---
title: "Lubuntu vs LXDE sessions -- Gtkperf differences"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by haresear on 2011-10-02
Anyone know why there are such large differences in gtkperf results between a Lubuntu session and a LXDE session? Obviously something strange about the Lubuntu result for "GtkDrawingArea - Text" -- its 10x slower than all other tests. But even when that test is excluded the LXDE session is nearly 2x faster than the Lubuntu session. (Currently running the nvidia-173 driver on an Nvidia FX5200 video card, but the results were similar for the nouveau driver.)
```
Lubuntu Session:
GtkPerf 0.40 - Starting testing: Sun Oct  2 03:42:39 2011

GtkEntry - time:  0.18
GtkComboBox - time:  3.63
GtkComboBoxEntry - time:  1.49
GtkSpinButton - time:  0.45
GtkProgressBar - time:  1.45
GtkToggleButton - time:  2.08
GtkCheckButton - time:  1.73
GtkRadioButton - time:  3.67
GtkTextView - Add text - time:  1.98
GtkTextView - Scroll - time:  0.84
GtkDrawingArea - Lines - time:  1.08
GtkDrawingArea - Circles - time:  1.24
GtkDrawingArea - Text - time: 11.05
GtkDrawingArea - Pixbufs - time:  0.72
 --- 
Total time: 31.60

LXDE Session:
GtkPerf 0.40 - Starting testing: Sun Oct  2 03:57:33 2011

GtkEntry - time:  0.17
GtkComboBox - time:  2.86
GtkComboBoxEntry - time:  1.80
GtkSpinButton - time:  0.50
GtkProgressBar - time:  0.40
GtkToggleButton - time:  0.48
GtkCheckButton - time:  0.37
GtkRadioButton - time:  0.60
GtkTextView - Add text - time:  1.85
GtkTextView - Scroll - time:  0.72
GtkDrawingArea - Lines - time:  1.03
GtkDrawingArea - Circles - time:  1.23
GtkDrawingArea - Text - time:  0.79
GtkDrawingArea - Pixbufs - time:  0.27
 --- 
Total time: 13.09


```

---

### Post by lucazade on 2011-10-02
haven't tried lxde or lubuntu recently so don't know what are the differences.. anyway usually what affects gtkperf is the theming engine used (murrine, clearlooks..), composite manager (like metacity compositor in gnome, xcompmgr) and opengl window manager (like compiz, kwin...)

---

