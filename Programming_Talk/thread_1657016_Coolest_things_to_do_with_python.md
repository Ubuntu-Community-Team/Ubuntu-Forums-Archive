---
title: "Coolest things to do with python"
date: 2010-12-31
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-12-31
I'd like to know some of the coolest things I can do with python!
I would prefer command line scripts, but if there is an animation-type thing you want to share (a simple thing like swirls in pygame without any extra buttons or anything) I will accept it.

Here's one thing I recently made which I think is pretty cool:
```
#!/usr/bin/env python
def getTerminalSize():
    def ioctl_GWINSZ(fd):
        try:
            import fcntl, termios, struct, os
            cr = struct.unpack('hh', fcntl.ioctl(fd, termios.TIOCGWINSZ,
        '1234'))
        except:
            return None
        return cr
    cr = ioctl_GWINSZ(0) or ioctl_GWINSZ(1) or ioctl_GWINSZ(2)
    if not cr:
        try:
            fd = os.open(os.ctermid(), os.O_RDONLY)
            cr = ioctl_GWINSZ(fd)
            os.close(fd)
        except:
            pass
    if not cr:
        try:
            cr = (env['LINES'], env['COLUMNS'])
        except:
            cr = (25, 80)
    return int(cr[1]), int(cr[0])
def getrandbin(): # get 1 or 0 randomly for the matrix
    import random
    return(random.randint(0, 2))
import time, sys
def matrix(): # this is actually just scrolling binary, not like the strange characters of the matrix
    x, y = getTerminalSize()
    def getLine():
        x, y = getTerminalSize()

        n1 = 0
        v = ''
        while n1 < x:
            x, y = getTerminalSize()
            v += str(getrandbin())
            n1 += 1
        return v
    n2 = 0
    v = ''
    while n2 < y:
        try: 
            t = 0.05
            #global t # uncomment this for the matrix to go a bit faster
            sys.stdout.write('\033[1m\033[32m' + getLine().replace('2', ' ') + '\033[0m\r')
            sys.stdout.flush()
            time.sleep(t)
        except KeyboardInterrupt: #Ctrl+C
            pass
        except EOFError: #Ctrl+D
            break

matrix()
```It's a matrix-like thing for the commandline, except it stays in one line until you press Ctrl+C
(press Ctrl+D to exit)

Make sure you put this in a file, don't paste it into the interactive interpreter or it won't work because there aren't enough newlines at the ends of functions

---

### Post by Vox754 on 2011-01-01
> **Crazedpsyc said:**
> ...

Here's one thing I recently made which I think is pretty cool:
...

That is one of the craziest Python programs I've seen. For instance, defining functions within functions, which also happen to import system modules within try-except blocks, is just plain weird.

Here is as saner version:
```

#!/usr/bin/env python

import fcntl, termios, struct, os
import random
import time, sys

def ioctl_GWINSZ(fd):
    ''' Get terminal size, by giving the proper file descriptor '''
    try:
        cr = struct.unpack('hh', fcntl.ioctl(fd, termios.TIOCGWINSZ, '1234'))
    except:
        return None
    return cr
        
def get_terminal_size():
    ''' Get terminal size, or assume one '''
    
    # Either stdin (0), stdout (1), stderr (2)
    cr = ioctl_GWINSZ(0) or ioctl_GWINSZ(1) or ioctl_GWINSZ(2)
    
    # If not available in either of these
    # obtain the proper file descriptor
    if not cr:
        try:
            fd = os.open(os.ctermid(), os.O_RDONLY)
            cr = ioctl_GWINSZ(fd)
            os.close(fd)
        except:
            pass

    # If still not available
    # get the information from the environment, or assume a size
    if not cr:
        try:
            cr = (env['LINES'], env['COLUMNS'])
        except:
            cr = (25, 80)

    return int(cr[1]), int(cr[0])

def get_rand_num():
    ''' Get 0, 1, or 2 randomly for the matrix '''
    return random.randint(0, 2)

def get_line():
    '''
    Return a line with numbers
    that is as long as the width of the current terminal
    '''
    n = 0
    line = ''

    width, height = get_terminal_size()

    while n < width:
        width, height = get_terminal_size()
        line += str(get_rand_num())
        n += 1
    return line

def matrix():
    '''
    Create a pseudo-matrix of binary numbers scrolling in one horizontal line.
    It is inspired in how the code looks like in the movie The Matrix
    '''
    n = 0
    t = 0.50  # Seconds after which the line refreshes

    width, height = get_terminal_size()

    # Refresh the line until a keyboard interrupt
    while n < height:
        try:
            # Only '0' and '1', with random spaces in between
            binary_line = get_line().replace('2', ' ')
            
            # Write to the terminal,
            # returning the cursor to the beginning of the line
            sys.stdout.write('\033[1m\033[32m' + binary_line + '\033[0m' + '\r')
            sys.stdout.flush()
            time.sleep(t)
        except KeyboardInterrupt, EOFError:
            # Ctrl+C, Ctrl+D
            sys.stdout.write('\n' + '=== END ===' + '\n')
            sys.stdout.flush()
            time.sleep(1.0)
            break

matrix()


```

---

### Post by unknownPoster on 2011-01-01
> **Vox754 said:**
> That is one of the craziest Python programs I've seen. For instance, defining functions within functions, which also happen to import system modules within try-except blocks, is just plain weird.



I completely agree with this.

@OP, perhaps you should research code standards among other things.

---

### Post by juancarlospaco on 2011-01-02
My Matrix Version:

```

[SIZE="1"]
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
import os, time, random, sys

class message(str):
    def __new__(cls, text, speed):
        self = super(message, cls).__new__(cls, text)
        self.speed = speed
        self.y = -1*len(text)
        self.x = random.randint(0, display().width)
        self.skip = 0
        return self
   
    def move(self):
        if self.speed > self.skip:
            self.skip += 1
        else:
            self.skip = 0
            self.y += 1

class display(list):
    def __init__(self):
        self.height, self.width = [int(x) for x in os.popen('stty size', 'r').read().split()]
        self[:] = [' ' for y in xrange(self.height) for x in xrange(self.width)]
   
    def set_vertical(self, x, y, string):
        string = string[::-1]
        if x < 0:
            x = 80 + x
        if x >= self.width:
            x = self.width-1
        if y < 0:
            string = string[abs(y):]
            y = 0
        if y + len(string) > self.height:
            string = string[0:self.height - y]
        if y >= self.height:
            return
        start = y*self.width+x
        length = self.width*(y+len(string))
        step = self.width
       
        self[start:length:step] = string
   
    def __str__(self):
        return ''.join(self)

i_message = raw_input("Input a message: ")
messages = [message(i_message, random.randint(1, 5))]
for t in xrange(1000):
    messages.append(message(i_message, random.randint(1, 5)))
    d = display()
    for text in messages:
        d.set_vertical(text.x, text.y, text)
        text.move()
    sys.stdout.write(str(d))
    sys.stdout.flush()
    del d
    time.sleep(0.1)[/SIZE]

```

Fake Kernel Panic Keyboard Leds, use with "xset dpms force off", need sudo:

```

[SIZE="1"]#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
import fcntl
import os
import time

KDSETLED = 0x4B32
SCR_LED  = 0x01
NUM_LED  = 0x02
CAP_LED  = 0x04

console_fd = os.open('/dev/console', os.O_NOCTTY)

all_on = SCR_LED | NUM_LED | CAP_LED
all_off = 0

while 1:
    fcntl.ioctl(console_fd, KDSETLED, all_on)
    time.sleep(0.1) 
    fcntl.ioctl(console_fd, KDSETLED, all_off)
    time.sleep(0.1)[/SIZE]

```

have fun...

---

### Post by ziekfiguur on 2011-01-02
> **juancarlospaco said:**
> My Matrix Version:
have fun...
```

Traceback (most recent call last):
  File "./foo.py", line 13, in <module>
    console_fd = os.open('/dev/console', os.O_NOCTTY)
OSError: [Errno 13] Permission denied: '/dev/console'

```
what does it do? I'm not going to run it as root to find out.

Here's mine, there's a similar C program in the repositories though, I just like reinventing the wheel :P
[SIZE="1"]```
#!/usr/bin/env python

import sys
import os
import termios

## function to do `cd` using `xd` add this to your .bashrc
## then use `xd usdpf' instead of `cd /usr/share/doc/python/faq/'
# xd()
# {
#     cd `/home/hans/bin/xd.py "$@"`
# }

class DontBlock:
    def __init__(self):
        self.error = False
        self.old_settings = termios.tcgetattr(0)
        if not self.old_settings:
            self.error = True
            return
        new_settings = termios.tcgetattr(0)
        new_settings[3] &= ~(termios.ECHO | termios.ICANON)
        new_settings[6][termios.VMIN] = 1
        new_settings[6][termios.VTIME] = 0

        if termios.tcsetattr(0, termios.TCSAFLUSH, new_settings):
            termios.tcsetattr(0, termios.TCSANOW, old_settings)
            self.error = True
            return

    def __del__(self):
        self.set_blocking()

    def set_blocking(self):
        if not self.old_settings:
            return
        if termios.tcsetattr(0, termios.TCSAFLUSH, self.old_settings):
            termios.tcsetattr(0, termios.TCSANOW, self.old_settings)
            self.old_settings = None

def choose(paths):
    db = DontBlock()
    if db.error:
        sys.stderr.write('Could not get non-blocking IO\n')

    indices = '1234567890abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
    for i in range(len(paths)):
        sys.stderr.write('{0:s}: {1:s}\n'.format(indices[i], paths[i]))

    try:
        x = 'spiny norman'
        while x not in indices[:len(paths)]:
            x = sys.stdin.read(1)
    except Exception as e:
        sys.stderr.write('Error {0:s}\n'.format(sys.exc_info()[1]))
    finally:
        db.set_blocking()

    return paths[indices.find(x)]

def find_paths(abbr):
    paths = ['/']
    for l in abbr:
        paths = find_paths2(l, paths)
        if not paths:
            break
    return paths

def find_paths2(l, paths):
    newpaths = []
    for p in paths:
        newpaths += [os.path.join(p, f) \
                     for f in os.listdir(p) \
                     if os.path.isdir(os.path.join(p, f)) \
                        and f[0] == l]
    return newpaths

def main(argv):
    if len(argv) == 1:
        return

    abbr = argv[1]
    paths = find_paths(abbr)
    paths.sort()
    if len(paths) == 1:
        sys.stdout.write('{0:s}\n'.format(paths[0]))
        return
    if len(paths) < 63:
        sys.stdout.write('{0:s}\n'.format(choose(paths)))
        return
    sys.stderr.write('ERROR: too many options.\n')


if __name__ == '__main__':
    main(sys.argv)

```[/SIZE]

---

### Post by juancarlospaco on 2011-01-02
i said *need sudo*  :)

---

### Post by ziekfiguur on 2011-01-02
> **juancarlospaco said:**
> i said *need sudo*  :)

I said I'm not going to run code I don't understand, with root privileges, to find out.

But, nevermind, by taking a closer look at the code i see what it does.

---

### Post by Crazedpsyc on 2011-01-02
wow! JCP, that is awesome! It made all me keyboard lights blink like craazy and messed up my keymap completely (don't worry, ziekfiguur, I just pressed Capslock and it was back to normal) I Know my structure was quite poor on that program, but It just took a minute to write ;)

JCP, the "My Matrix Version" is amazing! I am glad you shared that one!

ziekfiguur, Your code doesn't appear to do anything. When I run it it gets stuck at sys.stdin.read(1)
any idea why?

---

### Post by juancarlospaco on 2011-01-02
You are welcome...   :D

---

### Post by ziekfiguur on 2011-01-02
> **Crazedpsyc said:**
> ziekfiguur, Your code doesn't appear to do anything. When I run it it gets stuck at sys.stdin.read(1)
any idea why?

No, how did you run the script?

this is what it should do:```
## function to do `cd` using `xd` add this to your .bashrc
## then use `xd usdpf' instead of `cd /usr/share/doc/python/faq/'
# xd()
# {
#     cd `/home/hans/bin/xd.py "$@"`
# }

```
you give an abbreviation of a file path (starting at /) as a command line parameter, and the script prints the full path.

---

### Post by Crazedpsyc on 2011-01-02
I just ran ```
./zubf.py
```
and it exited without anything visible
then I ran ```
./zubf.py /home/me/.bashrc
```
and it sits there until I press Ctrl+c, then it prints:
```
Traceback (most recent call last):
  File "./zubf.py", line 95, in <module>
    main(sys.argv)
  File "./zubf.py", line 89, in main
    sys.stdout.write('{0:s}\n'.format(choose(paths)))
  File "./zubf.py", line 53, in choose
    x = sys.stdin.read(1)
KeyboardInterrupt
```

---

### Post by Vox754 on 2011-01-02
> **Crazedpsyc said:**
> I just ran ```
./zubf.py
```
and it exited without anything visible
then I ran ```
./zubf.py /home/me/.bashrc
```...

Realize that ziekfiguur sucks at explaining things.

You need to call the program with an argument. This argument is composed of the initial letters of each subdirectory of a path.

For example, call the program with the argument "usd"
```

./ziekfiguur.py usd

```
and you get
```

1: /usr/share/dbus-1
2: /usr/share/ddd
3: /usr/share/debconf
4: /usr/share/debhelper
5: /usr/share/debianutils
6: /usr/share/defoma
7: /usr/share/desktop-directories
8: /usr/share/desktopcouch
9: /usr/share/dict
0: /usr/share/dictionaries-common
a: /usr/share/directfb-1.2.10
b: /usr/share/djvu
c: /usr/share/doc
d: /usr/share/doc-base
e: /usr/share/dotnet
f: /usr/share/dpkg

```

Then choose a number or letter, and the program returns the full path of that option.

Now, ziekfiguur tells you to create a bash function (in the .bashrc file) to call this program and use it with the command "cd", thus creating a wrapper program "xd".

Naturally, ziekfiguur only wanted to show you something small, so the python program lacks documentation and testing to see if the argument corresponds to a valid path, or to gracefully exit in case of an error. Other than that, it's alright.

---

### Post by Crazedpsyc on 2011-01-03
Yes it could do with some error catching, but it is very good in my opinion, it would be very useful for a tab-completion addition to a shell, but I don't see how it could be used with cd because if there is more than one, it prints them all. this would cause it to cd to '1. /usr/share/something\n2. /us/share/somethingelse' right?

And the original program (xd) is little better with error catching and exiting. It sits there until I press enter (so a little better than Ctrl+C, but not much)

---

### Post by ziekfiguur on 2011-01-03
If you want a good program you should just get xd from the repositories.

If it finds more than one option, the options are printed to stderr, then you can type the number of the option you meant,
and only that one will be printed to stdout, so you can use it with cd.

---

### Post by ziekfiguur on 2011-01-03
> **Crazedpsyc said:**
> And the original program (xd) is little better with error catching and exiting. It sits there until I press enter (so a little better than Ctrl+C, but not much)
You are supposed to enter a number (or letter if there are more options) of the directory you want, then it prints that directory to stdout and exits.

---

### Post by Crazedpsyc on 2011-01-03
Ahh, I see. Well thank you for sharing ziekfiguur! As I said, it would be an excellent replacement for any standard tab-completion system. Maybe I'll even try adding it into my own python shell!

---

### Post by Crazedpsyc on 2011-01-03
[juancarlospaco]("http://ubuntuforums.org/member.php?u=784640"), your "Fake Kernel Panic" script looks great on my old Compaq keyboard! It has a light on everything!

---

### Post by juancarlospaco on 2011-01-03
add

import os 
# To turn OFF the screen.
os.system('xset dpms force off')

:)

---

### Post by Crazedpsyc on 2011-01-03
I did that, putting the os.system call in the loop and raising the time.sleep value so it was very fun!
;)
I'll have to share that with some friends! (of course I won't tell them I'm sharing it with them...;))
I also ran 
```
while [ 1 = 1 ]
do sleep 5
xset dpms force off
xset dpms force on
done
```from my shell (not python) and that was amusing!

If you have compiz with the Desktop Cube plugin "xset s activate" will make the cube twitch madly! Sorry, if this is annoying :D I just love artificially breaking things!

---

### Post by Crazedpsyc on 2011-01-04
BUmp

---

### Post by juancarlospaco on 2011-01-05
*Mm...*theres an interesting Kernel Panic simulator emerging here...

You can add this code to Temporally disable the Mouse device while using keyboard, requires sudo:
```

#!/usr/bin/env python
# -*- coding: utf-8 -*- 
import os
import time

fh = file('/dev/console')
while True:
    os.system('xmodmap -e "pointer = default"')
    fh.read(3)
    os.system('xmodmap -e "pointer = 0 2 3"')
    time.sleep(0.5)

```

:)

---

### Post by Crazedpsyc on 2011-01-05
Great! Thanks! I always get my hand on the touchpad and jerk the cursor around while I'm typing, so this is perfect for me!
If you have xautomation installed (it's in the repos) this is a fun one:
```
import os, random, time
def getn():
    x = random.randint(-100, 100)
    y = random.randint(-100, 100)
    t = random.randint(0, 3)
    if t is 1: x = 0 - x
    elif t is 2: y = 0 - y
    elif t is 3: 
        x = 0 - x
        y = 0 - y
    return(x, y)

while 1:
    x, y = getn()
    os.system('xte "mousermove %d %d"' % (x, y))
    time.sleep(0.05)
```
This one is ok to put in interactive ;) It moves your mouse around wildly! Take out the time.sleep to make it go faster :D and you will have to hold Control+c (probably) to make it stop

---

### Post by juancarlospaco on 2011-01-05
Im gonna try it, thanks!

On mine you can reduce the time.sleep(**0.5**) to make it more responsive...

---

### Post by raydeen on 2011-01-06
I made one slight alteration so that the text is up-down readable by reversing i_message (i_message[::-1]) as below. I gotta really look through this code to figure out how it was done. Very cool.

> **juancarlospaco said:**
> My Matrix Version:

```

messages = [message(i_message[::-1], random.randint(1, 5))]


```



have fun...

---

### Post by alwindoss on 2012-04-25
When I type Cntrl+D the program does not exit, did I do something wrong? [-o<

---

### Post by corrytonapple on 2012-04-25
I think it is CRTL-C Alwindoss.

---

### Post by Kwatiah on 2012-10-22
i really admire what you people i doing.i just started learning python programming.i'm new to programming.pls i reli need help on how to master it and do cool stuffs like what your are all doing.plsssssssssssssssss

---

### Post by Tony Flury on 2012-10-22
I don't think that these neccessarily count as cool - they certainly don't flash the keyboard lights, or make the text go upside down but they are useful to me : 

Scripts 2 to 5 work just as well as Nautilus scripts as they do as commandline - and for 1 to 5 - I use Zenity to provide a simple GUI to my scripts.

1- import : Imports pictures from a camera SD card to the relevants directory on my laptop - filing them under a date based folder structure.

2- Resize : Will resize all images in a given diectory - forming smaller versions - user defined scale and minimum size. If a 2nd Nautilus pane is open the resized pics are automatically saved there. Uses PIL to resize.

3- Watermark : Adds a user defined "watermark" and signature to all all images in a given diectory - ceating new images. If a second Nautilus pane is open the watermaked pics are automatically saved there. Uses PIL to add watermarks.

4- Contact Sheet : Builds one or more "contact sheets" for the images in the folder with a user definable page size and oientation and a number of fixed grid geometries.. If a second Nautilus pane is open the contact sheets are automatically saved there. Uses PIL to create the sheets and paste the thumbnails.

5- Scan : Allows the execution of a batched scan into a given directory, with user choosable scan size and quality. Uses the sane library to access the scanner

6- pyFlickr : A full functional GUI for uploading batches of files to flickr - including seting titles, descriptions, tags, sets and permissions. Will have a major re-wite soon.

7- Snake : Using pygame a standad Nokia style snake game - just a bit of fun.

8- TimeWarp : In pre-alpha development : An incremental near real time backup system - using iNotify to detect file changes. Includes a ncurses command line monitoring tool.

---

