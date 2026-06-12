---
title: "Python3.6.6 virtualenv error"
date: 2018-09-05
forum: Programming Talk
---

### Post by lance bermudez on 2018-09-05
I'm getting this error 
```

lance@Lubuntu1804:~/Python-3.6.6$ bin/python3.6 -m pip list
Package    Version
---------- -------
pip        18.0   
setuptools 40.2.0 
virtualenv 16.0.0 
wheel      0.31.1 
lance@Lubuntu1804:~/Python-3.6.6$ bin/python3.6 -m virtualenv -p ~/Python-3.6.6/bin/python3.6 /home/lance/python366/.env
Already using interpreter /home/lance/Python-3.6.6/bin/python3.6
Using base prefix '/home/lance/Python-3.6.6'
New python executable in /home/lance/python365/.env/bin/python3.6
Also creating executable in /home/lance/python365/.env/bin/python
Installing setuptools, pip, wheel.../home/lance/Python-3.6.6/lib/python3.6/site-packages/virtualenv.py:904: ResourceWarning: unclosed file <_io.BufferedReader name=5>
  call_subprocess(cmd, show_stdout=False, extra_env=env, stdin=SCRIPT)
done.

```

Source code came from python.org
```

./configure --enable-shared --prefix=$HOME/Python-3.6.6 --with-system-ffi --with-system-expat --with-pydebug LDFLAGS="-Wl,--rpath=$HOME/Python-3.6.6/lib" CPPFLAGS="-I$HOME/Python-3.6.6/include"; make -j 4; make test; make altinstall

```

---

