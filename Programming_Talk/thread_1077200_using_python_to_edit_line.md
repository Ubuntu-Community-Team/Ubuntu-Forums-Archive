---
title: "using python to edit line"
date: 2009-02-22
forum: Programming Talk
---

### Post by Sandsound on 2009-02-22
I have a small python/glade program with a spinbutton and two buttons.
I'd like to read a single line in a file and put the value into a spinbutton, change the value in the spinbutton and write the new value to the file.

This is what I have so far (not much I know) :
> 
def update_memlock_amount(self, spin_object):   
  memlock_entry_amount = str(int(self.memtotal*(spin_object.get_value()/100)))
  self.memlock.line_replacement = "@audio - memlock " + memlock_entry_amount
  print self.memlock.line_replacement
  global memlock_entry_amount
		
def read(self, widget):
  f = file('test.txt', 'r')
  line = f.readline()
  print line
  f.close()
  self.wTree.get_widget("memlock_spinbutton").set_value(float(line))
		
def write(self, widget):
  os.system('cp test.txt backup_text.txt')
  for line in fileinput.FileInput("test.txt",inplace=1):
    if "@audio - memlock" in line:
      line=line.replace("@audio - memlock - ","@audio - memlock - " + memlock_entry_amount)
      print line

When i change the value in the spinbutton and click the write-button, it deletes everything else in the file and only writes the new line, but also keeping the old value.

the test.txt is :
> @audio - rtprio - 99
@audio - nice - -10
@audio - memlock - 5000000
but all I get is this :
> 
@audio - memlock - 25000005000000

btw. this is supposed to be part of a project inspired by ubuntustudio-controls but with a few more options. you can find the project (ubuntu-audio-tweaks) here : [http://www.sandgreen.dk/index.php?side=prog_python]("http://www.sandgreen.dk/index.php?side=prog_python")

As it might be obvious, I'm am not a experienced python programmer :)

---

### Post by geirha on 2009-02-22
Please use code-tags instead of quote-tags for code. Especially python code where identation is part of the syntax.

There are several ways you can change the last number on that line. One is using regular expressions, another one is splitting the string. It all depends on the format of the file. Try doing the following in a python shell:
```

help(str.split)
help(str.join)

line="@audio - memlock - 5000000 "
s= line.split()
print s
s[-1]="2500000"
print s
line=" ".join(s)
print line

```

---

### Post by Sandsound on 2009-02-22
> **geirha said:**
> Please use code-tags instead of quote-tags for code.

Sorry, I did notice that it looked funny, now I know why :-)

split/join looks like it does exactly what I need, thanks.

---

### Post by Sandsound on 2009-02-24
This is what I ended up with :
```

	def limits(self, widget):
		# Hide notification
		self.wTree.get_widget("window1").hide()

		# Backup file before doing anything
		os.system("cp /etc/security/limits.conf /etc/security/backup_limits.conf")

		# Read @audio lines from limits.conf and make values global
		memtotal=int(meminfo_total.meminfo_total())
		# set max-range to memlock spinbutton
		self.wTree.get_widget("memlock_spinbutton").set_range(0, memtotal)
		
		# Read values from limits.conf to use in spinbuttons as globals 
		# and delete the @audio lines from limits.conf
		global rtpriovalue
		global nicevalue
		global memlockvalue
		for line in fileinput.input("/etc/security/limits.conf",inplace =1):
			line = line.strip()
			if not '@audio' in line:
				print line 
			if '@audio - rtprio' in line:
				s1= line.split()
				rtpriovalue=int(s1[-1])
				self.wTree.get_widget("rtprio_spinbutton").set_value(rtpriovalue)
			if '@audio - nice' in line:
				s2= line.split()
				nicevalue=int(s2[-1])
				self.wTree.get_widget("nice_spinbutton").set_value(nicevalue)
			if '@audio - memlock' in line:
				s3= line.split()
				memlockvalue=int(s3[-1])
				self.wTree.get_widget("memlock_spinbutton").set_value(memlockvalue)
		fileinput.close

```

Of course this is just a part of the source, the full source (called ubuntu-audio-tweak) can be downloaded here : [http://www.sandgreen.dk/index.php?side=prog_python]("http://www.sandgreen.dk/index.php?side=prog_python")
if someone should be interested :-)

---

### Post by geirha on 2009-02-24
Looks good to me. I do have a few comments on the code though, hope you don't mind.

I'd change some of those ifs to elif. If the line contains '@audio - rtprio' for instance, it should just read out the value and process it, then continue to the next line from the input file, not keep checking if it also matches '@audio - nice' and '@audio - memlock' as well.

Also, you can do file copy with shutil.copy. I prefer to use functions provided by the language, when available, rather than using a system call. Also more portable.

---

### Post by Sandsound on 2009-02-24
Thank you very much, any help is more than welcome.

Portability isn't really an issue for this particularly project since it is designed to work for Ubuntu only, but you are absolutely right, and I might as well learn to do it right in the first place.

Not sure if I understand the elif part correctly thou, have to read up on it.
I started about a month ago reading a book called "A byte of Python" but after a few chapters I decided to just start programming and learn what I needed along the way, so I have a few things to read up on :-)

---

### Post by Can+~ on 2009-02-24
elif is just else if.

if (condition is met):
    do something
elif (else if another condition is met):
    do something else
else:
    do one more thing.

The advantage of using elif after the first if, means that if the first condition is true, it won't need to check the following ones. Thus saving from making unnecessary "in" checks.

```
			if not '@audio' in line:
				print line 
			elif 'rtprio' in line:
				s1= line.split()
				rtpriovalue=int(s1[-1])
				self.wTree.get_widget("rtprio_spinbutton").set_value(rtpriovalue)
			elif 'nice' in line:
				s2= line.split()
				nicevalue=int(s2[-1])
				self.wTree.get_widget("nice_spinbutton").set_value(nicevalue)
			elif 'memlock' in line:
				s3= line.split()
				memlockvalue=int(s3[-1])
				self.wTree.get_widget("memlock_spinbutton").set_value(memlockvalue)

```

And with this edited version, now if @audio is not in line, it will just print, otherwise it will check for the following conditions (since we already discarded the possibility of not being @audio, you can cut off the "@audio -" part).

---

### Post by geirha on 2009-02-24
Another thing I just noticed. You are reading from a configuration file in which anything after a # is a comment. Your checks, « if '@audio - rtprio' in line:», etc. will match both commented and uncommented lines, but you probably only want to match the uncommented ones.

One way is to change those checks into if line.startswith('@audio - rtprio') etc.. Another way is to filter out any lines starting with # with something like
```

for line in inputfile:
  line=line.strip()
  if line.startswith('#'):
    print line
    continue

```

Yet another problem with comments is that you can have them at the end of a line, so the following is a legal line
```

@audio - rtprio - 1234 # setting rtprio to 1234 for the audio group

```
but since you are reading in the last field of the line (s1[-1]), it will try to cast the string "group" into an int. Instead you should use the actual field.

Yet another problem is that you don't need to have a space between the fields, it can be any combination of one or more whitespaces. So it might be better to split the line first thing, then go through several layers of ifs.
```

for line in inputfile:
  line.strip()
  ...
  s=line.split()
  if s[0] == "@audio" and s[1] == '-':
    if s[2] == "rtprio":
      do something
    elif s[2] == "nice":
      do something else
    ...

```

---

### Post by Can+~ on 2009-02-24
@geirha

I think this is one of the few situations when a regular expression could make things easier, rather than the usual split+matching combo.

---

### Post by geirha on 2009-02-24
> **Can+~ said:**
> @geirha

I think this is one of the few situations when a regular expression could make things easier, rather than the usual split+matching combo.

Hm, yes perhaps, but I think it's on the borderline. The regex approach will require about the same amount of code. Probably a good exercise for the OP to try both approaches though.

---

### Post by Sandsound on 2009-02-24
Thanks to you both.

I can see I have a lot of reading to do :-)

Regarding elif, some people have only set one or two of the values, so if I understand correctly, using elif will stop the process if say the rtprio isn't there, even if the memlock is ?

I had a quick glance at regular expression, and it looks very complex, but I guess most things do, until you get to know them :-)
Does it run faster than just using python ? or is it just faster to write ?

---

### Post by geirha on 2009-02-24
> **Sandsound said:**
> 
Regarding elif, some people have only set one or two of the values, so if I understand correctly, using elif will stop the process if say the rtprio isn't there, even if the memlock is ?


No more like the opposite. Consider this example:
```

if x == 'a': y=10
if x == 'b': y=11
if x == 'c': y=12
print "y is",y

```
If x happens to equal 'a' in the above snippet, then it will trigger on the first if and set y to 10. Then it will check if x equals 'b', which is now pointless since we already know it is 'a'. Then it will check if it is equal 'c', which it isn't, and then it will print the value of y.

Now with elif.
```

if   x == 'a': y=10
elif x == 'b': y=11
elif x == 'c': y=12
print "y is",y

```

If x happens to equal 'a' again, then it will trigger on the first if and set y to 10. Then it will skip past all elifs and just print the value of y, saving some processing.

If x happens to equal 'b', then it will first check if it equals 'a' which it doesn't, then it will check if it equals 'b', which it does, and set y to 11, and then skip the last check and print the value of y.

> **Sandsound said:**
> 
I had a quick glance at regular expression, and it looks very complex, but I guess most things do, until you get to know them
Does it run faster than just using python ? or is it just faster to write ?

Regular expressions can be complex, and it sometimes requires a bit of experience to get them right. If you are unfamiliar with regular expressions, it will be probably be a bit hard to do the above using regular expressions right away. I suggest you first try to get it right with the method you are currently using, and then afterwards see if you can get python's re module to do your bidding of parsing that file.

---

### Post by Can+~ on 2009-02-24
I'm not a regexp expert, so bear with me:

[PHP]#!/usr/bin/python

import re

#Regular expression
regexp = re.compile(
    r"""\s*@audio\s* \-               # @audio -
    \s*(nice|rtprio|memlock)\s* \-    # (nice, rtiprio or memlock) -
    \s*(\-?)\d+""",                   # Must be a number (signed or not)
    re.I+re.X)

#Work the file out

audio_config = open("test.txt", "r")

for line in audio_config:
    result = regexp.match(line)
    if result is not None:
        print "Match: %r" % result.group()
        print "     And the number: %d" % int(result.group().split("-", 2)[-1])

audio_config.close()
[/PHP]

So far, with this test file:

```
#hello world

word

@audio - rtprio - 99 # roflmao
@audio - nice - -10
@audio - memlock - 5000000
@audio - random - 50
@audio - nice - OVER NINE THOU...

#@audio - memlock - 30
```

Produced:

```
Match: '@audio - rtprio - 99'
     And the number: 99
Match: '@audio - nice - -10'
     And the number: -10
Match: '@audio - memlock - 5000000'
     And the number: 5000000

```

*EDIT: Imrpoved, twice.

---

### Post by Sandsound on 2009-02-26
Thank you both, again :-)

This has been a learning experience, and I can see that regexp have a clear advantage when dealing with files like this, only wish I understood it better.
Do you know of any books or online tutorials covering this ? something like "regexp for dummies", those I have been able to find, assumes that one already know how to write a program ;-) and most are for C or other languages.

btw. for now, I am rather pleased with my little ubuntu-audio-tweaks program, and have moved on to write a css generator for HTML, but I am facing the same problems with reading and writing specific lines to a file, so I can use much of the stuff what I have learned over the last days.

---

### Post by Can+~ on 2009-02-26
I actually never used a book or tutorial for regular expressions, I just look at the reference:

[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

See what characters you need, try creating small practices with known outcomes and see if you can reach the goal with re.

---

