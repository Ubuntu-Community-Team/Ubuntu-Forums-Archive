---
title: "Couple of Python questions"
date: 2012-04-02
forum: Programming Talk
---

### Post by Dubslow on 2012-04-02
Hey guys.

I'm a new Python (3.2.2) coder, and I have some questions.

Here are the first two.

1) How exactly do breaks and continues interact with try/except statements and a containing while loop?
```
from urllib import request, error

while True:
    try:
        contents = request.urlopen(url).read().decode('utf-8').splitlines()
    except HTTPError as e:
        log.warning('Couldn\'t contact FactorDB. Error code:\n' + \
                    str(e.code))
        log.warning('Sleeping for '+str(retry_time)+' minutes and trying\
                    again.')
        sleep(retry_time*60)
        continue
    else:
        if False in [line.isdigit() for line in contents]
        # The 'contents' from the url should be a newline-separated list of numbers, so splitlines() and examine each member string for isdigit
            log.warning('...no composites fetched; script will sleep for 30 \
                       seconds and try again.')
            log.warning('Here\'s what FactorDB returned:')
            log.warning(contents)
            sleep(30)
            continue
            # Restart from beginning of loop
        else:
            break
            # Break the while loop, continue with rest of script
```
Shortly, I want to open the URL, and retry (go around the while loop) if either 'urlopen' throws an exception or the response isn't what I'm looking for. The problem is, [here](http://docs.python.org/py3k/tutorial/errors.html) it says > The finally clause is also executed &#8220;on the way out&#8221; when any other clause of the try statement is left via a break, continue or return statement. So now I'm not sure if the breaks/continues are passed to the while loop, and if not, how to fix it.

Edit: Googled "goto python", which ironically lead me to a three year old thread here which suggested a while loop as a workaround. *headdesk*
Fortunately, the next suggestion was controlling the loop with an exit-condition variable instead of while True. However, while I can now complete the code, it's still a good thing to know the answer to the original question, so anybody have any ideas?

2) I'm not sure how to get real time stdout from a subprocess. Out there on the wide open web, I've seen a variety of proposed things to do, but none of them have seemed to really guarantee that I can read the output from my script right when the subp prints it.

For example, [this](http://www.doughellmann.com/PyMOTW/subprocess/) makes me think that stdout=subprocess.PIPE and communicate() or maybe check_output() might accomplish what I'm looking for, however I'm not sure. (If I use Popen and PIPE, then at least one example has proc.stdout.readline(), however I still don't know if this statement will be executed whenever a new line is printed to stdout by proc.

Someone suggested [this](http://sourceforge.net/projects/pexpect/?_test=b); are you guys familiar with it? (I would preferably like to avoid installing extra modules, because this script will eventually be used by others.)

If it helps, I'm 99% sure that the following Perl does what I'm looking for (however I don't really know Perl):
```
open(PROG, "prog args") or die "Couldn't start prog!";
		while (<PROG>) {
				print "$_";
```Any and all output is directed to $_ , which can then be printed or processed in some other way by the calling script. That's what I'm looking for.

3)
Edit2: I thought of another minor problem I've been having. [http://docs.python.org/py3k/tutorial/modules.html#the-module-search-path](http://docs.python.org/py3k/tutorial/modules.html#the-module-search-path)
> When a module named spam is imported, the interpreter first searches for a built-in module with that name. If not found, it then searches for a file named spam.py in a list of directories given by the variable sys.path. sys.path is initialized from these locations:

the directory containing the input script (or the current directory).
PYTHONPATH (a list of directory names, with the same syntax as the shell variable PATH).
the installation-dependent default.
I have not been able to get this feature to work.
```
bill@Gravemind:~&#8752;&#8706; echo $PYTHONPATH
/home/bill/bin/py
bill@Gravemind:~&#8752;&#8706; python
Python 3.2 (r32:88445, Dec  8 2011, 15:26:58) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.path
['', '/usr/lib/python3.2', '/usr/lib/python3.2/plat-linux2', '/usr/lib/python3.2/lib-dynload', '/usr/local/lib/python3.2/dist-packages', '/usr/lib/python3/dist-packages']
>>> 
```

---

### Post by wmcbrine on 2012-04-02
> **Dubslow said:**
> How exactly do breaks and continues interact with try/except statements and a containing while loop?

Let's find out.

```

a = 1
while True:
    a += 1
    try:
        raise
    except:
        break
    finally:
        print (a)

```

1. Prints "2".
2. Exits the loop.

---

