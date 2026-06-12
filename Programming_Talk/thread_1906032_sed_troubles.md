---
title: "sed troubles"
date: 2012-01-08
forum: Programming Talk
---

### Post by bcooperizcool on 2012-01-08
I am having trouble with sed.   It seems it is effecting the rest of my program, even after it's part is done.

my code, like such:
```
cp "$base/default" "$base/new"
while read programs; do

after=`grep "After: " < $base/$programs | sed 's/^After: //'`
sed "/$after/ a\
$programs" $base/new
done < "$base/programs"
PlistGenStart Settings-iPhone Preferences

while read gen; do
cat "$base/Sections_iPhone/$gen" >> "/Applications/Preferences.app/Settings-iPhone.plist"
done < $base/new

PlistGenEnd Settings-iPhone Settings Preferences

rm -rf "$base/new"
```

the contents of default is:
```
GroupCell
AirplaneMode
WiFi
Notifications
GroupCell
Sounds
Brightness
Wallpaper
GroupCell
General
AccountSettings
Phone
Safari
Messages
iPod
Photos
Store
Speakers
```

and the content of program is something like 
```
Ch40s-Launcher
      WinterSled
```
and there is a file in $base called each of the contents of "program", with the contents like
```
After: Store
```
or some other part of "default", so it finds and inserts the text after it finds it, modifying the file.

It then gets stuff from $base/Sections_iPhone which has files named as the things in "default" that contain text to be entered into a new file.   

It is having troubles.  Sed works exactly like it is supposed to, but it seems to cut off the second loop, with "$gen".  It gets the first phew charachters, then cuts off, thus causing cat to get an error of "/Library/Stuff/Sections_iPhone/Ai : no such file or directory" or something similar.

If I remove the sed part, it works fine, but alas, I cannot remove sed, as it is needed, otherwise my code is pointless :(

Any suggestions?

Thanks!

---

### Post by Arndt on 2012-01-08
I'm not following the logic completely, but it seems your 'sed' command has no effect - it needs to have its output redirected somewhere, or be used with the -i option.

---

### Post by bcooperizcool on 2012-01-10
Still not working :/   It still gives me the same error, but now it outputs it into a file correctly.   It still gives me the cut off error, where the loop doesn't complete all of the variable.  It still has some of it, but not all of the variable (In the second loop).

---

### Post by Arndt on 2012-01-10
> **bcooperizcool said:**
> Still not working :/   It still gives me the same error, but now it outputs it into a file correctly.   It still gives me the cut off error, where the loop doesn't complete all of the variable.  It still has some of it, but not all of the variable (In the second loop).

Insert some echo commands here and there, and/or run with the -x flag to see what is happening.

Reduce the script so you have a minimal script which exhibits the problem, and post it here.

---

### Post by bcooperizcool on 2012-01-10
it echoes it fine :/  it's just the cat function that is not working :(   It cuts it off like this 

[IMG]http://i1210.photobucket.com/albums/cc407/bcooperizcool/IMG_00031.png[/IMG]

It echoes the contents correctly.  But the $gen variable is not working as it should.  It cuts off.   Actually, the whole output is messed up.  It also looks like it is continuing through the error and coming out on the end of the error output.

---

