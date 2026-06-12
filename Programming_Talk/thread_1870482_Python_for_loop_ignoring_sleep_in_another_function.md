---
title: "Python: for loop ignoring sleep in another function?"
date: 2011-10-27
forum: Programming Talk
---

### Post by Nico-dk on 2011-10-27
I'm working on a Python 2.7 script which contains a call from one function to another function. My problem is that the ' another function' (that's calling 'one function' doesn't seem to wait for the 'one function' to finish before continuing.

If you look at the code example below, another_function continues the for loop. I thought the script would go to the one_function wait for it to finish before carrying on with the for loop, or am I missing something here?

```
def one_function(wait):
    child = subprocess.Popen(shell_command.split())
    sleep(wait_time)

    child.kill()

def another_function():
    for i in range(3):
        do some stuff
        
        for j in somelist:
            do some more stuff

            one_function(wait)


another_function()
```

---

### Post by karlson on 2011-10-27
> **Nico-dk said:**
> I'm working on a Python 2.7 script which contains a call from one function to another function. My problem is that the ' another function' (that's calling 'one function' doesn't seem to wait for the 'one function' to finish before continuing.

If you look at the code example below, another_function continues the for loop. I thought the script would go to the one_function wait for it to finish before carrying on with the for loop, or am I missing something here?

```
def one_function(wait):
    child = subprocess.Popen(shell_command.split())
    sleep(wait_time)

    child.kill()

def another_function():
    for i in range(3):
        do some stuff
        
        for j in somelist:
            do some more stuff

            one_function(wait)


another_function()
```

What's the value of "wait"?

---

### Post by Nico-dk on 2011-10-27
10 seconds, but the child is usually killed within 2-4 seconds

*edit*
Maybe the full script would help


```
#!/usr/bin/env python

import os, subprocess, errno
from time import sleep


wait_time = 10


def run_epiphany(wait_time):
    """Launches Epiphany.
    Runs shell_command while returning it for later termination"""

    # Vars
    weburl = "http://www.somesite.com"
    shell_command = "epiphany " + weburl


    child = subprocess.Popen(shell_command.split())
    sleep(wait_time)

    child.kill()



def cleanup():
    """Deletes histury related files in epiphany"""

    # Vars
    epiphany_path = "/home/nico/.gnome2/epiphany/"
    listing = os.listdir(epiphany_path + "favicon_cache/")
    filelist = ['ephy-history.xml', 'ephy-favicon-cache.xml',
            'session_crashed.xml', 'cookies.sqlite']


    # Iterate through files
    for i in range(3):

        if len(listing) == 0:
            # Delete favicons -- not important
            for infile in listing:
                os.remove(epiphany_path + "favicon_cache/" + infile)

        # Check for files, delete when neccessary
        for filename in filelist:
            try:
                fileprobe = open(epiphany_path + filename)

            # Error 2 = File does not exist
            except IOError as err:
                if err.errno == 2:
                    pass # If file doesn't exist, do nothing
            else:
                os.remove(epiphany_path + filename)

        run_epiphany(wait_time)


cleanup()
```

---

### Post by lexinerus on 2011-10-27
Well, it's still unclear, but maybe I can help a little.

Right now the function going to execute only 3 times, because is into range(3) for statement.

I don't know if you need execute the 'run_epiphany' function into the for statement that runs by each filename in filelist, so if that's true, you need move the function into that for statement. (It may cause a speed or non-execute illusion).

I hope to be clear,

Cheers

---

### Post by Nico-dk on 2011-10-27
Thanks, problem "solved" :)

Found this in the documenation:
> The actual suspension time may be less than that requested because any caught signal will terminate the sleep() following execution of that signal&#8217;s catching routine.

I then cranked sleep time up to 20 secs, and ran the script again. W/o fail epiphany was killed after 17 seconds in each iteration, so the problem seems to lie in an imprecise sleep function.

I think I'll try an create a more precise function myself, and call it with an int arg, so I can force the script to sleep for exactly as long as i want to.
Perhaps something like this

```
def sleeping(wait_time):
    new_wait_time = wait_time

    while some_flag == 0:
        a = get system time
        time.sleep(new_wait_time)
        b = get system time

        a = do some math on b-a

        if result == wait_time:
            flag = 1
        else:
            new_wait_time = a
```

Probably won't work, but it will fun trying ... and when it fails, I'll be back here asking for help ;)


On a side note:
'run_epiphany' is called with the for i in range(3): on purpose.

---

