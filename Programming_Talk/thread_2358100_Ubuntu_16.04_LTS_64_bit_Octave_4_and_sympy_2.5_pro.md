---
title: "Ubuntu 16.04 LTS 64 bit: Octave 4 and sympy 2.5 problem"
date: 2017-04-09
forum: Programming Talk
---

### Post by erotavlas on 2017-04-09
Hi,
I have a problem under ubuntu 16.04 64 bit lts, kernel 4.8.46, octave 4.0.0 and OctSymPy 2.5.0.
I have simple Octave code that requires sympy library of python.
I installed sympy via
```

sudo apt-get install python-pip
pip install --user sympy 
pkg install -forge symbolic

```
and also
```

sudo apt-get install python-sympy

```
The result is the following. The same Octave code works under different OS.
```

Traceback (most recent call last):   File "<string>", line 1, in <module>
ImportError: No module named sympy
OctSymPy v2.5.0: this is free software without warranty, see source.
Initializing communication with SymPy using a popen2() pipe.
error: Python cannot import SymPy: have you installed SymPy?
error: called from
    assert_have_python_and_sympy at line 37 column 5
    python_ipc_popen2 at line 78 column 5
    python_ipc_driver at line 58 column 13
    python_cmd at line 164 column 9
    valid_sym_assumptions at line 38 column 10
    assumptions at line 82 column 7
    syms at line 97 column 13
```
I'm using python 3.x and miniconda
```

pip install sympy
Requirement already satisfied: sympy in ./miniconda3/lib/python3.5/site-packages
Requirement already satisfied: mpmath>=0.19 in ./miniconda3/lib/python3.5/site-packages (from sympy)

```

Thank you

---

### Post by Rocket2DMn on 2017-04-10
Since you're using Python3, I suspect you need to install python3-sympy rather than python-sympy.

---

### Post by erotavlas on 2017-04-10
> **Rocket2DMn said:**
> Since you're using Python3, I suspect you need to install python3-sympy rather than python-sympy.

Thank, it does not work.

---

### Post by hughes1608 on 2017-04-24
I have the same issue.
i installed the python sympy library just as noted above.
Then did
  setenv PYTHON c:\Python27\python.exe
But I still get the same error...

OctSymPy v2.5.0: this is free software without warranty, see source.
Initializing communication with SymPy using a popen2() pipe.
error: Python cannot import SymPy: have you installed SymPy?

Any insights are greatly appreciated!

---

### Post by erotavlas on 2017-04-25
> **hughes1608 said:**
> I have the same issue.
i installed the python sympy library just as noted above.
Then did
  setenv PYTHON c:\Python27\python.exe
But I still get the same error...

OctSymPy v2.5.0: this is free software without warranty, see source.
Initializing communication with SymPy using a popen2() pipe.
error: Python cannot import SymPy: have you installed SymPy?

Any insights are greatly appreciated!

Which OS are you using? If you are on windows, I can confirm that it works well by using: octave 4.2.1, python 3.6.0 and symPy 2.5.0.
So you have to install python library via powershell and I suggest you to install the following libraries:
   ```


pip install --user numpy scipy matplotlib ipython jupyter pandas sympy nose

```

---

