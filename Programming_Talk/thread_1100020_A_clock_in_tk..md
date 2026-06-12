---
title: "A clock in tk."
date: 2009-03-18
forum: Programming Talk
---

### Post by jwbrase on 2009-03-18
I found a neat little decimal clock script at this site: [http://everything2.com/title/Decimal%2520Clock](http://everything2.com/title/Decimal%2520Clock)

I've spent some time modifying it to my liking, and now have the following script, which reformats the decimal clock as well as adding a hexidecimal clock: ```
#!/usr/bin/env wish
# clock.tk
# Display the date and time in conventional format, and the time of
# day in decimal

# Set background to your preference. The default background colour
# given by wish is far, far too bright for my eyes...
set bg \#8c8c90


# Date and current time without all that annoying syntax
# Though it's useful to mark the mod-6,s mod-3s and mod-4s is some way?
proc date_time { } {
  set date_time [clock format [clock seconds] -format "%m/%d/%Y	%H:%M:%S"]
  return $date_time
}

# Get current time as a decimal fraction of the day.
proc dec_time { } {

  # To save making multiple calls to clock, or faffing about with
  # seconds-past-the-epoch, local time and leap-seconds, make the date
  # format an expression for the number of seconds since midnight.
  # note the hack that each % substitution has a space before it: this
  # is because the default date format gives a leading '0' if the item
  # is in the range 0..9; since we want to evaluate this expression,
  # we have to trim this off otherwise expr will interpret it as an
  # octal number, and have a fit when it gets to 08.
  set secs_expr [
    clock format [clock seconds] -format "( %H * 60 + %M ) * 60 + %S"
  ]
  regsub -all " 0" $secs_expr "" secs_expr

  # Number of seconds into the day.
  set secs [expr $secs_expr]
  
  # Fraction of the day multiplied up by 1e5. Factored down by 10 on
  # each side here to stay in 2^32 range...
  set frac [expr 1000 * $secs / 864]

 set dec_hours [expr $frac / 10000 ]

 set dec_min [expr ($frac % 10000) / 100 ]

 set dec_sec [expr ($frac % 100) ]

  return [format "%0d:%02d:%02d" $dec_hours $dec_min $dec_sec]
}

proc hb_time { } {

  # To save making multiple calls to clock, or faffing about with
  # seconds-past-the-epoch, local time and leap-seconds, make the date
  # format an expression for the number of seconds since midnight.
  # note the hack that each % substitution has a space before it: this
  # is because the default date format gives a leading '0' if the item
  # is in the range 0..9; since we want to evaluate this expression,
  # we have to trim this off otherwise expr will interpret it as an
  # octal number, and have a fit when it gets to 08.
  set secs_expr [
    clock format [clock seconds] -format "( %H * 60 + %M ) * 60 + %S"
  ]
  regsub -all " 0" $secs_expr "" secs_expr

  # Number of seconds into the day.
  set secs [expr $secs_expr]
  
  # Fraction of the day multiplied up by 1e5. Factored down by 10 on
  # each side here to stay in 2^32 range...

  #Fraction of the day multiplied up by 2^12
 set hbfrac [expr 4096 * $secs / 5400]

  return [format "%04X" $hbfrac]
}

# Periodically update decimal time display
proc dectime_update { widget } {
  $widget configure -text [dec_time]
  after [expr [expr (24 * 60 * 60 / 100)]] dectime_update $widget
}

#Periodically update hex/bin time display every (24*60*60)/(2^16) seconds
#or 1000*(24*60*60)/(2^16) milliseconds. Factored down  on either side by a factor of 256
#to fit within 2^32 
proc hbtime_update { widget } {
$widget configure -text [hb_time]
after [expr 1319] hbtime_update $widget
}

# Periodically update conventional time display
proc date_update { widget } {
  $widget configure -text [date_time]
  after [expr 1000] date_update $widget
}

# Create a widget to display a clock time
proc clockwidget { widget } {
  global bg
  pack [
    label $widget \
      -bg "$bg" \
      -font [ font create \
                -family lucidatypewriter \
		-size 10 -weight normal \
		-slant roman ]
  ] -side top -ipadx 8 -ipady 6 -fill both -expand 1
  return $widget
}

# Create the display:
# .f: frame to contain both clocks.
#  +.datetime: date/time widget
#  +.dectime: decimal time widget
pack [frame .f -borderwidth 1 -bg $bg ] -fill both -expand 1
date_update [clockwidget .f.datetime]
dectime_update [clockwidget .f.dectime]
hbtime_update [clockwidget .f.hbtime]
```

The problem is that every once in a while the non-standard clocks will, when their time comes to update, move forward by 0 or 2 of their "seconds" instead of 1. I assume this has to do with some type of rounding error converting from seconds to "seconds," but this is the first time I've messed with tk, so I'm not sure of the best way to remove this bug.

---

