---
title: "Simple BASH shell script to rename webcam jpg and copy into a new directory."
date: 2009-03-21
forum: Programming Talk
---

### Post by robfindlay on 2009-03-21
System: Ubuntu Intrepid Ibex

I'm running webcamd as a sort of "security" program, but I need a script that will archive my webcam.jpg files.

So, take the following file:
/home/slag/www/webcam.jpg

Rename it--preferably with a time stamp.

Place it in say:
/home/slag/www/history/

Copying the file say ever 60 seconds or so.

And that's it.  I wont need to run this as a cronjob as I'll just execute the script from a screen when needed.

Thanks guys!

Rob Findlay

---

### Post by kaibob on 2009-03-22
I haven't written a shell script like this before but the one copied below appears to work. You type in the length of time that you want the script to run as a command-line parameter. So, if you wanted the script to run for 1 hour, you would type the following in a terminal window:

```
scriptname 60
```

```
#!/bin/bash

# Change to source directory
cd /home/slag/www

# Issue error and exit if no command-line parameter. 
if [ "$1" = "" ]; then
echo "You forgot a time parameter!"
exit 1
fi

# Set counter
number=0

# Start while loop and continue until counter reaches $1.
# The variable $1 is command-line parameter. 
while [ $number -lt $1 ]; do

# Assign date to variable.
datestamp=$(date +%m.%d.%y)

# Assign time to variable. 
timestamp=$(date +%H.%M.%S)

# Copy source file to target directory with date and time as filename.
cp webcam.jpg /home/slag/www/history/${datestamp}-${timestamp}.jpg

# Pause for 60 seconds
sleep 60

# Increase counter by 1
number=$((number + 1))

done
```

Perhaps some of the more experienced members of the forum will have a better solution.

---

### Post by robfindlay on 2009-03-22
> **kaibob said:**
> I haven't written a shell script like this before but the script copied below appears to work. You type in the length of time that you want the script to run as a command-line parameter. So, if you wanted the script to run for 1 hour, you would type:

```
scriptname 60
```

```
#!/bin/bash

cd /home/slag/www

number=0

while [ $number -lt $1 ]; do

datestamp=$(date +%m.%d.%y)

timestamp=$(date +%H.%M.%S)

mv webcam.jpg /home/slag/www/history/${datestamp}-${timestamp}.jpg

sleep 60

number=$((number + 1))

done
```

Perhaps some of the more experienced members of the forum will have a better solution.

Spits this out regarding line number 9: 

line 9: [: 0: unary operator expected

---

### Post by kaibob on 2009-03-22
You received that error message because you didn't type in a number after the script name. If your script is named webarchive, you would type the following in a terminal window to run the program for 60 minutes:

```
webarchive 60
```

I have modified the the script to check for this. Also, I have changed move (mv) to copy (cp) in the script. I don't know which you want, but copy is better for testing purposes.

I checked the script with some sample files and it works OK.

---

### Post by robfindlay on 2009-03-22
> **robfindlay said:**
> Spits this out regarding line number 9: 

line 9: [: 0: unary operator expected

I actually made the changes i needed--working great now!!! thank you...

don't suppose you could comment that out so I can follow what it's doing, I used to know C++ so i can tell where you're assigning variables, but beyond that I'm lost! :-)

---

### Post by kaibob on 2009-03-22
> **robfindlay said:**
> I actually made the changes i needed--working great now!!! thank you...

don't suppose you could comment that out so I can follow what it's doing, I used to know C++ so i can tell where you're assigning variables, but beyond that I'm lost! :-)

I'm not good at this, but I added comments that should be understandable. Glad you got the script working OK.

---

### Post by robfindlay on 2009-03-22
> **kaibob said:**
> I haven't written a shell script like this before but the one copied below appears to work. You type in the length of time that you want the script to run as a command-line parameter. So, if you wanted the script to run for 1 hour, you would type the following in a terminal window:

```
scriptname 60
```

```
#!/bin/bash

# Change to source directory
cd /home/slag/www

# Issue error and exit if no command-line parameter. 
if [ "$1" = "" ]; then
echo "You forgot a time parameter!"
exit 1
fi

# Set counter
number=0

# Start while loop and continue until counter reaches $1.
# The variable $1 is command-line parameter. 
while [ $number -lt $1 ]; do

# Assign date to variable.
datestamp=$(date +%m.%d.%y)

# Assign time to variable. 
timestamp=$(date +%H.%M.%S)

# Copy source file to target directory with date and time as filename.
cp webcam.jpg /home/slag/www/history/${datestamp}-${timestamp}.jpg

# Pause for 60 seconds
sleep 60

# Increase counter by 1
number=$((number + 1))

done
```

Perhaps some of the more experienced members of the forum will have a better solution.

So if i wanted to leave this running constantly until I killed it what would I have to change?  I guess I could just input 1000000000000000000 seconds :-)

Thnks again!
-R

---

### Post by robfindlay on 2009-03-22
> **kaibob said:**
> I haven't written a shell script like this before but the one copied below appears to work. You type in the length of time that you want the script to run as a command-line parameter. So, if you wanted the script to run for 1 hour, you would type the following in a terminal window:

```
scriptname 60
```

```
#!/bin/bash

# Change to source directory
cd /home/slag/www

# Issue error and exit if no command-line parameter. 
if [ "$1" = "" ]; then
echo "You forgot a time parameter!"
exit 1
fi

# Set counter
number=0

# Start while loop and continue until counter reaches $1.
# The variable $1 is command-line parameter. 
while [ $number -lt $1 ]; do

# Assign date to variable.
datestamp=$(date +%m.%d.%y)

# Assign time to variable. 
timestamp=$(date +%H.%M.%S)

# Copy source file to target directory with date and time as filename.
cp webcam.jpg /home/slag/www/history/${datestamp}-${timestamp}.jpg

# Pause for 60 seconds
sleep 60

# Increase counter by 1
number=$((number + 1))

done
```

Perhaps some of the more experienced members of the forum will have a better solution.

Now what if I wanted to enable directory listing? E.g. domain.com/history/ and then be able to see a list of all the files?

---

### Post by kaibob on 2009-03-23
> **robfindlay said:**
> So if i wanted to leave this running constantly until I killed it what would I have to change?  I guess I could just input 1000000000000000000 seconds :-) Thnks again! -R
```
#!/bin/bash

cd /home/slag/www

while sleep 60 ; do

datestamp=$(date +%m.%d.%y)

timestamp=$(date +%H.%M.%S)

cp webcam.jpg /home/slag/www/history/${datestamp}-${timestamp}.jpg

done
```

---

