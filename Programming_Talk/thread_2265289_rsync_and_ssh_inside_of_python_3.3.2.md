---
title: "rsync and ssh inside of python 3.3.2"
date: 2015-02-14
forum: Programming Talk
---

### Post by lance bermudez on 2015-02-14
import os
os.system('''rsync -vaPhz /home/lance/bin/ -e \"ssh -p 9455\" 192.186.12.21:/home/lance/bin/''')

or
from subprocess import Popen, PIPE, STDOUT
shell_command = '''rsync -vaPhz /home/lance/bin/ -e \"ssh -p 9455\" 192.168.2.2:/home/lance/bin/'''
event = Popen(shell_command, shell=True, stdin=PIPE, stdout=PIPE, stderr=STDOUT)
output = event.communicate()
print (output)

both work but do not show files.

It works but is their a way to show the files as they are being copied over? I'm new to python and just learned this tonight.

---

### Post by lance bermudez on 2015-03-04
will let you see the output from rsync as the files are copied

import subprocess
subprocess.call(['rsync','-vaPhz','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/bin'])

---

