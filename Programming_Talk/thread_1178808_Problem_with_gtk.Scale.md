---
title: "Problem with gtk.Scale"
date: 2009-06-04
forum: Programming Talk
---

### Post by monraaf on 2009-06-04
Consider the following small python script:

```

#!/usr/bin/env python
import gobject, gtk

val = 0
def timeout():
    global val
    val +=1
    scale.set_value(val)
    return True

win     = gtk.Window()
scale   = gtk.HScale()

scale.set_range(0, 100)
scale.set_update_policy(gtk.UPDATE_CONTINUOUS)
scale.set_value(val)
win.add(scale)

win.set_default_size(300,50)
win.show_all()
gobject.timeout_add(1000, timeout)
gtk.main()

```

All works as expected: the slider moving and label updating every second. Now instead of 0 - 100, use a range of 0 - 10000, and the label isn't update anymore every second.

Edit: I will use my own label, instead of the one provided by the scale. as a work around.

---

### Post by crdlb on 2009-06-04
Presumably, the reason it's not updating is that 1/10000 is not nearly enough to move the slider, so it doesn't bother updating the text either. The text will eventually update when the indicator moves by a pixel. If you really need the number to be precise, turn off the value display (set_draw_value) and handle it yourself with something like a label.

BTW, what are you using the HScale for? Is this a progress meter for a video/audio player?

---

### Post by monraaf on 2009-06-04
Yes the scale is used as a progress meter and for seeking purposes.

---

### Post by Pistolpete2 on 2010-08-27
Hi,

I also have a problem with gtk.Scale.  I'm using c++ as programming language but that shouldn't matter I think.

I've setup a callback for when te value of gtk.Scale changes. The callback get's triggered because maxHue gets updated but the set_value on the slider isn't performed. The code looks as follows:

```

void on_sliderHueMax_value_changed(Gtk::ScrollType scroll, double new_value) {
	if(new_value < minHue){
		new_value = minHue;
	}
	maxHue = (int) new_value;
	pSliderHueMax->set_value(maxHue);
        /*Could below I just for forcing redraw but doesn't work either*/
	Gtk::Allocation alloc = pSliderHueMax->get_allocation();
	int x = alloc.get_x();
	int y = alloc.get_y();
	int width = alloc.get_width();
	int height = alloc.get_height();
	pWindow->queue_draw_area(x,y,width,height);

}
```

(Some background information:  I just want to have 2 sliders, 1 for the maximum value and 1 for the minimum value and I want to make sure the user is not able to select a minimum value that's higher than the maximum value and vice versa.)

Anyone who has got an idea?

---

### Post by StephenF on 2010-08-27
Running on Gentoo stable this bug does not appear and I do consider this a bug.

---

### Post by Pistolpete2 on 2010-08-27
Ok, thank you for the information.

So normally (if the bug wouldn´t exist). 
 ```
pSliderHueMax->set_value(maxHue); 
```
should be enough?

---

