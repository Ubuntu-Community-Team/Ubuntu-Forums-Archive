---
title: "HOWTO: One remind to rule them all"
date: 2007-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by reclusivemonkey on 2007-04-04
I discovered Remind some time ago via [http://www.43folders.com/](http://www.43folders.com/) and it has transformed my life. IMHO its by far the best calendaring software out there by a long way. If you are not afraid of the command line, and are looking for a way to remind yourself of everything, read on!

Remind is in the repos (Universe), so all you need to do is

```

sudo apt-get install remind

```

And that's it. You can now start to set up your remind files.

Remind depends on plain text files to store your reminders. The syntax of these files can be very simple or very complex depending on your needs. Usually though, you will find that a particular syntax suits a particular type of reminders. As a first example, lets start with something pretty much anyone would use; Birthdays.

In my home folder, I have a gtd (getting things done) folder. You can create your own folder, or indeed just keep them in your home folder. Remind is very flexible and will let you organise things just how you like. Within my gtd folder, I use a small number of files depending on the sort of reminder I want. Again, you can organise this just how you like, but here are mine for an example.

**Birthdays**
I have a birthdays.txt file. The contents look a little like this;

```

# Function for calculating age
FSET _yr_num(yr)		ORD(YEAR(TRIGDATE()) - yr)
# Birthdays
REM 20 Feb +14 MSG %"My [_yr_num(1973)] birthday%" is %b

```

The first uncommented line creates the function for calculating the age of the person who's birthday it is. You can use this function anywhere, but its particularly useful for birthdays. Then, I have my birthday in. Start with a "REM" for reminder, then put the date and month of the birthday. I add "+14" to get remind to start reminding me 14 days before the actual date of the birthday. Then add "MSG" and then the syntax you see in the line. You can of course change "My" to the name of the person you are adding the birthday of. The %b is substituted for today, or before that day, into "in n days time" where n is the number of days until the event (starts from the number of reminder days you specify). Although the syntax isn't completely straighforward, once you have added your first birthday, then you can simply copy this line and change the details for the next person. Of course once you have added a person you will get a reminder every year.

**Holidays**
In my holidays.txt file, I don't have any particular functions. However, I do use the "UNTIL" syntax fairly regularly in this file;

```

REM 9 Apr 2007 *1 UNTIL 10 Apr 2007 MSG Easter Holidays %b

```

Make sure you add *1 before the "UNTIL" as this is needed for remind to know you want to recur one day for the duration of the reminder. The "%b" creates a "today" in all reminders, so its entirely optional whether you use it.

**Work Tasks**
I like to keep all my work tasks in remind, because its quick and simple to add them, text files make them future proof and I can add priorities and times as well. In work_tasks.txt I have many items like;

```

REM 21 Mar 2007 PRIORITY 100 AT 17:00 MSG Send TPS Report 

```

This is a pretty simple reminder. We have just added a "PRIORITY" (anywhere between 0 and 9999) and an "AT TIME" in 24 hour clock. Of course you don't need either of these, but I find them particularly useful in my work reminders.

**Home Tasks**
No, not the housework; I have a better reminding system for that. My girlfriend! However, I do have little "techno" tasks I like to do. I usually like to know when I decided to start the task, and when I plan to do it by. For this I use a remind function again. At the top of work_tasks.txt I have;

```

FSET float(y,m,d) trigger(MAX(realtoday(), date(y,m,d)))
FSET due(y,m,d) "(" + (date(y,m,d)-trigdate()) + ")"
REM [float(2007,04,1)] MSG Create Remind HOWTO for Ubuntu Forums [due(2007,04,28)]

```

The float function defines when the task was started, and the due function is when the tasks is due. Again, once you have created one task, you can simply copy and paste to make sure you get it right. I actuall wrote a very simple script to create a default start date of today and a due date in 28 days time, which you can use if you like (see end of post).

You can create as many different text files you want, categorising them how you like. You can mix and match the syntax, but if you want to use a function be sure to include it at the top of that particular text file. Other option you may want to explore are "RUN" (for running script files) * add some more examples here.

Once you have created a few remind files, you can now start to enjoy the fruits of your labours. Firstly, we need to create an "include" file which lists your default remind files. The default for the version of remind in Ubuntu is ~/.reminders. The format is simple;

```

include /home/monkey/gtd/birthdays.txt

```

and that's it. Just add all the text files you want to use by default. You can use different include files for different functions, which is one of the benefits of using seperate text files for different reminders.

Now, just type "remind" at the CLI and you should see your reminders appear! This is just one of the ways remind can remind you. You can also get a calendar like output by using

```

remind -c

```

Adding numbers after c will increase the number of months produced. You can change the date you want to look at by adding the date after remind, so

```

remind 1 Jan 2010

```

Will give you your reminders for the 1st of January 2010. You tweak many, many things remind shows you with various command line arguments, read the man page for lots more. The man pages will also give you many, many more examples of the power and flexibility of remind. However, you are probably thinking that just a CLI remind program is pretty lame in this day and age. However, that's where the added extras come in!

**HTML**
Included with remind is a rem2html perl script. This script allows you to output your remind files as HTML, so you can look at them in a browser. Just pipe it all together like;

```

remind -p -m 1 April 2007 | rem2html  > calendar.html 

```

This will make a simple calendar from the 1st of April. This is very useful, but personally I found I had to make a couple of tweaks to the script to get it working as I wanted. If you have even a basic working knowledge with HTML/CSS/Javascript you should be able to do whatever you like with this. The things I like about the script are;

1. You can use your own remind.css file to style the calendar how you like.
2. With Javascript you can highlight reminders as you move your mouse over them.
3. HTML is platform agnostic, and you can find a browser just about anywhere!

I also created a little script to automate the production of my HTML calenders which I do on a daily basis. The script makes sure that previous and future month calendars are linked from the mini calendars. 

**iCal**
All the above is pretty clever, but what about other systems? Well remind also has an iCal script, which will output remind files to iCal format and bring in iCal formatted calendars. Personally I only use this for outputting remind to iCal format, so I can't vouch for it working the other way. Once I have converted a remind file to iCal, I then upload it to Google Calendar. I can then link to this from Evolution, which pulls it into my desktop. You can find the script on the [43 folders wiki]("http://wiki.43folders.com/index.php/Rem2ics").

**Other options**
As you can probably see, remind is very powerful and flexible and can be leveraged into many applications. I also like to use conky on my desktop, and remind fits in here easily with a list of todos at the bottom of my configuration. I also periodically pipe my reminders through festival so my computer can speak my reminders to me. There are some GUIs specifically for Remind, such as wryd, but they are not particularly to my liking, not when you can leverage other applications to use the HTML or iCal formatted remind files.

So there you have it. I've barely scratched the surface of remind here, so if you like what you have read so far, dive in, create your first few reminders and be sure to read the man page and share any tips you find yourself. You'll never forget an important date ever again! If you have any comments/suggestions for this HOWTO, please reply.

**Links**
[Roaring Penguin: Remind]("http://www.roaringpenguin.com/en/penguin/openSourceProducts/remind")
[43 Folders Wiki: Remind]("http://wiki.43folders.com/index.php/Remind")

---

### Post by reclusivemonkey on 2007-04-15
Well I see 126 views... any of you like remind? =]

---

### Post by ShirishAg75 on 2007-05-24
people are curious, but the idea that one has to CLI puts them off, if it had ncurses interfaces or something then I'm sure you would have got more people interested. The function stuff is also not easy to get a hang of. Not tht I'm criticizing, just why most people haven't answered I guess.

---

### Post by sk545 on 2007-05-24
yeah, good guide.  However, GUI is where its at and will be for a while to come.  But to each his/her own.

---

### Post by reclusivemonkey on 2007-05-24
> **ShirishAg75 said:**
> people are curious, but the idea that one has to CLI puts them off, if it had ncurses interfaces or something then I'm sure you would have got more people interested. 

There is;

[http://www.eecs.umich.edu/~pelzlpj/wyrd/](http://www.eecs.umich.edu/~pelzlpj/wyrd/)

My guide really isn't for newcomers; I know they fact that remind doesn't have a default GUI will immediately put them off. Maybe everyone who it appeals to already knows about it!

---

### Post by gordon58 on 2007-06-11
This looks very cool. I have to get used to CLI....

---

### Post by clesage on 2007-10-02
I just started using Remind, and I love it. Thanks for the writeup. If you feel like writing more, I would love to see some remind.css examples. I can't find any online.

I'm using both Remind and ToDoTxt from [http://www.todotxt.com](http://www.todotxt.com) and I output to Conky so that all my tasks and reminders are on the desktop.

I still haven't found the best way to integrate the todo list and remind. I would use Remind for Todo tasks, but I can't think of a simple way of marking them as done, without opening the text file in an editor.

Here's an excerpt from my .conkyrc if anyone is interested. The remind command is very short. :)

```

${font Bitstream Vera Sans Mono:size=7}
${execi 5 /home/clesage/docs/todo/birdseye.py /home/clesage/docs/todo/todo.txt /home/clesage/docs/todo/done.txt}

${font monospace:size=8}
${color #98c2c7}SBI:${color}
${execi 5 /home/clesage/docs/todo/todo.sh -d /home/clesage/docs/todo/.todo ls p:sbi}
${color #98c2c7}Freelancing:${color}
${execi 5 /home/clesage/docs/todo/todo.sh -d /home/sage/docs/todo/.todo ls p:Freelancing}
${color #98c2c7}Tasks:${color}
${execi 5 /home/clesage/docs/todo/todo.sh -d /home/sage/docs/todo/.todo ls p:tasks}
${color #98c2c7}Leisure:${color}
${execi 5 /home/clesage/docs/todo/todo.sh -d /home/sage/docs/todo/.todo ls p:Leisure}

${font Bitstream Vera Sans Mono:size=7}
${execi 15 rem}

```

---

### Post by dandyx on 2007-11-05
Great HOWTO!
I've got a question Google and the man-pages couldn't answer (most probably a stupid one - have been playing around with conky and remind for only a couple of days): trying to display the remind-calendar on my desktop I get only one week displayed and just one or two lines of the second week. The calendar is just cut off, sometimes horizontally uneven. I suppose it's not because conky can't display more lines for one script (my five-day weather forecast is displayed in one piece). Any suggestions or pointers?

---

### Post by reclusivemonkey on 2007-11-05
> **dandyx said:**
> Great HOWTO!
I've got a question Google and the man-pages couldn't answer (most probably a stupid one - have been playing around with conky and remind for only a couple of days): trying to display the remind-calendar on my desktop I get only one week displayed and just one or two lines of the second week. The calendar is just cut off, sometimes horizontally uneven. I suppose it's not because conky can't display more lines for one script (my five-day weather forecast is displayed in one piece). Any suggestions or pointers?

How are you getting the remind information to Conky? Can you attach your conkyrc?

---

### Post by reclusivemonkey on 2007-11-05
> **clesage said:**
> If you feel like writing more, I would love to see some remind.css examples. I can't find any online.


There was nothing specific to remind as its all done in HTML. Just style the tables, cells and links as you would normally. This was mine, or at least an early version;

```

html{
	background-color:black;
	color:white;
	font-family: Tahoma, sans-serif;
}

table{
	width:99%;
	border: solid 1px white;
	background: black;
	color:white;
}

td{
	font-size:8pt;
	border-size: 1px;
	border-style: solid;
	border-color: silver gray gray silver;
}

table table{
	border-style: none;
}

td td{
	text-align: center;
	border-style: none;
}

a:link{
	color:cyan;
}

a:hover{
	color:yellow;
}

a:visited{
	color:orange;
}

```

---

### Post by dandyx on 2007-11-05
Here comes my .conkyrc

TEXT
$color

${color black}${time %a, } ${color }${time %e %B %G} | 

${color black}${time %Z,    }${color }${time %H:%M:%S}

${color black}SYSTEM 
$nodename $sysname $kernel on $machine

${color black}CPU
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
${cpubar 8,240}
${cpugraph 25,240 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color black}NETWORK (${addr eth0}) 
Down: $color${downspeed eth0}              Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${upspeedgraph eth0
25,140 000000 00ff00}$color

${color black}${execi 3600 /bin/remind_script}

and the remind_script:

#!/bin/sh
remind -c -w100,3,0

---

### Post by reclusivemonkey on 2007-11-05
> **dandyx said:**
> 
#!/bin/sh
remind -c -w100,3,0

Try using -w80, I think 100 is too wide for a terminal. I know its the desktop, but you are still outputting to a terminal there.

Have you considered printing out to a list format rather than a calendar?

---

### Post by dandyx on 2007-11-05
With 'remind -c -w70,,' I get two weeks on the desktop. At least a progress. But I've seen a whole month on several screenshots. A list is no option for me. Thank you for the help by the way!

---

