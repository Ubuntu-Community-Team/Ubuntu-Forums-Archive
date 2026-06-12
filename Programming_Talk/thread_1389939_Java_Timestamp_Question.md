---
title: "Java Timestamp Question"
date: 2010-01-25
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-01-25
Anyone know how to make this code more efficient?

[PHP]
import java.util.Calendar;
import java.util.Date;
import java.sql.Timestamp;

class someclass
{
	public static void main(String args[])
	{
		long timeinms = 1264390683432L;
		int nanos = 3498143;

		date.setTime(timeinms);
		cal.setTime(date);
		
		double milliseconds = (double)(cal.get(Calendar.MILLISECOND)*1000000 + nanos) / 1000000000;
		String timestamp = cal.get(Calendar.HOUR_OF_DAY) + ":" + cal.get(Calendar.MINUTE) + ":" + cal.get(Calendar.SECOND) + "." + milliseconds;
		timestamp = timestamp.replace(".0.", ".");
		System.out.println(timestamp);
	}
}
[/PHP]

Basically, I feed in time in milliseconds as well as nanoseconds and I want to get a timestamp like this:

22:27:4.359452  (hour::minute::second.fraction-of-second)

As a string.  The java.sql.timestamp class almost works.  It supports milliseconds and prints the string I am looking for (except for the year/month/day part), but the trick is that when setting the nanoseconds, it "over-writes" fractional second part of time time.  So one would have to know the number of milliseconds lost and add that back when calling setNano()...there must be a simpler way.  Anyone know?

---

### Post by Axos on 2010-01-25
How are you getting the nanoseconds? If you are getting them from System.nanoTime(), they are not in any way whatsoever correlated with System.currentTimeMillis(). Adding them together is completely meaningless:

> This method can only be used to measure elapsed time and is not related to any other notion of system or wall-clock time. The value returned represents nanoseconds since some fixed but arbitrary time (perhaps in the future, so values may be negative). This method provides nanosecond precision, but not necessarily nanosecond accuracy. No guarantees are made about how frequently values change.

---

### Post by SNYP40A1 on 2010-01-26
> **Axos said:**
> How are you getting the nanoseconds? If you are getting them from System.nanoTime(), they are not in any way whatsoever correlated with System.currentTimeMillis(). Adding them together is completely meaningless:

It's coming off of a quote ticker and not from my computer.  I don't think it's so much used to accuracy down to the milli/micro/nano second, but more used to designate different quotes printing under the same millisecond.

---

### Post by Axos on 2010-01-26
What doesn't make sense is that that nanoseconds are greater than 999,999. That's what tipped me off that they weren't correlated with the milliseconds. If the nanoseconds were in the range of 0 to 999,999, you could simply zero-pad the milliseconds to 3 digits on right and zero-pad the nanoseconds to 6 digits on the left and append the two strings. No messy floating point. But if the nanoseconds are greater than 999,999, that simply doesn't make sense. I don't think they are correlated and you should just maintain the nanoseconds separately. Don't add them or append them. Separate field.

---

### Post by Shin_Gouki2501 on 2010-01-26
Regarding formating have you looked at:
[http://java.sun.com/j2se/1.5.0/docs/api/java/text/SimpleDateFormat.html](http://java.sun.com/j2se/1.5.0/docs/api/java/text/SimpleDateFormat.html)
?

---

### Post by dwhitney67 on 2010-01-26
> **Axos said:**
> What doesn't make sense is that that nanoseconds are greater than 999,999. That's what tipped me off that they weren't correlated with the milliseconds. If the nanoseconds were in the range of 0 to 999,999, you could simply zero-pad the milliseconds to 3 digits on right and zero-pad the nanoseconds to 6 digits on the left and append the two strings. No messy floating point. But if the nanoseconds are greater than 999,999, that simply doesn't make sense. I don't think they are correlated and you should just maintain the nanoseconds separately. Don't add them or append them. Separate field.

There are 1E9 nanoseconds in 1 second.  There are 1E6 microseconds in one second.  Perhaps you were thinking of the latter when you wrote your reply?

---

### Post by dwhitney67 on 2010-01-26
> **SNYP40A1 said:**
> 
Basically, I feed in time in milliseconds as well as nanoseconds and I want to get a timestamp like this:

22:27:4.359452  (hour::minute::second.fraction-of-second)

Please clarify if the milliseconds represents the actual time since some predetermined epoch, say 1970-01-01 00:00:00.

The number that you are using in your test program is way out of range if it represents the number of milliseconds within the current second, or even if it is used to represent the current time of day relative to midnight (00:00:00).

It appears that you intend to imply that the milliseconds indicate a quantity of time into the current second; well, that's what I get from reading the code.  Your range of milliseconds should be 0 to 999.  The nanoseconds should range from 0 to 999,999,999.

Maybe all you need to do is compute what fraction of a second does the nanoseconds represent, perhaps rounding the result to 6 digits, per your requirements?
```

double fraction = (double) nanoseconds / 1000000000L;

```

---

### Post by Axos on 2010-01-26
EDIT: I've deleted my original post because I realized I was too wrapped up with the meaning of combining the milliseconds and nanoseconds. In reality (which is not where I was), all that is needed is a practical way to use the nanoseconds to establish the order of two quotes when the milliseconds are the same. Beyond that, the exact number of nanoseconds is irrelevant. Sorry for not being grounded in reality. :D

---

### Post by SNYP40A1 on 2010-02-02
> **dwhitney67 said:**
> Please clarify if the milliseconds represents the actual time since some predetermined epoch, say 1970-01-01 00:00:00.

The number that you are using in your test program is way out of range if it represents the number of milliseconds within the current second, or even if it is used to represent the current time of day relative to midnight (00:00:00).

It appears that you intend to imply that the milliseconds indicate a quantity of time into the current second; well, that's what I get from reading the code.  Your range of milliseconds should be 0 to 999.  The nanoseconds should range from 0 to 999,999,999.

Maybe all you need to do is compute what fraction of a second does the nanoseconds represent, perhaps rounding the result to 6 digits, per your requirements?
```

double fraction = (double) nanoseconds / 1000000000L;

```

I changed my datalogging format and no longer interested in this question, but do appreciate the advice and feedback.  The number of ms is time since 1970.  So that's why the number is huge.

---

