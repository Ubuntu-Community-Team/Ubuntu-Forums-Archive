---
title: "Need help with small bash script - autocomplete and system files"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by e-San on 2014-01-19
Hi!

I am looking for help with preparing small script to change some settings with /sys files.
For example in samsung's folder there are many files:

```
find /sys/devices/platform/samsung/sys/devices/platform/samsung
/sys/devices/platform/samsung/usb_charge
/sys/devices/platform/samsung/power
/sys/devices/platform/samsung/power/control
/sys/devices/platform/samsung/power/runtime_active_time
/sys/devices/platform/samsung/power/autosuspend_delay_ms
/sys/devices/platform/samsung/power/runtime_status
/sys/devices/platform/samsung/power/runtime_suspended_time
/sys/devices/platform/samsung/modalias
/sys/devices/platform/samsung/subsystem
/sys/devices/platform/samsung/battery_life_extender
/sys/devices/platform/samsung/rfkill
/sys/devices/platform/samsung/rfkill/rfkill1
/sys/devices/platform/samsung/rfkill/rfkill1/hard
/sys/devices/platform/samsung/rfkill/rfkill1/name
/sys/devices/platform/samsung/rfkill/rfkill1/soft
/sys/devices/platform/samsung/rfkill/rfkill1/type
/sys/devices/platform/samsung/rfkill/rfkill1/claim
/sys/devices/platform/samsung/rfkill/rfkill1/index
/sys/devices/platform/samsung/rfkill/rfkill1/power
/sys/devices/platform/samsung/rfkill/rfkill1/power/control
/sys/devices/platform/samsung/rfkill/rfkill1/power/runtime_active_time
/sys/devices/platform/samsung/rfkill/rfkill1/power/autosuspend_delay_ms
/sys/devices/platform/samsung/rfkill/rfkill1/power/runtime_status
/sys/devices/platform/samsung/rfkill/rfkill1/power/runtime_suspended_time
/sys/devices/platform/samsung/rfkill/rfkill1/state
/sys/devices/platform/samsung/rfkill/rfkill1/persistent
/sys/devices/platform/samsung/rfkill/rfkill1/device
/sys/devices/platform/samsung/rfkill/rfkill1/subsystem
/sys/devices/platform/samsung/rfkill/rfkill1/uevent
/sys/devices/platform/samsung/rfkill/rfkill2
/sys/devices/platform/samsung/rfkill/rfkill2/hard
/sys/devices/platform/samsung/rfkill/rfkill2/name
/sys/devices/platform/samsung/rfkill/rfkill2/soft
/sys/devices/platform/samsung/rfkill/rfkill2/type
/sys/devices/platform/samsung/rfkill/rfkill2/claim
/sys/devices/platform/samsung/rfkill/rfkill2/index
/sys/devices/platform/samsung/rfkill/rfkill2/power
/sys/devices/platform/samsung/rfkill/rfkill2/power/control
/sys/devices/platform/samsung/rfkill/rfkill2/power/runtime_active_time
/sys/devices/platform/samsung/rfkill/rfkill2/power/autosuspend_delay_ms
/sys/devices/platform/samsung/rfkill/rfkill2/power/runtime_status
/sys/devices/platform/samsung/rfkill/rfkill2/power/runtime_suspended_time
/sys/devices/platform/samsung/rfkill/rfkill2/state
/sys/devices/platform/samsung/rfkill/rfkill2/persistent
/sys/devices/platform/samsung/rfkill/rfkill2/device
/sys/devices/platform/samsung/rfkill/rfkill2/subsystem
/sys/devices/platform/samsung/rfkill/rfkill2/uevent
/sys/devices/platform/samsung/uevent
/sys/devices/platform/samsung/performance_level
```

/sys/devices/platform/samsung/battery_life_extender accepts settings 1 and 0,
and
/sys/devices/platform/samsung/performance_level takes silent, normall and overclock
and many more.

I would like to create small bash script ie. samsung-power which take arguments like performance_level, wifi, battery_extender and so on but with autocomplete and sub-argument for status like on/off and silend/normall/overclock (depends on what we want to controll) - with autocomplete.

Anyone can help me with doing so?

Best regards!

---

### Post by TheFu on 2014-01-19
echo "1" > /sys/devices/platform/samsung/battery_life_extender 

It will need to be run with admin rights ... i.e. sudo or in a system startup script like /etc/rc.local.
You can create a function to toggle these settings.  

I will not write the script for you, but will strongly suggest looking at the "advanced bash scripting guide" ... it contains all you need to know in a useful, example-driven, how-to.  If you want to see many example scripts with status, start/stop then look in /etc/init.d/ folder.  I'm all about teaching you to fish, not handing a meal to you ... unless you are buying. ;)

Auto complete is a different animal and needs to be a different question.

---

### Post by e-San on 2014-01-19
Ok, thank You for Your help.

One question before i start trying:
can I use somehow matrix to store file and possible options?
Something like:

```

no. | name  | sys file                                                  | possible options
0   | wifi  |[COLOR=#000000][FONT=Ubuntu Mono]/sys/devices/platform/samsung/rfkill/rfkill1/power/control | {1, 0}[/FONT][/COLOR]
1   | bt    |[COLOR=#000000][FONT=Ubuntu Mono]/sys/devices/platform/samsung/rfkill/rfkill2/power/control | {1, 0}[/FONT][/COLOR]
2   | power |[COLOR=#000000][FONT=Ubuntu Mono]/sys/devices/platform/samsung/performance_level            | {silent, normal, performancce}[/FONT][/COLOR]
etc.
```

---

### Post by TheFu on 2014-01-19
I'm almost positive that is possible - don't know how to do it in bash. I'd switch to perl or python for more complex scripting. The syntax of those languages "feels" cleaner to me for this stuff.
In perl, creating arrays of arrays or arrays of hashes is trivial - happens ALL THE TIME.

So ... matrix isn't the term to use when you search for help. Look for arrays of arrays. Those are the computer terms.
Here's a link to the ABSG - [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)  It is the best guide that I know for bash.

---

### Post by e-San on 2014-01-19
```
#!/bin/bash

#	 name:sys-file:value1:value2:value3:...
#	 nazwa:plik:warto&#347;&#263;1:warto&#347;&#263;2:warto&#347;&#263;3:...
array2d="performance:/sys/devices/platform/samsung/performance_level:silent:normal:overclock
	 battery_life:/sys/devices/platform/samsung/battery_life_extender:0:1
	 usb_charge:/sys/devices/platform/samsung/usb_charge:0:1"


function process2ndDimension {
    t=0
    for dimension2 in $*
    do
	if [ $t != 1 ]
	then
	  echo -ne $dimension2 "\t"
        fi
        t=$[t+1]
    done
    echo
}


function process1stDimension {


    echo -e "   [setting]\t[    possible values\t]"
    for dimension1 in $array2d
    do
        process2ndDimension `echo $dimension1 | tr : " "`
    done
}


process1stDimension 
```
found [here]("http://stackoverflow.com/questions/11233825/multi-dimensional-arrays-in-bash") (bit modified) and seems to be a good start. i'll continue tomorrow.
i Was thinking if bash is good language for this. do You think so?

---

### Post by TheFu on 2014-01-20
Whatever language works for you is fine.  My bash skills would have me switching to a language with better data structures built-in rather than using an add-on hack. Pretty much any language other than bash/sh/ksh/csh/tcsh will have better data structures available.

That is all opinion and doesn't matter at all. Whatever works for you is what matters, unless you are trying to create code that someone else will help maintain. Then I'd be pushing python, perl, ruby instead.

---

