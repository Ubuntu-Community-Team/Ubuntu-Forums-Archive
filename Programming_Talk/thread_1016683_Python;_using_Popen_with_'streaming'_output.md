---
title: "Python; using Popen with 'streaming' output"
date: 2008-12-20
forum: Programming Talk
---

### Post by Sprut1 on 2008-12-20
Okay, so I have been using subprocess.Popen() lately to execute various commands on my Kubuntu machine. I use the subprocess.PIPE to read output, something like this:
```

ret = subprocess.Popen("iwlist ath0 scan", shell=True, stdout=subprocess.PIPE)

output = ret.communicate()[0]
lines = output.split('\n')

for line in lines:
	if not line == "":
		print line

```

This works like a charm, I can take this output and print it to a listctrl or whatever, BUT if I use the same code to execute the command 'top' or something similar (that constantly updates its output) the output is forced to the terminal from where I'm running the code, I can't use the PIPE to read output and print it to a listctrl (which is basically what I want to do). I have no clue where to go from here, did some google searches and found out nothing.

I might add that I'm running these process' on own threads, would it be possible to have them running and just read output when I want? I really, really hope so.

Any help appriciated.

---

### Post by scooper on 2008-12-20
I don't have an answer to the technical issue of getting top to cooperate with a pipe.  But I do wonder why you chose that approach.  You could periodically run the ps command, directly access the /proc filesystem, or see if other APIs are available.  I'm sure there are other process-reporting programs that you could look at to see how they use the /proc filesystem or an API.

Is there a strong reason you want to use top?

---

### Post by Sprut1 on 2008-12-20
> **scooper said:**
> I don't have an answer to the technical issue of getting top to cooperate with a pipe.  But I do wonder why you chose that approach.  You could periodically run the ps command, directly access the /proc filesystem, or see if other APIs are available.  I'm sure there are other process-reporting programs that you could look at to see how they use the /proc filesystem or an API.

Is there a strong reason you want to use top?

I'm sorry but you misunderstood me, my bad for not making myself clear. I'm not using the 'top' command at all actually, it was just an example. What I'm making is an GUI for the aircrack-ng programs. 'Airodump-ng' produces the same output as the 'top' command, thats why I used that example.

---

### Post by Sprut1 on 2008-12-20
I think I'm just going to read from the file the same program writes to, I guess this is somewhat slower, but at least I don't have to worry about this anymore:)

If anyone do know a solution I'll be more than happy to hear it though:)

---

### Post by imdano on 2008-12-20
Programs like top use curses (or a similar library) to display output, I don't think its as simple as it printing to stdout or stderr...

---

### Post by Sprut1 on 2008-12-20
> **imdano said:**
> Programs like top use curses (or a similar library) to display output, I don't think its as simple as it printing to stdout or stderr...

That I found out, you got any experience with the issue?

---

