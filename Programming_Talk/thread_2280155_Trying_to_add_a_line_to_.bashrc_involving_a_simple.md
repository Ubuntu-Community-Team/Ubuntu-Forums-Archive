---
title: "Trying to add a line to .bashrc involving a simple Python command but getting errors"
date: 2015-05-28
forum: Programming Talk
---

### Post by wizrddreams on 2015-05-28
I am setting up my system for ease of use with Python. (Hopefully)
I am add the following lines to the .bashrc file:
```

pyversion='python -c 'import sys; print sys.version.split()[0]''
export PYTHONSRC=$SYSDIR/src/python/Python-$pyversion

```
Running that command in terminal:
```
python -c 'import sys; print sys.version.split()[0]'
```
Yields:```
2.7.10
```
So pyversion should be 2.7.10

However I get the following errors from the .bashrc when I start up a new terminal:
```
bash: /home/kblawlor/.bashrc: line 128: syntax error near unexpected token `('
bash: /home/kblawlor/.bashrc: line 128: `pyversion='python -c 'import sys; print sys.version.split()[0]'''
```

I am wrapping the whole line of working code in these quotations ''

Does anyone know how to get this to work?
For some reason the .bashrc line of code is not communicating itself to the terminal properly. (So it seems)
I think it may be the way I am using quotations.

---

### Post by steeldriver on 2015-05-28
You need to assign the *result* of the command using command substitution $( ... )

```

pyversion="$(python -c 'import sys; print sys.version.split()[0]')"

```

NOTE: there is an older equivalent syntax using backticks ` ... ` but those are NOT the same as single quotes ' ... '

---

### Post by sisco311 on 2015-05-28
**Thread moved to Programming Talk!**


Here are some links regarding command substitution and quoting in BASH:
[http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution)
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)


I don't know much about programming in Pyhton, but your python command throws an error for me in Python 3.4.3...

---

### Post by wizrddreams on 2015-05-28
Hi sisco.  I am using Python 2.7.10. (For future people who may use this thread). 
Just to confirm `` around the command worked for me. 
Thanks for the references, bookmarking the page for future use.
Cheers.

---

### Post by steeldriver on 2015-05-28
... it might be more portable to use

```

python --version

```
or
```

python -V

```

which seems to work for both python2.x and python3 - however, just to be ornery it appears that python2.x writes the result to stderr while python3 writes it to stdout, so you'd need to do something like

```

pyversion="$(python --version 2>&1 | cut -d' ' -f2)"

```
or
```

pyversion="$(python --version 2>&1 | awk '{print $2}')"

```

to cover both bases.

---

