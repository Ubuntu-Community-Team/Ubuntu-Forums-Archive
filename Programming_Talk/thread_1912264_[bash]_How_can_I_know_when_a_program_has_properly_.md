---
title: "[bash] How can I know when a program has properly started?"
date: 2012-01-20
forum: Programming Talk
---

### Post by Paddy Landau on 2012-01-20
When I click to start a program on the Unity Launcher, the icon flashes until the program has properly started. So, somehow, the launcher knows when the program has properly started and waits until then before it stops flashing the icon.

Now, I have a Bash script where I start a program (in the background) and wait until the program has properly started before continuing.

At the moment, I'm guessing when the program has started (with *sleep 2s*), but that's not good enough. I'd like to know (as does the Launcher) when the program that I have started has actually started up properly, without waiting unnecessarily (if it's quicker than 2s) or not long enough (if a slow machine takes longer than 2s).

How can I do this? If I list the job with *ps*, it does not show me whether the program is busy starting up or has finished starting up. There must be a way if the Launcher can do it!

---

### Post by CoffeeRain on 2012-01-20
Does it matter? I would assume that it would wait until the program is started before going on.

---

### Post by Paddy Landau on 2012-01-20
> **CoffeeRain said:**
> Does it matter? I would assume that it would wait until the program is started before going on.
It does matter, because the next command will fail if the program has not yet finishing its start-up process.

The script doesn't wait until the program has started; it simply sends it off to the background and continues immediately, as follows.```
myprog &                    # Start the program in the background.
do something with myprog    # Does not wait for myprogram to start.
```So, I need something between starting myprog and using it.

---

### Post by CoffeeRain on 2012-01-20
Oh, so then would trial and error work?

---

### Post by Paddy Landau on 2012-01-20
> **CoffeeRain said:**
> Oh, so then would trial and error work?
Well, that's how I came up with sleep. But sometimes the machine is busy and takes longer than others.

---

### Post by Zugzwang on 2012-01-20
@OP: I think what you actually need is what is called a **barrier** in multi-threading.

The following page has some nice examples: [http://stackoverflow.com/questions/2425870/multithreading-in-bash](http://stackoverflow.com/questions/2425870/multithreading-in-bash)

---

### Post by cortman on 2012-01-20
> **Paddy Landau said:**
> Well, that's how I came up with sleep. But sometimes the machine is busy and takes longer than others.

What's the nature of the confirmation you want? Do you want to just observe it yourself, or do you want it recorded in a log, or...?

You can confirm if a program has executed succesfully with

```
if [ $? -eq 0 ] ; then
```

I guess you could tell the script to do whatever you wanted with the then command.

The $? variable stores the execution status of the last command issued. If it = 0, that means it executed successfully. If it = 1, problems.

Don't know if that's what you're looking for or not...

---

### Post by Paddy Landau on 2012-01-20
Thanks for the replies.

The barrier idea is not suitable, because I don't want to wait for the background program to *finish*; I want to wait for it to finish *starting up fully* -- just as the Launcher icon continues to flash until the program has started up.

Here's an example using Firefox:
```
firefox &                      # Start up Firefox in the background.
firefox htp://www.google.com/  # Ask Firefox to load Google's page.
```With that code, Firefox will start up once with a blank tab. Then, depending on the state of the computer, a *second* instance will start up, either loading Google, or reporting an error ("Firefox is already running") and failing.

However:
```
firefox &                      # Start up Firefox in the background.
sleep 2s                       # Wait for Firefox to start up.
firefox htp://www.google.com/  # Ask Firefox to load Google's page.
```In this case, Firefox will start up. Then, Google will load into it without starting a new instance.

The second version is what I want. The problem is that depending on the load of my machine, Firefox will sometimes load in a second, and other times take as long as 15 seconds, so my sleep has to be the worst case scenario. I'd rather be able to find out when the instance has started up and is ready to take new commands.

I tried looking at *kill* to send signals, but I drew a blank on that.

This is not seriously important, so if I don't find a solution it's OK. I just thought I'd try to solve this partly to make my life easier and partly to learn more about Linux!

---

### Post by ofnuts on 2012-01-20
> **Paddy Landau said:**
> Thanks for the replies.

The barrier idea is not suitable, because I don't want to wait for the background program to *finish*; I want to wait for it to finish *starting up fully* -- just as the Launcher icon continues to flash until the program has started up.

Here's an example using Firefox:
```
firefox &                      # Start up Firefox in the background.
firefox htp://www.google.com/  # Ask Firefox to load Google's page.
```With that code, Firefox will start up once with a blank tab. Then, depending on the state of the computer, a *second* instance will start up, either loading Google, or reporting an error ("Firefox is already running") and failing.

However:
```
firefox &                      # Start up Firefox in the background.
sleep 2s                       # Wait for Firefox to start up.
firefox htp://www.google.com/  # Ask Firefox to load Google's page.
```In this case, Firefox will start up. Then, Google will load into it without starting a new instance.

The second version is what I want. The problem is that depending on the load of my machine, Firefox will sometimes load in a second, and other times take as long as 15 seconds, so my sleep has to be the worst case scenario. I'd rather be able to find out when the instance has started up and is ready to take new commands.

I tried looking at *kill* to send signals, but I drew a blank on that.

This is not seriously important, so if I don't find a solution it's OK. I just thought I'd try to solve this partly to make my life easier and partly to learn more about Linux!

```

firefox htp://www.google.com/  &

```
would cover both cases properly...

Normally these programs set up somemechanism to detect if an instance is already running and answering. Firefox seems to use a "lock" link in the profile directory (this should allow it to run one instance per profile)

---

### Post by Paddy Landau on 2012-01-20
> **ofnuts said:**
> ... would cover both cases properly...
Yes, I realise. I was using Firefox as an example, but mine is a different program that needs to start before I can send further instructions to it.

I was wondering what mechanism Unity's Launcher uses to tell when the program has started up fully. Maybe something about the programs status -- sitting and not using CPU, perhaps?

---

### Post by Zugzwang on 2012-01-20
> **Paddy Landau said:**
> I was wondering what mechanism Unity's Launcher uses to tell when the program has started up fully. Maybe something about the programs status -- sitting and not using CPU, perhaps?

You can do that, the point is that it is left to the program to signal in any way that it has "fully started" - not all programs have such a state anyway. 

Thus, the only *real* solution is to use some feature of the specific program to ask it if it has fully started. For example, for a server, you could check every 500 ms if you can connect to the port the server program should open. Desktop programs can sometimes be communicated with via D-BUS. Perhaps you can add a plugin to the program you want to start to signalize the "readiness" of the application.

The idea to check for CPU utilization by the program is a bit tricky, as the program might in general be waiting for I/O or something like that. Checking for the CPU utilization of the overall system is not the way to go, either, as you might be doing some calculations in the background, which would be taken into account.

---

### Post by ofnuts on 2012-01-20
> **Paddy Landau said:**
> Yes, I realise. I was using Firefox as an example, but mine is a different program that needs to start before I can send further instructions to it.

I was wondering what mechanism Unity's Launcher uses to tell when the program has started up fully. Maybe something about the programs status -- sitting and not using CPU, perhaps?
Unity may be looking at  the window. It's normally painted when the program enters the event loop, after some initialization has been ran.

But in the general case, you can't really tell...

---

### Post by Paddy Landau on 2012-01-21
Thanks again for the replies.

This seems to be a puzzling one.

> **ofnuts said:**
> Unity may be looking at  the window.
You are right! I've just been testing with a script.

The launcher flashes for ten seconds or until the script displays something on the screen (I used *yad*), whichever comes first.

Interestingly, if the script displays something in a background process while the current process dies, the Launcher does not detect this.

Here are the test scripts:
```
**[COLOR=Navy]#!/bin/bash[/COLOR]**[COLOR=Navy]
# The Launcher flashes its icon for **four** seconds.[/COLOR]
[COLOR=DarkRed]**sleep**[/COLOR] 4s                             [COLOR=Navy]# Wait four seconds.[/COLOR]
yad --title=[COLOR=Magenta]'Hello'[/COLOR] --text=[COLOR=Magenta]'Boo!'[/COLOR]    [COLOR=Navy]# Display something.[/COLOR]
``````
**[COLOR=Navy]#!/bin/bash[/COLOR]**[COLOR=Navy]
# The Launcher flashes [/COLOR][COLOR=Navy]its icon [/COLOR][COLOR=Navy]for **ten** seconds.[/COLOR]
[COLOR=DarkRed]**sleep**[/COLOR] 20s                            [COLOR=Navy]# Wait twenty seconds.[/COLOR]
yad --title=[COLOR=Magenta]'Hello'[/COLOR] --text=[COLOR=Magenta]'Boo!'[/COLOR]    [COLOR=Navy]# Display something.[/COLOR]
``````
**[COLOR=Navy]#!/bin/bash[/COLOR]**[COLOR=Navy]
# The Launcher flashes [/COLOR][COLOR=Navy]its icon [/COLOR][COLOR=Navy]for **ten** seconds.[/COLOR]
[COLOR=DarkRed]**sleep**[/COLOR] 4s                             [COLOR=Navy]# Wait four seconds.[/COLOR]
yad --title=[COLOR=Magenta]'Hello'[/COLOR] --text=[COLOR=Magenta]'Boo!'[/COLOR] [COLOR=DarkRed]**&**[/COLOR]  [COLOR=Navy]# Display something using a background process.[/COLOR]
``````
**[COLOR=Navy]#!/bin/bash[/COLOR]**[COLOR=Navy]
# The Launcher flashes [/COLOR][COLOR=Navy]its icon [/COLOR][COLOR=Navy]for **four** seconds.[/COLOR]
[COLOR=DarkRed]**sleep**[/COLOR] 4s                             [COLOR=Navy]# Wait four seconds.[/COLOR]
yad --title=[COLOR=Magenta]'Hello'[/COLOR] --text=[COLOR=Magenta]'Boo!'[/COLOR] [COLOR=DarkRed]**&**[/COLOR]  [COLOR=Navy]# Display something using a background process.[/COLOR]
[COLOR=DarkRed]**sleep**[/COLOR] 0.1s                           [COLOR=Navy]# Wait a tiny bit to let the Launcher detect the[/COLOR]
                                     [COLOR=Navy]# [/COLOR][COLOR=Navy]background display. It[/COLOR][COLOR=Navy] can be longer.[/COLOR]

``````
**[COLOR=Navy]#!/bin/bash[/COLOR]**[COLOR=Navy]
# The Launcher flashes [/COLOR][COLOR=Navy]its icon [/COLOR][COLOR=Navy]for **ten** seconds.[/COLOR]
[COLOR=DarkRed]**sleep**[/COLOR] 4s                             [COLOR=Navy]# Wait four seconds.[/COLOR]
                                     [COLOR=Navy]# End without displaying anything.[/COLOR]
```So... how can a script tell whether or not a specific process has displayed something on the screen?

---

### Post by Vaphell on 2012-01-21
try xdotool
[http://www.semicomplete.com/projects/xdotool/xdotool.xhtml#window_commands](http://www.semicomplete.com/projects/xdotool/xdotool.xhtml#window_commands)

few options that look interesting:
search <regex>
--title --name --class allow to use regex against chosen properties
--onlyvisible
--pid PID

xprop and xwininfo may be useful too

---

### Post by MG&amp;TL on 2012-01-21
I am thinking that since the launcher is mainly used for GUI items, as all the GUI toolkits I've come across so far have a mainloop() or whatever, perhaps Unity can sense that?

It's pretty clever, however they do it.

---

### Post by Paddy Landau on 2012-01-21
> **Vaphell said:**
> try xdotool
Perfect! Thank you.

Every half-a-second, I check the process (and each of its children, because it could be a child process that opens the window) with this command:
```
xdotool search --pid=${PID} &>/dev/null
```As soon as this returns code 0, the window has been opened. Just as the Launcher does, I put a time limit in case something goes wrong.

I can mark this as solved now.

---

