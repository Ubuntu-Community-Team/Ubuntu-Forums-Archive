---
title: "uTouch Application Development, where to start?"
date: 2011-02-08
forum: Programming Talk
---

### Post by Garske on 2011-02-08
Hello,

I am not sure if this is the right place to ask this, but I am looking for information on how to develop a multi-touch application using utouch.

I guess I am looking for what language to use, and maybe a sample application.

If this is not the right place to ask, please direct me to the correct source.

Thanks!

---

### Post by bregma on 2011-02-09
The programming API for uTouch gestures is GEIS.  The [utouch-geis project on launchpad]("https://launchpad.net/utouch-geis") has seom demo code called "geistest" that is an example of programming with that API, and documentation on the forthcoming [GEIS v2]("http://people.canonical.com/~stephenwebb/geis-v2/") are available.

If you want to deal with just touch, that interface is still in flux.

---

### Post by Garske on 2011-02-09
This was exactly what I was looking for...  Thanks!

---

### Post by NoBugs! on 2012-07-31
Those links aren't working anymore :(
Is there any information on how to enable the smooth-scrolling in a pyGTK app?

I noticed most apps don't have pixel-smooth scrolling (though in Nautilus it works great). Is there an option I need to set to enable it everywhere?

---

### Post by bregma on 2012-07-31
The project name changed in launchpad.  Try [here]("http://launchpad.net/geis").

There are python bindings available for the geis library.

Smooth scrolling is not yet available in GTK (they're reinevnting their own gesture recognition library of course).

---

### Post by NoBugs! on 2012-07-31
Thanks, I found the Python geis module and installed it (apt-get install python-utouch-geis), but I don't see any obvious way to attach it to a scrollview or webview to enable pixel scrolling:

```
>>> import geis
>>> print geis.__doc__
Python bindings for the GEIS gesture recognition interface.

>>> print dir(geis)
['Event', 'Filter', 'GEIS_ATTR_TYPE_BOOLEAN', 'GEIS_ATTR_TYPE_FLOAT', 'GEIS_ATTR_TYPE_INTEGER', 'GEIS_ATTR_TYPE_POINTER', 'GEIS_ATTR_TYPE_STRING', 'GEIS_CLASS_ATTRIBUTE_ID', 'GEIS_CLASS_ATTRIBUTE_NAME', 'GEIS_CONFIGURATION_FD', 'GEIS_CONFIG_UTOUCH_MAX_EVENTS', 'GEIS_DEVICE_ATTRIBUTE_DIRECT_TOUCH', 'GEIS_DEVICE_ATTRIBUTE_ID', 'GEIS_DEVICE_ATTRIBUTE_INDEPENDENT_TOUCH', 'GEIS_DEVICE_ATTRIBUTE_NAME', 'GEIS_DEVICE_ATTRIBUTE_TOUCHES', 'GEIS_EVENT_ATTRIBUTE_CLASS', 'GEIS_EVENT_ATTRIBUTE_DEVICE', 'GEIS_EVENT_ATTRIBUTE_GROUPSET', 'GEIS_EVENT_ATTRIBUTE_TOUCHSET', 'GEIS_EVENT_CLASS_AVAILABLE', 'GEIS_EVENT_CLASS_CHANGED', 'GEIS_EVENT_CLASS_UNAVAILABLE', 'GEIS_EVENT_DEVICE_AVAILABLE', 'GEIS_EVENT_DEVICE_UNAVAILABLE', 'GEIS_EVENT_ERROR', 'GEIS_EVENT_GESTURE_BEGIN', 'GEIS_EVENT_GESTURE_END', 'GEIS_EVENT_GESTURE_UPDATE', 'GEIS_EVENT_INIT_COMPLETE', 'GEIS_EVENT_USER_DEFINED', 'GEIS_FILTER_CLASS', 'GEIS_FILTER_DEVICE', 'GEIS_FILTER_OP_EQ', 'GEIS_FILTER_OP_GE', 'GEIS_FILTER_OP_GT', 'GEIS_FILTER_OP_LE', 'GEIS_FILTER_OP_LT', 'GEIS_FILTER_OP_NE', 'GEIS_FILTER_REGION', 'GEIS_GESTURE_ATTRIBUTE_ANGLE', 'GEIS_GESTURE_ATTRIBUTE_ANGLE_DELTA', 'GEIS_GESTURE_ATTRIBUTE_ANGULAR_VELOCITY', 'GEIS_GESTURE_ATTRIBUTE_BOUNDINGBOX_X1', 'GEIS_GESTURE_ATTRIBUTE_BOUNDINGBOX_X2', 'GEIS_GESTURE_ATTRIBUTE_BOUNDINGBOX_Y1', 'GEIS_GESTURE_ATTRIBUTE_BOUNDINGBOX_Y2', 'GEIS_GESTURE_ATTRIBUTE_CHILD_WINDOW_ID', 'GEIS_GESTURE_ATTRIBUTE_DELTA_X', 'GEIS_GESTURE_ATTRIBUTE_DELTA_Y', 'GEIS_GESTURE_ATTRIBUTE_DEVICE_ID', 'GEIS_GESTURE_ATTRIBUTE_EVENT_WINDOW_ID', 'GEIS_GESTURE_ATTRIBUTE_FOCUS_X', 'GEIS_GESTURE_ATTRIBUTE_FOCUS_Y', 'GEIS_GESTURE_ATTRIBUTE_GESTURE_NAME', 'GEIS_GESTURE_ATTRIBUTE_POSITION_X', 'GEIS_GESTURE_ATTRIBUTE_POSITION_Y', 'GEIS_GESTURE_ATTRIBUTE_RADIAL_VELOCITY', 'GEIS_GESTURE_ATTRIBUTE_RADIUS', 'GEIS_GESTURE_ATTRIBUTE_RADIUS_DELTA', 'GEIS_GESTURE_ATTRIBUTE_ROOT_WINDOW_ID', 'GEIS_GESTURE_ATTRIBUTE_TAP_TIME', 'GEIS_GESTURE_ATTRIBUTE_TIMESTAMP', 'GEIS_GESTURE_ATTRIBUTE_TOUCHES', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_0_ID', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_0_X', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_0_Y', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_1_ID', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_1_X', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_1_Y', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_2_ID', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_2_X', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_2_Y', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_3_ID', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_3_X', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_3_Y', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_4_ID', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_4_X', 'GEIS_GESTURE_ATTRIBUTE_TOUCH_4_Y', 'GEIS_GESTURE_ATTRIBUTE_VELOCITY_X', 'GEIS_GESTURE_ATTRIBUTE_VELOCITY_Y', 'GEIS_INIT_SERVICE_PROVIDER', 'GEIS_INIT_SYNCHRONOUS_START', 'GEIS_INIT_TRACK_DEVICES', 'GEIS_INIT_TRACK_GESTURE_CLASSES', 'GEIS_INIT_UTOUCH_DBUS_BACKEND', 'GEIS_INIT_UTOUCH_GRAIL_BACKEND', 'GEIS_INIT_UTOUCH_MOCK_BACKEND', 'GEIS_INIT_UTOUCH_XCB_BACKEND', 'GEIS_REGION_ATTRIBUTE_WINDOWID', 'GEIS_REGION_X11_ROOT', 'GEIS_REGION_X11_WINDOWID', 'GEIS_STATUS_BAD_ARGUMENT', 'GEIS_STATUS_CONTINUE', 'GEIS_STATUS_EMPTY', 'GEIS_STATUS_NOT_SUPPORTED', 'GEIS_STATUS_SUCCESS', 'GEIS_STATUS_UNKNOWN_ERROR', 'GEIS_TOUCH_ATTRIBUTE_ID', 'GEIS_TOUCH_ATTRIBUTE_X', 'GEIS_TOUCH_ATTRIBUTE_Y', 'Geis', 'NoMoreEvents', 'Subscription', '__all__', '__builtins__', '__doc__', '__file__', '__name__', '__package__', '__path__', 'geis_v2']
>>> 


```

---

