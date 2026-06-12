---
title: "sudo -S means in layman term"
date: 2015-06-09
forum: New to Ubuntu
---

### Post by houmingc on 2015-06-09
Like to enquire what does sudo -S means ?
Is it similar to sudo su?
did 'man sudo'   *it imply read password from standard input instead terminal device



The below code works in qt, but i do not understand 'sudo -S" means
because without -S, i can't get the below code to work.

QProcess *myProcess = new QProcess;
QStringList args;
args<"-c"<<"sudo -S ifconfig eth0 192.168.100.1 < /var/passwd.txt");
myProcess->start("/bin/sh",args);

---

### Post by nerdtron on 2015-06-09
> man sudo
     -S, --stdin
                 Write the prompt to the standard error and read the password from the standard input instead of using the terminal device.  The password must be followed by a newline character.


From your code: 
"sudo -S ifconfig eth0 192.168.100.1 < **/var/passwd.txt**");

Since sudo requires you to type your password, -S option will allow your sudo to accept the password from the standard input, in which case this is the /var/passwd.txt which contains the sudo password.

---

### Post by seijirou on 2015-06-10
[COLOR=#000000]sudo -S ifconfig eth0 192.168.100.1 < /var/passwd.txt

The -S is telling sudo to expect the passwod to come from "standard input".  It might be worth doing a google on "linux standard input" to better understand what that is.

The "< /var/passwd.txt" portion after the ifconfig command is basically reading the contents of passwd.txt up to standard input and directing it over to sudo.

> would be the opposite, where the output of a commend is being read up to standard input.  "command > /some/file.txt" would extend that to be read the output of command up to standard output, then direct it over to file.txt.
[/COLOR]

---

