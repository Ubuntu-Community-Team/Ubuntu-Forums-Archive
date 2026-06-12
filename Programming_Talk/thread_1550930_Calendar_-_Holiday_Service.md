---
title: "Calendar - Holiday Service"
date: 2010-08-11
forum: Programming Talk
---

### Post by arindam.das on 2010-08-11
The ubuntu calendar widget can display local holidays based on 2 parameters 
1)Calendar System {values:{Local, Coptic, Ethiopian, Gregorian..}}
2)Holidays {value:{All Countries}}

My question is how does it do this. Does it use a web service to get the data or is it put in some file somewhere on my hard drive. I would like to implement a similar feature in my Java Application which will be able to figure out local holidays based on the country. A pointer in the right direction will be greatly appreciated.

---

### Post by WitchCraft on 2010-08-11
> **arindam.das said:**
> The ubuntu calendar widget can display local holidays based on 2 parameters 

Which widget? How to install ?

---

### Post by WitchCraft on 2010-08-11
I wanted to do that myself. I need the public holidays ;-)))

I think you mean the calendar widget in
```

sudo apt-get install screenlets

```

I did apt-get source screenlets and in /plugins/iCal.py

and found this:
[http://www.google.com/calendar/ical/4dmslp71qlvjhl1q6g6f88gfv4@group.calendar.google.com/public/basic.ics](http://www.google.com/calendar/ical/4dmslp71qlvjhl1q6g6f88gfv4@group.calendar.google.com/public/basic.ics)


So I'd say one needs this:
[http://code.google.com/apis/calendar/](http://code.google.com/apis/calendar/)
and this:
[http://labnol.blogspot.com/2006/04/add-national-religious-holidays-to.html](http://labnol.blogspot.com/2006/04/add-national-religious-holidays-to.html)


Edit: Oh here you go:
[http://www.google.com/calendar/ical/usa__en%40holiday.calendar.google.com/public/basic.ics](http://www.google.com/calendar/ical/usa__en%40holiday.calendar.google.com/public/basic.ics)
[http://www.google.com/calendar/feeds/usa__en%40holiday.calendar.google.com/public/basic](http://www.google.com/calendar/feeds/usa__en%40holiday.calendar.google.com/public/basic)
[http://www.google.com/calendar/embed?src=usa__en%40holiday.calendar.google.com&ctz=America/Los_Angeles](http://www.google.com/calendar/embed?src=usa__en%40holiday.calendar.google.com&ctz=America/Los_Angeles)


Source: [http://stackoverflow.com/questions/59934/national-holiday-web-service](http://stackoverflow.com/questions/59934/national-holiday-web-service)

---

