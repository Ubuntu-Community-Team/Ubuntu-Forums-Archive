---
title: "Python - time.sleep causes app to stop responding"
date: 2007-12-18
forum: Programming Talk
---

### Post by mevets on 2007-12-18
I am writing a simple alarm clock application. I am using GTK for the gui. At some point in the code I calculate the time between now and when the alarm should sound. I then *time.sleep(difference)*. The problem is that when the application is on these long time.sleep()s it will cause the gui to become unresponsive. It ends up actually ringing at the right time, but what if someone set the alarm and wants to cancel it? They cant because the gui is frozen.

Is there a way around  this? Should I be going about this problem differently?
```

def alarmCheck(self, alarm):
        while(True):
            fullNow = datetime.datetime.now()
            now = datetime.datetime(fullNow.year, fullNow.month, fullNow.day, fullNow.hour, fullNow.minute)
            diff = alarm - now
            try:
                secs
            except UnboundLocalError:
                secs = (diff.days*86400) + (diff.seconds)
            else:
                pass
            
            if now > alarm:
                print "It is too late for the alarm to go off."
                break
            elif now < alarm:
                print "too early.."
                if secs < 300: # 5 minutes
                    time.sleep(secs)
                else:
                    # someone told me Cron will sleep for 75% of the time
                    # in order to not be too far off if something goes terribly
                    cronTime = int(75 * secs / 100)
                    secs = secs - cronTime
                    print "This is going to take longer than 5 mins... Will sleep " + str(cronTime)
                    time.sleep(cronTime)
            elif now == alarm:
                self.soundAlarm()
                break
        return

```

Entire script here: [http://www.shorttext.com/wioonq](http://www.shorttext.com/wioonq)

---

### Post by LaRoza on 2007-12-18
You can try threading.

---

### Post by engla on 2007-12-18
If you are using a gui (pygtk I presume), you are already using an event loop and can put timed events into it. Try this

[gobject.timeout_add]("http://doc.async.com.br/python/pygtk/reference/gobject-functions.html#function-gobject--timeout-add")

```
# Register a callback in 5000 millisecs
gobject.timeout_add(5000, self.update_alarm)
```

Then in update_alarm you update your info about the alarm and either let timeout_add call it again with the same interval (by returning True) or registering the callback anew with another time and return False.

If you know your event loop, you can post events into it and avoid multithreading. Your alarm will be handled as an application event just like redrawing and control interaction, so that both can function together. Remember that explicitly sleeping is a strong anti-pattern in programming; sleeping, polling etc should not be used. Use events.

---

