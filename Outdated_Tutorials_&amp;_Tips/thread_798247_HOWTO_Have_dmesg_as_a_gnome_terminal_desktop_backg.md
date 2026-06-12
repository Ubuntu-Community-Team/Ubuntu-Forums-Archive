---
title: "HOWTO: Have dmesg as a gnome terminal desktop background"
date: 2008-05-18
forum: Outdated Tutorials &amp; Tips
---

### Post by kitrule on 2008-05-18
[[IMG]http://img253.imageshack.us/img253/5859/screenshot8su7.th.png[/IMG]](http://img253.imageshack.us/my.php?image=screenshot8su7.png)

1) Install Devil's Pie
```
sudo apt-get install devilspie
```

2) Create a configuration file 
```

mkdir ~/.devilspie
gedit ~/.devilspie/DesktopConsole.ds

```

3) Paste the following configuration
```
(if
        (is (window_name) "DesktopConsole")
        (begin
		(below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "dock")
                (geometry "1200x700+40+50")
		(stick)
        )
)
```

Notes:
- Adjust the [geometry](http://wiki.foosel.net/linux/devilspie#geometry) line to match your screen.
- **Read** the [Devil's Pie Wiki](http://wiki.foosel.net/linux/devilspie) for other options.

4) Create a new gnome-terminal profile named "DesktopConsole"
[[IMG]http://img293.imageshack.us/img293/5489/screenshot7ob3.th.png[/IMG]](http://img293.imageshack.us/my.php?image=screenshot7ob3.png)
- in the "General" tab, untick "show menubar by default..."
- in the "Scrolling" tab, select "Scrollbar is" -> Disabled.

5) Create a shell script
```

gedit ~/desktop.sh

```

6) Paste the following code
```
dmesg | tail -n 5000
j=`dmesg | tail -n 1`
while [ 0 -ne 1 ]; do
	k=`dmesg | tail -n 1`
	if [ "$j" != "$k" ]; then
		echo $k
		j=$k
	fi
done
```

7) Add devilspie and gnome-terminal to the Startup Programs in your session:
in System->preferences->sessions, "Startup Programs" tab, add the following command:
```
devilspie | gnome-terminal --window-with-profile=DesktopConsole -e ./desktop.sh
```

8) Logout, Login

9) Right click on the desktop terminal with dmesg and adjust it's transparency and colouring as desired. I selected a black background, with about 70% transparency and a green font.

Known issues ( - please comment if you have a solution):

a) The terminal misses some dmesg updates when there are several within the same second because of the way it's called from the while loop.

b) The desktop icons appear behind the terminal.

c) The terminal is interactive, pressing [ctrl][c] on it will close it in all viewports.


So ideally, I'd love it to be constantly up to date without missing anything. All desktop icons (static and dynamic) displayed in front of the terminal. And the terminal to be read only somehow, whilst retaining the ability to scroll up and down with my touchpad or with your mouse wheel.

Thanks to jinacio for publishing [his how-to](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop) on how to get the terminal integrated in to the background.

---

### Post by enkoan on 2009-11-24
about this code: > ```
dmesg | tail -n 5000
j=`dmesg | tail -n 1`
while [ 0 -ne 1 ]; do
	k=`dmesg | tail -n 1`
	if [ "$j" != "$k" ]; then
		echo $k
		j=$k
	fi
done
```

isn't this pretty processor intensive? It seems like there could be a better solution.  I know its easy to pipe the kernel messages to a virtual terminal (eg. tty10) by editing /etc/syslog.conf.

is there perhaps some way to re-direct that to a dedicated rxvt window in X or something?

---

### Post by kitrule on 2009-11-25
You're right, it was very processor intensive. It was probably my first script. I don't use it anymore and almost forgot about this thread. If you find a way to do it how you say I'd love to learn how.

I only recently learnt about customising syslog when I configured it to read messages from my router and put them in router.log.

I noticed dmesg -c clears the buffer after printing, so if you did that you wouldn't need to check if any of the lines were the same before printing and you shouldn't miss any messages. -c requires root privileges though, so you'd have to call it with sudo. the script could be as follows:

```
while [ 1 ]; do              # loop forever
	dmsg=`sudo dmesg -c` # only run dmesg once per loop
	if [ "$dmsg" ]; then # don't echo empty lines
		echo "$dmsg" # print dmesg to console
		sleep 1      # wait 1 seconds between loops if something's happening
	elif	sleep 5      # wait 5 seconds between loops if not much is happening
	fi
done
```

and type your password to sudo once after you sign in.

the unfortunate side-effect is that if you run dmesg in a terminal after you start the script you'll never have the complete history. a compromise would be to add something like:

```
dmsg=`sudo dmesg -c`
echo $dmsg
echo $dmsg > ~/.dmesg.log
```

above the while loop, and

```
echo "$dmsg" >> ~/.dmesg.log
```

inside the if statement then `cat ~/.dmesg.log` instead of running dmesg from other terminals.
you could put `cat ~/.dmesg` in another executable script called dmsg and run that instead of dmesg from the other terminals.

---

