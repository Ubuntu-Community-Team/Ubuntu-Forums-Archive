---
title: "Python Subprocess Problem"
date: 2011-02-08
forum: Programming Talk
---

### Post by fret669 on 2011-02-08
I've been trying to learn how to make gtk applications with python and glade, and so far so good. My issue is with the subprocess module. I am trying to run mkisofs in a sub process, and use 2 python variables as the input, and output of the process. I've tried every way I've found online, and it doesn't work. 

```
class Iso():
	"""Runs mkisofs"""
	def __init__(self, inFile, outFile):
		
		print '\nread:'
		proc = subprocess.Popen(['mkisofs', '-o', outFile, inFile],
			shell=True,
			stdout=subprocess.PIPE,
                       )
		stdout_value = proc.communicate()[0]
		print '\tstdout:', repr(stdout_value)
```

mkisofs is telling me "missing pathspec", but I'm giving it the input and output file paths.

So, just in case I haven't made clear what I want to do... I want my python variables to be used as arguments for mkisofs. Any help will be greatly appreciated :D

---

### Post by MadCow108 on 2011-02-08
why do you use shell=True?
that executes: sh -c mkisofs -o test.iso tmp which fails because of wrong quoting
removing it should make the code work
without it you also do not need to care about quoting filenames with spaces

also you might want to pipe stderr too
mkisofs does not print much to stdout

---

### Post by fret669 on 2011-02-08
lol That worked. I did try to set it to False as well, but still nothing. So simple, but so damaging lol. Thank you :)

I'll also try that, and see what I get. I'm just making this for myself, so I don't think I need anything detailed, but I'll still try and see.

---

