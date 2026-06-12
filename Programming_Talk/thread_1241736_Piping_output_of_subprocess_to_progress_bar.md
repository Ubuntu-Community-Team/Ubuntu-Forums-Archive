---
title: "Piping output of subprocess to progress bar"
date: 2009-08-16
forum: Programming Talk
---

### Post by Nevon on 2009-08-16
I'm using growisofs to burn an iso through my Python application. I have two classes in two different files; GUI() (main.py) and Boxblaze() (core.py). GUI() builds the window and handles all the events and stuff, and Boxblaze() has all the methods that GUI() calls.

Now when the user has selected the device to burn with, and the file to be burned, I need to call a method that calls the following command:`

```
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /burner/device=/full/path/to.iso
```

This command should give an output similar to this:

```
/dev/scd0: "Current Write Speed" is 2.5x1352KBps.
44719360/7835492352 ( 4.4%) @39.9x, remaining 2:10 RBU   0.0% UBU   0.0%
536346624/7835492352 ( 6.8%) @41.5x, remaining 2:02 RBU   0.0% UBU   0.0%
720568320/7835492352 ( 9.2%) @39.9x, remaining 2:08 RBU   0.0% UBU   0.0%
909049856/7835492352 (11.6%) @40.8x, remaining 2:01 RBU   0.0% UBU   0.0%
# ETC.
7798128640/7835492352 (99.5%) @3.8x, remaining 0:06 RBU 100.0% UBU  99.8%
7815495680/7835492352 (99.7%) @3.8x, remaining 0:03 RBU  59.7% UBU  99.8%
7832862720/7835492352 (100.0%) @3.8x, remaining 0:00 RBU   7.9% UBU  99.8%
builtin_dd: 3825936*2KB out @ average 3.9x1352KBps
/dev/burner: flushing cache
/dev/burner: closing track
/dev/burner: closing disc
```

This command is run via core.Burning.burn(), which looks like this:

```
class Burning(threading.Thread):
    def run(self, file, device):
        self.command = ["growisofs", "-use-the-force-luke=dao", "-use-the-force-luke=break:1913760", "-dvd-compat", "-speed=2", "-Z",  device +'='+ file]
        self.proc = subprocess.Popen(self.command,stdout=subprocess.PIPE)
        for line in self.proc.stdout.readlines():
            self.parseburn(line)
            
    def parseburn(self, output):
        self.re1='.*?'	# Non-greedy match on filler
        self.re2='([+-]?\\d*\\.\\d+)(?![-+0-9\\.])'	# Float 1

        self.rg = self.re.compile(re1+re2,re.IGNORECASE|re.DOTALL)
        self.m = self.rg.search(output)
        if self.m:
            self.float1 = self.m.group(1)
            print "("+self.float1+")"+"\n"
```

Now my questions are the following:

[LIST=1][*]How can I get the progress from the output (the percentage in brackets) and have my progress bar be set to "follow" that progress? My progress bar is called in the GUI() class, as such:

```
get = builder.get_object
self.progress_window = get("progressWindow") 
self.progressbar = get("progressbar")
```

As you can see, I'm trying to get the output of the command and parse it through my regular expression and then print it (eventually I'll send it to the progress bar, but for now I just want to see if I can catch it).

[*]Do I have to run this command in a separate thread in order for the GUI to remain responsive (so that I can update the progress bar and allow the user to cancel the burn if they want to)? As you can see, that's what I'm trying to do currently. But I'm not sure if I'm doing it right.[/LIST]

The full code is available on Launchpad if you are interested. If you have bazaar installed, just run:

bzr branch lp:boxblaze

Oh, and in case you were wondering, this application is only meant to work in Linux - so don't worry about cross-platform compatibility.

This question is also up on stackoverflow, where I have recieved some answers - but I haven't been able to make use of them properly. Here's the link: [http://stackoverflow.com/questions/1284196/piping-output-of-subprocess-call-to-progress-bar](http://stackoverflow.com/questions/1284196/piping-output-of-subprocess-call-to-progress-bar)

---

