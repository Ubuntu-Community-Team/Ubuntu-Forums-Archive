---
title: "OS specific command in Python"
date: 2006-06-20
forum: Programming Talk
---

### Post by krypto_wizard on 2006-06-20
I want to write a python program and call OS specific commands in it.
So basically, instead of typing in on the command line argument I want
to have it in a python program and let it do the action.

for example. in my program I would want to call the ssh feature like
one does on the command line

ssh Admin@192.168.2.10          .....etc

How can I do this easily ? What module deals with it ?

Every help is appreciated.

Thanks

---

### Post by Revert on 2006-06-20
I think what you want is the [os module.]("http://docs.python.org/lib/module-os.html")

> import os
os.system('<system command here>')

---

### Post by krypto_wizard on 2006-06-20
Thank you Revert, that helped me.

[QUOTE=Revert]I think what you want is the [os module.]("http://docs.python.org/lib/module-os.html")[/QUOTE]

---

### Post by Van_Gogh on 2006-06-20
os.system is fine, but it is recommended actually to use the subprocess module instead, as os.system will deprecate in the future.

However, I will usually rather use os.system myself for most things, because os.system is just simpler than subprocess. subprocess is however better for piping stuff back and forth between programs.

---

### Post by Revert on 2006-06-21
Thanks, I hadn't seen the subprocesses before.

[This]("http://docs.python.org/dev/lib/node533.html") might be helpful to anyone else looking to change os.system() into a subprocess.

---

### Post by krypto_wizard on 2006-06-21
I want to communicate using subprocess module but my task is a little different. May be you can guide me.

I have a linux box, from where I remotely execute all the commands. The remote machine is windows machine. I installed an OpenSSH server for windows to send the shutdown command. I setup the public keys in such a way that I could login to SSH server without using password.

I used

import os
os.system('ssh Admin@IP_ADDRESS shutdown -s')


I was wondering how can I interact with an application . Since you mentioned about subprocess module, I want an ability that my Python script can actually interact with the windows box and launch and close application there remotely.

Any suggestions on how to do this ?

Every help is appreciated.

Thanks for your time


[QUOTE=Van_Gogh]os.system is fine, but it is recommended actually to use the subprocess module instead, as os.system will deprecate in the future.

However, I will usually rather use os.system myself for most things, because os.system is just simpler than subprocess. subprocess is however better for piping stuff back and forth between programs.[/QUOTE]

---

### Post by foxylad on 2006-06-21
Check out the popen commands - these let you "open" a system command, and pipe commands to/from it.

---

