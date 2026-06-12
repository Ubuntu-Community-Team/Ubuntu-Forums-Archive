---
title: "Start python console with a command"
date: 2010-03-13
forum: Programming Talk
---

### Post by carlosgs91 on 2010-03-13
.

---

### Post by jfparis on 2010-03-13
try this

```

#!/bin/sh

python -c "from sympy import *"

```

it might also work with 

```

#!/bin/sh

python -m sympy

```

---

### Post by carlosgs91 on 2010-03-13
.

---

### Post by ronocdh on 2010-03-13
> **carlosgs91 said:**
> I want to create a bash file that does the same, so I can do the three steps by running the file.I believe what you want to do is research adding something to your path. That way you could make a custom script to perform those three steps (should be a Bash script, as you've been doing), and then link that Bash script to /usr/bin/ or wherever you please.

The advantage of a link is that you could edit the script in, say, your home directory, and then the link would magically point to the newly edited version of the file.

Anything in your PATH can be run from a terminal by just typing the associated command, e.g. sympy if sympy is in your PATH.

---

### Post by tomchuk on 2010-03-13
You can also accomplish this by setting the PYTHONSTARTUP variable in your ~/.bashrc (or other file sourced from your shell)

in ~/.bashrc:
```

export PYTHONSTARTUP=~/.pythonrc


```

in ~/.pythonrc:
```

try:
  import sys
  sys.path.append('/var/mobile/Media')
  from sympy import *
except:
  print 'sympy not imported'

```

Everything from sympy will be imported in every python shell you run. The sys.path.append bit could also be accomplished by setting PYTHONPATH in your ~/.bashrc.

Here's my .pythonrc, that if run from a django project will setup the django environment and import all models.
```

try:
    from django.core.management import setup_environ
    import settings
    setup_environ(settings)
    print 'imported django settings'
    try:
        exec_strs = ["from %s.models import *"%apps for apps in settings.INSTALLED_APPS ]
        for x in exec_strs:
            try:
                exec(x)
            except:
                print 'Not imported for %s' %x
        print 'imported django models'
    except:
        pass
except:
    pass

```

---

