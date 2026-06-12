---
title: "[SOLVED] Java Calendar/Date Help!!!"
date: 2008-10-21
forum: Programming Talk
---

### Post by bostonaholic on 2008-10-21
I'm having a problem when converting a java.util.Date object into a java.util.Calendar object using the *Calendar.setTime(Date)* method.  The day of the Calendar object is the 26th while the Date's day is the 27th.  This only happens for the date 10/27/2008, no other date.  I have installed the Time Zone Updater tool from Sun but that did not seem to fix the problem.

Any suggestions?  Here's the code
```
private Calendar newCal( Date date ) {
	Calendar calendar = null;
	if (date != null) {
		calendar = Calendar.getInstance();
		calendar.setTime(date); // calendar is 10/26/2008 (instead of date's 10/27/2008) after this method
	}

	return calendar;
}
```

EDIT: JRE 1.4.2_13 is being used, I cannot upgrade to 1.6 because our client will not yet run on 1.6 :(

---

### Post by drubin on 2008-10-21
Does this work in isolation? ie using this method in a small demoable application? if not can you post the demo-able application.  

I have used the Calander object before and never had an issue with it.

The only thing I can think of is Daylight savings or something like that?

---

### Post by bostonaholic on 2008-10-21
> **drubin said:**
> Does this work in isolation? ie using this method in a small demoable application? if not can you post the demo-able application.  

I have used the Calander object before and never had an issue with it.

The only thing I can think of is Daylight savings or something like that?

I am creating an isolated app right now so we'll see.  I'm suspecting it will still fail because the fault is in the java api.

I've never had problems with it either until now, using this date.

---

### Post by drubin on 2008-10-21
> **bostonaholic said:**
> I am creating an isolated app right now so we'll see.  I'm suspecting it will still fail because the fault is in the java api.

I've never had problems with it either until now, using this date.

In the app, include a date or 2 that work as expected. Like creating a simple unit test :).

---

### Post by bostonaholic on 2008-10-21
> **drubin said:**
> In the app, include a date or 2 that work as expected. Like creating a simple unit test :).

That's what I'm working on now.

---

### Post by Shin_Gouki2501 on 2008-10-21
Try getTime() on both to see what values (long ) you get.

---

### Post by jespdj on 2008-10-22
How do you determine that the date is set to 10/26, while the calendar is set to 10/27? Are you taking timezones into account?

Note that class java.util.Date does not know anything about timezones. Class Date is just a wrapper around a millisecond value that counts the number of milliseconds since 1 January 1970, 12:00 AM UTC. When you call toString() on a Date object, you'll get a string that represents the date in the default timezon to which your operating system is set. If you want a Date object formatted in a specific timezone, use a DateFormat object, like this:
```
Date date = ...; // wherever you get this

DateFormat df = new SimpleDateFormat("MM/dd/yyyy hh:mm a z");
df.setTimeZone(TimeZone.getTimeZone("EST"));

System.out.println(df.format(date));
```
Class Calendar does know about timezones. If the timezone of your Calendar object is set differently than the default timezone of your operating system, then it can seem as if the Date and the Calendar object have different values (when they really don't).

---

### Post by bostonaholic on 2008-10-22
> **jespdj said:**
> How do you determine that the date is set to 10/26, while the calendar is set to 10/27? Are you taking timezones into account?

Note that class java.util.Date does not know anything about timezones. Class Date is just a wrapper around a millisecond value that counts the number of milliseconds since 1 January 1970, 12:00 AM UTC. When you call toString() on a Date object, you'll get a string that represents the date in the default timezon to which your operating system is set. If you want a Date object formatted in a specific timezone, use a DateFormat object, like this:
```
Date date = ...; // wherever you get this

DateFormat df = new SimpleDateFormat("MM/dd/yyyy hh:mm a z");
df.setTimeZone(TimeZone.getTimeZone("EST"));

System.out.println(df.format(date));
```
Class Calendar does know about timezones. If the timezone of your Calendar object is set differently than the default timezone of your operating system, then it can seem as if the Date and the Calendar object have different values (when they really don't).

Thanks for the info--the first good response I've had on this (even on multiple forums).  I'll check the default TZ of calendar and of the machine.

---

### Post by jespdj on 2008-10-22
[IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG] :)

---

### Post by bostonaholic on 2008-10-28
The TZUpdater tool from Sun fixed the problem.  I found out that the application server was running a much older version of the time zone data.  I had only updated the client jar and the date was still being processed incorrectly on the server.  I ran the updater on the server and voila.

Thanks for the help though.

---

