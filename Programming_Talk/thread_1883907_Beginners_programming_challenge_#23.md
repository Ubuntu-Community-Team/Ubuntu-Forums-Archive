---
title: "Beginners programming challenge #23"
date: 2011-11-20
forum: Programming Talk
---

### Post by Bodsda on 2011-11-20
_[SIZE=4][COLOR=Red]Welcome to the 23rd Beginners programming challenge.[/COLOR][/SIZE]_

This challenge was inspired by a problem that I have been facing at work recently. The aim of the challenge is to demonstrate how even beginner programmers with very little experience can use their skills to automate repetitive tasks.

[U][B]Background
[/B][/U]
The challenge, should you choose to except it, is to automate a daily backup check. The check is a manual task of opening 100 folders, looking at the date modified value of the contents and seeing if any are older than 24hours. Any files older than 24hours indicate that this particular server has not been backed up

[U][B]Assumptions
[/B][/U]

[LIST]
[*] The location is ~/server_backups/
[*] In this location is 100 directories named after the respective servers (server1, server2 etc.) - (Note, there will be no naming convention)
[*] In each directory is an unknown number of flat files which represent server backups
[*] All backups have finished for the day, no additions are made whilst you are checking them
[/LIST]
 
Feel free to use just 5 folders when testing your code, it should work identically with 5, 100, 2000 folders.

_**Task**_

Write a program that automates this daily check. 
The program should output either:

[LIST=1]
[*]An all OK message
[*]A single line for every server with an out of date backup (each server, not each file)
[/LIST]
_**Cookie points**_

Cookie points will be awarded for the following extras

[LIST=1]
[*]The ability to specify an out-of-date time frame via command line switch
[*]Prioritization of failures; longest time since last backup outputted first
[*]An output of the total amount of servers successfully backed up in the last 24hours
[/LIST]

_***Disqualified Entries:***_

Any overly obfuscated code will be immediately disqualified without  account for programmers skill. Please remember that these challenges are  for beginners and therefore the code should be easily readable and well  commented.

Any non-beginner entries will not be judged. Please use common sense  when posting code examples. Please do not give beginners a copy paste  solution before they have had a chance to try this for themselves.


_***Assistance:***_

If you require any help with this challenge please do not hesitate to  come and chat to the development focus group. We have a channel on  irc.freenode.net #ubuntu-beginners-dev
Or you can pm me

Have fun,
Happy coding

Bodsda
Ubuntu Beginners Team

---

### Post by cgroza on 2011-11-20
Some Haskell code that respects the minimum requirements. I will maybe improve it to get the cookie points.
The program gets the current directory and checks every folder in it.

```

import System.Time
import System.Directory
import Monad
import Control.Applicative

isNotFileBacked :: FilePath -> IO Bool
isNotFileBacked file =
  (return . ((60 * 60 * 24) <=) . tdSec) =<< (diffClockTimes <$> getClockTime <*> getModificationTime file)

isNotBackedUp ::  FilePath -> IO Bool
isNotBackedUp dir =
  ((return . not . null =<<) . filterM isNotFileBacked . map ((dir ++) . ("/" ++)))
                                                              =<< getDirectoryContents dir

main :: IO ()
main =do servers <- (getDirectoryContents =<< getCurrentDirectory) >>= filterM doesDirectoryExist
                    >>= filterM (return .  (`notElem` [".",".."])) >>= mapM canonicalizePath
         notBacked <- filterM isNotBackedUp servers
         if null notBacked then putStrLn "All OK" else mapM_ putStrLn notBacked


```Compile with ghc filename.hs.

---

### Post by JDShu on 2011-11-20
I'm decently familiar with Python, but I decided to explore the os module, which I don't know too well. I might modify it to improve the style/ get cookie points later.

```

import os
import time

SECONDS_IN_DAY = 60*60*24
ROOT_FOLDER = os.path.join(os.getenv("HOME"),"server_backups")

def file_is_dated(filename):
    return (time.time()-os.stat(filename).st_mtime) > SECONDS_IN_DAY

def has_dated(directory):
    for filename in os.listdir(directory):
        if file_is_dated(os.path.join(directory, filename)):
            return True
    return False

def get_server_list():
    return filter(os.path.isdir, os.listdir('.'))

def main():
    backed_up = True
    os.chdir(ROOT_FOLDER)
    servers = get_server_list()
    for s in servers:
        if has_dated(s):
            print s, "is not backed up"
            backed_up = False

    if backed_up:
        print "Everything's OK!"

if __name__ == '__main__':
    main()

```

---

### Post by bgs100 on 2011-11-26
I might not be considered a beginner, but I did this in [Chicken Scheme]("http://www.call-cc.org/"), which I've never used before (and I haven't messed with lisp in a while).

```
(use posix)
(use srfi-1)

(cond ((member "-h" (command-line-arguments))
    (display "Usage: challenge23 [-t s]\n")
    (display "where s is a number of seconds representing when to consider something out of date\n")
    (display "(defaults to 86400, the number of seconds in a day)\n")))

(define root-dir "~/server-backups/")
(define dirs
    (map (lambda (s) (string-append root-dir s))
         (directory root-dir)))

(define outdated-time (* 60 60 24))
(let ((sub (member "-t" (command-line-arguments))))
    (if sub
        (let ((i (string->number (cadr sub))))
            (if i
                (set! outdated-time i)))))

(define (age file)
    (- (current-seconds) (file-modification-time file)))

(define (age-directory dir)
    (apply max
        (map (lambda (f) (age (string-append dir "/")))
             (directory dir))))

(filter-map
    (lambda (age) (and
                    (> (cdr age) 0)
                    (format #t "~a is ~a seconds out of date~%" (car age) (cdr age))))
    (sort (map (lambda (d) (cons d (- (age-directory d) outdated-time))) dirs)
          (lambda (a b) (< (cdr a) (cdr b)))))
```

Compile with:
```
$ csc challenge23.scm
```

Or just run with:
```
$ csi -script challenge23.scm
```

Fulfills extras 1 (via the -t option) and 2.

---

### Post by red_Marvin on 2011-11-27
Here is a bash variant, which may fail to fulfil the qualifications
for various reasons, It may be considered obfuscated and I'm probably
not really a beginner anymore, which is not a problem for me, as I
participate for the code writing and not the chance to win.
I have written up some comments on the more convoluted parts of the
code though if anyone is interested.

```
server_root=$HOME/server_backups
maxage=86400 # 24h in seconds
ok=
for server in $(ls $server_root)
do
    if [[ -n $(ls $server_root/$server/) ]]
    then
        if (($(date +%s)-$(stat -c%Y $server_root/$server/*|sort|head -n1) > $maxage ))
        then
            echo $server
            ok=nope
        fi
    else
        echo $server
        ok=nope
    fi
done
if [[ -z $ok ]]
then
    echo ALL OK
fi

# OK, what does this code do, then?
#
# the test [[ -n $(ls $server_root/$server/) ]]
# is true if the string generated by the ls ..
# command contains any characters, which in this
# case corresponds to that there are one or more
# files in the directory $server_root/$server/
#
# the line (($(date +%s)-$(stat -c%Y $server_root/$server/*|sort|head -n1) > $maxage ))
# is an arithmetic comparision on the form
# a-b < c, where
#
# a: $(date +%s) is the number of seconds since
# EPOCH
#
# b: $(stat -c%Y $server_root/$server/*|sort|head -n1)
# can be split up into
# stat -c%Y $server_root/$server/*
# which gives the modification times of all the files
# in $server_root/$server/ as seconds since EPOCH
#
# they are then run through sort, which sort them
# and by default ascending, so the oldest file
# will be first in the output list
#
# the output from sort is then sent to head -n1
# which simply just outputs the first line of the
# input and then exits
#
# so b corresponds to the modification date in seconds
# since EPOCH of the oldest file in that particular
# directory
#
# c: c is the maximum age that a file is allowed
# without the server needing a new backup.
#
# so basically, in pseudo code it would be
#
# for each server
#   if filecount in server directory > 0 then
#       if current time - oldest file modification time > max allowed time
#           echo server, since at least one file is too old
#       endif
#   else
#       echo server, since there are no backups at all
#   endif
# endfor
#
# * there are probably better ways of doing this
# * this has not been checked to work with and is not
#   expected to work with servers with spaces or otherwise
#   funny stuff in their names.
```

---

### Post by Bodsda on 2011-12-01
Excellent entries so far, this challenge will be judged next weekend.

Bodsda
Ubuntu Beginners Team

---

### Post by Bodsda on 2011-12-10
This challenge will be judged tomorrow, unless anyone asks for an extension.

Happy Coding,
Bodsda
Ubuntu Beginners Team

---

### Post by epicoder on 2011-12-12
Hopefully I just managed to squeeze this in. Sorry if I'm late and messing this up... 

```
#!/usr/bin/env python3.2

import os, time
from sys import argv

SECONDS=60*60*24 # Seconds in a day

try:
    t=argv[1].lower()
    if t[-1]=="d": SECONDS*=int(t[:-1])
    elif t[-1]=="m": SECONDS=60*int(t[:-1])
    elif t[-1]=="h": SECONDS=60*60*int(t[:-1])
    elif t[-1]=="s": SECONDS=int(t[:-1])
    elif t[-1].isdigit(): SECONDS=int(t)
    else: raise ValueError
except IndexError: pass
except ValueError:
    print("Error - garbled time\n")
    print("Usage:", argv[0], "[time]")
    print("time:")
    print("    How old a file must be before it is considered out of date. 24 hours is default.")
    print("    A number, optionally followed by one of these case-insensitive suffixes:")
    print("        S: Seconds. This is used if there is no suffix.")
    print("        M: Minutes.")
    print("        H: Hours.")
    print("        D: Days.")
    exit(1)

outdated=[]
good=0

try:
    if os.name=="nt": # Essentially if windows:
        os.chdir(os.path.join(os.getenv("USERPROFILE"), "server_backups"))
    else: os.chdir(os.path.join(os.getenv("HOME"), "server_backups"))
except:
    print("Unable to find ~/server_backups. Using current directory")
    
subdirs=[]
for name in os.listdir("."): 
    if os.path.isdir(os.path.join(".", name)): subdirs.append(os.path.join(".", name))
    
for dir in subdirs:
    for file in os.listdir(dir):
        age=time.time()-os.stat(os.path.join(dir, file)).st_mtime
        if age > SECONDS:  # If current time - file modified time is greater than the number of seconds in a day
            outdated.append((age, dir)) # Age first, so I can sort them easily later
            break
    else: good+=1 # Break statement not hit: server is backed up.
    
print(good, "server(s) successfully backed up")
if outdated == []: print("All servers backed up"); exit(0)

outdated.sort()
outdated.reverse() # Sort by descending age

print("Outdated servers, in order of importance (oldest first):\n")
for age, dir in outdated: 
    print(os.path.basename(dir))
```Written in python 3.2, should work on most platforms and with python 3.x.
All cookie points are implemented. Cookie 1 is used sleep style, for instance "backup.py 3d" to change the time to 3 days.

---

### Post by Bodsda on 2011-12-13
This challenge has now been judged. There was a good mix of languages in these entries, and some very elegant solutions. In the end, it came down to features and logic. 

The winner is......

[SIZE=3]***[COLOR=Red]sh228[/COLOR]***[/SIZE]

With straight forward logic and all cookie points implemented, this entry was the most coplete. The added exception handling and in-line comments made this the winning entry. Congratulations.

The comment king award goes to red_Marvin, and the sexiest code badge is won by bgs100.

Well done to everyone who enterred. I look forward to seeing the next challenge.

Bodsda
Ubuntu Forums Beginners Team

---

### Post by epicoder on 2011-12-13
I wasn't really expecting to judged, much less win, after entering that late (sheepish grin) so I don't have another challenge prepared yet. I'll think on it and hopefully it'll be up sometime this week, Saturday at the latest. I'll put a link in the sticky when it's up.

---

