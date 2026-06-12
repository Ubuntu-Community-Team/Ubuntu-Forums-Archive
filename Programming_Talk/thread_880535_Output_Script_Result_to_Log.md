---
title: "Output Script Result to Log"
date: 2008-08-05
forum: Programming Talk
---

### Post by OffHand on 2008-08-05
Hi there,

Is there a way to write the results of the script below to a log file?

The script is made for OS X but I will probably be able to figure out how to do it once I know the Linux way.

Thanks in advance!

```

#!/bin/bash

# this should find all users currently logged in 
users=( `who | awk '{print $1}' | sed '/^root$/d' | uniq` )

for user in "${users[@]}"; do
    # find the homedir
    homedir=/Users/$user
    find $homedir/Library/Caches -name "*AdobeFnt*" -delete
done

```

---

### Post by loell on 2008-08-05
```
./script.sh > my.log
```

---

### Post by OffHand on 2008-08-05
> **loell said:**
> ```
./script.sh > my.log
```

OS X moved from Cron to Launchd. Basically the command is put in a xml plist which looks like this:
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>Label</key>
	<string>ClearFontCache</string>
	<key>ProgramArguments</key>
	<array>
		<string>sh</string>
		<string>/Library/ITScripts/clean_font_cache.sh</string>
	</array>
	<key>RunAtLoad</key>
	<true/>
</dict>
</plist>

```

Should I change

<string>/Library/ITScripts/clean_font_cache.sh</string>

to 

<string>/Library/ITScripts/clean_font_cache.sh > my.log</string>

?

---

### Post by OffHand on 2008-08-05
> **OffHand said:**
> 
Should I change

<string>/Library/ITScripts/clean_font_cache.sh</string>

to 

<string>/Library/ITScripts/clean_font_cache.sh > my.log</string>

?

Tried it but that does not work. Is there a way to put it in the script itself instead of the command?

---

### Post by OffHand on 2008-08-05
I finally managed to make the script write to a log file but unfortunately the file is empty. This should be easy to fix. I have added "echo >> /home/user/testlog.txt" to the script like posted below.

[code]
#!/bin/bash

# this should find all users currently logged in 
users=( `who | awk '{print $1}' | sed '/^root$/d' | uniq` )

for user in "${users[@]}"; do
    # find the homedir
    homedir=/Users/$user
    find $homedir/Library/Caches -name "*AdobeFnt*" -delete
    echo >> /home/user/testlog.txt
done

---

### Post by nanotube on 2008-08-05
```

#!/bin/bash

# this should find all users currently logged in 
users=( `who | awk '{print $1}' | sed '/^root$/d' | uniq` )

for user in "${users[@]}"; do
    # find the homedir
    homedir=/Users/$user
    find $homedir/Library/Caches -name "*AdobeFnt*" -delete >> /home/user/testlog.txt
done
```

echo >> bla puts a newline into the file and nothing else. so append the >> to the find command, if you want the output of find to be in the file.

---

### Post by OffHand on 2008-08-05
For some reason that generates an empty log file even though the files were deleted  :(

Edit: I assume that there is nothing to log because the files that were found are already deleted. It would be great though if it could log what has been deleted.

Any ideas?

---

### Post by ABCC on 2008-08-05
All you need to do is sit back, relax and allow someone else's code do it for you by the mere use of the commandline option -fprint:


```

find $homedir/Library/Caches -name "*AdobeFnt*" -fprint logfile -delete

```

---

### Post by geirha on 2008-08-05
Building on ABCC's suggestion, you can also print some more descriptive messages like this. This will also not truncate the logfile each run.
[php]
#!/bin/bash

# this should find all users currently logged in
users=( `who | awk '{print $1}' | sed '/^root$/d' | uniq` )

for user in "${users[@]}"; do
  # find the homedir
  homedir=/Users/$user
  find $homedir/Library/Caches -name "*AdobeFnt*" -printf "`date`: Removing %p\n" -delete
done >> /home/user/testlog.txt
[/php]

---

### Post by OffHand on 2008-08-05
I'll try that tomorrow and let you know. Thanks!

---

### Post by OffHand on 2008-08-06
That did not work Geirha but I have decided that just knowing the script ran is good enough for me. It's already tested and verified that the files are deleted. 

Thanks for your help!

---

