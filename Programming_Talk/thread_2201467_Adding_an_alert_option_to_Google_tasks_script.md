---
title: "Adding an alert option to Google tasks script"
date: 2014-01-24
forum: Programming Talk
---

### Post by GrouchyGaijin on 2014-01-24
Hi Guys,

I've been using the Google tasks cli script Tasky along with another bash script to make Tasky easier to use.

```

!/bin/bash
params=()
read -p "Subject: " sub
read -p "Due date (MM/DD/YY): " ddate 
read -p "Note (ex:@09:00@Alert:08:30): " note
[ -n "$ddate" ] && params+=( "-d" "$ddate" )
[ -n "$note" ] && params+=( "-n" "$note" )
~/scripts/tasky a "$sub" "${params[@]}"

```

Tasky works great and this script above does make it easier to write a task.
Basically, I found that on my phone if I add @due_time@Alert:alert_time in the note field I can get an alert sound to go off when I need to do something.

[B]My question is how could I modify the above script so that when entering a new task I am asked for both the due time and alert time and then have that information put into the note option -n as for example: @18:00@Alert:17:45

[/B]I'm guessing that I could add two read -p commands one for due_time and one for alert_time and then join those two to make a third variable which could be added as:
```

[ -n "$third_variable" ] && params+=( "-n" "$third_variable" )

```
The thing is I don't know how to combine two variables (due_time and alert_time) to make the third_variable.  And I'm not sure how to add the @ to the due_time and @Alert: to the alert_time
I hope this makes sense and I appreciate any help you could give me.

---

### Post by Vaphell on 2014-01-24
```
read -p "Time: " time
read -p "Alert: " alert
[ -n "$time" ] && note="@$time"
[ -n "$alert" ] && note="$note@Alert:$alert"
[ -n "$note" ] && params+=( -n "$note" ) 
```
?

---

### Post by GrouchyGaijin on 2014-01-24
Thank you man!
Once again you have made my life easier.
I use your weather program almost every day.

---

