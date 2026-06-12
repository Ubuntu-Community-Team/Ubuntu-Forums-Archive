---
title: "how to start script with gdm3 login for a user"
date: 2021-08-13
forum: Programming Talk
---

### Post by echodevnull on 2021-08-13
Hello community,
i tried to start a script in Ubuntu 21.04. in the gdm3 login for a user before usersession(the script must run before), i found this:
[https://unix.stackexchange.com/questions/450835/how-to-execute-command-before-user-login-on-linux](https://unix.stackexchange.com/questions/450835/how-to-execute-command-before-user-login-on-linux)
there they say i have to put the script in /etc/gdm3/PostLogin/Default and then its started before usersession - but nothing happens. 
please help

---

### Post by TheFu on 2021-08-13
> **echodevnull said:**
> Hello community,
i tried to start a script in Ubuntu 21.04. in the gdm3 login for a user before usersession(the script must run before), i found this:
[https://unix.stackexchange.com/questions/450835/how-to-execute-command-before-user-login-on-linux](https://unix.stackexchange.com/questions/450835/how-to-execute-command-before-user-login-on-linux)
there they say i have to put the script in /etc/gdm3/PostLogin/Default and then its started before usersession - but nothing happens. 
please help

Please post the script and the permissions on the file.

---

### Post by echodevnull on 2021-08-14
what i want to program later is an other kind of login for users and a gui-menu for the user to choose before userlogin but first i tested to how to get a window so
i try with test of zenitywindow and i tried to write a log and there is no log in /tmp:

root@user-virtual-machine:/bin# ls -l testzen.sh
-rwxrwxrwx 1 root root 62 Aug 14 09:29 testzen.sh
root@user-virtual-machine:/bin# cat testzen.sh
zenity --notification --window-icon=info --text "Hello World"
root@user-virtual-machine:/bin# cat /etc/gdm3/PostLogin/Default
/bin/testzen.sh >> /tmp/testzen.log 2>&1

root@user-virtual-machine:/bin#

---

### Post by TheFu on 2021-08-14
Typically, no window can be displayed before there is a user GUI session.  That happens AFTER login.  You'll need to work with lower level tools that aren't dependent on an X/Session or Wayland session to do what you want.  

This is non-trivial, but there are lots of examples with full code.

Perhaps a different option would work easier?  Login using a guest account, only allow the chooser you want to be run from that account and have the selection, drop back to a non-GUI session, login so a new GUI session, and run the other program you want?

I've never done this, so I'm just guessing.  Zenity requires a GUI session (typically X/Windows) and X/Windows requires an X/Session, which happens after user login.

---

### Post by echodevnull on 2021-08-15
yes it seems PostLogin isnt the right thx - ok i changed, but in **PreSession** it **should** work. 

gdm-Doc says:
>After the user session has been initialized, GDM will run the         PreSession script.  This script is useful for         doing any session initialization that needs to happen after the          session has >been initialized.  It can be used for session management or         accounting, for example.

now i get a log and it says:
[COLOR=#ff0000][B]Unable to init server: Could not connect: Connection refused

(zenity:1541): Gtk-WARNING **: 12:25:53.374: cannot open display: [/B][/COLOR]

---

