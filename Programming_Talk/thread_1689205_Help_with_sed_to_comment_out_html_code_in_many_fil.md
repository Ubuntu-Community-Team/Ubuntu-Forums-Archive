---
title: "Help with sed to comment out html code in many files?"
date: 2011-02-16
forum: Programming Talk
---

### Post by Wildscot on 2011-02-16
I'm trying to comment out the following line of code in many files but I just can't get it to work.
```
<p style="text-align: center; margin-top: 15px; margin-bottom: 0px"><? echo getimg("allpages.php", '06', '0'); ?></p>
```
I've been at this so long that I can't remember everything I've tried but I don't know where I'm going wrong. I've been working on variations of the following
```
find ./ -type f -exec sed -i 's|<p style="text-align: center; margin-top: 15px; margin-bottom: 0px"><? echo getimg("allpages.php", '06', '0'); ?></p>|<!--&-->|g' {} \;
```
Both using the full string and the & sign, various seperators and successively escaping everything I can think of. 
It either seems to execute and I can see the code above seems to run and I can see that it changes the time-stamp on all of the files in the path, not just those with the relevant line but nothing seems to change.
I would have been quicker to do this by hand but then I'd learn nothing!

---

### Post by Vaphell on 2011-02-16
maybe try some less specific pattern that would match only that line? i guess it all fails because of single quotes inside the pattern that interfere with proper parsing.

```
echo '<p style="text-align: center; margin-top: 15px; margin-bottom: 0px"><? echo getimg("allpages.php", "06", "0"); ?></p>' | sed -r 's:<p.*echo.*getimg.*allpages.php.*06.*0.*</p>:<!--&-->:g'
```

---

### Post by Wildscot on 2011-02-16
Excellent, thanks. That seems to do the trick.
I'm guessing I should go and read up on the echo command but any chance you can give me a quick explanation of how that operates?

---

### Post by Vaphell on 2011-02-16
echo simply prints out the text, variables included
```
echo current user: $USER, home dir: $HOME
```
i used it as an input for sed via pipe (with your line to see if it triggers correct response). It's a good way to test some command chains with the specific input.
```
echo $'abc\n123\nxyz000'
echo $'abc\n123\nxyz000' | grep [0-9]
echo $'abc\n123\nxyz000' | sed -r 's/[0-9]+/*DIGITS*/g'
```

Of course it does nothing directly useful for your case as you feed data to sed directly from a file.
There are some caveats to echo usage, you'll get to know them when you familiarize yourself with shell scripting.

---

### Post by Wildscot on 2011-02-16
Many thanks, I'm sure I will ;)

---

