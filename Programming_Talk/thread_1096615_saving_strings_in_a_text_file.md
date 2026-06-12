---
title: "saving strings in a text file"
date: 2009-03-15
forum: Programming Talk
---

### Post by renkinjutsu on 2009-03-15
having some trouble with scripting
Below is just a test i'm running, and trying to get to work correctly.
```
#!/bin/bash
echo "Please enter working directory: "
read wdir

if [ ! -f "$wdir"/cvprefs ] ; then
    echo "input filetype is: "
    read ext ; echo "ext=\"$ext\"" >> "$wdir/cvprefs"
    echo "output filetype is: "
    read extout ; echo "extout=\"$extout\"" >> "$wdir/cvprefs"
    echo "Video encode bitrate desired: "
    read vbit ; echo "vbit=\"$vbit\"" >> "$wdir/cvprefs"
    echo "filename: front portion"
    read ff ; echo "ff=\"$ff\"" >> "$wdir/cvprefs"
    echo "Series? y/n"
    read ser ; echo "ser=\"$ser\"" >> "$wdir/cvprefs"
  else
    echo "Continuing from incomplete job"
    wait 5
    sh "$wdir/cvprefs"
fi

echo $ext
echo $extout
echo $vbit
echo $ff
echo $ser
echo
echo Correct?
```

i'm trying to write a script that queues video conversion using the handbrakecli .. i got the queue to work fine, and the script prompts the user for settings .. then i realized that it'd be bothersome having to keep inputting the settings for a specific batch/job (if you stopped the job in the middle without finishing it) everytime you open up the script again

so my solution was to save the preferences for that specific job into the working directory.. but the problem is, when i sh into that text file(cvprefs), the variables don't stick! I get a bunch of blank lines outputted from the echo commands. I believe it's because sh runs as a separate process... right?

also i tried to use `cat cvprefs` with the backward ticks instead of using sh, but that gives me
```
bash: ext="avi": command not found
```
i'm not very experienced, so this is driving me nuts! i can't find a solution!

---

### Post by geirha on 2009-03-15
That is because when you do «sh "$wdir/cvprefs"», you open a new shell that reads that file, sets those variables, and then that shell exits, and those variables disappears with it. In addition you are calling sh, which is even a different shell than bash. 

If you want them to stick, you'll need to source the file. That'll execute the lines of the script in the current shell
```

. "$wdir/cvprefs"
# or 
source "$wdir/cvprefs"

```

---

