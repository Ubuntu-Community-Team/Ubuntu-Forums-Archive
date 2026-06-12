---
title: "RegExp help needed"
date: 2006-07-20
forum: Programming Talk
---

### Post by bluecherry on 2006-07-20
Hi all,

I'm looking for ways to perform basic string parsing from the terminal.

To make my question more clear, i've included an example:

From the following text I would like to get:
* count GPUs >0 (line 1)
* count display devices (line 2)
* for each display device: name, sync (min/max horiz/vert), pref width/height, pref vertrefresh

I'm looking at grep and updating my RegExp knowledge but it has been years since I used it and I haven't used it in such advanced ways.

***nvidia-xconfig --query-gpu-info***
```

Number of GPUs: 1

GPU #0:
  Name      : GeForce4 Ti 4200
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 2

  Display Device 0 (CRT-0):
     EDID Name             : Brilliant Technology Bigtide-CM1770MK-0000007595
     Minimum HorizSync     : 26.237 kHz
     Maximum HorizSync     : 68.677 kHz
     Minimum VertRefresh   : 60 Hz
     Maximum VertRefresh   : 85 Hz
     Maximum PixelClock    : 108.000 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 1024 pixels
     Preferred Width       : 1024 pixels
     Preferred Height      : 768 pixels
     Preferred VertRefresh : 85 Hz
     Physical Width        : 320 mm
     Physical Height       : 240 mm

  Display Device 1 (CRT-1):
     EDID Name             : CAL L15CX
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 60.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 75 Hz
     Maximum PixelClock    : 80.000 MHz
     Maximum Width         : 1024 pixels
     Maximum Height        : 768 pixels
     Preferred Width       : 1024 pixels
     Preferred Height      : 768 pixels
     Preferred VertRefresh : 75 Hz
     Physical Width        : 300 mm
     Physical Height       : 230 mm


```

Thx!

---

### Post by GarlicFish on 2006-07-20
grep 'Number of GPUs' regexp.txt | cut -d' ' -f4

grep 'Number of Display Devices' regexp.txt | cut -d' ' -f7

Gets you the first two items

---

### Post by bluecherry on 2006-07-20
Thanks!

I didn't even know of the existence of cut.

I'm gonna play with it right away!

---

### Post by GarlicFish on 2006-07-20
Not sure about the next bit :-? 

I'd probably look at python or perl or similar to read the text line by line and associate the values with their correct display.

Can't help though as I haven't got round to learning either yet.  I'm still stuck in VB land ;)

---

### Post by jordilin on 2006-07-20
take a look at the command 
```
awk
```
and 
```
sed
```
Awk is extremely powerful to get chunks of text out of lines.

---

### Post by GarlicFish on 2006-07-20
Ah Ha :)

Just found this little beauty

#!/bin/bash
# START OF SCRIPT
exec < regexp.txt 
while read line
do
echo $line
done
#END OF SCRIPT

---

### Post by GarlicFish on 2006-07-20
#!/bin/bash
# START OF SCRIPT
exec < regexp.txt 
while read line
   do
      strParameter=$(echo $line | cut -d: -f1)
      strValue=$(echo $line | cut -d: -f2)
      echo Parameter = $strParameter
      echo Value = $strValue
   done

#END OF SCRIPT

I guess the next step would be to use grep, awk or sed to check each parameter to see if it is what you are after and if so store the value in a variable until you need to use it.

What do you want to do with the values once you have them?

---

### Post by ifokkema on 2006-07-21
Maybe this is of any use to you:

```

for i in 0 1;
  do
  echo "Display ${i} returns:";
  nvidia-xconfig --query-gpu-info | grep -A 13 "Display Device ${i}" | grep -E "HorizSync|VertRefresh|Preferred";
done

```

It's simple (without sed or awk), but it might just do what you need.

---

### Post by mikeym on 2006-07-21
Here is a start for using sed and awk.

```

NOCPUS=`nvidia-xconfig --query-gpu-info | sed -n -e '1p' | awk 'BEGIN { FS=":" } { print $2 }'`
NODISPLAYS=`nvidia-xconfig --query-gpu-info | sed -n -e '7p' | awk 'BEGIN { FS=":" } { print $2 }'`

echo "CPU's: $NOCPUS"
echo "Displays: $NODISPLAYS"

COUNT=0
while [ $COUNT -lt $NODISPLAYS ]; do
   NAME=`nvidia-xconfig --query-gpu-info | sed -n -e "/Display Device $COUNT/,/Physical Height/p" | awk 'BEGIN { FS=":" } /EDID Name/ { print $2 }'`
   echo "Name display $COUNT: $NAME"
   COUNT=$((COUNT+1))
done


```

Hope this helps.

I'm not sure about calling the same procedure 3+ times but I found when I put it in a variable it list the new lines?? Maybe you could put it in a temporary file and 'cat' it?

---

### Post by bluecherry on 2006-07-22
Thx all! 

I'll try all your sugestions asap.

I would like to use these values as a part of an nvidia driver installer -> no manual editing anymore, just input in dialogs (zenity).

If I get this to work it will save me some trips to my friends (friends) to get their nvidia cards to work on a fresh install :-).

thx!!

---

### Post by Eric_T on 2006-07-25
Not sure if it's what you're after, but here's how you can put the numbers into variables using awk:
```

nvidia-xconfig --query-gpu-info > nvid.txt
gpus=`awk '/Number of GPUs/{print $4}' nvid.txt`
disps=`awk '/Number of Display Devices/{print $5}' nvid.txt`

```
The text between the slashes is the search string. The curly brackets contain the action, print $4 indicates that we want to print column 4 of the matched line(i.e. the number).

EDIT: I see that mikeym is two steps ahead of me...](*,)

---

### Post by hasimir44 on 2006-07-27
can't leave out perl :)

```

#!/usr/bin/perl
while (<>) {
        if (/GPU\s\#(\d+)/) {
                print "GPU: $1\n";
        } elsif (/Display Device\s(\d+)/) {
                print "Display Device: $1\n";
                $disp_devs++;
        } elsif (/EDID Name\s+\:(.*)$/) {
                print "Name: $1\n";
        } elsif (/Sync/) {
                print "$_";
        } elsif (/Preferred/) {
                print "$_";
        }
}
print "Total Display Devices: $disp_devs\n";

```

I named the above perl script "help.pl" and your text as "help.txt" .. 
Here's the output: 

```

ubuntu@ubuntu:~$ ./help.pl help.txt
GPU: 0
Display Device: 0
Name:  Brilliant Technology Bigtide-CM1770MK-0000007595
     Minimum HorizSync     : 26.237 kHz
     Maximum HorizSync     : 68.677 kHz
     Preferred Width       : 1024 pixels
     Preferred Height      : 768 pixels
     Preferred VertRefresh : 85 Hz
Display Device: 1
Name:  CAL L15CX
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 60.000 kHz
     Preferred Width       : 1024 pixels
     Preferred Height      : 768 pixels
     Preferred VertRefresh : 75 Hz
Total Display Devices: 2


```

*Note: you asked for a VerticalSync, but there wasn't any in your example text..

---

### Post by bluecherry on 2006-07-28
Hehe, you're right vert sync was not in the list, I meant vert refresh.

Thx for the perl example, I was hoping to do it all in bash-script but I'm already considering perl and other language because of the complexity of the prog.

Thx!

---

