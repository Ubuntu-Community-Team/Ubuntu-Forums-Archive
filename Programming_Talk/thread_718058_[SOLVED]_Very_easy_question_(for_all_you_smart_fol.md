---
title: "[SOLVED] Very easy question (for all you smart folks)"
date: 2008-03-07
forum: Programming Talk
---

### Post by Nerdriot on 2008-03-07
I'm still pretty new to all of this stuff. I just recently started teaching myself bash scripting (about 3 weeks ago), and I understand it. It makes sense, but I still have very small questions I can't find answers to.

My question is pretty simple for you guys, I'm sure, but I'll make a quick script as an example, so you'll know what I'm talking about:

```
#!/bin/bash

selection=$(zenity --title "A or B" --text "Choose 'A' or 'B'." --list --radiolist --column "Option" --column "Selection" True "A" False "B")

choice=$?

if [ "$choice" = "0" ]; then

	echo 'You chose:' $selection
	else
		if [ "$choice" = "1" ]; then
		echo "Cancelled."

		fi
fi
```

What exactly is "$?" in "choice=$?" saying? I mean, I know that, without it, it won't output what's being selected. I know that it will just close the box when anything is selected, and either "ok" or "cancel" is selected. But why? What does "$?" mean?

I'm way too curious a person. I should just be happy that it works, but my curiosity kills me.

Oh, and one more question: if it's not specific to zenity (which I kind of doubt it is), what else could that be applied to?

Sorry for such n00bish questions... I just like learning as much as possible.

Thanks in advance!

---

### Post by LaRoza on 2008-03-07
$? means the return value of the previous command.

```

$ sudo apt-get update
$ echo $?
$ 0
$ sudo apt-get r b
$ echo $?
$ 100

```

0 usually means success, other numbers are usually error codes.

---

### Post by Nerdriot on 2008-03-07
Thank you! Greatly appreciated... :)

---

