---
title: "batrename - Batch renaming python script"
date: 2011-02-01
forum: Programming Talk
---

### Post by AtomicClock on 2011-02-01
Hello everyone,
Forgive me if I should've posted this somewhere else, but I wanted to share this and see what happens. 

There have been times in the past where I've had a large number of non-unique files (for example, say I've got 150 images of the moon that I took during an observing session). The default names that they are given are pretty useless, (e.g. 'IMG242.jpg') so I wanted a way to quickly and easily rename them all using some kind of indexing mechanism. Surprisingly, I couldn't really find anything that could do it easily, so eventually I decided to write a python script. So, I've been working on it for the last 3 days and here it is.

The help function will hopefully explain most of the ideas behind it. Basically, it follows a pattern and renames all files in a given directory, using an indexing mechanism (there are 4 so far: numeric, alphabetic, as well as Greek and Hebrew letter names, mainly for fun).

If anyone knows a better way to do something like this, I'd appreciate a pointer. And if anyone has an idea for a useful feature, or maybe another indexing method, that'd be good too.

```
#!/usr/bin/env python

__prog__ = "batrename"
__version__ = "1.0"

import os
import sys
import math
import datetime
import string
import re
import glob
import argparse

def main():
	args = setupArguments()
	
	if args.style == "numeric":
		batchNumeric(args)
	elif args.style == "alpha":
		batchAlpha(args)
	elif args.style == "greek":
		batchGreek(args)
	elif args.style == "hebrew":
		batchHebrew(args)
		
def batchNumeric(args):
	filePaths = cleanPaths(args.directory, args.match)
	length = len(filePaths)
	
	for i in range(length):
		index = getNextIndex(args, i, len(str(length)))
		newname = getNewname(filePaths[i], index, args)
		renameFile(filePaths[i], newname)
	
	sys.stdout.write("\nBatch rename complete - %s files renamed\n" % str(length))
			
def batchAlpha(args):
	filePaths = cleanPaths(args.directory, args.match)
	length = len(filePaths)

	for i in range(length):
		index = getNextIndex(args, i, int(math.ceil(math.log(length, 26))))
		newname = getNewname(filePaths[i], index, args)
		renameFile(filePaths[i], newname)
	
def batchGreek(args):
	filePaths = cleanPaths(args.directory, args.match)
	
	if len(filePaths) > 24:
		sys.stderr.write("Error: too many files - the Greek alphabet only has 24 letters\n")
		sys.exit()
	
	for i in range(24):
		index = getNextIndex(args, i)
		newname = getNewname(filePaths[i], index, args)
		renameFile(filePaths[i], newname)
	
	sys.stdout.write("\nBatch rename complete - %s files renamed\n" % str(len(filePaths)))
	
def batchHebrew(args):
	filePaths = cleanPaths(args.directory, args.match)
	
	if len(filePaths) > 22:
		sys.stderr.write("Error: too many files - the Hebrew alefbet only has 22 letters\n")
		sys.exit()
		
	for i in range(22):
		index = getNextIndex(args, i)
		newname = getNewname(filePaths[i], index, args)
		renameFile(filePaths[i], newname)
	
	sys.stdout.write("\nBatch rename complete - %s files renamed\n" % str(len(filePaths)))

def setupArguments():
	parser = argparse.ArgumentParser(description='Batch rename files using an iterative approach.', formatter_class=argparse.RawTextHelpFormatter)

	parser.add_argument("pattern", help="a pattern that defines how to rename the files,\n"
		"must be enclosed in single quotes to avoid conflicts\n"
		"with shell syntax, the following keywords can be used,\n"
		"as shown:\n\n"
		"{index} [required, inserts the current index]\n\n"
		"{base} [optional, inserts the entire original filename,\n"
		"minus the extension]\n\n"
		"{regex:FILENAMEREGEX:} [optional, inserts the result of\n"
		"a comparison of the original filename with a regex\n"
		"supplied within the colons in the tag,\n"
		"i.e. FILENAMEREGEX]\n\n"
		"{date} [optional, inserts the current date in the form\n"
		"YY-mm-dd]\n\n"
		"{date:DATEFORMAT:} [optional, inserts the current date\n"
		"using the format supplied by DATEFORMAT, for usage\n"
		"look up python's strftime() function]")
	parser.add_argument("-s", "--style", dest="style", default="numeric",
		help="the index STYLE used during renaming:\n"
		"numeric, alpha, greek, hebrew [default: %(default)s]",
		choices=["numeric", "alpha", "greek", "hebrew"])
	parser.add_argument("-d", "--directory", dest="directory", default=os.getcwd(),
		help="the directory in which the files are located\n"
		"[default: current directory]")
	parser.add_argument("-m", "--match", dest="match", default="*",
		help="a file match string that supports shell-style wildcards,\n"
		"must be enclosed in quotes for best results\n"
		"[default: all files]")
	parser.add_argument("-o", "--override-ext", dest="override", default=False,
		action="store_true", help="do not protect file extension [default: %(default)s]")
	parser.add_argument("-z", "--zero", dest="zero", default=False,
		action="store_true", help="begin the index with 0 instead of 1 [default: %(default)s]")
	
	alphagroup = parser.add_mutually_exclusive_group()
	alphagroup.add_argument("-l", "--lower", dest="lower", default=False,
		action="store_true", help="index using lowercase letters,\n"
		"does not apply to numeric [default: %(default)s]")
	alphagroup.add_argument("-u", "--upper", dest="upper", default=False,
		action="store_true", help="index using uppercase letters,\n"
		"does not apply to numeric [default: %(default)s]")
	alphagroup.add_argument("-p", "--pascal", dest="pascal", default=False,
		action="store_true", help="index using pascal case,\n"
		"only applies to language styles [default: %(default)s]")
	
	parser.add_argument("--version", action="version",
		version="{0} - Version {1}".format(__prog__, __version__),
		help="display the version")

	return parser.parse_args()
	
def cleanPaths(directory, match):
	filePaths = []
	if os.path.isdir(directory):
		for pathname in glob.glob(os.path.join(directory, match)):
			if os.path.isfile(pathname):
				filePaths.append(pathname)
		filePaths.sort()
	else:
		sys.stderr.write("Error: %s is not a directory\n" % directory)
		sys.exit()
		
	return filePaths

def getNextIndex(args, i, length=1):
	index = ""
	if args.style == "numeric":
		if args.zero == False:
			i += 1
		index = ("{0:0" + str(length) + "d}").format(i)
	
	elif args.style == "alpha":
		index = getAlphaFromNum(i, length)
		
		if args.upper == True:
			index = index.upper()
		
	elif args.style == "greek":
		graphemes = ["alpha", "beta", "gamma", "delta", "epsilon",
			"zeta", "eta", "theta", "iota", "kappa",
			"lambda", "mu", "nu", "xi", "omicron",
			"pi", "rho", "sigma", "tau", "upsilon",
			"phi", "chi", "psi", "omega"]
		
		if args.upper == True:
			index = graphemes[i].upper()
		elif args.pascal == True:
			index = graphemes[i][0].upper() + graphemes[i][1:]
		else:
			index = graphemes[i]
			
	elif args.style == "hebrew":
		graphemes = ["alef", "bet", "gimel", "dalet", "he",
			"vav", "zayin", "het", "tet", "yod",
			"kaf", "lamed", "mem", "nun", "samekh",
			"ayin", "pe", "tsadi", "qof", "resh",
			"shin", "tav"]
		
		if args.upper == True:
			index = graphemes[i].upper()
		elif args.pascal == True:
			index = graphemes[i][0].upper() + graphemes[i][1:]
		else:
			index = graphemes[i]
			
	return index

def getNewname(oldname, index, args):
	base, ext = os.path.splitext(os.path.basename(oldname))
	newname = args.pattern
	
	if "{index}" in args.pattern:
		newname = string.replace(newname, "{index}", index)
	else:
		sys.stderr.write("Error: %s is not a valid pattern - {index} must be specified\n" % args.pattern)
		sys.exit()
	
	if "{base}" in args.pattern:
		newname = string.replace(newname, "{base}", base)
		
	if re.search(r"{regex:.*:}", args.pattern) != None:
		for regex in re.findall(r"{regex:([^E]+):}", newname):
			extraction = re.search(regex, base)
			if extraction != None:
				newname = string.replace(newname, "{regex:" + regex + ":}", extraction.group())
	
	if "{date}" in args.pattern:
		newname = string.replace(newname, "{date}", datetime.datetime.now().strftime("%Y-%m-%d"))
	
	if re.search(r"{date:.*:}", args.pattern) != None:
		for dateformat in re.findall(r"{date:([^E]+):}", newname):
			newname = string.replace(newname, "{date:" + dateformat + ":}", datetime.datetime.now().strftime(dateformat))
	
	if args.override == False:
		newname += ext
	
	return newname

def renameFile(oldname, newname):
	sys.stdout.write("Renaming {0} to {1} ... ".format(os.path.basename(oldname), newname))
	newname = os.path.join(os.path.dirname(oldname), newname)
	
	if os.path.exists(newname):
		sys.stdout.write("Error: file already exists\n")
	else:
		os.rename(oldname, newname)
		sys.stdout.write("Done\n")

def getAlphaFromNum(num, digits):
	# There has to be a better way to do this, needs reimplementation
	index = ""
	while num >= 26:
		index = string.ascii_lowercase[num % 26] + index
		num = num / 26
	
	if num < 26:
		index = string.ascii_lowercase[num] + index
	
	while len(index) != digits:
		index = string.ascii_lowercase[0] + index
	
	return index
	
if __name__ == "__main__":
	main()

```

---

### Post by Vaphell on 2011-02-02
support for exif data from .jpg

edit: btw
```
def getAlphaFromNum(num, digits):
    index = ""
    i = digits - 1
    while i >= 0:
        index += string.ascii_lowercase[num / (26**i)]
        num %= (26**i)
        i -= 1
  return index

```

---

### Post by AtomicClock on 2011-02-02
Thanks for replying.

Do you mean like a search of the EXIF data? As in, only renaming the files that match certain constraints?

Also, unfortunately that code won't work for this function. The way that it's set up now is that it basically a base-26 numbering system for the index, using the alphabet. One of my goals was that the renamed files would be in the same order that they were previously. Thus, depending on the total number of files, there would be different numbers of "digits" in the index, but all files would have the same number of digits, e.g. "aa", "ab", "ba", "bb", and so on. But there would be no single "a" or "b" in this particular case, since each index has two "digits".

I hope that seems logical.

---

### Post by Vaphell on 2011-02-03
if you look at my snippet closely, you'll see that i use the very concept of base-26 numbering system and the output is identical (though i made a mistake assuming brainlessly that (num>0) is a logical equivalent of (i>=0), which buggered the output in some cases - fixed it in the code above)
```
for i in range(1000,30000, 2077):
    print i, getAlphaFromNum( i, 4 ), getAFN(i, 4 )
```
getAFN is my version, getAlphaFromNum is yours.
output is identical:
```
1000 abmm abmm
3077 aeoj aeoj
5154 ahqg ahqg
7231 aksd aksd
9308 anua anua
11385 aqvx aqvx
13462 atxu atxu
15539 awzr awzr
17616 babo babo
19693 bddl bddl
21770 bgfi bgfi
23847 bjhf bjhf
25924 bmjc bmjc
28001 bpkz bpkz
```

exif stores a bunch of data, eg date the photo was taken. Renaming in chronological order would be nice, one can come up with some other exif-based criteria.
Also maybe allow using some exif tags as a part of the new filename?

---

### Post by AtomicClock on 2011-02-03
Oh, great! I should have looked more carefully the first time. Indeed, that function gives the exact same results. Thanks!

I tried seeing if there was an easy way to access the EXIF data from python, and it seems the [Python Imaging Library]("http://www.pythonware.com/products/pil/") is the closest thing. I'll try reading up a bit more on it soon.

---

