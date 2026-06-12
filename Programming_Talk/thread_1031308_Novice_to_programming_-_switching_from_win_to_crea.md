---
title: "Novice to programming - switching from win to create custom apps to manage time etc."
date: 2009-01-05
forum: Programming Talk
---

### Post by future_jack on 2009-01-05
Hi,
As per the title I want to create some custom apps for myself. I am choosing Linux because I believe it will be easier and that I will get more satisfaction (and learn more) from doing so.

The main thing I want to do for now is relatively simple.

I want to create an app that will monitor my time on a specific task. ie. Let's say I have one large task which includes several sub-tasks. I would like to map all these sub-tasks to function keys. When I hit a function key it will start or turn off a timer. When I'm finished my tasks I will copy the output into my excel document (may consider changing to open office!!) for reports etc.

Only problem now is that I don't know how to go about such a task. I haven't programmed before but am confident I will be able to grasp it fairly quickly.

Any suggestions appreciated.

Thanks.

---

### Post by iharrold on 2009-01-05
I would personally stick with Excel and write a VB application as part of the Excel file.

[http://www.google.com/search?q=VB+excel&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=VB+excel&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

VB will even allow a gui interface.

In office 2007,  Alt+F11 will take you directly to the Microsoft Visual Basic project that is embedded into the excel file.  I think Office XP, 2000, etc... is identical.  I wrote quite a few applications using this method that is driven by the excel spread sheet data.

---

### Post by stevescripts on 2009-01-06
Creating a timer program is *realtively* simple, however, interacting with Excel from an external program is considerably more difficult and time consuming ...

As iharrold posted, probably the easiest way to interact with Excel is from VB. (I have not done any VB for a long time now, and have no interest in doing any again)

That said, there are other programming tools available, that can interact with/control Excel via its COM interface, however, that will take you a bit more time and effort to learn than you may think...

As an example of a timer, the following is a tcl script I wrote many years ago, (this is not particularly well-written, but it is pretty easy to follow, and it works)

```

#! /usr/bin/tclsh

package require Tk

wm iconify .

global myvar
set myvar "START"
button .b -textvariable myvar
button .b1 -text "RESET" -command { reset }
entry .e -width 16 -textvariable et -justify center

grid .e -columnspan 2
grid .b -row 1 -column 0 -sticky ew
grid .b1 -row 1 -column 1 -sticky ew
.b configure -width 6

proc chgvar { } {
	global myvar
	if {$myvar == "STOP"} {
	set myvar "START"
		} else {
	set myvar "STOP"}
	.b1 configure -state disabled
	run
	}

.b configure -command { chgvar }

set mins 0
set secs 0
set hrs 0

proc run {  } {
	global et myvar hrs mins secs
	if {$myvar == "START" } {
		.b1 configure -state normal
		return } else {
		if {$myvar == "STOP"} {
			after 1000 run
			set secs [expr $secs + 1]
			if {$secs >= 60} {
				set secs 0
				set mins [expr $mins+1] 				
			}
			if {$mins >= 60} {
				set secs 0
				set mins 0
				set hrs [expr $hrs + 1]
			}				
			set et [format "%02d:%02d:%02d" $hrs $mins $secs]
			return $et
			}
		}
	}

proc reset { } {
	global hrs mins secs et myvar
	if {$myvar == "START" } {
		set mins 0
		set secs 0
		set hrs 0
		set et [format "%02d:%02d:%02d" $hrs $mins $secs]
		return $et
	} else {
	return
	}	
}

wm resizable . 0 0
wm deiconify .
wm title . {}

```

Hope you find this a bit helpful.

Steve

---

