---
title: "Python Timer not going off"
date: 2008-05-14
forum: Programming Talk
---

### Post by mevets on 2008-05-14
I am writing a alarm clock application w/ a gui using GTK. When a user makes a change to the gui it activates self.setAlarm which calls self.calcAlarm which calculates a dates based on what days are selected and what time the alarm on that day is set to. Of the dates generated, they are all in the future. It then returns the earlist one because that is the date of the alarm that should go off next. It calculates the number of seconds between now and the date of the next alarm. Then self.timer gets a new timer with an interval of the difference that should call self.soundAlarm when it goes off.

My problem is that the alarm never sounds. The timer never goes off. I have it print the interval of the timer before it is started so I know that should go off in a matter of seconds, but after it is started it never does. I believe I have a threading problem, but I don't know how to troubleshoot that problem because I am only just learning python. I have also found that if I set an alarm and wait fro the time for it to go off, it does not go off but if I wait for that time to pass and I close the application, then it freezes for a bit then finally closes. When it closes it finally prints that the alarm is going off, instead off when it should have. Its as if this finally closes the thread and it decides to execute soundAlarm. I added self.timer.cancel() to the closing method cause I figured it would resolve the freezing at the closing of the application. I was mistaken and that is probably pointless. As you can see, I really am a novice to the threading module.

Can anyone explain why my timer is not going off when it should?
```

#!/usr/bin/env python

# alarm.py

import pygtk
pygtk.require('2.0')
import gtk
import time
import datetime
from datetime import timedelta
import threading

class Clock:
    weekDays = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"]
    timer = None
    chkDay = [1,2,3,4,5,6,7]
    for i in range(0, 7):
        chkDay[i] = gtk.CheckButton(weekDays[i])
    cmbMeridiem = [1,2,3,4,5,6,7]
    spinHour = [1,2,3,4,5,6,7]
    spinMin = [1,2,3,4,5,6,7]
    adjMins = [1,2,3,4,5,6,7]
    adj12hr = [gtk.Adjustment(7, 1, 12, 1, 0, 0),
               gtk.Adjustment(7, 1, 12, 1, 0, 0),
               gtk.Adjustment(7, 1, 12, 1, 0, 0),
               gtk.Adjustment(7, 1, 12, 1, 0, 0),
               gtk.Adjustment(7, 1, 12, 1, 0, 0),
               gtk.Adjustment(7, 1, 12, 1, 0, 0),
               gtk.Adjustment(7, 1, 12, 1, 0, 0)]
    adj24hr = [gtk.Adjustment(7, 0, 23, 1, 0, 0),
               gtk.Adjustment(7, 0, 23, 1, 0, 0),
               gtk.Adjustment(7, 0, 23, 1, 0, 0),
               gtk.Adjustment(7, 0, 23, 1, 0, 0),
               gtk.Adjustment(7, 0, 23, 1, 0, 0),
               gtk.Adjustment(7, 0, 23, 1, 0, 0),
               gtk.Adjustment(7, 0, 23, 1, 0, 0)]
    
    def soundAlarm(self):
        print "im going off at " , datetime.datetime.now()
        return   
    
    def setAlarm(self, widget):
        nextAlarm = self.calcAlarm(widget)

        if type(nextAlarm) == datetime.datetime and nextAlarm > datetime.datetime.now():
            nextAlarm = datetime.datetime.now() + datetime.timedelta(seconds=5)
            # cancel alarm
            if self.timer != None:
                self.timer.cancel()
        
            # calculate interval til alarm must go off
            alarmWeekday = nextAlarm.strftime("%A")
            tIndex = self.weekDays.index(alarmWeekday)
            diff = nextAlarm - datetime.datetime.now()
            interval = diff.days*86400 + diff.seconds
            self.timer = threading.Timer(float(interval), self.soundAlarm)
            print "timer's interval = " , self.timer.interval
            self.timer.start()
    
    def calcAlarm(self, widget):
        todayName = datetime.datetime.now().strftime("%A")
        todayIndex = self.weekDays.index(todayName)
        today = datetime.datetime.now()
        
        alarmsOn = {}
        for i in range(0, 7):
            if self.chkDay[i].get_active():
                alarmsOn[len(alarmsOn)] = self.weekDays[i]

        dates = {}
        for i in range(0, len(alarmsOn.keys())):
            diff = self.weekDays.index(alarmsOn[i]) - self.weekDays.index(todayName)
            if diff < 0:
                # this day of the week has already passed
                dates[i] = today + timedelta(days=diff, weeks=1)
            elif diff == 0:
                year = today.year
                month = today.month
                day = today.day
                hour = int(self.spinHour[self.weekDays.index(alarmsOn[i])].get_value())
                min = int(self.spinMin[self.weekDays.index(alarmsOn[i])].get_value())
                # datetime uses military time so convert it if the
                # user is using 12hr time and it is in the PM
                if(not self.chk24hr.get_active() and
                self.cmbMeridiem[self.weekDays.index(alarmsOn[i])].get_active() == 1 and
                self.spinHour[self.weekDays.index(alarmsOn[i])].get_value() < 12):
                    hour += 12
                
                sameDay = datetime.datetime(year,month,day,hour,min)
                # if specific alarms's time has passed already today
                # then it has to go off next week
                if sameDay < today:
                    sameDay += timedelta(weeks=1)

                dates[i] = sameDay
            else: # diff > 0
                dates[i] = today + timedelta(days=diff)
            i+=1
            
        values = dates.values()
        values.sort()
            
        if len(dates) <= 0:
            return None
        else:
            return dates[0] 
    
    def togHourFormat(self, widget):
        format24 = widget.get_active()
        if format24:
            for cmb in self.cmbMeridiem:
                cmb.hide()
            i = 0
            for spin in self.spinHour:
                ampmval = self.spinHour[i].get_value()
                spin.set_adjustment(self.adj24hr[i])
                if self.cmbMeridiem[i].get_active() == 1:
                    self.spinHour[i].set_value(ampmval + 12)
                i += 1
        elif not format24:
            for cmb in self.cmbMeridiem:
                cmb.show()
            i = 0
            for spin in self.spinHour:
                militaryval = self.spinHour[i].get_value()
                spin.set_adjustment(self.adj12hr[i])
                if militaryval >= 13:
                    self.spinHour[i].set_value(militaryval - 12)
                    self.cmbMeridiem[i].set_active(1)
                elif militaryval < 13 and militaryval > 0:
                    self.cmbMeridiem[i].set_active(0)
                elif militaryval == 0:
                    self.spinHour[i].set_value(12)
                    self.cmbMeridiem[i].set_active(0)
                i += 1

    def __init__(self):

        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)

        self.window.connect('destroy', lambda w: gtk.main_quit())

        self.window.set_border_width(10)

        mainbox = gtk.VBox(False, 5)
        self.window.add(mainbox)
        tabs = gtk.Notebook()


        # weekly gui
        weeklybox = gtk.VBox(False, 5)
        for i in range(0, 7):
            dayhbox = gtk.HBox(False, 5)
            self.chkDay[i].connect("toggled", self.setAlarm)
            timehbox = gtk.HBox(False, 5)
            adjHour = self.adj12hr[i]
            self.adj12hr[i].connect("value_changed", self.setAlarm)
            self.adj24hr[i].connect("value_changed", self.setAlarm)
            self.spinHour[i] = gtk.SpinButton(adjHour, 0, 0)
            lblcolon = gtk.Label(":")
            self.adjMins[i] = gtk.Adjustment(30, 0, 59, 1, 0, 0)
            self.adjMins[i].connect("value_changed", self.setAlarm)
            self.spinMin[i] = gtk.SpinButton(self.adjMins[i], 0, 0)
            self.cmbMeridiem[i] = gtk.combo_box_new_text()
            self.cmbMeridiem[i].append_text("AM")
            self.cmbMeridiem[i].append_text("PM")
            self.cmbMeridiem[i].set_active(0)
            self.cmbMeridiem[i].connect("changed", self.setAlarm)
            dayhbox.pack_start(self.chkDay[i], False, False, 0)
            timehbox.pack_start(self.spinHour[i], False, False, 0)
            timehbox.pack_start(lblcolon, False, False, 0)
            timehbox.pack_start(self.spinMin[i], False, False, 0)
            timehbox.pack_start(self.cmbMeridiem[i], False, False, 0)
            dayhbox.pack_end(timehbox, False, False, 0)
            weeklybox.pack_start(dayhbox, False, False, 0)
        
        # preferences gui
        prefsbox = gtk.VBox(False, 5)
        self.chk24hr = gtk.CheckButton("24-hour clock")
        alarmhbox = gtk.HBox(False, 10)
        lblAlarm = gtk.Label("Noise")
        fcbSound = gtk.FileChooserButton("Locate a sound file")
        alarmhbox.pack_start(lblAlarm, False, False, 0)
        alarmhbox.pack_start(fcbSound)
        prefsbox.pack_start(self.chk24hr, False, False, 10)
        prefsbox.pack_start(alarmhbox, False, False, 0)
        self.chk24hr.connect("toggled", self.togHourFormat)
        
        # add the tabs and pack them
        tabs.append_page(weeklybox, gtk.Label("Weekly"))
        tabs.append_page(prefsbox, gtk.Label("Preferences"))
        mainbox.pack_start(tabs)
        
        closebox = gtk.HBox(False, 0)
        close = gtk.Button("Close", gtk.STOCK_CLOSE)
        close.connect("clicked", lambda wid: gtk.main_quit())
        closebox.pack_end(close, False, False, 0)
        mainbox.pack_start(closebox, False, False, 0)

        # show everything
        self.window.show_all()

        return

    def delete_event(self, widget):
        self.timer.cancel()
        gtk.main_quit()
        return False


def main():
    gtk.main()
    return False

if __name__ == "__main__":
    Clock()
    main()

```

---

### Post by Can+~ on 2008-05-15
Well, that's a deep amount of code you got there, so it isn't easy to say. But I'll try to guess:

-The most likely thing, is that somewhere, you set up a loop that checks for the current date/time until the alarm time is equal. But! loops inside gtk doesn't work, because GTK itself starts it's own loop (Gtk iteration), so, when an infinite loop is ran inside a GTK application on a single thread, then the environment stops receiving signals from your app, and thinks it's hang up. 

Also, for the sake of readability, I think you should split the alarm into another class, so you can instance multiple alarms, possibly into another module, and use glade.

---

