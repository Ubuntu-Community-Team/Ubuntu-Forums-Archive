---
title: "Date calculator - written in Python and Qt4"
date: 2010-04-26
forum: Programming Talk
---

### Post by Siph0n on 2010-04-26
Here is my first attempt at a gui. Please let me know how it works and any improvements that can be helpful. Download the svn for the latest.

Right now it adds and subtracts days, weeks, months, and years. When adding months, if the end month does not have the day in the start month (jan 31st + 1 month), than the end month is set to the last day of that month.

When adding years, if the start date is feb 29th (leap year), and the end date is not a leap year, than the end date is feb 28th of that year.

The End Of Month checkbox only works if the start date is the last day of the month, and you are adding or subtracting months. If it is the last day of the month, and the End of Month checkbox is checked, than the end date is rounded to the end of the month. Example: April 30th + 1 month = May 31st, instead of May 30th.

The Skip Weekends checkbox only works when you are adding or subtracting days. It will not count the weekends. Example: April 3rd (Saturday) + 15 days = April 23rd.

[http://code.google.com/p/date-calculator/](http://code.google.com/p/date-calculator/)

[Edit]
There is a command line only version, and gui version. The dateCalc_cli.py file is the command line script. It is not as up to date as the gui version. The gui script is dateCalc_ui.py and dateCalc.py. Run the dateCalc.py file to start the program. dateCalc_ui.py has all the code and layout. dateCalc.py only starts dateCalc_ui.py. I used the Qt Designer to make the gui, and did not know a different way. Constructive criticism on how to organize and maintain the files are welcome. Thanks!
[/Edit]

---

### Post by sujoy on 2010-04-27
having gone through the cli program, i would suggest that you read up on the following,

[LIST]
[*]dicts
[*]exception handling
[*]command line argument parsing
[/LIST]

good attempt though :)

---

### Post by Siph0n on 2010-04-27
Thanks sujoy. I added the argument list, and exception handling into the command line version (rev 22). I plan into dictionaries later.

[Edit]
How would dictionaries help me? The only thing I can think of is using them for the days of the month, but I think the way I do it is just fine for that.

Also, I added functions, to try and make the program more readable, and modular.
[/Edit]

---

### Post by sujoy on 2010-04-28
yea the code is much better organised now :D

as for dicts, well,

```
if endDate.isoweekday()==1: print '(Monday)'
    elif endDate.isoweekday()==2: print '(Tuesday)'
    elif endDate.isoweekday()==3: print '(Wednesday)'
    elif endDate.isoweekday()==4: print '(Thursday)'
    elif endDate.isoweekday()==5: print '(Friday)'
    elif endDate.isoweekday()==6: print '(Saturday)'
    elif endDate.isoweekday()==7: print '(Sunday)'

```

can be 

```

print weekdays[endDate.isoweekday()]
```
if you have a dict weekdays, so on and so forth

---

### Post by Bachstelze on 2010-04-28
Not to mention that it would make l10n much easier.

---

### Post by Siph0n on 2010-04-28
Thanks for the suggestion sujoy. It does look a lot nicer now. I am up to revision 27 now! :)


Bachstelze, What is l10n ?

---

### Post by Bachstelze on 2010-04-28
> **Siph0n said:**
> 
Bachstelze, What is l10n ?

Localization. Because it's long an there's 10 letters beween the initial l and the final n, it's abbreviated l10n. ;) Basically, having all your string literals defined in one place and having your program only use references to those, not directly the literals themselves, makes translating your app easier if someone wants to.

---

