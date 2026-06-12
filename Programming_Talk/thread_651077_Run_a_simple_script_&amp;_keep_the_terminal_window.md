---
title: "Run a simple script &amp; keep the terminal window open"
date: 2007-12-27
forum: Programming Talk
---

### Post by akimatsu123 on 2007-12-27
hi. i use PPPoE, and i do not want the connection to start at startup. And its a pain to type "pon dsl-provider" and "poff dsl-provider" every time so i wrote a little shell script that looks like this:

```

echo "start or stop PPPoE? Y=Start N=Stop (y/n)"

	read answer

		if [ "$answer" = "y" ]; then

		pon dsl-provider
		plog

		fi

		if [ "$answer" = "n" ]; then

		poff dsl-provider
		plog

		fi

```

the "plog" command is in there so that i can make sure the connection was established (ISP is a little glitchy at times with username/password so it doesnt work sometimes)

to execute this i made a launcher with the command (script is called "PPPoE_Toggle")

```
 sudo /home/username/PPPoE_Toggle 
```

except it just flashes the terminal, runs the script, and closes very quickly. So fast that i cannot read the message from the "plog" command. 

how do i create a launcher on my desktop that would start the script, and keep the terminal open after it finishes?

the only way i know now is to actually OPEN terminal and type in 

```
/home/username/PPPoE_Toggle
```

which keeps the ternimal open but then its still a lot of typing and im lazy :P

thanks in advance. sorry for the long post.

---

### Post by zero-9376 on 2007-12-27
dont know if you have tried it or not but you might want to look at gpppon (in repos) I used it to allow my partners parents to connect easily when they were still on dialup

---

### Post by akimatsu123 on 2007-12-27
thank you, i will check that out. meanwhile. any ideas to get my script to do what i want it to do?

---

### Post by ghostdog74 on 2007-12-27
> **akimatsu123 said:**
> and keep the terminal open after it finishes?

in your script, put a "read" statement
```

....
... 
# last command
read
....
# end of script...

```

then you can see what happens.

---

### Post by akimatsu123 on 2007-12-27
works like a charm. thank you very much.

---

### Post by geirha on 2007-12-27
Alternatively, you can use zenity to do it graphically. Something like this perhaps:
```

# Displays plog and asks user whether to start or stop
choice=$(zenity --list --title="PPPoE" --text="`plog`" --column="Choice" "Start" "Stop")

case $choice in
  "Start")
    ( pon dsl-provider; plog ) 2>&1 | 
    zenity --text-info --title="PPPoE connect"
  ;;
  "Stop")
    ( poff dsl-provider; plog ) 2>&1 |
    zenity --text-info --title="PPPoE disconnect"
  ;;
  *)
    zenity --error --title="PPPoE" --text="Aborting"
  ;;
esac

```

---

