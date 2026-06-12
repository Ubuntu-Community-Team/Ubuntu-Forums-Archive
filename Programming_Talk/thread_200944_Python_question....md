---
title: "Python question..."
date: 2006-06-21
forum: Programming Talk
---

### Post by SilverTab on 2006-06-21
Hi there!

Ok it's kinda late and my head hurts so I need a little help :)

What I want to do is, check for a string (which will be a sentence) if the string is longer than X ammount of characters (let's say 60 char) then I want to split the string on multiple lines (add a \n to expand it on multiple lines). The thing is, I don't want to split it in the middle of a word...so I want to replace a space character with a '\n' char.

For example:
mystring = "This is a long sentence that would need to be splitted"

I want it to become:
mystring = "This is a long sentence that \n would need to be splitted"

I've been messing for a while with string methods, but I can't find a decent way to do it ](*,)   Any help or idea would be appreciated!

---

### Post by ynef on 2006-06-21
I know nothing about Python, but conceptually all you need to do is keep track of the position of the last "space" character you've encountered while iterating over the list of characters in the string. Once you've on the current line counted up to your limit of characters, you can break at the position of the last space. If you're not doing something like this, the string functions in Python will.

---

### Post by SilverTab on 2006-06-21
Yeah this is basically what I am trying to achieve! :)

Im just not sure how to do it with python's string function... I might be able to figure it out with a rested head LOL But I'm trying to finish this thing tonight, hence why I turned to the Ubuntu Forum, which is full of smart people ;)

Thanks for the tip though, I'm still banging my head trying to figure out a way to do it LOL

---

### Post by Gustav on 2006-06-21
I did something like that in java (I hate that language so much!) some time ago. It should be easy to change it to python (and it would look better!).

Here´s the code:```
private String lineBreak(String string, int maxWidth) {
        String s = string;
        String strings[];
        if (s.length() > maxWidth) {
            strings = s.split(" ");
            for (int i = 1; i < strings.length; i++) {
                if (concatUntil(strings, i).length() > maxWidth) {
                    s = concatUntil(strings, i - 1) + "<br>" + lineBreak(concatAfter(strings, i), maxWidth);
                    break;
                }
            }
        }
        return s;
    }

    private String concatUntil(String[] strings, int nr) {
        if (nr >= strings.length) nr = strings.length - 1;
        String s = strings[0];
        for (int i = 1; i <= nr; i++)
            s = s + " " + strings[i];
        return s;
    }

    private String concatAfter(String[] strings, int nr) {
        if (strings.length > nr) {
            String s = strings[nr];
            if (strings.length > nr)
                for (int i = nr+1; i < strings.length; i++)
                    s = s + " " + strings[i];
            return s;
        } else {
            return "";
        }
    }
```

---

### Post by SilverTab on 2006-06-21
Thanks alot! Exactly what I needed :)

Here is the python version!

```

        def lineBreak(self, string, maxWidth):
		if len(string) > maxWidth:
			self.sSplitted = string.split(" ")
			for i in range(0, len(self.sSplitted)):
				if len(self.concatUntil(self.sSplitted, i+1)) > maxWidth:
					string = self.concatUntil(self.sSplitted, i) + "|nl|" + self.lineBreak(self.concatAfter(self.sSplitted, i+1), maxWidth)
					break
		return string
        
	def concatUntil(self, strings, nr):
		if nr >= len(strings):
			nr = len(strings) - 1

		self.s = strings[0]
		for i in range(1, nr+1):
			self.s = self.s + " " + strings[i]
		return self.s
        
        
	def concatAfter(self, strings, nr):
		if len(strings) > nr:
			self.s = strings[nr];
			if len(strings) > nr:
				for i in range(nr+1,len(strings)):
					self.s = self.s + " " + strings[i]
			return self.s
		else:
			return ""

```

---

### Post by foxylad on 2006-06-21
Or you could...

import textwrap
lines=textwrap.wrap(s,maxWidth)

This returns a list of lines (without terminating EOLs). Easier, but not half as much fun!

---

### Post by SilverTab on 2006-06-21
Hahaha oh my...I just tested it...works well! 


.... well...I think I will keep my python function after all! As you said, more fun! ;)

Thanks though, I won't forget that one LOL

---

### Post by thumper on 2006-06-22
Damn, I didn't know about textwrap either.  But I did come up with a different python one...
```
def splitter(line, size):
    lines = []
    while len(line) > size:
        pos = line.rfind(' ', 0, size + 1)
        if pos < 0:
            pos = line.find(' ')
        if pos < 0:
            lines.append(line)
            line = ''
        else:
            lines.append(line[:pos])
            line = line[pos+1:]
    if len(line) > 0:
        lines.append(line)
    return lines

```

---

### Post by Gustav on 2006-06-22
It may look nicer and shorter than mine. But mine uses recursion!

(It would look fantastic in lisp :))

---

