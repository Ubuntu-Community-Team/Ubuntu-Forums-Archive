---
title: "Useful script to search (not-)installed packages"
date: 2008-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by MonkeeSage on 2008-04-26
You can show / search a list of installed packages a number of different ways. For example, to search installed packages for FOO, you could do:

```

dpkg --get-selections | awk '/\tinstall/ {print $1}' | grep FOO

```


This works just fine, but it doesn't have any pretty formatting, and it only shows the package names (you can do more complicated things with grep / sed / awk, but that's a bit beyond the scope of normal users).

The following is a python script that tries to make searching for a certain package a bit nicer. You can search only in installed packages (default), or you can search all packages with the -v switch.

Example:

# apt-checkinstalled rdoc

```
[font=mono][b][color=green]*[/color] [color=blue]rdoc1.8[/color]
  [color=grey]version:[/color][/b] 1.8.6.111-2ubuntu1
  **[color=grey]summary:[/color]** Generate documentation from Ruby source files (for Ruby 1.8)[/font]
```


# apt-checkinstalled -v rdoc

```
[font=mono]**[color=green]*[/color] [color=blue]rdoc[/color] ([color=yellow]not installed[/color])**

[b][color=green]*[/color] [color=blue]rdoc1.8[/color]
  [color=grey]version:[/color][/b] 1.8.6.111-2ubuntu1
  **[color=grey]summary:[/color]** Generate documentation from Ruby source files (for Ruby 1.8)

**[color=green]*[/color] [color=blue]rdoc1.9[/color] ([color=yellow]not installed[/color])**[/font]

```


This is the python code:

```

#!/usr/bin/python

import warnings
warnings.filterwarnings('ignore', 'apt API not stable yet', FutureWarning)
import os, sys, apt

bash_colors = {
	'gray'   : '\033[1;30;40m%s\033[0m',
	'blue'   : '\033[1;34;40m%s\033[0m',
	'green'  : '\033[1;32;40m%s\033[0m',
	'yellow' : '\033[1;33;40m%s\033[0m'
}

def colorize(color, str):
	return bash_colors[color] % str

script = sys.argv.pop(0)
def show_help():
	sys.exit('Usage: %s [-v] pkg1 pkg2 ...' % os.path.basename(script))

verbose = False

if not sys.argv or sys.argv[0] in ('-h', '--help', '-help'):
	show_help()
else:
	if sys.argv[0] == '-v':
		verbose = True
		del sys.argv[0]
	cache = apt.Cache()
	pkgs = {}
	for pkg in sys.argv:
		pkgs[pkg] = 1
		for item in cache.keys():
			if pkg in item:
				pkgs[item] = 1
	pkgs = pkgs.keys()
	pkgs.sort()
	for pkg in pkgs:
		try:
			cand = cache[pkg]
			if cand.isInstalled:
				print
				print ' %s %s' % (colorize('green', '*'), colorize('blue', cand.name))
				print '   %s %s' % (colorize('gray', 'version:'), cand.installedVersion)
				print '   %s %s' % (colorize('gray', 'summary:'), cand.summary)
			else:
				if verbose:
					print
					print ' %s %s (%s)' % (colorize('green', '*'), colorize('blue', cand.name),
					                       colorize('yellow', 'not installed'))
		except KeyError:
			if verbose:
				print
				print ' %s %s (%s)' % (colorize('green', '*'), colorize('blue', pkg),
				                       colorize('yellow', 'not in cache'))
print

```


Happy hacking. :)

---

### Post by petteriIII on 2008-04-26
Thanks, operates fine.

---

### Post by swegner on 2008-04-26
If you simply need a list of installed packages, you can the built-in search functions of aptitude.  For example, if you want all installed packages:

```
aptitude search ~i
```

I like to search for installed, but not include packages that were automatically installed.  This gets a little hairy with the search logic and escaping it for the terminal, but the command is:

```
aptitude search \!\(\!~i\|~M\)
```

You can also customize the formatting using the -F switch.  To get just the packages names, use -F %p.  For example, to save a simple list of installed (but not automatically installed) packages to a text file, I use the command:

```
aptitude search \!\(\!~i\|~M\) -F %p > ~/packages.txt
```

--Scott

---

### Post by MonkeeSage on 2008-05-16
> **swegner said:**
> If you simply need a list of installed packages, you can the built-in search functions of aptitude.  For example, if you want all installed packages:

```
aptitude search ~i
```

If you just want to list all installed packages, the command I posted is much faster (i.e., "dpkg --get-selections | awk '/\tinstall/ {print $1}" beats "aptitude search ~i").

If you want to do something more complex, then using the aptitude commandline api is a good solution. The main purpose of the script I posted is to make searching for (not-)installed packages quicker and easier. As an added bonus, you get nice colors in the output.

---

### Post by Snabbdist on 2011-03-02
```
dpkg -l | grep linux-
```

works best because it's short and simplest afaik.

---

