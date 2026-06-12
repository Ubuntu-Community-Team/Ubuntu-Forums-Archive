---
title: "No permission to edit config files"
date: 2023-07-01
forum: New to Ubuntu
---

### Post by dhoelder on 2023-07-01
[COLOR=#232629][FONT=-apple-system]I have a problem with editing config files. E.g. in the opt/ or in the etc/ folder. I understand that I need to do this as root. But even with[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]*sudo gedit path/filename*[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]it doesn&#8217;t work:
[/FONT][/COLOR]
[FONT=Helvetica]daniel@Pi4: $ sudo gedit opt/traccar/conf/traccar.xml[/FONT]
[FONT=Helvetica]mkdir: cannot create directory "/run/user /0': Permission denied[/FONT]
[FONT=Helvetica]Authorization required, but no authorization protocol specified[/FONT]
[FONT=Helvetica](gedit: 16128): Gtk-WARNING **: 22:08:45.591: cannot open display: : 0[/FONT]
[FONT=Helvetica]daniel@Pi4: $

[/FONT]
[COLOR=#232629][FONT=-apple-system]With *sudoedit* I could edit the file but when I tried to save it (overwrite the old one) I got the error message &#8222;no permission&#8220;.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I have the permission to execute sudo since &#8222;*sudo -i*&#8220; works:
[/FONT][/COLOR]
[FONT=Helvetica]daniel@Pi4:~$ sudo -i [sudo] password for daniel:[/FONT]
[FONT=Helvetica]root@Pi4:~#

[/FONT]
[COLOR=#232629][FONT=-apple-system]I tried *gedit admin///* as well. Didn&#8217;t work as well.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Of course, I tried to edit the file with a graphical editor as well. Same result.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]And I tried to edit other config files (e.g. in etc/): same result.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]What am I doing wrong?

I use [SIZE=2][COLOR=#222222][FONT=Helvetica]Ubuntu 23.04 (GNU/Linux 6.2.0-1007-raspi aarch64) on a Raspberry Pi 4 B (8GB)[/FONT][/COLOR][/SIZE][/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-07-01
You are trying to use a GUI as root... root does does not have the permission to open a display, becasue it doesn't have .Xauthority and such to wrtie the temp files to it's own user directory... That is why it is frowned upon.

To edit config files, I use vi or nano... Console Text editors. Why? Becasue most of my configs are done over ssh.

Given that warning, there is a way around that.
```

sudo visudo

```
Adding this line to the end of the /etc/sudoers file will bring it up...
```

Defaults env_keep="DISPLAY"

```
But you can carry over more environment variables to make it work better with a line like this
```

Defaults env_keep="XAUTHORIZATION XAUTHORITY TZ PS2 PS1 PATH LS_COLORS KRB5CCNAME HOSTNAME HOME DISPLAY COLORS"

```
That way when you do 
```

sudo gedit opt/traccar/conf/traccar.xml

```
Then it will carry over those ENV VARs with it...

Be very careful with that... You have been warned. Be responsible.

---

### Post by dhoelder on 2023-07-01
Thank you @MAFoElffen!

Some questions for clarification:

- For editing via ssh I only need &#8222;sudo visudo&#8220;?
- What does it bring up, if I add line to /etc/sudoers? Do I need that for SSH or for GUI only?
- If I add the other line to /etc/sudoers I can edit the file with gedit?

Thanks again!

---

### Post by MAFoElffen on 2023-07-01
You need that for local using gedit as root via sudo... The GUI Gedit editor. Both lines will work. I would use the later line. only use one or the other. Not both.

Over ssh, to edit system files remotely, I just use nano. I can use both nano and vi,. I just personally prefer nano. Over ssh, in nano, I can still paste commands into the editor remotely.

---

### Post by ajgreeny on 2023-07-01
Your command will never work as you did not use the correct full pathway to that file in /opt.
You needed to add the extra / at the start of the pathway, ie,
```
sudo gedit /opt/traccar/conf/traccar.xml
```
Without that / your written pathway will be within your home which of course it is not.

---

### Post by TheFu on 2023-07-01
Uh .... using sudo with any GUI program is asking for trouble, but with editors it is even worse.  I see 2 issues with the OP's attempt.

a) Clearly the OP doesn't understand the difference between full/absolute file paths and relative paths.  That knowledge, which is identical on all OSes, needs to be understood.
b) Use **sudoedit**, not *sudo {edit command}* to edit system files.  Any editor can be used, just set the EDITOR environment variable to the editor you wish and the sudoedit program will honor that.  This assumes the userid is allowed/authorized to use sudo. If not, then that userid cannot be used.
```
export EDITOR=gedit
```
add that to the bottom of your ~/.bashrc - logout, login and from that point forward, sudoedit will use gedit to edit system files.

---

