---
title: "ssh through python, help with subprocess module"
date: 2011-07-08
forum: Programming Talk
---

### Post by pi3guy on 2011-07-08
Hello everyone,

Newbie programmer here. I want to use paramiko in a python script to login through a ssh and execute an application on a server; basically automate some bash commands with python.

I couldn't get paramiko to run on my machine so I am trying to achieve these task with the subprocess module.

When I write something like:
subprocess.Popen(['ssh', 'username@server'], shell=False)

how do I continue writing code so that my shell commands are directed at the server?
example:
if I write
subprocess.Popen(['cd', 'directory1'], shell=False)

I want to navigate to directory1 on the server, not the computer I'm currently typing on.

Thanks

alan

---

### Post by Bachstelze on 2011-07-08
You Can't Do That&#8482;

There is no need for Python, just create a shell script on the server with your commands and run it with

```
ssh server /path/to/script.sh
```

---

### Post by pafoo on 2011-07-08
Heres what I built recently

```

 server = sys.argv[1]


####### Building the command line with an argument for the server to build a list
  part1 = "ssh -q -i /home/user/.ssh/id_rsa otheruser@"
  part2 = server
  part3 = ' ls /logs/*-r-fxm-00[1-4]-*`date --date="yesterday" + \%m\%d`*.log.gz | sed s/\\\/logs\\\///'  
parts = part1 + part2 + part3
   
  ### Small piece to verify we can ssh to the server, if not exit and send a email ssh_test = part1 + part2 + ' "echo"'
  aha = os.system(ssh_test)
  if aha != 0:
    message.write("Unable to SSH, please look for expired password/keys etc to ")
    message.write(server)
    message.close()
    messages = open("/tmp/errors", "r")
    message = messages.read()
    messages.close()
    sendMail(body=message)


[FONT=&quot]####### Define function to gather the list that is going to be SCP'd 
[/FONT]
  
[FONT=&quot]def[/FONT] gather_list():
    list = os.popen(parts).read()
    list = list.split()
    return list
   
  ### Making the function a variable so we do not keep calling the ssh command 

base_list = gather_list()
    
```Look at it carefully that will help. I use os.system to return a 0 success or anyother number a failure, otherwise I use os.popen

You can also set os.popen to a function to run multiple commands, but generally speaking you should never "really" need to cd in a script, because you can do anything you want just use absolute path's.

---

### Post by pafoo on 2011-07-09
@[Bachstelze]("http://ubuntuforums.org/member.php?u=51114")

Your idea works great, but if you are managing 100+ servers, the effort it takes to constantly scp scripts then if you need to edit them later... then if you need to cremove them up... because VERY time consuming and annoying.

---

### Post by Russss on 2011-07-09
> **pi3guy said:**
> Hello everyone,

Newbie programmer here. I want to use paramiko in a python script to login through a ssh and execute an application on a server; basically automate some bash commands with python.

I couldn't get paramiko to run on my machine so I am trying to achieve these task with the subprocess module.


What errors are you getting from paramiko?

---

### Post by pi3guy on 2011-07-12
thanks for the help guys

@pafoo: I am just starting to learn bash scripting and am having trouble following your code. What is the variable part3 doing? Does your script just login to the server or does it perform a task there as well? 
That is the main point I'm confused about. How do I say, open a file or run a program when I'm logged on to the server?

@russss: I couldn't get py-crypto to install, which is a prerequisite for paramiko. I'm running 9.04 x64 and python 2.6.6
Neither paramiko nor py-crypto are found in synaptic so I downloaded source files online for paramiko 1.7.7.1 and py-crypto 2.0.1. If you could point me to a site for py-crypto that would be great.

---

### Post by Russss on 2011-07-12
> **pi3guy said:**
> thanks for the help guys

@russss: I couldn't get py-crypto to install, which is a prerequisite for paramiko. I'm running 9.04 x64 and python 2.6.6
Neither paramiko nor py-crypto are found in synaptic so I downloaded source files online for paramiko 1.7.7.1 and py-crypto 2.0.1. If you could point me to a site for py-crypto that would be great.

I'm using Arch Linux so I'm not sure if you can find a deb somewhere, but if you install pip, [http://www.pip-installer.org/en/latest/installing.html#using-the-installer](http://www.pip-installer.org/en/latest/installing.html#using-the-installer) , you can install packages from the Python Package Index, [http://pypi.python.org/pypi](http://pypi.python.org/pypi), using ```
pip install package
```

Both paramiko, [http://pypi.python.org/pypi/paramiko/1.7.7.1](http://pypi.python.org/pypi/paramiko/1.7.7.1) , and pycrypto, [http://pypi.python.org/pypi/pycrypto/2.3](http://pypi.python.org/pypi/pycrypto/2.3) , are on there. 

Also if you are using paramiko I will go ahead and point you to paraproxy, [http://pypi.python.org/pypi/paraproxy/1.2](http://pypi.python.org/pypi/paraproxy/1.2) , in case you ever need it. paraproxy hooks into paramiko to allow the use of an ~/.ssh/config file. All you have to do to hook in is import paraproxy when you import paramiko. ssh/config lets you do some useful stuff such as give 'alias' to ssh connections and also lets you hop through proxies to get to remote machines that generally require you to go through a middle machine to get to.

I am also learning python and am using paramiko to connect to remote clusters for school research and have my code I am working on here: [http://bazaar.launchpad.net/~stilesr28/fiber/trunk/files](http://bazaar.launchpad.net/~stilesr28/fiber/trunk/files)
There I have my connection class to make paramiko easier and an example of my ssh/config, I am still working on this as I speak but if you want to use it go ahead, and if you see something wrong or that could be better feel free to tell me.

Finally here are some links that could be useful:
explanation on some ssh/config
[http://sshmenu.sourceforge.net/articles/transparent-mulithop.html](http://sshmenu.sourceforge.net/articles/transparent-mulithop.html)

Examples of paramiko: 
[http://jessenoller.com/2009/02/05/ssh-programming-with-paramiko-completely-different/](http://jessenoller.com/2009/02/05/ssh-programming-with-paramiko-completely-different/)

[http://www.saltycrane.com/blog/2010/02/python-paramiko-notes/](http://www.saltycrane.com/blog/2010/02/python-paramiko-notes/)

---

### Post by pi3guy on 2011-07-18
**EDIT:** Think I have solved my problem. I had an older version of pycrypto in /usr/lib/python2.6/dist-packages without Random. Deleting that directory has allowed me to import paramiko. disregard subsequent post




I tried to install paramiko after upgrading to 10.04 lts
I've installed pip and pycrypto 2.3 successfully (I can import Crypto)
My comp said I successfully installed paramiko 1.7.7.1 after
 sudo pip install paramiko

However, when I'm in python 2.6.5 and I try to import paramiko, I get this error:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python2.6/dist-packages/paramiko/__init__.py", line 69, in <module>
    from transport import SecurityOptions, Transport
  File "/usr/local/lib/python2.6/dist-packages/paramiko/transport.py", line 32, in <module>
    from paramiko import util
  File "/usr/local/lib/python2.6/dist-packages/paramiko/util.py", line 32, in <module>
    from paramiko.common import *
  File "/usr/local/lib/python2.6/dist-packages/paramiko/common.py", line 98, in <module>
    from Crypto import Random
ImportError: cannot import name Random



outside of paramiko, I get the same ImportError if I try from Crypto import Random? How can I fix this problem? I installed pycrypto very carefully and have python-dev, python2.6-dev and gmp and got no errors when I installed from source.

thanks

---

### Post by Russss on 2011-07-18
I'm not sure whats wrong, it works for me, you can try to ask on stackoverflow: [http://stackoverflow.com/questions/tagged/python](http://stackoverflow.com/questions/tagged/python)

---

