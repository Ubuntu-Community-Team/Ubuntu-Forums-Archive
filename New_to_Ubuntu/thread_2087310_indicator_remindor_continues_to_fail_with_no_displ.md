---
title: "indicator remindor continues to fail with no display"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by rocketscove on 2012-11-23
run from terminal gives:

/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py:391: Warning: g_object_set_property: construct property "type" for object `IndicatorRemindorWindow' can't be set after construction
  Gtk.Window.__init__(self, type=type, **kwds)
Traceback (most recent call last):
  File "/usr/bin/indicator-remindor", line 44, in <module>
    indicator_remindor.main()
  File "/usr/lib/python2.7/dist-packages/indicator_remindor/__init__.py", line 108, in main
    window = IndicatorRemindorWindow.IndicatorRemindorWindow()
  File "/usr/lib/python2.7/dist-packages/indicator_remindor/IndicatorRemindorWindow.py", line 88, in __new__
    new_object.finish_initializing(builder)
  File "/usr/lib/python2.7/dist-packages/indicator_remindor/IndicatorRemindorWindow.py", line 183, in finish_initializing
    self.update_alarms()
  File "/usr/lib/python2.7/dist-packages/indicator_remindor/IndicatorRemindorWindow.py", line 520, in update_alarms
    t = timestamp(str_to_date(a.time, a.date))
  File "/usr/lib/python2.7/dist-packages/remindor_common/datetimeutil.py", line 53, in str_to_date
    d = str_to_day(d).strftime(internal_date_format)
  File "/usr/lib/python2.7/dist-packages/remindor_common/datetimeutil.py", line 117, in str_to_day
    start = datetime.strptime(dl[-1], internal_date_format).date()
  File "/usr/lib/python2.7/_strptime.py", line 325, in _strptime
    (data_string, format))
ValueError: time data '12-3-2012' does not match format '%m/%d/%Y'

Can I do something to fix this myself or must I find another reminder package?

---

