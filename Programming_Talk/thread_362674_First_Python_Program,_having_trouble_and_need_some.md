---
title: "First Python Program, having trouble and need some help."
date: 2007-02-15
forum: Programming Talk
---

### Post by SuperCow56 on 2007-02-15
This program implements a digital clock display for a European-style 24 hour clock. The clock shows hours and minutes. The range of the clock is 00:00 (midnight) to 23:59 (one minute before midnight). 

The clock display receives "ticks" (via the timeTick method) every minute and reacts by incrementing the display. This is done in the usual clock fashion: the hour increments when the minutes roll over to zero.
```

import NumberDisplay

# Clockdisplay implements a digital clock display of a 24 hour clock. The clock shows hours and minutes.
# range of the clock is 00:00 (midnight) to 23:59 (one minute before midnight).
def Strings():
	hours = newNumberDisplay
	minutes = newNumberDisplay
	updateDisplay()
	
# Constructor for ClockDisplay objects.
def ClockDisplay(hour, minute):
		hours = newNumberDisplay
		mintes = newNumberDisplay
		setTime(hour, minute)

# This method should get called once every minute.
# It makes the clock display go one minute forward.

def timeTick():
		minutes.increment();
		if(minutes.getValue() == 0
			hours.increment();
		updateDisplay()

# Set the time of the display to the specified hour and minute.

def setTime(hour, minute):
		hours.setValue(hour)
		minutes.setValue(minute)
		updateDisplay()

# Returns the current time of this display in this format HH:MM

def getTime():
		return displayString

def updateDisplay():
		displayString = hours.getDisplayValue() + ":" + minutes.getDisplayValue()

```
Help me with this please. I know that I am missing a lot of things :(

---

### Post by Mirrorball on 2007-02-15
Maybe you should post what's in the module you are importing (ClockDisplay). Also you are importing and not using it anywhere. You have a constructor but you don't have a class. Yes, I think you are missing a lot of things. But first tell us what you are importing.

---

### Post by SuperCow56 on 2007-02-15
well as you noticed I am very new to python, and I am still learning.  There is another module but I did manage to import the wrong one, it should have been import NumberDisplay

Here is the code
```

# The NumberDisplay represents a digital number display that can hold values from zero to a given limit. The limit can be specified when creating the display. The values range from zero (inclusive) to limit-1. If used, for example, for the seconds on a digital clock, the limit would be 60, resulting in display values from 0 to 59.

# When incremented, the display automatically rolls over to zero when reaching the limit.

def NumberDisplay
	int limit:
	int value:
# Constructor for objects of class Display

def NumberDisplay(int rollOverLimit):
	limit = rollOverLimit
	value = 12

# Return the current value.

def int getValue()
	return value:

# Return the display value (that is, the current value as a two-digit string. If the value is less than the, it will be padded with a leading zero.

def str getDisplayValue()
	if(value < 10)
		return "0" + value:
	else
		return "" + value:

# Set the value of the display to the new specified value. If the new valus is less than zero or over the limit, do nothing.

def setValue(int replacementValue)
	if((replacementVaule > 0) && (replacementValue < limit))
		value = replacementValue:

# Increment the display value by one, rolling to the zero if the limit is reached.

def increment()
	value = (value + 1) % limit:


```

---

### Post by Mirrorball on 2007-02-16
It has **lots** of syntax errors; for instance, you can't set a type for the return value and parameters of functions. Also no classes and colons at the wrong places.

You should write a short piece of code and test it immediately, because then there will be only a few errors to correct each time. Or better yet, you should play a little with the interactive shell, because it gives you immediate feedback. Just type "python" in a terminal window and write Python code.

---

