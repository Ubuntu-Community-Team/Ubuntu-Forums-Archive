---
title: "[Python] Piping to STDIN for Sudo Password"
date: 2011-12-11
forum: Programming Talk
---

### Post by dodle on 2011-12-11
I can pipe a password to the sudo command using the following methods:

[php]os.popen('echo password | sudo -S command')[/php]
[php]commands.getoutput('echo password | sudo -S command')[/php]

But I understand that [color=red]subprocess[/color] is supposed to replace those two modules. And I've finally figured out how to use it for this purpose.

[php]subprocess.Popen('echo password | sudo -S command', shell=True)[/php]

But calling the system "echo" command seems like an ugly hack. Is there a better way to do this with subprocess?

---

### Post by MadCow108 on 2011-12-11
import subprocess
p = subprocess.Popen(["sudo", "-S", "whoami"], stdin=subprocess.PIPE, stdout=subprocess.PIPE)
print p.communicate("password\n")

---

### Post by dodle on 2011-12-11
> **MadCow108 said:**
> p.communicate("password\n")

D'oh! ](*,)

I had been trying that and it wasn't working. All because I left out the "\n" character.

Thanks MadCow, you're always there for me.

---

