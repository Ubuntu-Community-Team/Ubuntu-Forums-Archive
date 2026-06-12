---
title: "Clever constructs that weren't that clever"
date: 2008-10-07
forum: Programming Talk
---

### Post by Greyed on 2008-10-07
I'm not sure if this has been posted before but here goes.

What is the most clever construct you've programmed.  Something that, on the day you made it, was insanely clever and you were proud of it.  However, some time after that it dawned on you that it was completely unneeded.

I'll give mine as an example.

I was rewriting a daily batch file that we used into Python.  The goal was to remove as much of the human input as possible so as to avoid mistakes.  The main input was entering the date in different formats.  One had to enter the month with a leading 0 if needed, then without, the date with a leading 0, then without.  The full 4 digit year and then the 2 digit year.  This is because we were renaming some files to reflect the current date, copying others into directories named the current date and there was no standard formatting for any of it.

No problem.  Import date from datetime, use date.today() to get the current date and then date.strftime() to return the required formats.  No problem, %d gave me the day with leading 0 if needed, %m did the same for the month.  %y and %Y for the year in 2-digit and 4-digit notation.  But there was no formatting for month/date without a leading 0.

```

>>> from datetime import date
>>> spam = date.today()
>>> spam.strftime('%d %m %y %Y')
'07 10 08 2008'

```I wracked my brain for a good hour over that one trying to figure out how to get it since I needed them in string format.  Then it dawned on me, if I int() the date or month then str() that the 0 would not be stored as an integer thus would not be there on the conversion back to a string!

```

>>> spam.strftime('%d')
'07'
>>> str(int(spam.strftime('%d')))
'7'

```Brilliant!  I told a fellow Python programmer of mine as well as some other people.  I loved how I was able to reliably strip a leading 0 from the string without having to actually inspect the string and run it through some logic.  It was simple, short, elegant and clever.

It wasn't until a year later that I was digging through that library again cleaning up some cruft that had accumulated over time when I looked at that routine again and it dawned on me.  The reason they don't give formatting strings for the date/month without a leading 0 is because they already give you those.... in the object itself!

```

>>> spam
datetime.date(2008, 10, 7)
>>> spam.day, spam.month
(7, 10)
>>> str(spam.day), str(spam.month)
('7', '10')

```If you needed to store it as a string, just convert it with str().  If you're printing it %s or %d will do just fine.  The str(int()) trick was only needed because I was, in effect, converting to a string and adding the 0 first.  #-o

In my defense none of my friends caught it (or if they did they let me live my fantasy) and I have actually found uses for that str(int()) trick in areas where I really am starting with a 0-padded number.  :)

---

