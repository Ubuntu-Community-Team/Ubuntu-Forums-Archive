---
title: "Problems with NTLM Authorization Proxy Server"
date: 2008-11-10
forum: Programming Talk
---

### Post by Titan8990 on 2008-11-10
I downloaded APS from here: [http://ntlmaps.sourceforge.net/](http://ntlmaps.sourceforge.net/)

The instructions are simple but do not seem to work for me. I think that it might have to do with the fact that I have python 2.0+ and it is written in python 1.5.2.

It seems that I don't have the needed modules and it doesn't explain what modules are needed or how to get them.

Anyways here is what I get:

```
Traceback (most recent call last):
  File "main.py", line 26, in <module>
    import server, logger
  File "lib/server.py", line 21, in <module>
    import proxy_client, www_client
  File "lib/proxy_client.py", line 22, in <module>
    import ntlm_auth, basic_auth
  File "lib/ntlm_auth.py", line 21, in <module>
    import ntlm_messages, utils, ntlm_procs
  File "lib/ntlm_messages.py", line 20, in <module>
    import ntlm_procs, utils
  File "lib/ntlm_procs.py", line 21, in <module>
    import des, md4, utils
  File "lib/des.py", line 20, in <module>
    import des_c, utils
  File "lib/des_c.py", line 22
SyntaxError: Non-ASCII character '\xd7' in file lib/des_c.py on line 22, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```

To verify that I don't have the needed modules:

```
root@bourne:~/tools/aps098# python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import server
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named server
>>> import logger
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named logger
```


How do I go about attaining these modules? Does anyone know of any other stand-alone proxies that will handle NTLM authentication?

Thanks in advance for any help.

---

