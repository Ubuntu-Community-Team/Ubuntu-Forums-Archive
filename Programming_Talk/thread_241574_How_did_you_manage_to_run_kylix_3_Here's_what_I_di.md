---
title: "How did you manage to run kylix 3? Here's what I did!"
date: 2006-08-22
forum: Programming Talk
---

### Post by oskar.hansen on 2006-08-22
Hi, i'm going to learn Delphi in school (as the only one in my class, because I have Linux instead of a MS OS).

Today I've tried to install Borland Kylix 3 on my computer, and finaly it seems to be working ! :D (But i still have a problem, please look in the very bottom of this post)

Here's what i did (Or should have done, if i knew everything from the start):

1. Get the kylix3_open.tar.gz from borland.com by registreing.

2. copy the reg92.txt to ~/ (the one that is attached to the mail from borland)

3. unpack the kylix3_open.tar.gz

4. Just to see if every dependences is installed: ```
cd ~/kylix3_open/borpretest
./testsystem
```

If the test is passed it should show something like this:

> Borland Kylix
System Compatibility Test
Checking loader....OK
Checking kernel >= 2.2....OK
Checking libc >= 2.1.2....OK
Checking libjpeg >= 6.2.0....OK
Looks GOOD !!!
This system should be able to run Borland Kylix!


In my case that wasn't enough, I had to install these too.

```
sudo apt-get install gcc libgtk1.2 libxaw6
```

And make a shortcut:

```
sudo ln -s /usr/X11R6/lib/libx11.so.6 /usr/X11R6/lib/libx11.so
```

5. Install the program (just follow the describtion on the screen)

```
cd ~/kylix3_open/
sudo sh setup.sh
```

6. Reboot (not really sure of this, but i couldn't see the shortcuts in the gnome menu just after the install)

7. To make the program start from the menu:

I made a backup (if anything should went wrong) and opened the script in gedit:
```
cd /usr/local/kylix3/bin/
sudo cp startdelphi startdelphi_backup
sudo gedit startdelphi
```

Here I replaced the first couple of lines with:

```
#!/bin/bash

# BEGIN STRING TABLE
export LD_ASSUME_KERNEL=2.4
LANG=en_US.ISO8859-1
KYDEF_LOCALE="en_US"
LC_ALL_IS_C1="The LC_ALL environment variable is set to C. Kylix cannot start with this setting."
LC_ALL_IS_C2="Defaulting LC_ALL to"

# END STRING TABLE
```

saved and exit

in order to avoid starting the program as su every time I changed owner and rights in the ~/.borland/ folder:

```
sudo chown [your username]~/.borland/*
sudo chmod 700 ~/borland/*
```

8. to start the program:

type```
startdelphi
```

or

click on the Kylix 3 (Delphi) icon in the gnomemenu.



Now it should be working. But I still have a problem: everytime I use the start button the program freezes! Does anyone have a solution for this?


Thank you for your time, please post if I'm wrong anywhere in this "guide" :)

---

