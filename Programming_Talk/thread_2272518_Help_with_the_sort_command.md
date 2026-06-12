---
title: "Help with the sort command"
date: 2015-04-07
forum: Programming Talk
---

### Post by GrouchyGaijin on 2015-04-07
Hi Linux Guys,

Background:
I am using remind to keep track of important things I need to do and the deadline for doing them.
I call the reminders from Conky and they appear on my desktop.

I have a script that allows me to enter a task's information and that task is then added to the reminders' file in remind's format.  Example:  ```
REM 2015-05-04 +30 AT 14:00 MSG Second Draft %b (in [_countdown(trigdatetime()-current())])

```
 
The Problem:
New reminders are added at the end of the reminders' file and then displayed in Conky in the order they were added to the file.  I'd like them sorted with tasks due soonest at the top and tasks that are due latest at the bottom.

Work around:  I use the Sublime text editor and am able to open the reminders' file and sort a selected section of text.  If I select all of the reminders and then choose sort I can have the list exactly the way I want it - reminders sorted by due date with the item that is due next at the top of the list.

[IMG]https://docs.google.com/uc?id=0B05fj21T_0AtalFYTU5sZ21LWG8&export=download[/IMG]

[I]**Caveat:**  The reminders' file has several lines of text at the top of the file that need to remain the way they are.
The first reminder is on line number 13.[/I]

Question:
Is there a command line way to sort a file and have the sort start at a given line number (ie 13) and continue to the end of the file?  I've searched Google and found some examples with header and tail, but did not find anything about sorting to the end of a file.

---

### Post by Lars Noodén on 2015-04-07
> **GrouchyGaijin said:**
> ...
 
The Problem:
New reminders are added at the end of the reminders' file and then displayed in Conky in the order they were added to the file.  I'd like them sorted with tasks due soonest at the top and tasks that are due latest at the bottom.

...
Question:
Is there a command line way to sort a file and have the sort start at a given line number (ie 13) and continue to the end of the file?  I've searched Google and found some examples with header and tail, but did not find anything about sorting to the end of a file.

About [sort](http://manpages.ubuntu.com/manpages/trusty/en/man1/sort.1.html), you can use -k to define a start/stop position for sorting.  From the data line you showed, something like this might work:

```
sort -k 2,2 -k5,5n
```

It looks at the second and fifth columns and sorts the latter numerically.

About sorting starting after a certain line, you'd have to pipe it through [sed](http://manpages.ubuntu.com/manpages/trusty/en/man1/sed.1posix.html) to skip the n first lines.

```

sed -e '1,4d'

```

That will print starting with the 5th line.  But if your file is shorter than 5 lines, it won't print anything.

---

### Post by ofnuts on 2015-04-07
> **Lars Noodén said:**
> AAbout sorting starting after a certain line, you'd have to pipe it through [sed]("http://manpages.ubuntu.com/manpages/trusty/en/man1/sed.1posix.html") to skip the n first lines.

```

sed -e '1,4d'

```

That will print starting with the 5th line.  But if your file is shorter than 5 lines, it won't print anything.

Also:
```

tail -n +5

```
To start printing at the 5th line.

---

### Post by GrouchyGaijin on 2015-04-07
Thank you guys,

I really appreciate the help.
This is close to what I want to do, but not quite.  I think the problem is either my explanation or that I didn't understand something.

The file that contains lines I want to sort has this at the beginning of the file:

```

INCLUDE /home/john/Reminder-files/remindershollidays
# Helper functions
FSET _days(x) iif(x>1, x + " days", x==1, "1 day", "")
FSET _hrs(x)  iif(x>1, x + " hours", x==1, "1 hour", "")
FSET _mins(x) iif(x>1, x + " minutes", x==1, "1 minute", "")
FSET _smush(x, y) iif(x != "" && y != "", x + " and " + y, x + y)

# Main function
FSET _countdown(x) _smush(_smush(_days(x/1440), _hrs((x - 1440*(x/1440))/60)), _mins(x%60))


```

I want all of that to stay where it is, unchanged.  These are needed for remind to work.

When I tried ```
sed -e '1,12d' /home/john/Reminder-files/test | sort -k 2,2 -k5,5n
``` 
I got the reminders sorted the way I want, but the code at the top of the file was deleted.  I think the d in the sed command deleted those lines.
I then tried ```
tail -n +12 /home/john/Reminder-files/test | sort -k 2,2 -k5,5n
``` and got the same result.

Right now the file that I have has 20 lines.  That will change as I add more reminders.  I want to keep everything from lines 1 through 12 the way they are.
The sort should start with the data on line 13 and continue to the end of the file (which right now is line 20, but will be past line 20 as soon as I add another reminder).

Is it possible to print lines 1-12 the way they are and sort then print lines 13 to EOF.  (I am not sure if print is the correct word, I mean display or write to a file).

So in the end all of the lines in the file are printed, but the sorting affects only lines 13 onward. Does that make sense?

---

### Post by GrouchyGaijin on 2015-04-07
Hi Guys,

Thank you so much for the tips.  Using your suggestions and Goggling further I found a solution.
The page with an explanation is at: [http://unix.stackexchange.com/questions/75366/sort-part-of-a-file](http://unix.stackexchange.com/questions/75366/sort-part-of-a-file) 

In my case, I edited the command to:
```

(head -n 12; sort -k 2,2 -k5,5n) </path/to/file 1<> /path/to/output/file/with/same/name

```

I am going to mark this as solved.

---

