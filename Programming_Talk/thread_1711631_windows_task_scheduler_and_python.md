---
title: "windows task scheduler and python"
date: 2011-03-21
forum: Programming Talk
---

### Post by Bigmon on 2011-03-21
I am trying to use windows task scheduler to run a program at a specific time of day. I have put the python program in a batch file and the task scheduler launches the file(or says it is running the program) but there are no results to be seen.

It is a program that should take a couple of seconds but after some 20 minutes the task scheduler still shows that it is "running" the program.

I put it in a batch file because I could not get task scheduler to run the python file direct. 

I do not have to use windows - but since the computer may be turned off at the designated time, I could not think of any other way.

Can anyone suggest anything that may help ?

---

### Post by DaithiF on 2011-03-21
Hi, so is there a connection to Ubuntu here or is this just pure Windows?  I don't know what you mean by:
> I do not have to use windows - but since the computer may be turned off  at the designated time, I could not think of any other way.

does the python program wait for some user input when it is run?  What happens when you run the batch file directly (via. Start->Run..., or from a windows terminal)

---

### Post by Bigmon on 2011-03-22
when the program is run direct, there is no problem. It does not need a user input - it basically takes information from the internet and saves it to  a file.

I referred to "windows task scheduler" since I am unaware of any other program that will run another program at a scheduled time (and will even power up the computer to do so).

---

### Post by DaithiF on 2011-03-22
add some logging to the python program to see whats happening -- open a file, write out a status line after each logical step in the program to see where its getting stuck.

---

### Post by Bigmon on 2011-03-22
The log file never shows anything because I guess the program is never run. Task Scheduler just shows "running" and nothing happens. I have tried task scheduler with other programs (.exe programs) and it is fine. So I am setting it correctly. Has it got something against .py programs ?

---

### Post by DaithiF on 2011-03-22
works fine for me when I set the command to run in scheduled tasks to something like:
```
C:\apps\Python26\python.exe c:\temp\test.py

```
(where first part is whereever you're python .exe is installed and second part is location of your script)

---

### Post by Bigmon on 2011-03-22
I still have a problem when I follow this path:

C:\Python31\python.exe C:\Users\myname\Desktop\folder\file.bat

A console window flashes up briefly, but the program does not run. Task Scheduler says that it is running the program however ?

---

### Post by DaithiF on 2011-03-22
why are you running the .bat file with python rather than a .py file?

---

### Post by Bigmon on 2011-03-22
This is because I could not get a .py file to run and after some research on the internet I found something somewhere that mentioned that you should put the python program in a batch file for task scheduler to run. This still did not work. 

I have followed this path as well and still no joy:

C:\Python31\python.exe C:\Users\myname\Desktop\folder\file.py

---

### Post by DaithiF on 2011-03-22
you can either have a batch file containing the contents:
c:\Python31\python.exe c:\path\to\yourfile.py
and run that batch file in task scheduler
**or**
in task scheduler run:
C:\Python31\python.exe c:\path\to\yourfile.py

you say you've tried the latter ... what happens when you enter that line into a windows terminal?

---

### Post by Bigmon on 2011-03-22
If I "browse" to the program through the windows terminal, press OK, the program launches. So if I copy and paste that path into the task scheduler and then run task scheduler, it does not work. When I follow this path:

C:\Python31\python.exe C:\Users\myname\Desktop\folder\file.py

It asks me if I want to "add arguments" ? (the argument apparently being "C:\Users\myname\Desktop\folder\file.py ")

---

### Post by DaithiF on 2011-03-22
So the python script is asking you a question about arguments when run via the python .exe but not when the .py file is executed directly?  That seems slightly odd but ok ... can you post the contents of the python script?

---

### Post by Bigmon on 2011-03-22
```

import datetime

import urllib.request

def find_temp_from_web():
    page = urllib.request.urlopen("http://www.foreca.com/United_Kingdom/Coningsby")
    text = page.read().decode("utf8")

    where = text.find("""<span class="warm txt-xxlarge"><strong>""")
    start_of_price = where  + 39
    #note - if single figures, need to strip "<". Need to wait till double figures to view
    end_of_price = start_of_price + 3

    temp = text[start_of_price:end_of_price]
    return temp



# strip the plus sign and < signs that will appear. Leave minus.
def strip_unwanted_charachter(temp):
    text = str(temp)
    stripped_temperatue = ""
    for c in text:
        if c in "< +":
            c = ""
        stripped_temperatue += c
    print(stripped_temperatue)
    return stripped_temperatue

def find_month():
    now = datetime.datetime.now()
    x = now.month

    print(x)
    return x

def find_day():
    now = datetime.datetime.now()
    x = now.day

    print(x)
    return x

def find_year():
    now = datetime.datetime.now()
    x = now.year

    print(x)
    return x

def add_to_file(temp,day,month,year):
    temp = str(temp)
    day = str(day)
    month = str(month)
    year = str(year)

    filename = "temperatue.dat"
    FILE = open(filename,"a")

    FILE.write (temp + " " + day + " " + month + " " + year + " " + "\n")

    FILE.close()






def main():
    month = find_month()
    day = find_day()
    year = find_year()
    temperatue = find_temp_from_web()
    stripped_temperatue = strip_unwanted_charachter(temperatue)
    add_to_file(stripped_temperatue,day,month,year)



main()


#this keeps window open
#r = input("")


```

---

### Post by DaithiF on 2011-03-22
works for me as a scheduled task.  Also nothing in that script is going to ask you about adding arguments or behave differently when run by python.exe vs. launched directly itself via a .py file association.

maybe if you post a screenshot of the terminal after you attempt to run it, showing the exact command you run, and the exact message output it might spark some ideas.

---

### Post by Bigmon on 2011-03-22
I can see from the brief time that the console window is open when the program is run through task scheduler that there is an error message when my python program tries to access the internet, but I cannot work out how to keep the console window open long enough. I have put a user input in the program to try and keep the window open but it does not work.

---

### Post by Bigmon on 2011-03-22
I have entered user input in various sections of "main" to see if I could find where the problem is, and it seems to be where I write to file. This code works fine:
```

def main():
    month = find_month()
    day = find_day()
    year = find_year()
    temperatue = find_temp_from_web()
    stripped_temperatue = strip_unwanted_charachter(temperatue)
    j = input("press enter to continue")
    add_to_file(stripped_temperatue,day,month,year)

```

but this causes an error and the console window quickly disappears:

```

def main():
    month = find_month()
    day = find_day()
    year = find_year()
    temperatue = find_temp_from_web()
    stripped_temperatue = strip_unwanted_charachter(temperatue)
    add_to_file(stripped_temperatue,day,month,year)
    j = input("press enter to continue")

```

---

### Post by DaithiF on 2011-03-23
the code that writes to a file uses just a filename without any path.  that means that the script will try to write the file to whatever is the working directory of the parent process.  Maybe that directory that task scheduler is starting from isn't writable by your user.  In short, use an explicit path to the file ... 

filename = 'c:\\path\\to\\temperature.dat'

---

### Post by Bigmon on 2011-03-23
If I am understanding you correctly, I tried this in the code:```

filename = "C:\Users\myname\Desktop\temperatue.dat"

```

But got this error:

(unicode error)"unicodeescape"codec can't decode bytes in position 2-4:truncated\UXXXXXXXX escape

---

### Post by DaithiF on 2011-03-23
> **Bigmon said:**
> If I am understanding you correctly, I tried this in the code:```

filename = "C:\Users\myname\Desktop\temperatue.dat"

```

But got this error:

(unicode error)"unicodeescape"codec can't decode bytes in position 2-4:truncated\UXXXXXXXX escape

double-slashes please:
filename = "C:\\Users\\myname\\Desktop\\temperatue.dat"

---

### Post by Bigmon on 2011-03-23
:KS
Thankyou very much - that works !! Being an inexperienced programmer I am not quite sure I understand why, but thanks again !!

---

### Post by Bronek-TB on 2011-06-08
Hi everybody!

The same problem - the same solution works for me.

DaithiF, Thank you very much!!!!

Regards
Bronek

---

### Post by jenders on 2012-06-30
I also found the solution extremely helpful. Thank you very much!

---

