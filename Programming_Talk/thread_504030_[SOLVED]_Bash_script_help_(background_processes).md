---
title: "[SOLVED] Bash script help (background processes)"
date: 2007-07-18
forum: Programming Talk
---

### Post by olejorgen on 2007-07-18
I'm having some problems with a simple script:
```

#!/bin/bash


for f in *.ram ; do
	url="$(cat $f)" # rtsp url
#	echo mplayer -dumpstream $omg -dumpfile temp/$f\.rm \& ;
	mplayer -dumpstream "$url"  -dumpfile temp/$f\.rm &;
done

wait

```
When I run ./dl I get:
```

./dl: line 7: syntax error near unexpected token `;'
./dl: line 7: ` mplayer -dumpstream "$url"  -dumpfile temp/$f\.rm &;'

```

Is it not possible to start background processes inside a loop? If that's the case, what do I do?

A typical .ram file looks like this:
```

rtsp://169.229.131.16:554//bibs/s2005/group1/ns10/20050119.rm?start=1:40&end=43:40

```

---

### Post by jmazzarelli on 2007-07-18
I've run into this before, too, but I can't remember what I did. There is probably a clean elegant way to do it, but I'll offer the first hack that comes to mind. Build a string up through the loops (or append each command to a file) then after the loop execute it.

---

### Post by olejorgen on 2007-07-18
Damn, I need to get better at searching. Found it on google: You have to put your commands inside {}. 
```

#!/bin/bash


for f in *.ram ; do
	{ 
		url="$(cat $f)" # rtsp url
		mplayer -dumpstream "$url"  -dumpfile temp/$f\.rm & 
	};
#	echo mplayer -dumpstream $omg -dumpfile temp/$f\.rm \& ;
done

wait

```

---

### Post by jmazzarelli on 2007-07-18
And there is the clean way. Thanks for sharing, I'm sure I'll have that same problem again myself.

---

### Post by Mr. C. on 2007-07-18
> **olejorgen said:**
> Damn, ... you have to put your commands inside {}. 

Actually, you don't.

The problem is that you have both ; and & terminating the line.

Both ; and & are *line terminators*, therefore you only use one of them.  What you have a a line followed by an empty command being backgrounded.

You don't need semicolon's ending your shell commands.  This would be sufficient:

```
for f in *.ram ; do
		url="$(cat $f)" # rtsp url
		mplayer -dumpstream "$url"  -dumpfile temp/$f\.rm & 
done
```

That said, it is generally a bad idea to startup lots of background processes all at once; they won't get done any faster, and will cause performance issues in general.  If you know there won't be too many started, there's no issue.  Just a caveat.

MrC

---

### Post by olejorgen on 2007-07-18
Thanks for the extra info

I'm quite sure that mplayer is fecthing the stream at playback rate, so in this case it should be quicker. Wether this is nice (or even legal) to do is another question :)

---

