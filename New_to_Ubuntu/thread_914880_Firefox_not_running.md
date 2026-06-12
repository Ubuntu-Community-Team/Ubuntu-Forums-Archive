---
title: "Firefox not running"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by zeththedarkmage on 2008-09-09
Just randomly last night my firefox web browser stopped working. Although I hadn't changed any thing when I would go through applications>internet>Firefox web browser it would give me the error message

Failed to execute child process firefox (file or directory not found)

So I uninstalled firefox and reinstalled it several times and I still get the same error. 

I installed firefox 2 and it is running fine, but I still can't get firefox to run at all. And yea I only installed firefox 2 to get on the internet, I'm not sure if there are incompatibility errors but I can just uninstall firefox 2 once the original problem of firefox not working is solved.

---

### Post by decoherence on 2008-09-09
what method are you using to install/uninstall?

what happens if you type 'firefox' at the terminal? how about 'firefox-bin'?

what is the output of the command 

```
echo $PATH
```

---

### Post by zeththedarkmage on 2008-09-09
I've been uninstalling and reinstalling it through the synaptic package manager 

when I typed in firefox in terminal I got this

zeth@zeth-desktop:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
zeth@zeth-desktop:~$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
firefox-3.0 set to manually installed.
The following packages were automatically installed and are no longer required:
  gappletviewer-4.2 mesa-common-dev libglu1-mesa-dev libgl1-mesa-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zeth@zeth-desktop:~$ firefox-bin
bash: firefox-bin: command not found

it said it wasn't installed, so then I tried to install it but it gave me that message


and heres what I get from the code

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

