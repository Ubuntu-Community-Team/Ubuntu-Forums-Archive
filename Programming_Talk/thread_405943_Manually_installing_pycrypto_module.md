---
title: "Manually installing pycrypto module"
date: 2007-04-10
forum: Programming Talk
---

### Post by zmjrahl on 2007-04-10
I'm pretty new to working in Linux. I installed Ubuntu server 6.06 on a spare laptop I had laying around and have been using it for a project recently. Today I'm trying to install pycrypto manually. I downloaded the tgz, extracted it, etc, but when I run the setup with 'python setup.py install' or 'python setup.py build' I'm getting a huge amount of errors:

```
src/hash_template.c: At top level:
src/hash_template.c:95: error: syntax error before â*â token
src/hash_template.c:96: error: syntax error before â*â token
src/hash_template.c:97: warning: return type defaults to âintâ
src/hash_template.c:97: warning: function declaration isnât a prototype
src/hash_template.c: In function âALG_hexdigestâ:
src/hash_template.c:98: error: âPyObjectâ undeclared (first use in this function)
src/hash_template.c:98: error: âvalueâ undeclared (first use in this function)
src/hash_template.c:98: error: âretvalâ undeclared (first use in this function)
src/hash_template.c:98: warning: left-hand operand of comma expression has no effect
src/hash_template.c:98: warning: statement with no effect
src/hash_template.c:102: error: âargsâ undeclared (first use in this function)
src/hash_template.c:103: error: âNULLâ undeclared (first use in this function)
src/hash_template.c:106: error: syntax error before â)â token

```

Pages and pages of that sort of thing. I figured the file must have been corrupted somehow, but it looks fine.
```
     95 static PyObject *
     96 ALG_hexdigest(ALGobject *self, PyObject *args)
     97 {
     98         PyObject *value, *retval;
     99         unsigned char *raw_digest, *hex_digest;
    100         int i, j, size;
    101
    102         if (!PyArg_ParseTuple(args, ""))
    103                 return NULL;
    104
    105         /* Get the raw (binary) digest value */
    106         value = (PyObject *)hash_digest(&(self->st));
    107         size = PyString_Size(value);
    108         raw_digest = PyString_AsString(value);

```

So what's going on here?

---

### Post by ssavelan on 2009-02-27
I have something similar when I use the easy_install script...

---

### Post by ssavelan on 2009-02-27
Well, I know this is an old, dead thread but I needed to install python2.5-dev it turned out for me :)

---

