---
title: "Embedded Lua with imput from Labview"
date: 2009-01-15
forum: Programming Talk
---

### Post by skintythe1andonly on 2009-01-15
Hi

I have been working with a Keithley 2602A dual channel sourcemeter for the last while and all my programs have been running through labview over a GPIB connection. This would mean I would source current or something and get the voltage back with the signals pinging back and forth between the PC and the Keithley. 

I now need it to run faster for a fairly simple task. The unit can take Lua scripts and implement them. This I know adds a HUGE degree of freedom but having only recently started with python, I am limited to the few commands from reading the manual.

What I want to do is...
[LIST=1][*]Apply a voltage from channel 1[*]Measure current in channel 1[*]Take current reading in channel 1, and give a voltage output in channel 2 proportional to this value[*]Break when it receives some signal from Labview




[/LIST]

It should go something along the lines of 

```

while "no_input" do
channel1.source.levelv() = v1
reading = channel1.measure(i)
channel2.source.levelv() = reading*R
"check if there was input"

```

What I dont know is how to check for a user input in this to break this loop. I was thinking of implementing a read() function with a timeout so that it should return nil should it not receive any input, but having a timeout in there defeats the purpose I think. Im not sure if passing info will work along a GPIB to one of these units. Anybody have any ideas?

---

