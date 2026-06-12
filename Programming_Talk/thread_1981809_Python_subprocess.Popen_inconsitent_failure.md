---
title: "Python subprocess.Popen inconsitent failure"
date: 2012-05-17
forum: Programming Talk
---

### Post by ricomoss on 2012-05-17
I'm completely baffled and don't really know where to start.

I have two scripts that manage Git repositories.  One script is used by several developers to help with cloning, check-ins and see who's actively developing on their local branch (via a database).

The second script is used by myself to handle automated unit testing, and deployment of our software on a server.

I'm currently testing a functionality that will do automated unit tests.  If a module is "missing" from the collection it will automatically clone the Git repository before starting the tests.

The cloning mechanism in the first script works fine.  The second script fails.  Relevant portions of the code can be seen below.

Script 1:
```

    def handleClone(self):
        # Clone the project
        self.command = "git clone git@our_server:~/" + self.project_name
        result = self.handleCommand()
        
    def handleCommand(self):
        process = subprocess.Popen(self.command, shell = True, stderr = subprocess.PIPE, stdout = subprocess.PIPE)


```

Script 2:
```

    def clone(self, module):
        self.command = "git clone git@our_server:~/" + module
        process = subprocess.Popen(self.command, shell = True, stderr = subprocess.PIPE, stdout = subprocess.PIPE)


```

If I do a simple print statement of the command for each I get the following:

Script 1:
```
git clone git@our_server:~/project_name
```

Script 2:
```
git clone git@our_server:~/project_name
```

Yes, they are *exactly* the same.

Running script 1 is successful.  Running script 2 gives the following error message:

```

ssh_exchange_identification: Connection closed by remote host
fatal: The remote end hung up unexpectedly

```

I've run this command manually and verified it works.

In case it's relevant I'll include the imports I'm using.

Script 1:
```

import sys
import subprocess
import psycopg2
import os
import re

```

Script 2:
```

import subprocess
import paramiko
import sys
import os

```

Does anyone have any ideas what could be going on here?  Please let me know if you need me to provide more info.

---

### Post by ricomoss on 2012-05-17
I figured out what the problem is but I have no idea how to fix it.

The problem has something to do with using Paramiko to open an SSH connection.

Script 2:
```

    def clone(self, module):
        #  ... does stuff...

        self.command = "git clone git@our_server:~/" + module
        process = subprocess.Popen(self.command, shell = True, stderr = subprocess.PIPE, stdout = subprocess.PIPE)

        #  ... does more stuff...

    def handleCreate(self):
        #  ... does stuff...

        # Create a bare repository on the server
        self.command = "mkdir " + self.project_name + ";cd " + self.project_name + ";git --bare init"
        ssh = paramiko.SSHClient()
        ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
        ssh.connect('our_server', username = 'git')
        ssh.exec_command(self.command)
        ssh.close()

        #  ... does more stuff...


```

Note that these methods are mutually exclusive.  That is, this management class does not have functionality to call both these methods during a single process.

The code that used Paramiko to create the SSH connection never actually gets run when I use the script to do cloning.

Any ideas?

---

