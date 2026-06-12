---
title: "Beginners guide to SSH"
date: 2010-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by olof_ on 2010-12-30
Definitions:
computer A is the computer which initiates the ssh connection. that computer needs no additional software.
computer B is the computer which will run the ssh server, and is the computer which will be accessed.

[SIZE=4]First, The only-CLI way:[/SIZE]
[SIZE=3]On Computer B:[/SIZE]
[SIZE=2]1.[/SIZE] First open the Terminal (Applications->Accesories->Terminal, or the quick way [ctrl]+[alt]+[t]), on the computer you want to control (connect to) and install openssh-server :

```

sudo apt-get install openssh-server

```[SIZE=2]2.[/SIZE] then you need to know the IP and the user of the computer which you will connect to:
to see the ip-address:
```

ifconfig | grep “inet addr”

```to see the username:
```

whoami

```[SIZE=3]On Computer A:[/SIZE]
[SIZE=2]3.[/SIZE] It is time to connect, and it is in the form
ssh <username>@<ip-address>
```

ssh john@192.168.1.17

```just to mention: if you only have one computer but still want to learn, it it possible to issue a ssh connection to yourself, with openssh-server installed you just choose your own username as username and “localhost” as ip-address.

[SIZE=2]4.[/SIZE] then you need accept the RSA fingerprint (just write yes, it only happens once for every connection) and write the password for the user.

that is it, you are connected.

To disconnect and close the ssh session just type logout:
```

logout

```

---------------------------------------------------------------------------

[SIZE=4]The half-GUI way: -Y[/SIZE]
Then there are several extra parameters which changes ssh in different ways.
The parameter which I am in love with is -Y.

from the ssh manual page regarding -Y:
“Enables trusted X11 forwarding.  Trusted X11 forwardings are not subjected to the X11 SECURITY extension controls.”

In  stage 3, you just add -Y after ssh:
ssh -Y <username>@<ip-address>
```

A:~$ ssh -Y username@192.168.1.17

```When you are connected you can start graphical programs just like you ran them from your own computer.

Example:
```

xclock

```Will show a clock on your screen.

(to stop the clock, press [ctrl]+[c] in the terminal window)
```

username@hokatorp-serv:~$ xclock
^C
username@hokatorp-serv:~$

```What you do is that you run the program on computer B, but display them on computer A.

[SIZE=2]export DISPLAY[/SIZE]
But what if you both want to run the program and show it on computer B, using computer A as a “remote control“?

First, connect with computer A to computer B with the -Y using the same steps as mentioned before. When you are connected you have to tell the computer you are connected to that you want to use another display output. You want to change the DISPLAY variable.

> **gmargo said:**
> To set the DISPLAY environment variable in bash syntax:
```

export DISPLAY=:0

```

And to restore it you can either disconnect the ssh session and then connect again or change the display variable to point at your desired DISPLAY.

> **gmargo said:**
> The proper syntax for the $DISPLAY variable, pointing back through the **ssh** link, is "localhost:10.0" (or 11.0 for the second connection, 12.0 for the third connection, etc).

from there its just as before, try to run xclock again and see on which screen it appears:
```

xclock

```for more info see:
```

man ssh

```to exit from a help file, press [q]

Thanks to gmargo, tgalati4, msandoy and nerdy_kid for helping me and answering my questions!
see the whole thread here: [http://ubuntuforums.org/showthread.php?t=1650950](http://ubuntuforums.org/showthread.php?t=1650950)

This tutorial was made on Ubuntu 10.10 x64, in gnome-terminal but should work in any linux environment.

If you want to remove openssh-server and ssh which was installed in the first step:

```

sudo apt-get remove ssh openssh-server

```

---

