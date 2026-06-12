---
title: "Matplotlib value error"
date: 2009-09-07
forum: Programming Talk
---

### Post by filifunk on 2009-09-07
I'm trying to plot some financial data in matplotlib.

I'm plotting simply plot(x, y)

where x are dates

and y are closing prices.

It's not working I get this:

ValueError: Invalid literal for float(): 2009-09-04


So I figured maybe my dates had to be parsed, so I did this:

```


for i in x:
    strptime(i, '%Y-%m-%d')


```that didn't work either.

The problem is in my dates.  It looks like a formatting issue, but I've only started on python for the last two weeks.

Maybe I need to parse it using the datetime module:

datetime.strptime(*date_string*, *format*)[¶]("http://docs.python.org/library/datetime.html#datetime.datetime.strptime")Return a [datetime]("http://docs.python.org/library/datetime.html#datetime.datetime") corresponding to *date_string*, parsed according to *format*.  This is equivalent to datetime(*(time.strptime(date_string, format)[0:6])). [ValueError]("http://docs.python.org/library/exceptions.html#exceptions.ValueError") is raised if the date_string and format can&#8217;t be parsed by [time.strptime()]("http://docs.python.org/library/time.html#time.strptime") or if it returns a value which isn&#8217;t a time tuple.

     - from the python website

but I just imported the module and added 'datetime' before strptime and that didn't change anything.

hmmm.....suggestions?

---

### Post by Can+~ on 2009-09-07
> **filifunk said:**
> hmmm.....suggestions?

Learn python first, then start with individual modules.

The problem here is basic types; plot expects two numbers; you're trying to hand a string ("DD-MM-YYYY") and later a datetime object (which may contain an number, but not exactly what python expects).

Now, I first thought on using the seconds from the epoch as a X value, but then I realized that Matplotlib has a "plot_date" function:

[http://matplotlib.sourceforge.net/api/pyplot_api.html#matplotlib.pyplot.plot_date](http://matplotlib.sourceforge.net/api/pyplot_api.html#matplotlib.pyplot.plot_date)

I'm happy that you are learning python to do some real application, but your last set of threads (getting things from csv, dates, plotting) seems that you just jumped in instead of doing the proper learning, because most of those issues are trivial once you grasp the basic language and learn how to read a manual.

---

### Post by filifunk on 2009-09-08
OK, will do.  I think I'll go through more tutorials.  I did buy a book, and have been through 75% of it.  I have been through 50% of another tutorial.  I generally understand what I see as examples, but actually creating is the hard part, and what I think will help me learn best.

I've never programmed before, and I've been doing some python for about a couple weeks total.

yeah and I have a hard time understanding the manuals.  And by manuals I think you mean whats on the python website to explain modules.  I think if I knew how to read those, I'd feel a lot more comfortable.  Probably just takes time.

---

