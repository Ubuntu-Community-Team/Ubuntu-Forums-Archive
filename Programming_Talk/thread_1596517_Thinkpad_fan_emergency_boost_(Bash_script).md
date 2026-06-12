---
title: "Thinkpad fan emergency boost (Bash script)"
date: 2010-10-14
forum: Programming Talk
---

### Post by alexdrouin on 2010-10-14
Hi all,

Here is a simple bash script for all those who are struggling with the Thinkpad's overheating problem in Ubuntu. Sometimes, when Thinkfan is simply not enough, you can use this little script to temporarily boost the fan's speed to the full-speed level. You can get a few degrees down in a very short time, but be careful, it will probably be a lot more battery consuming.

Here it is:

```

#!/bin/sh
#Thinkpad Fan Boost
#By: Alexandre Drouin
#October 14 2010
#For all those who struggle with keeping their Thinkpad to a decent temperature

on_die()
{
    #Reset fan control to automatic
        echo
    echo "Resetting automatic fan control..."
        sudo echo "level auto" >> fan
        echo "Done!"
    exit 0
}

main()
{
    echo "Fan: Going full speed!"
    while [ true ]
    do
      cd "/proc/acpi/ibm"
      echo 
      echo "System temperatures:"
      cat thermal
          echo
      sudo echo "level full-speed" >> fan
      sleep 10
    done
}

# Execute function on_die() receiving Ctrl-C signal
#
trap 'on_die' 2


main

```Hope it helps a few of you... :P

Cheers,
Alex

---

### Post by Diametric on 2010-10-14
Would this work on any laptop? I didn't see how the code would be thinkpad specific - nice contribution, though!
 
Cheers.

---

### Post by alexdrouin on 2010-10-14
Thank you!

I think it would work on most laptops if acpi control is available. The path "/proc/acpi/ibm" would have to be changed for "/proc/acpi/[vendor]" and the acpi features would have to manual fan control.

To activate manual fan control on any Thinkpad use the following:

```

sudo echo "options thinkpad_acpi experimental=1 fan_control=1" >/etc/modprobe.d/thinkpad_acpi.conf

```

Maybe someone could test this! :)

---

### Post by Diametric on 2010-10-15
I wouldn't mind testing on my Vaio but, I'm running puppy linux on the sony, so I'll have to fool around with it.
 
I'm still working on bash scripting skills, so if you want to update the code, I'll be happy to test it on my machine.

---

