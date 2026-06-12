---
title: "Zenity Progress Not Assigning Varables!"
date: 2010-05-01
forum: Programming Talk
---

### Post by Dart00 on 2010-05-01
Im working on a project on a bit of a deadline and this problem is the last thing I need right now... :(

Iv been working with Zenity using Ubuntu 9.10. The script is highly complex but for some reason this lil aspect is not working out...

I have a few things happening.I want to get the user a nice waving bar to look at so they know the computer is working. A lot of the "things" happening is variables are being updated...but when I go to use the updated values later in the script...they never got updated! After playing with it more i realized NOTHING I do with variables gets saved!

I know this must be something small but iv been reading a lot of documents and other code and they dont seem to be having this problem???

Example 1:

#```
!/bin/bash

# Declare Variables:
VAR1=""
VAR2=""

# Assign Values:
VAR1="Unset"
VAR2="Unset"

# Start zentity code to pipe to zentity
(

# Assign Values:
VAR1="set"
VAR2="set"

# Do something....
sleep 2

# End of zentiy code and pipe to zentity
) |
zenity --width="400" --progress --title="Checking Compatibility:" --text="Checking System Compatibility. Please Wait..." --percentage=0 --pulsate --auto-close

# echo Variables to screen with new values:
echo "VAR1: $VAR1"
echo "VAR2: $VAR2"

# ==== WHY DO THOSE VARIABLES NOT SET TO "Set"? ====

# Press Enter to Close:
read close

exit 0
```
Example 2:

```
!/bin/bash

# Declare Variables:
VAR="Unset"

(
VAR="Set"
)|zenity --progress --title="Copy files progress" --text="Copying $# files to $USER@$REMOTE..." --auto-close

echo "Answer: $VAR"

exit 0
```Any help would be greatly appreciated!

---

