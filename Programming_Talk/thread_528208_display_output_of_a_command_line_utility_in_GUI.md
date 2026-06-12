---
title: "display output of a command line utility in GUI"
date: 2007-08-17
forum: Programming Talk
---

### Post by NeillHog on 2007-08-17
The problem in a nutshell &#8211; I am writing a GUI wrapper for a command line utility (GPSBabel) and want to show the output of the command line on an error. I am a very inexperienced Python programmer.

Calling the program from the command line as follows
   ```
neill@NeillsPC:$ gpsbabel -igarmin -f/dev/ttyS1 -o zzz -F/home/neill/temp
```
produces the following output to the screen
[I][ERROR] GPS_Packet_Read: Timeout.  No data received.
GARMIN:Can't init /dev/ttyS1[/I]
This is what I would like to show the user of the GUI but I can find no way of doing so.

I though that sending the output to the file would be a good start. From the command line I changed the command to 
```
gpsbabel -igarmin -f/dev/ttyS1 -o zzz -F/home/neill/temp > /home/neill/temp/err.log  2>&1
```
which sent everything to the file err.log as expected.

In my program I call GPSBabel with
```
result = os.spawnlp(os.P_WAIT, 'gpsbabel', 'gpsbabel', dataString, inputFormatStr, inputFileStr, outputFormatStr, outputFileStr)
```
and can not see how to change that to be the same as my command line option.

I also tried 
```
import sys
saveout = sys.stdout 
fsock = open('out.log', 'w')
sys.stdout = fsock
```
with stdout and stderr before calling the spawn.

Now I am stumped. Please help me some one even if only by telling me that it is impossible.

Thanks!
Neill

---

### Post by strider1551 on 2007-08-17
> I want to show the output of the command line on an error.

Personally, I prefer to use the [subprocess]("http://docs.python.org/lib/module-subprocess.html") module.

```

import subprocess
process = subprocess.Popen("your command here", shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE, stdin=subprocess.PIPE, bufsize=0)
print process.stdout.read()
print process.stderr.read()

```

---

### Post by NeillHog on 2007-08-17
Thank you for that.
I just had a quick look at the code and it looks complicated.
I will get back to you in a few hours/days once I have worked out what I need to do.
As I said "thanks"

Neill!

---

### Post by NeillHog on 2007-08-17
It works :-)

```
# the command line to call
progString = 'gpsbabel ' + dataString + inputFormatStr + ' ' + inputFileStr + ' ' + \
outputFormatStr + ' ' + outputFileStr				
# Information what we are calling
self.textEditInfo.append('Command: ' + progString + '\n')
# Call GPSBabel
extProcess = subprocess.Popen(progString, shell=True, stderr=subprocess.PIPE)
#  and read any errors
errStr = extProcess.stderr.read()
self.textEditInfo.append('GPSBabel says: ' + errStr + '\n')
```

Thank you so much for your simple but very effective tip.
I found spawn starnge but subprocess acted exactly as I expected.

What held me up for an hour was that all the little strings that go to make up progString are input from lineEdits and I was using lineEdit.text() which would not work - lineEdit.text().ascii() would though.

Thanks!
Neill

---

