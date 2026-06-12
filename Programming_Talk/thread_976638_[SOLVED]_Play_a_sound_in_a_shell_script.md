---
title: "[SOLVED] Play a sound in a shell script?"
date: 2008-11-09
forum: Programming Talk
---

### Post by josephellengar on 2008-11-09
Bash- I'm looking for a command that makes a system beep and for a command that plays a sound file (mp3 or the like) and then closes whatever program was used to do that.  Also, is there a command that allows me to pause a script for a little while?  Finally, if I put a && between two commands on the same line, that would make the next one start when the first one ended, correct?  Thanks!

---

### Post by gnusci on 2008-11-09
> **idigchess said:**
> Bash- I'm looking for a command that makes a system beep and for a command that plays a sound file (mp3 or the like) and then closes whatever program was used to do that.  Also, is there a command that allows me to pause a script for a little while?  Finally, if I put a && between two commands on the same line, that would make the next one start when the first one ended, correct?  Thanks!

[B]sudo apt-get beep
sudo apt-get mpg123[/B]

Well if you add only one **&** it will be as you said, but if you use two **&&** the second one will be executed only if the first one was successful executed without errors.

---

### Post by geirha on 2008-11-10
> **idigchess said:**
> Bash- I'm looking for a command that makes a system beep 

You can also get a simple system beep with just ```
echo -e '\a'
``` but with the beep command you can get longer beeps and other frequencies etc.

> **idigchess said:**
> and for a command that plays a sound file (mp3 or the like)
mplayer is also a nice option here, it will play a lot of formats, including mp3.

> **idigchess said:**
> and then closes whatever program was used to do that.

That's a bit difficult. I'm sure it's possible, but I don't know how. It's probably easiest to look for known programs that play music, and then kill them.

> **idigchess said:**
> 
Also, is there a command that allows me to pause a script for a little while? 

```

sleep 60  # Pause for a minute
sleep 1   # Pause for a second
sleep 0.1 # Pause for a tenth of a second
read -n1 -p "Press any key to continue..." # Pause until a key is pressed

```

> **idigchess said:**
> 
 Finally, if I put a && between two commands on the same line, that would make the next one start when the first one ended, correct?  Thanks!

```

command1 && command2 # command2 is run after command1 if and only if command1 succeeded (returned zero)
command1 || command2 # command2 is run after command1 if and only if command1 failed (returned non-zero)
command1 ; command2 # command2 is run after command1 regardless of the exit status of command1 (; is virtually the same as a new line)
command1 & command2 # command1 is run and immediately sent to the background so the script just continues on by running command2

```

---

