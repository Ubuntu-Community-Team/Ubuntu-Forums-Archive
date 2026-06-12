---
title: "How do I determine if a blank CD is in the drive? -- Bash Scripting -- HAL"
date: 2008-07-03
forum: Programming Talk
---

### Post by _UsUrPeR_ on 2008-07-03
I think I have this kind of figured out. That is to say, I have figured out how to get a "true" statement out of HAL.

Here's the code:

```
CDEmpty()
{
	EMPTYCD=${"hal-get-property --udi '/org/freedesktop/Hal/devices/volume_empty_cd_r' --key volume.disc.is_blank"}

	while [ "$EMPTYCD" != "true" ]
	do
		echo -n "Please insert a blank CD into the tray and push enter..."
		Pause #this is a unlisted Pause function. It waits for user input.
		EMPTYCD=${"hal-get-property --udi '/org/freedesktop/Hal/devices/volume_empty_cd_r' --key volume.disc.is_blank"}
	done
}
```

If I try to run that, I get an error on the first "EMPTYCD=${etc..." line saying that is a bad substitution.

If I remove the "${...} " from the EMPTYCD variable, it leaves it as a variable storing a string instead of being executed with a return.

Can someone give me a hint about this?

---

### Post by geirha on 2008-07-03
You want to use $( ) or ` ` if you want to save the output of a command into a variable.
```
EMPTYCD=$( hal-get-property --udi '/org/freedesktop/Hal/devices/volume_empty_cd_r' --key volume.disc.is_blank )
```

---

### Post by _UsUrPeR_ on 2008-07-09
That did it! works great now. Thank you.

---

