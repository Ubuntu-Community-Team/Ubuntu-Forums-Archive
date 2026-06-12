---
title: "zenity list, inconsistent behavior"
date: 2011-03-12
forum: Programming Talk
---

### Post by fsmithred on 2011-03-12
I've got a block of code to display disk partitions in a zenity window. It works, but it displays the partitions out of order.```
#!/usr/bin/env bash
# test a zenity window

part=$(find /dev -mindepth 1 -maxdepth 1  -name "*[sh]d[a-z][0-9]"  -printf 'FALSE\0%p\0' | \
xargs -0 zenity --list --title="Partition" --text="This one shows the partitions out of order." \
--radiolist --multiple --column ' ' --column 'Partitions')

echo "$part"
```

If I run the 'find' command alone in a terminal, the partitions come out in the same wrong order. This behavior is the same in several places that I've tested it (two computers, live iso running in VirtualBox, installed system running in vbox, live system running from usb stick. (Debian Squeeze in all cases, kernel 2.6.32.)```
find /dev -mindepth 1 -maxdepth 1  -name "*[sh]d[a-z][0-9]"  -printf 'FALSE\0%p\0'
```

If I take the printf out of find, run it through sort and awk with printf, it displays the partitions in the correct order.```
find /dev -mindepth 1 -maxdepth 1  -name "*[sh]d[a-z][0-9]" | sort | awk '{ printf "FALSE""\0"$0"\0" }'
```

But when I put that altered line back into the piece with zenity, it only displays the partitions correctly in my main machine. In all the other places I mentioned, zenity displays only one radio button with no labels.```
#!/usr/bin/env bash
# test a zenity window

part=$(find /dev -mindepth 1 -maxdepth 1  -name "*[sh]d[a-z][0-9]" | sort | awk '{ printf "FALSE""\0"$0"\0" }' | \
xargs -0 zenity --list --title="Partition" --text="This one shows the partitions in order when it shows them, which is not always." \
--radiolist --multiple --column ' ' --column 'Partitions')

echo "$part"

```

I'm at a loss for an explanation or a fix for this. BTW, I'm not sure that the 'xargs -0' is necessary. Seems to work the same without it. I'll add that I'm fairly new to bash scripting, and the code is an alteration of something I found on this forum.

Main machine is athlon x2, five years old, on asus motherboard with via chipsets, the test machine is six year old sempron on asus with via. And I just did one more test while I was writing this...

Test machine had IDE drives when the problem occurred. I just unplugged those and put in a sata drive, like the main machine. Partitions now show in order in the zenity window with the second block of code. (vbox is emulating sata, but second script still won't show any partitions, so it only seems to work with real sata drives.)

Still, if anyone has insights as to why this is, or can suggest a way to get it to display correctly in all situations, I'd appreciate it.

---

### Post by gzarkadas on 2011-03-15
xargs is definitely not needed here. The use of '\0' characters is not needed also - in fact it may be the cause of this weirdness due to increased code complexity - because /dev is root-land and typically no non-trusted user can create filenames there. Use plain newlines then, to make life simpler.

Try the following (if you only echo $part, then it is not needed also):
```

find /dev -mindepth 1 -maxdepth 1  -name "*[sh]d[a-z][0-9]" \
  | sort \
  | awk '{print "FALSE\n" $0 }' \
  | zenity --list --title="Partition" --text="This one shows the partitions in order when it shows them, which is not always." --radiolist --multiple --column 'Select' --column 'Partitions'

```

---

### Post by fsmithred on 2011-03-16
gzarkadas: Thank you! I thought the newlines had to be removed. I'm sure I was trying it without removing them first, but I'm also sure I was doing it differently. What you posted seems to work. I just tested it in two places, and it worked the same in both.

No, I'm not just echoing it. That was for the test. I'm picking a partition to be formatted and installed. The rest of that script is working. I just couldn't get the partitions to list in order on all the test systems I have.

---

