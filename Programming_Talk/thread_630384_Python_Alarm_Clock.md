---
title: "Python Alarm Clock"
date: 2007-12-03
forum: Programming Talk
---

### Post by mevets on 2007-12-03
I am writing a simple alarm clock in python. Currently it works but not so well. The way that I implemented it was I recieve what time the alarm should go off and what time it currently is. I get the current time every second. So each second I compare the times to see if they are the same time. This locks up the program though. Obviously this is not the most effcient method. I guess I could up the interval to 30 seconds, but I still dont think it would be most correct.

So my question is, What is a better way of implementing an alarm clock? My other idea was to take the alarm time and subtract from it the current time. Hopefully I would be left with something I could convert into seconds and I could time.sleep(thoseseconds). But, would this be right? I just want to know before I implement it.

Mu current code
```

#!/usr/bin/env python

# alarm.py
# requires python-pygame python-configobj

import pygtk
pygtk.require('2.0')
import gtk
import sys, os, time, datetime
from configobj import ConfigObj
import pygame

class Clock:
    weekDays = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"]
    config = ConfigObj("/home/steve/Documents/projects/alarm/settings.ini")
    
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def __init__(self):
        pygame.init()
        pygame.mixer.music.set_endevent(pygame.USEREVENT)

        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)

        self.window.connect('destroy', lambda w: gtk.main_quit())

        self.window.set_border_width(10)

        vbox1 = gtk.VBox(False, 5)
        self.window.add(vbox1)
        vbox1.show()

        # make Snooze button
        btnSnooze = gtk.Button("Stop", gtk.STOCK_CANCEL)
        hboxSnooze = gtk.HBox(True, 0)
        hboxSnooze.pack_start(btnSnooze, True, True, 0)
        #vbox1.pack_start(hboxSnooze, True, True, 0)

        # make the day combobox
        cmbDay = gtk.combo_box_new_text()
        cmbDay.append_text("Monday")
        cmbDay.append_text("Tuesday")
        cmbDay.append_text("Wednesday")
        cmbDay.append_text("Thursday")
        cmbDay.append_text("Friday")
        cmbDay.append_text("Saturday")
        cmbDay.append_text("Sunday")

        # set to current day
        now = datetime.datetime.now()
        curDay = now.strftime("%A")
        intDay = 0
        cmbDay.set_active(self.weekDays.index(curDay))
        vbox1.pack_start(cmbDay, False, False, 0)

        hboxSetTime = gtk.HBox(False, 0)
        vbox1.pack_start(hboxSetTime, True, True, 0)
        
        # make AM/PM combobox
##        togAMPM = gtk.combo_box_new_text()
##        togAMPM.append_text("AM")
##	togAMPM.append_text("PM")
##	togAMPM.se-t_active(0)
##        hboxSetTime.pack_end(togAMPM, False, False, 0)

        # make minute spin button
        adjMins = gtk.Adjustment(30, 0, 59, 1, 0, 0)
        spinMins = gtk.SpinButton(adjMins, 0, 0)
        hboxSetTime.pack_end(spinMins, False, False, 0)

        hboxSetTime.pack_end(gtk.Label(":"), False, False, 0)

        # make hour spin button
        adjHour = gtk.Adjustment(7, 1, 12, 1, 0, 0)
        spinHour = gtk.SpinButton(adjHour, 0, 0)
        hboxSetTime.pack_end(spinHour, False, False, 0)

        # connect cmbDay's changed event
        cmbDay.connect("changed", self.dayChanged, spinHour, spinMins)

        # add a separator
        hsep = gtk.HSeparator()
        vbox1.pack_start(hsep, False, True, 0)

        # make a horizontal box for the close and apply buttons
        btnBox = gtk.HBox(False, 5)

        # make close button
        btnClose = gtk.Button("Close", gtk.STOCK_CLOSE)
        btnClose.connect("clicked", lambda wid: gtk.main_quit())
        btnBox.pack_end(btnClose, False, False, 0)

        # make status combobox
        cmbStatus = gtk.combo_box_new_text()
        cmbStatus.append_text("OFF")
        cmbStatus.append_text("ON")
        cmbStatus.set_active(0)
        cmbStatus.connect("changed", self.statusChanged, spinHour, spinMins)
        btnBox.pack_end(cmbStatus, False, False, 0)
        vbox1.pack_start(btnBox, False, False, 0)
	
	# make alarm notice
	lblAlarm = gtk.Label("Status:")
	btnBox.pack_end(lblAlarm, False, False, 0)

	# show everything
        self.window.show_all()

        return

    def readConfig(self, day):
        hour = self.config[day]["hour"]
        minute = self.config[day]["minute"]
        return [hour, minute]

    def dayChanged(self, widget, spinHour, spinMins):
        model = widget.get_model()
        index = widget.get_active()
        if index:
            arrNow = self.readConfig(datetime.datetime.now().strftime("%A"))
            day = self.weekDays[index]
            hour = arrNow[0]
            minute = arrNow[1]
            if len(str(hour)) > 0:
                spinHour.set_value(float(hour))
            else:
                spinHour.set_value(0.0)
            if len(str(minute)) > 0:
                spinMins.set_value(float(minute))
            else:
                spinMins.set_value(0.0)
            
        return

    def statusChanged(self, widget, spinHour, spinMins):
        index = widget.get_active()
        ymd = datetime.date.today()
        hours = int(spinHour.get_value())
        mins = int(spinMins.get_value())
        alarmDate = datetime.datetime(ymd.year, ymd.month, ymd.day, hours, mins)
        if index:
            self.alarmStatus = True
            self.alarmCheck(alarmDate)
        else:
            self.alarmStatus = False
        return

    def alarmCheck(self, alarm):

        while(True):
            fullNow = datetime.datetime.now()
            now = datetime.datetime(fullNow.year, fullNow.month, fullNow.day, fullNow.hour, fullNow.minute)
            if now > alarm:
                print "It is too late for the alarm to go off."
                break
            elif now < alarm:
                print "too early.."
                print now
                print alarm
                time.sleep(30)
            elif now == alarm:
                self.soundAlarm()
                break
        return

    def clicked_btnApply(self, widget):
        #strDay = self.cmbDay.get_text()
        #print strDay
        self.soundAlarm()
        return False

    def soundAlarm(self):
        pygame.mixer.music.load("/home/steve/Documents/projects/alarm/alarm.wav")
        pygame.mixer.music.play()
        return

def main():
    gtk.main()
    return False

if __name__ == "__main__":
    Clock()
    main()


```

---

### Post by smartbei on 2007-12-03
You have two options as I see them:
[list=1]
[*]Use a thread that will keep track of the passing seconds, or
[*]Use a Timer function to callback a specified function of your choice (that would actually handle the alarm).
[/list]
The second option appears to me to be far better architecture-wise. Look at [http://www.koders.com/python/fidCF8AA788FEA2D330899C9CA82E1050557C9F1A15.aspx?s=checkbutton](http://www.koders.com/python/fidCF8AA788FEA2D330899C9CA82E1050557C9F1A15.aspx?s=checkbutton). Specifically:
```

self.timer = gobject.timeout_add (100, progress_timeout, self)

```

Hope that helps!

---

### Post by evymetal on 2007-12-04
I think this is how CRON works:

(in it's own thread)

Look at the alarm next in line.

If it is a long time until the alarm, sleep for 75% of  the time until the next alarm.

If it's half a second or so, do as you've been doing.

This should save you billions of cycles.

---

### Post by evymetal on 2007-12-04
BTW, any chance you can implement this as a GNOME-DOCK app? I've been meaning to do this, and I'd love it in the Ubuntu repository.

---

### Post by mevets on 2007-12-05
You mean give it an icon in the notification tray? I dont know how to do that, but I can look into it. Especially cause someone is interrested in it.

---

### Post by sodoku on 2008-05-05
have a look at [AlarmClock]("http://getdeb.net/app/Alarm+Clock")

---

### Post by rinishak on 2008-10-19
Thanks for the update, sodoku. I was also on my way to writing my own program for this.

---

