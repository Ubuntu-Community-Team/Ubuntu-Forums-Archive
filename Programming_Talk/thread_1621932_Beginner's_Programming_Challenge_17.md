---
title: "Beginner's Programming Challenge 17"
date: 2010-11-14
forum: Programming Talk
---

### Post by appi2012 on 2010-11-14
Well, I won the last programming challenge, so here is the next one. This involves parsing input with regards to tasks. 

**[SIZE="4"]The challenge:[/SIZE]**
Build a program that asks for input in the format:
```
[Task Title] due [Date]
```
Where [Task Title] is the title of the task, and [Date] is a string representing a date. This date string could be:
[LIST=1]
[*]An Absolute Date ("5 Nov 2010")
[*]A week day ("Tuesday"--meaning its due the next day that is a Tuesday)
[*]A Relative Date ("Tomorrow", "the day after tomorrow", "in 2 days")
[/LIST]

The program should return an array with the title of the task, and an absolute representation of the due date.

**[SIZE="4"]Bonus:[/SIZE]**
At the very least, the program should understand absolute dates and "tomorrow."

Anything more counts as bonus.

Also, if you can get the program to actually keep track of your tasks, that would be great.

Remember, normal rules apply - the code should be all your code - try not to copy/paste other code, but read it, understand it, and type it yourself.

Good luck

---

### Post by austinprete on 2010-11-14
Not familiar with these challenges, are we free to code in any language for this?

---

### Post by schauerlich on 2010-11-14
> **austinprete said:**
> Not familiar with these challenges, are we free to code in any language for this?

Yup, although we usually ask that you use languages with a package available from the repos (for convenience). This includes most popular languages.

---

### Post by austinprete on 2010-11-14
Alright, I wasn't going to do anything crazy with it.  I'll probably either attempt it in C or Python.  Just wanted to make sure it wasn't a specific language.

---

### Post by krazyd on 2010-11-15
My entry in ruby:
```
#!/usr/bin/env ruby

require 'date'

puts "Enter your task in the form:"
puts "[Task Description] due [Date]"
date_string,task = gets.chomp.reverse.split(" eud ",2).each{|s| s.reverse!}

begin
    date = Date.parse(date_string)
rescue ArgumentError
    date = case
           when date_string.downcase.match("day after tomorrow")
               then Date.today + 2
           when date_string.downcase.match("tomorrow")
               then Date.today + 1
           when days = date_string.downcase.match(/in (\d+) day/)
               then Date.today + days[1].to_i
           else nil
           end
end

if !date
    $stderr.puts "ERROR: Unable to parse date."
    exit -1
end

puts task,date
```
Features:
[LIST]
[*]understands "tomorrow", "day after tomorrow" and "in xx day(s)", in addition to most permutations of YYYY-MM-DD.
[*]correctly handles the string " due " appearing in a task description.
[/LIST]

---

### Post by mo.reina on 2010-11-15
revised edition..
```
'''convert received date from stdin to datetime object with the following format, DD-month_abbreviation-YYYY
ex. 2000 12 november -> 12 Nov 2000'''

import datetime
import re

local = datetime.date.today()

def get_task():
	task_date = input('input task title and date:')
	return [a.rstrip().lstrip() for a in task_date.split('due')]

def parse_date(today):
	days = ['monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday', 'sunday']
	if 'in' in today:
		diff = int(re.search('(\d+)', today).group(0))
		reply = lang_format(diff)
	elif 'day after tomorrow' in today:
		diff = 2
		reply = lang_format(diff)
	elif today == 'tomorrow':
		diff = 1
		reply = lang_format(diff)
	elif today.lower() in days:
		reply = days_format(today, days)
	else:
		reply = iso_format(today)
	if reply != None:
		return reply

def iso_format(today):
	date_formats = ["%d %b %Y", "%d %b %y", "%Y %b %d", "%d %B %Y", "%d %B %y"]
	for form in date_formats:
		try:
			iso_date = datetime.datetime.strptime(today, form)
			return iso_date
		except ValueError:
			pass
	else:
		print("entry not valid")
		return None

def lang_format(diff=1):	
	'''lang_format (int -> datetime object)
	add the integer given to today's date and return 
	ex. today = 2000-12-11, int = 3 -> 2000-12-14'''

	future = datetime.datetime.toordinal(local)
	tomorrow = future + diff
	tomorrow = datetime.date.fromordinal(tomorrow)
	return tomorrow

def days_format(today, days):
	'''days_format (string, list -> datetime object)
	take the literal day as input and calculate the date that it falls on.
	ex. today is thursday, nov. 11
	string = friday -> nov. 12'''

	now = datetime.datetime.today().strftime("%A").lower()
	days = days * 2
	diff = days[days.index(now):].index(today)
	if diff == 0: #diff == 0 if the entered day is the same as today, add 7 to calculate the date that the day falls on next
		diff = 7
	return lang_format(diff)

def main():
	task_date = get_task()
	future = parse_date(task_date[1])
	print("{} due {}".format(task_date[0], future))

if __name__ == "__main__":
	main()
```

understands 'tomorrow', 'the day after tomorrow', 'in xx days', any day of the week

*fixed bug: if 'tomorrow', 'the day after tomorrow', 'in xx days', any day of the week carries over into the next month, it will crash.  haven't handled it yet. 

oh the code is commented, it might make it a bit harder to read here since there's no syntax highlighting.

---

### Post by Arndt on 2010-11-15
> **mo.reina said:**
> nowhere near as short or as concise as what's above but....
```
import datetime

def from_abs_date(given_date):
    '''from_abs_date( given_date ) -> absolute date
    will take an absolute date, e.g. 2000 nov 21 and return an absolute date in the format of DD-month_abbreviation-YYYY, e.g. 21 nov 2000'''

    try:
        return_date = datetime.datetime.strptime(given_date, "%d %b %Y")
    except ValueError:
        try:
            return_date = datetime.datetime.strptime(given_date, "%d %b %y")
        except ValueError:
            try:
                return_date = datetime.datetime.strptime(given_date, "%Y %b %d")
            except ValueError:
                try:
                    return_date = datetime.datetime.strptime(given_date, "%y %b %d")
                except ValueError:
                    print("not a valid entry")
    return return_date.strftime("%d %b %Y")

def from_date(given_date, days):
    '''from_date( day, list-of-days ) -> absolute date.
    will take a day of the week, e.g. 'friday', and give the absolute date of that day, e.g. the date of the next friday.'''
    
    today = datetime.datetime.today().strftime("%A").lower() # this is the current day today
    given_date = given_date.lower() # user given day
    for difference, day in enumerate(days[days.index(today):]): # checks the difference in days between today and the user given day
        if day == given_date:
            future = str(int(datetime.datetime.today().strftime("%d")) + difference)
            break
    future = future + datetime.datetime.today().strftime(" %b %Y")
    return from_abs_date(future)

def from_string(days, offset):
    '''from_string( list-of-days, offset ) -> absolute date.
    tomorrow = offset of 1
    the day after tomorrow = offset of 2
    in x days = offset of x'''
    today = datetime.datetime.today().strftime("%A").lower()
    future = days[days.index(today) + offset: days.index(today) + offset + 1][0]
    return from_date(future, days)

def main():
    
    days = ['monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday', 'sunday']
    days = days * 2

    task, given_date = input('please enter the task title and the due date: ').split('due')
    given_date = given_date.lstrip()

    try:
        int(given_date.split()[0])
        return_date = from_abs_date(given_date)

    except ValueError:
        if given_date.split()[0] in days:
            return_date = (from_date(given_date, days))
        else:
            if given_date.lower() == 'tomorrow':
                return_date = from_string(days, 1)
            elif given_date.lower() == 'the day after tomorrow':
                return_date = from_string(days, 2)
            else:
                try:
                    int(given_date.split()[1])
                    return_date = from_string(days, int(given_date.split()[1]))
                except ValueError:
                    print("i'm all out of ideas")

    answer = [return_date, task]
    print(answer)

if __name__ == "__main__":
    main()
```

understands 'tomorrow', 'the day after tomorrow', 'in xx days', any day of the week

bug: if 'tomorrow', 'the day after tomorrow', 'in xx days', any day of the week carries over into the next month, it will crash.  haven't handled it yet.

oh the code is commented, it might make it a bit harder to read here since there's no syntax highlighting.

The from_abs_date function can be cleaned up somewhat, which will make it easier to extend:

```
def from_abs_date(given_date):
    '''from_abs_date( given_date ) -> absolute date
    will take an absolute date, e.g. 2000 nov 21 and return an absolute date in the format of DD-month_abbreviation-YYYY, e.g. 21 nov 2000'''

    formats = ["%d %b %Y", "%d %b %y", "%Y %b %d", "%y %b %d"]

    for format in formats:
        try:
            return_date = datetime.datetime.strptime(given_date, format)
            return return_date.strftime("%d %b %Y")
        except ValueError:
            pass

    print("not a valid entry")
    return
```

Admittedly it doesn't do exactly the same thing when no format works, but that can be fixed.

---

### Post by mo.reina on 2010-11-15
> **Arndt said:**
> The from_abs_date function can be cleaned up somewhat, which will make it easier to extend:

```
def from_abs_date(given_date):
    '''from_abs_date( given_date ) -> absolute date
    will take an absolute date, e.g. 2000 nov 21 and return an absolute date in the format of DD-month_abbreviation-YYYY, e.g. 21 nov 2000'''

    formats = ["%d %b %Y", "%d %b %y", "%Y %b %d", "%y %b %d"]

    for format in formats:
        try:
            return_date = datetime.datetime.strptime(given_date, format)
            return return_date.strftime("%d %b %Y")
        except ValueError:
            pass

    print("not a valid entry")
    return
```

Admittedly it doesn't do exactly the same thing when no format works, but that can be fixed.

thanks, that makes it much easier to read.

---

### Post by ziekfiguur on 2010-11-15
I didn't know about the python datetime module, so i have been playing with regular expressions. My solution may not be very efficient but it supports most different input formats up till now. Also, it's easily expandable.
Here is my (Python) script:
```

#!/usr/bin/env python

import re, sys, time

days_long = ['monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday', 'sunday']
days_short = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun']
months_long = ['january', 'february', 'march', 'april', 'may', 'june', 'july', 'august', 'september', 'october', 'november', 'december']
months_short = ['jan', 'feb', 'mar', 'apr', 'may', 'jun', 'jul', 'aug', 'sep', 'oct', 'nov', 'dec']

taskexpr = re.compile(r'(.*)\s+due\s+(.*)')
tomorrowexpr = re.compile(r'.*?(((\d+)\s+days\s+after\s+)|(the\s+day\s+after\s+)+)?(tomorrow)')
inxdaysexpr = re.compile(r'.*?in\s+(\d+)\s+days')
weekdayexpr = re.compile(r'(' + '|'.join(days_long + days_short) + r')')
dateexpr = re.compile(r'(\d\d?)\W+(([a-z]+)|(\d\d?))\W+(\d\d(\d\d)?)')
date2expr = re.compile(r'the (\d\d?)(st|nd|th) of (' + '|'.join(months_long) + r') (\d\d(\d\d)?)')

today_year    = int(time.strftime('%Y'))
today_month   = int(time.strftime('%m'))
today_day     = int(time.strftime('%d'))
today_weekday = int(time.strftime('%w'))

tasks = []

def to_int_time(year, month, day, add_days = 0):
    date = '{0:04d} {1:02d} {2:02d}'.format(year, month, day)
    date = time.mktime(time.strptime(date, '%Y %m %d'))
    date += 86400 * add_days # 86400 seconds in a day
    return date

def parse_tomorrow(match):
    days = 1
    if match.group(4): # the day after
        days += len([i for i in match.group(1).split() if i == 'after']) # just count the number of afters
    elif match.group(2): # n days after
        days += int(match.group(3))
    return to_int_time(today_year, today_month, today_day, days)

def parse_inxdays(match):
    return to_int_time(today_year, today_month, today_day, int(match.group(1)))

def parse_weekday(match):
    day = match.group(1)
    if day in days_long:
        day = days_long.index(day) + 1 # +1 because monday is 1 instead of 0
    if day in days_short:
        day = days_short.index(day) + 1
    day = (day - today_weekday) % 7
    if day == 0: day = 7 # make sure it is always the next xxxday, and not today
    return to_int_time(today_year, today_month, today_day, day)

def parse_date(match):
    day = int(match.group(1))
    year = int(match.group(5))
    if year < 100:
        year += 2000
    if match.group(4):
        month = int(match.group(4))
    elif match.group(3):
        month = match.group(3)
        if month in months_long:
            month = months_long.index(month) + 1 # +1 because january should be 1 instead of 0
        elif month in months_short:
            month = months_short.index(month) + 1
        else:
            #invalid month
            return None
    return to_int_time(year, month, day)

def parse_date2(match):
    day = int(match.group(1))
    month = months_long.index(match.group(3)) + 1
    year = int(match.group(4))
    if year < 100:
        year += 2000
    return to_int_time(year, month, day)

def parse(date):
    match = tomorrowexpr.match(date)
    if match:
        return parse_tomorrow(match)

    match = inxdaysexpr.match(date)
    if match:
        return parse_inxdays(match)

    match = weekdayexpr.match(date)
    if match:
        return parse_weekday(match)

    match = dateexpr.match(date)
    if match:
        return parse_date(match)

    match = date2expr.match(date)
    if match:
        return parse_date2(match)

    # everything failed
    return None

while True:
    input = sys.stdin.readline()
    if not input:
        break
    match = taskexpr.match(input)
    if not match:
        # print warning
        continue
    title = match.group(1)
    date = parse(match.group(2).strip().lower())
    tasks.append((date, title))

tasks = [i for i in tasks if i[0] != None]
tasks.sort()

sys.stdout.write('Today is {0:s}, your tasks:\n'.format(time.strftime('%d %B %Y')))

for t in tasks:
    sys.stdout.write('{0:s} due {1:s}\n'.format(t[1], time.strftime('%d %B %Y', time.localtime(t[0]))))


```
and my test input:
```

t1 due tomorrow
t2 due tuesday
t3 due in 2 days
t4 due 30 nov 2010
t5 due the 14th of january 2011
t6 due the day after the day after tomorrow
t7 due 7 days after tomorrow
t8 due wednesday
t9 due 12/06/2014
t10 due the day after the day after the day after tomorrow
t11 due 16 february 2012
t12 due 15-jun-2011

```I also let my program sort the tasks by their due time.

EDIT 1:
I just noticed that i have the same bug as mo.reina when the days go over the end of the month, working on that now.

EDIT 2:
fixed it.

---

### Post by appi2012 on 2010-12-01
Just a reminder that this contest is still going on.

Also, I'll probably judge entries after New Year's, so if you're working on an entry now, try to have it in before them.

Great job for the people who already submitted entries, and good luck to all those still working!

---

### Post by YourMomsASmurph on 2010-12-02
Don't know how all your programs are so tiny. Looks like I'm gonna hit 600 lines. (C++) Though that does include my own custom Date and Task classes.

Question though: Should we include input validation

---

### Post by roccivic on 2010-12-03
Here's mine:

[PHP]<?php
    error_reporting(0);
    function error($text) {
        echo "ERROR: ".$text."<p><a href='".$_SERVER['PHP_SELF']."'>Click here to go back.</a>";
        die();
    }
?>
<!DOCTYPE html>
<head><title>Tasks</title></head>
<body>
<div style="width: 500px; padding: 20px; border: 1px solid black;">
<?php
    echo "Welcome. Today is " . date('l, j F Y') . ".<p>";
    if ( $_GET['action'] == "add" ) {    // If the user has requested to add a new task
        // Parse the parameter and , if possible, save the task
        $string = trim($_GET['task']);
        if ( empty( $string ) ) {
            error("No valid input was found.");
        }
        if ( strpos( $string, " due " ) === false ){
            error("Unable to parse the input.");
        }
        
        $date = substr( $string, strrpos($string, " due ") + strlen(" due ") );         
        $timestamp = strtotime( $date );
        if ( $timestamp == -1 || $timestamp === false ) { // PHP's internal could not parse the date, maybe it is the "in N timeunits" format.
			if ( strpos( $date, "in " ) !== false ) {
				if ( strpos( $date, " day" ) !== false ) {
					$word = " day";
					$multiplier = 24 * 3600;
				} elseif ( strpos( $date, " week" ) !== false ) {
					$word = " week";
					$multiplier = 7 * 24 * 3600;
				} else {
					error("Unable to parse the date.");
				}
				$start = strpos( $date, "in " ) + strlen( "in " );
				$length = strpos( $date, $word ) - $start;
				$date = trim(substr( $date, $start, $length ));
				if ( is_numeric( $date ) && (int)$date == $date && (int)$date > 0 ) {
					$date *= $multiplier;
					$timestamp = time() + $date;
				} else {
				   	error("Unable to parse the date.");
				}
			} else {
				error("Unable to parse the date.");
			}
        }
        
        $new_task = substr( $string, 0, strrpos($string, " due ") );
        $new_task =  $new_task . " due on " . date('l, j F Y', $timestamp) . "\n";
        echo "New task: " . $new_task;
        
        @ $fp = fopen( "taskfile", "a+" );
        if ( !$fp ) {
            echo "<p>";
            error("Unable to open the taskfile for writing.");
        } else {
            fputs($fp, $new_task);
            echo " has been successfully saved.";
            echo "<p><a href='".$_SERVER['PHP_SELF']."'>Click here to go back.</a>";
        }

    } else { // This is the default action
         // Read the file and display saved entries
        $tasks = array();
        @ $fp = fopen( "taskfile", "r" );
        if ( $fp ) {
            while ( !feof( $fp ) ) {
                $temp = fgets( $fp, 999 );
                if ( $temp ) {
                    $tasks[] = $temp;
                }
            }
        }
        echo "You currently have " . count( $tasks ) . " tasks.<p>";
        if ( count( $tasks ) ) {
            foreach ( $tasks as $key => $value ) {    
                echo "Task " . $key . ": $value<br>";
            }
        }
        ?>
        <p>
        <div style="padding: 15px; border: 1px dotted gray;">
        Please input a new task in the following format:<br><b>[Task Title] due [Date]</b> and click "Submit"<p>
        <form method="GET">
                <input type="hidden" name="action" value="add">
                <input type="text" name="task" style="width: 300px;">
                <input type="submit" value="Submit" style="width: 100px;">
        </form>
        </div>
        <?php
    }
?>
</div>
</body></html>[/PHP]

Features:
* Saves entries to a file and displays them
* Correctly handles "due" in the title

Sample input:
```
foo due now
foo due today
bar due wednesday
bar due tomorrow
foobar due next week
foo bar due next friday
bar foo due 5 dec 2010
bar goo due 5-12-2010
foo due in 2 days
foo due in 2 weeks
```

Corresponding output:
```
foo due on Friday, 3 December 2010
foo due on Friday, 3 December 2010
bar due on Wednesday, 8 December 2010
bar due on Saturday, 4 December 2010
foobar due on Monday, 6 December 2010
foo bar due on Friday, 10 December 2010
bar foo due on Sunday, 5 December 2010
bar goo due on Sunday, 5 December 2010
foo due on Sunday, 5 December 2010
foo due on Friday, 17 December 2010
```

Peace

---

### Post by mo.reina on 2010-12-07
put up the revised edition

```
>>> main()
input task title and date:foo due tomorrow
foo due 2010-12-08
>>> main()
input task title and date:fue due day after tomorrow
fue due 2010-12-09
>>> main()
input task title and date:fue due 12 nov 2010
fue due 2010-11-12 00:00:00
>>> main()
input task title and date:foo due in 10 days
foo due 2010-12-17
>>> main()
input task title and date:foo due friday
foo due 2010-12-10
>>> main()
input task title and date:foo due in 365 days
foo due 2011-12-07

```

---

### Post by cprofitt on 2011-01-11
bump: will this one be concluding and a new one be put up soon?

---

### Post by appi2012 on 2011-01-12
Yes, the contest has closed, and I'm reviewing the entries. A winner will be announced shortly.

---

### Post by Tony Flury on 2011-01-13
As an aside - on a project I once worked on we developed a date algebra for our reporting system - so we could set up a repeating schedule of reports with variable dates, and run the same reports over weeks, months etc. The algebra worked like this

Start -7D
End -1D

When this report runs the Start paremeter would be calcualted at 7 days prior to the run date and the End parameter would be calulated as 1 day prior to the run date.

We also could do Weeks - using the W Identifier, and Months - using the M Identifier - these had wrinkles - W went to the previous Monday (i.e. the start of the business week), unless the current date was a monday), and M went to the start of the Month (unless the current date was the 1st).

Algebra was calculated left to right so : 

Start : -2W
End : -1W - 1D

this would run a report over the last full week - Monday to Sunday

Start : -2M
End : -1M -1D

Would run the report but over the last full month.

Operators worked intuitively "-" (minus) moved the "clock" backwards, "+" moved it forward.

so : 
Start : -1W
End : +1W -1D

Would run the report for this current weeks data.

---

### Post by appi2012 on 2011-01-16
**And the Winner is...**
**roccivic**, for the nice display, saving of the tasks, and good error handling.

I would like to give a special shout out to krazyd for the (extremely) concise code. Also, ziekfiguur had a very unique, expandable solution.

All the code I tried worked (I only had to make some small changes), so great job to all participants!

As per contest tradition, roccivic is now in charge of submitting the next challenge.

Good luck to all participants in future challenges!

---

### Post by roccivic on 2011-01-16
That's nice, thanks.

I'll post a new challenge some time soon.

Rouslan

---

### Post by Queue29 on 2011-01-16
You can play with roccivic's solution live here:

[http://bozosort.com/dloads/roccivic.php](http://bozosort.com/dloads/roccivic.php)

No hacking my server please :(

---

### Post by roccivic on 2011-01-17
> **Queue29 said:**
> You can play with roccivic's solution live here:

[http://bozosort.com/dloads/roccivic.php](http://bozosort.com/dloads/roccivic.php)

No hacking my server please :(

I just exploited an XSS vulnerability on it, lol. :biggrin:
But that doesn't count as hacking your server, right?

You might want to change line 16, from:
[PHP]        $string = trim($_GET['task']);[/PHP]
to:
[PHP]        $string = trim(strip_tags($_GET['task']));[/PHP]

---

