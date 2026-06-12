---
title: "Java: Compare Dates/Timestamps?"
date: 2012-04-30
forum: Programming Talk
---

### Post by fallenshadow on 2012-04-30
How can I compare these in an if statement?

I keep running into this error:

> Type mismatch: cannot convert from int to boolean

This seems like a big brick wall I keep hitting one way or another. ](*,)

---

### Post by mehaga on 2012-04-30
> **fallenshadow said:**
> How can I compare these in an if statement?

I keep running into this error:



This seems like a big brick wall I keep hitting one way or another. ](*,)

[http://stackoverflow.com/questions/2811121/date-comparison-using-java](http://stackoverflow.com/questions/2811121/date-comparison-using-java)

---

### Post by 11jmb on 2012-04-30
Timestamp has a compareTo(Date) method that you can check out.

---

### Post by fallenshadow on 2012-04-30
Thanks mehaga!

I can now compare dates... however I also want to do time comparison. I tried modifying the code from stackoverflow but it doesn't seem to work.

```

int hour = trackEvent.getTimestamp().getHour(); //this equals 22 when tested

currDtCal.set(Calendar.HOUR_OF_DAY, hour);

```

I don't have any errors but im getting the hours as 00 even though the hours should be 22. :confused:

---

### Post by mehaga on 2012-04-30
> **fallenshadow said:**
> Thanks mehaga!

I can now compare dates... however I also want to do time comparison. I tried modifying the code from stackoverflow but it doesn't seem to work.

```

int hour = trackEvent.getTimestamp().getHour(); //this equals 22 when tested

currDtCal.set(Calendar.HOUR_OF_DAY, hour);

```

I don't have any errors but im getting the hours as 00 even though the hours should be 22. :confused:
You are welcome :)

There are 3-4 interesting answers to that SO question. One of them, IIRC, resets hours to zero, in order to make date to date comparison work. Maybe you did that? In any case, see all the answers there, and see which one suits your situation best. If none of them work, ask a question there and you'll probably get an answer within minutes...

---

### Post by Some Penguin on 2012-04-30
Consider migrating to [joda-time]("http://joda-time.sourceforge.net/index.html").

And in the future, consider spending more time making your questions more detailed and posting more relevant code snippets.

---

### Post by ofnuts on 2012-04-30
> **fallenshadow said:**
> Thanks mehaga!

I can now compare dates... however I also want to do time comparison. I tried modifying the code from stackoverflow but it doesn't seem to work.

```

int hour = trackEvent.getTimestamp().getHour(); //this equals 22 when tested

currDtCal.set(Calendar.HOUR_OF_DAY, hour);

```I don't have any errors but im getting the hours as 00 even though the hours should be 22. :confused:
Be very careful about timezones.  A Java Date() is timezone independent. To get hours of day from a Date requires a timezone, explicit or not.

---

### Post by fallenshadow on 2012-05-01
@Some Penguin

I have heard of Joda time but im not currently interested in using it. As for my code I thought it was relevant to what I was asking. :/

To solve my problem I just changed to use "GregorianCalendar" as it is much easier to compare dates including the time and you can do direct comparisons. :)

---

### Post by muteXe on 2012-05-01
two weeks ago i was in hell with date/time stuff in java.
joda time lib saved my life tbh.

---

