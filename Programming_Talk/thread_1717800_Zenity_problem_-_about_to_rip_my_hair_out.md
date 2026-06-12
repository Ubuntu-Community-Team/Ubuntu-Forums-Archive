---
title: "Zenity problem - about to rip my hair out"
date: 2011-03-30
forum: Programming Talk
---

### Post by Thund3rstruck on 2011-03-30
Ok, I'm about to give up on this because I just can't figure out what the f@$k is going on here. 

I have a zenity checklist here:
```

selectedItems=`zenity --list \
          --title="Select the samba share(s) to mount" --checklist --multiple --width="500" --height="300" \
	  --column="Choice" --column="Remote Share" --column="Local Path" "${zenColumns[@]}" --print-column="ALL" --separator="|" `

```

If I manually populate the zenColumns array it works correctly:
```

zenColumns=( True "//baileyfs01/Music" "/media/baileyfs01/music" )

```

But when I add the columns in a for loop, zenity always interprets the True value as the 2nd column and not whether the checkbox is checked or not!

```

zenColumns+=( True "${arrShares[$i]}" "$bMount/$mnt" )

```

The True value shows up in the 2nd column (the Remote Share column) and the share shows up in the Local Path column and the local Path is missing. 

:confused:

---

### Post by Thund3rstruck on 2011-03-30
Whoa boy... ugh... apparantly you can not initialize an array in bash like this:

```

# The zenity columns
zenColumns=

```

I must have mis-read the doc... initializing with ( ) fixed it. 

```

# The zenity columns
zenColumns=( )

```

---

