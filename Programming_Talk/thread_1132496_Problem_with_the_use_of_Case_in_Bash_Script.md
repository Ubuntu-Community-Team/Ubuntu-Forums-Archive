---
title: "Problem with the use of Case in Bash Script"
date: 2009-04-21
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-04-21
Ey guys, here is the problematic portion of my code:
```


	if !(test -s $a); then
		read -p "Do you wish to remove $a?(Y/N)" choice
		case $choice in
			[Yy]* ) echo rm "$a"
			[Nn]* )  echo "$a not removed" #line 20
			* ) echo "Enter \"Y\" or \"N\""
		esac

	fi



```

Which I got from this online example: [http://stackoverflow.com/questions/226703/how-do-i-prompt-for-input-in-a-linux-shell-script](http://stackoverflow.com/questions/226703/how-do-i-prompt-for-input-in-a-linux-shell-script)

And when I run my script I get this error:
```

t$ bash cleaner.sh 
cleaner.sh: line 20: syntax error near unexpected token `)'
cleaner.sh: line 20: `			[Nn]* )  echo "$a not removed"'

```

I am having a hard time figuring out why... any help would be greatly appreciated! Thanks in advance!

---

### Post by StunnerAlpha on 2009-04-21
Nevermind I got it, I omitted putting two semi colons at the end of each line... for some reason I thought that would make the script exit prematurely...

---

