---
title: "sipie errors"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by m_ad on 2008-05-16
I've searched all over the forums, and I can't find a solution to this specific problem I'm having..


after executing /usr/bin/sipie.py, I'm prompted to enter the text show in the captcha file img_***.jpg once, I enter it.

for some reason, I get prompted AGAIN to enter the text shown in the captcha file, but a different file with different text. after I enter it, I get a long error message:

```
Traceback (most recent call last):
  File "/usr/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1196144357', 'sipie.py')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie.py", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 377, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 308, in tryGetStreams
Sipie.Factory.AuthError

```

any guidance would be appreciated :confused:

---

### Post by m_ad on 2008-05-16
bump..

---

### Post by squid68 on 2008-05-19
Search the forum for Sirius Internet Radio Online. There is a post started by Barton.Jones that has answers to almost all the Sirius ways to listen and with bugs and fixes for Sipie.

---

