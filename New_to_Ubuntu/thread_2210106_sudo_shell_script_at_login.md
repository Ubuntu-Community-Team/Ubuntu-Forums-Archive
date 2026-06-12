---
title: "sudo shell script at login"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by ken18 on 2014-03-09
I'd like to run a shell script immediately after login that opens an xterm window, executes some commands that require sudo, then closes the xterm window after the user presses any key.

I've been partially successful by creating an item in Startup Applications using the following command:
> x-terminal-emulator -e /home/user/myscript.sh

This opens a terminal window after login and runs the script, but the commands in the script fail because they require sudo.  I know I could preface each command in the script with sudo, but I really don't want to have to type in the password.  What can I do?

Ken

---

### Post by Lars Noodén on 2014-03-09
If your script is the way you like it, I would move your script off to /usr/local/bin and make sure it is not writeable by anyone than root.  

Then you could consider modifying sudoers.

```

%ken18 ALL=(ALL) PASSWD: /usr/bin/x-terminal-emulator -e  /usr/local/bin/myscript.sh 

```

Check the manual page for sudoers first.  There's also very good, in depth coverage in *Sudo Mastery* by Michael W Lucas about what can be done and pitfalls to avoid.

---

### Post by ken18 on 2014-03-09
I decided to use zenity instead of opening an xterm, but I'm having trouble with sudoers.  Here's what I've done:
> 1. created myscript.sh that contains commands requiring sudo privilege
2. moved myscript.sh to /usr/local/bin
3. created startup application entry using command /usr/local/bin/myscript.sh
4. added following entry to sudoers file: xxx host=(root)NOPASSWD:/usr/local/bin/myscript.sh where 'xxx' is the user name and 'host' is the actual host name

If I try to execute the script from a standard xterm I get the following error message: must be super-user to perform this action.  Rebooting will execute the script but nothing is displayed.  I know the script works correctly with sudo permission.

Here is the result of sudo -l:
> User xxx may run the following commands on this host:
    (ALL : ALL) ALL
    (root) NOPASSWD: /usr/local/bin/myscript.sh

What have I done wrong?

---

### Post by pqwoerituytrueiwoq on 2014-03-09
Unless the script requires user input do this
```
sudo chmod +x /usr/local/bin/myscript.sh
echo "session-setup-script=/usr/local/bin/myscript.sh" | sudo tee -a /etc/lightdm/lightdm.conf
```
then your script will be ran silent at every login

---

### Post by ken18 on 2014-03-09
What I want to do is display an informational dialog box after every login.  The shell script contains commands that require sudo authority.  I used sudoers to add specific permission for the command requiring sudo authority but it still wasn't working.  I finally figured out that I needed to preface each command in the script with 'sudo'.  Problem solved.  Beginner mistake for sure...

---

### Post by pqwoerituytrueiwoq on 2014-03-09
you mean like a dialog box you hit OK on?
[FONT=courier new]session-setup-script=sh -c 'DISPLAY=":0.0" zenity --info --text "By pressing OK, you agree that Cats Rule and Dogs Drool"'[/FONT]
this will create a dialog on the screen, the destkop will not load until OK is pressed
the window will have no title bar (or theme for that matter) as the window manager has not loaded yet
[[img]http://www.zimagez.com/miniature/screenshot-03092014-092722pm.php[/img]](http://www.zimagez.com/zimage/screenshot-03092014-092722pm.php)

---

### Post by Lars Noodén on 2014-03-10
Have you verified that you can run the script without the password manually?

```

sudo -K
sudo /usr/local/bin/myscript.sh 

```

---

### Post by ken18 on 2014-03-10
It's working now, thanks.  I like the idea of the dialog box before the desktop loads. I'll try that.  Thanks for all the help.

Ken

---

### Post by ken18 on 2014-03-11
> **pqwoerituytrueiwoq said:**
> you mean like a dialog box you hit OK on?
[FONT=courier new]session-setup-script=sh -c 'DISPLAY=":0.0" zenity --info --text "By pressing OK, you agree that Cats Rule and Dogs Drool"'[/FONT]
this will create a dialog on the screen, the destkop will not load until OK is pressed the window will have no title bar (or theme for that matter) as the window manager has not loaded yet

Where should this command reside?  Clearly, it can't go in the Startup Applicatons Preferences (I already tried it).

Ken

---

### Post by pqwoerituytrueiwoq on 2014-03-16
> **ken18 said:**
> Where should this command reside?  Clearly, it can't go in the Startup Applicatons Preferences (I already tried it).

Ken
sorry for late reply
add it to [FONT=courier new]/etc/lightdm/lightdm.conf[/FONT] 
figured you would figure it out after my last post #4 in this thread

---

### Post by ken18 on 2014-03-17
Thanks!

Ken

---

