---
title: "[SOLVED] buggy getopt in python"
date: 2008-01-01
forum: Programming Talk
---

### Post by Spr0k3t on 2008-01-01
I'm a bit of a python newbie, but I'm not new to development.  I'm following many of the online examples on building this emelent of my main() definition.  The problem however, I can't seem to capture anything but the args of "-a *" or "-h".  This is a very generic framework and logic shows it should work.

The other problem with this, it should loop through every option argument pair.  It seems once it hits a valid option, it will not continue on to the next option pair.

Suggestions on what I'm doing wrong here.  Thanks!

```
#!/usr/bin/python
import sys, getopt

def main():
    try:
        opts, args = getopt.getopt(sys.argv[1:], "ctla:h", ["channel", "track", "longname", "artist"])
    except getopt.GetoptError:
        usage()
        sys.exit(2)
    output = ""
    for opt, arg in opts:
        if opt in ("-c", "--channel"):
            channel = arg
            output += channel
        if opt in ("-t", "--track"):
            track = arg
            output += track
        if opt in ("-l", "--longname"):
            longname = arg
            output += longname
        if opt in ("-a", "--artist"):
            artist = arg
            output += artist
        if opt == "-h":
            usage()
            sys.exit()

    print output

def usage():
    print "arg.py [-c][-t][-l][-a]\nArgs: " + str(sys.argv[1:])

if __name__ == "__main__":
    main()
```

---

### Post by Spr0k3t on 2008-01-03
I was able to resolve the issue.  Turns out I overlooked the requirements of ":" and "=" in the getopt methods.

```
opts, args = getopt.getopt(sys.argv[1:], "c:t:l:a:h", ["channel=", "track=", "longname=", "artist="])
```

Added this and it worked like a charm.  Updated post so anyone else with the same problem would get the help they need.

---

