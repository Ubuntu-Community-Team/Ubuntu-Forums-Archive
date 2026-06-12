---
title: "[SOLVED] What is &amp;quot;root password&amp;quot;?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by embed_dev on 2008-10-07
Hello all,

I want to install JRE to my ubuntu and then I follow the instruction from the web. When I type su on the terminal, it asking for the "root password". What is it? How can I retrieve it if I lost it? 

Also, is that any other way to install JRE without using terminal?

I'm an absolute beginner on Linux stuff. Please help.

Thanks.
embed_dev

---

### Post by Elfy on 2008-10-07
root password isn't installed in ubuntu - use sudo instead of su to accomplish what you want.

You could use add/remove or synaptic to install java without the need to use the terminal

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Joeb454 on 2008-10-07
To further forestpixie's example of using sudo, you may run something like this from a terminal ```
sudo apt-get install openjdk-6-jre
```

I *think* that would install the JRE under Ubuntu, though I'm not 100% sure

---

### Post by Idefix82 on 2008-10-07
In the old versions of Linux you could login as a so called "super user" with all the permissions there are. This super user is traditionally called root. It's like an administrator account under Windows. This was found to be insecure because viruses can then perform any operation if they are executed from a root account.

In Ubuntu you don't have all the permissions by default even if you are the only user on the system. Instead, whenever you want to execute a command which can potentially harm the system, like installing software, you need to provide the password with which you log in. To tell the terminal that you want to execute a command with root privileges you start it with "sudo". For example if you want to copy a file to the /usr folder, if you just try
```
cp file /usr
```
you will get a "permission denied" error. If instead you type
```
sudo cp file /usr
```
you will be prompted for your password and then the command will be executed.

If you want to start a GUI application with root privileges (eg you want to change the file /etc/modprobe.d/blacklist in gedit) then you use "gksudo instead:
```
gksudo gedit /etc/modprobe.d/blasklist
```

About avoiding the terminal: you sometimes can avoid it but sometimes you can't, without making things too complicated. If you ask questions on the forums you will usually get instructions for the terminal because it is unambiguous and quick. This way you will slowly learn to use it. You really don't need to be afraid of it.

I hope this helps.

---

### Post by iaculallad on 2008-10-07
Just be sure to place a check mark on "Multiverse" before doing the command below to install your JRE application:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

The command above will ask for a password: Input your own user password.

---

### Post by Elfy on 2008-10-07
> if you ask questions on the forums you will usually get instructions for the terminal because it is unambiguous and quick. This way you will slowly learn to use it. You really don't need to be afraid of it. +1

---

### Post by Liviu-Theodor on 2008-10-07
> **embed_dev said:**
> Hello all,

I want to install JRE to my ubuntu and then I follow the instruction from the web. When I type su on the terminal, it asking for the "root password". What is it? How can I retrieve it if I lost it? 

Also, is that any other way to install JRE without using terminal?

I'm an absolute beginner on Linux stuff. Please help.

Thanks.
embed_dev

Root is the user with the highest privileges in other Linux distributions, but ubuntu has disabled it by default, so chances are you haven't lost it, because you never had it. Instead, ubuntu uses the first user as an administrator. So, if a program requires "root password", you should generally run it with sudo or gksudo, as it asks in fact your password. Or you can install the package [FONT="Courier New"]nautilus-gksu[/FONT].

And for installing programs without using the terminal, try [FONT="Courier New"]Applications->Add/Remove...[/FONT] or [FONT="Courier New"]System->Administration->Syanptic Package Manager[/FONT]. And be sure to check which [repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") you are using.

---

### Post by alphacrucis2 on 2008-10-07
> **embed_dev said:**
> Hello all,

I want to install JRE to my ubuntu and then I follow the instruction from the web. When I type su on the terminal, it asking for the "root password". What is it? How can I retrieve it if I lost it? 

Also, is that any other way to install JRE without using terminal?

I'm an absolute beginner on Linux stuff. Please help.

Thanks.
embed_dev

As others said use sudo followed by a command. If you must it is sometimes convenient when you want to do a series of commands as root to use the command:

sudo -i

Enter your own password and then following commands will be run as root.

---

### Post by embed_dev on 2008-10-07
OK, I understand now. But first, I need to download the JRE. Let me try.

Thanks for all of you.
embed_dev

---

### Post by iaculallad on 2008-10-07
And remember to force-expire (remove the time stamp) your sudo password when leaving your PC unattended (Recommended when unit is used by multiple users).

```
sudo -K
```

---

