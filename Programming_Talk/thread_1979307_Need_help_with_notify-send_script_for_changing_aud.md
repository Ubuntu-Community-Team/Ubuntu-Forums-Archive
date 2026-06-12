---
title: "Need help with notify-send script for changing audio output."
date: 2012-05-13
forum: Programming Talk
---

### Post by n4h0j on 2012-05-13
Greetings.

I have the following script keybinded to change my default audio sink:

```
#!/usr/bin/env bash

sinks=($(pacmd list-sinks | grep index | \
    awk '{ if ($1 == "*") print "1",$3; else print "0",$2 }'))
inputs=($(pacmd list-sink-inputs | grep index | awk '{print $2}'))

[[ ${sinks[0]} = 0 ]] && swap=${sinks[1]} || swap=${sinks[3]}

pacmd set-default-sink $swap && notify-send -u normal 'Sound output changed as you commanded, my lord.' &> /dev/null
for i in ${inputs[*]}; do pacmd move-sink-input $i $swap &> /dev/null; done
```

This works very well!

I am however trying to improve the bit with the "notify-send". It would be very useful to have the notification state what sink is the new default.

How would I do this?

Regards,
Johan

---

### Post by steeldriver on 2012-05-13
you could try a backtick expansion maybe? something like

```

notify-send -u normal "message from me: `echo $MYVAR`"

```

---

### Post by n4h0j on 2012-05-13
Thank you, you pushed me in the right direction.

This works very well for me:

```
#!/usr/bin/env bash

sinks=($(pacmd list-sinks | grep index | \
    awk '{ if ($1 == "*") print "1",$3; else print "0",$2 }'))
inputs=($(pacmd list-sink-inputs | grep index | awk '{print $2}'))

[[ ${sinks[0]} = 0 ]] && swap=${sinks[1]} || swap=${sinks[3]}

pacmd set-default-sink $swap 

for i in ${inputs[*]}; do pacmd move-sink-input $i $swap &> /dev/null; done


if [ "$swap" = "0" ]; then
notify-send -u normal -i audio-volume-medium-symbolic "Sound output changed. Now using: Corsair 2.1 Speakers!" 

else 
notify-send -u normal -i audio-volume-medium-symbolic "Sound output changed. Now using: Logitech G930 Headset!" 

fi

```

---

