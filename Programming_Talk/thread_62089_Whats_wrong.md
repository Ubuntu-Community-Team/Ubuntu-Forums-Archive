---
title: "Whats wrong ?"
date: 2005-09-03
forum: Programming Talk
---

### Post by Drakx on 2005-09-03
Hi guys

i have been stopped dead in my tracks the following code looks fine to me but still i get the errors

```
Traceback (most recent call last): 
   File "quickrip.py", line 61, in ? 
     main(sys.argv[1:]) 
   File "quickrip.py", line 56, in main 
     cli.main() 
   File "cli/cli.py", line 430, in main 
     cli.switch('front') 
   File "cli/cli.py", line 44, in switch 
     self.front() 
   File "cli/cli.py", line 68, in front 
     self.scanDVD() 
   File "/home/drakx/quickrip-0.9-alpha/quickrip-0.9-alpha/base.py", line 197, in scanDVD 
     self.raw_dvd = mmpython.parse(self.config['dvd_device']) 
 NameError: global name 'mmpython' is not defined
``` 

here is the code snippets 
 
line 61: 

```
# The famous __name__ + __main__ trick... 
 if __name__ == '__main__': 
  main(sys.argv[1:])
``` 

line 56:

```
# Fallback to CLI mode... 
  sys.path.append("cli") 
  import cli 
  cli.main() 
  sys.exit(2)
``` 

File "cli/cli.py", line 430

```
def main(): 
  #print "QuickRip v0.6, (C) Tom Chance, 2003" 
  print "%s v%s, %s\n" % (__app__, __version__, __copyright__) 
  cli = CLI() 
  cli.switch('front')
``` 

File "cli/cli.py", line 44: 

```
def switch(self, mode, title=1): 
   """send user into various modes (entry, toplevel, title)""" 
   os.system("clear") 
   print output.bold("%s v%s, %s\n" % (__app__, __version__, __copyright__)) 
   if mode == 'front': 
    self.level = 'front' 
    self.front() 
   elif mode == 'toplevel': 
    self.level = 'toplevel' 
    self.toplevel() 
   elif mode == 'title': 
    self.level = 'title' 
    self.showTitle(title) 
   elif mode == 'configure': 
    self.level = 'configure' 
    self.configure() 
   elif mode == 'rip': 
    self.level = 'ripping' 
    self.ripScreen()
``` 

File "cli/cli.py", line 68:

```
def front(self): 
   """show the front screen""" 
   print output.bold("\nHit enter to scan DVD") 
   try: 
    null = raw_input() 
    del null 
   except KeyboardInterrupt: 
    print output.bold("\n\nExiting...") 
    sys.exit(2) 
   self.scanDVD() 
   self.switch("toplevel"
``` 

base.py", line 197: 

```
# The following functions are threaded, but are processed in the order 
  # in which they appear here. - biggs 
  def scanDVD(self): 
   """Scan the DVD and build up a data structure for the titles""" 
   self.notify_startScanning() 
   self.titles = [] 
   self.numtitles = 0 
 
   # Reset values to default (in case user scans two different discs in same session) 
   self.raw_dvd = mmpython.parse(self.config['dvd_device']) 
   
   # If there aren't any titles... 
   if self.raw_dvd.tracks == []: 
    self.notify_noTitles()
``` 

The above code is the whole section instead of just the line in hope some one more skilled than i can spot the problem right out :S from what i can see every thing is fine, now im not a big python expert but for pice of mind python is backwards compatable ?

Sorry for beeing a pest but i think ive found some thing i can learn from and bring back life

---

### Post by thumper on 2005-09-03
[QUOTE=Drakx]base.py", line 197: 

```
# The following functions are threaded, but are processed in the order 
  # in which they appear here. - biggs 
  def scanDVD(self): 
   """Scan the DVD and build up a data structure for the titles""" 
   self.notify_startScanning() 
   self.titles = [] 
   self.numtitles = 0 
 
   # Reset values to default (in case user scans two different discs in same session) 
   self.raw_dvd = mmpython.parse(self.config['dvd_device']) 
   
   # If there aren't any titles... 
   if self.raw_dvd.tracks == []: 
    self.notify_noTitles()
``` 
[/QUOTE]
The problem is on the last line of the exception stack trace.
```
self.raw_dvd = mmpython.parse(self.config['dvd_device']) 
```
Notice that mmpython is not passed in as a parameter to the function.  Python then looks for a local variable, but that is not there, so then it looks for a global variable.  Unfortunately can't see the whole file, but my guess is that mmpython should be a module, and perhaps it is not being imported, or this code was cut and paste from somewhere else where mmpython was a variable that was passed in.

HTH.

---

### Post by Drakx on 2005-09-03
[QUOTE=thumper]The problem is on the last line of the exception stack trace.
```
self.raw_dvd = mmpython.parse(self.config['dvd_device']) 
```
Notice that mmpython is not passed in as a parameter to the function.  Python then looks for a local variable, but that is not there, so then it looks for a global variable.  Unfortunately can't see the whole file, but my guess is that mmpython should be a module, and perhaps it is not being imported, or this code was cut and paste from somewhere else where mmpython was a variable that was passed in.

HTH.[/QUOTE]
 I hear you but im at a dead end every thing i try seems to go wrong all because of 

```

self.raw_dvd = mmpython.parse(self.config['dvd_device'])
```

so as a result here is the whole file where the above code is stated

EDIT : Took out code

any help you can give will be great

---

### Post by Drakx on 2005-09-04
I fixed the above mmpython error infact i got it working last night came to try it again and its stopped working arr 

this is the error

```

self.notify_dispDVD(self.raw_dvd.label, len(self.raw_dvd.tracks))
AttributeError: DVDInfo instance has no attribute 'label'
```

```

self.notify_dispDVD(self.raw_dvd.label, len(self.raw_dvd.tracks))  # throwing problems here was working but not now ??
  
  for t in self.raw_dvd.tracks:
   title = {}
   title['rip'] = 'no'
   title['id'] = t['trackno']
   title['name'] = ''.join([self.raw_dvd.label, '-', str(t['trackno'])])
   title['size'] = 680.0
   title['vbr'] = float(min(4000, self.calcRate(int(t['length']), 96, 680.0)))
   title['abr'] = 128
   title['length'] = t['length']
   l = float(t['length'])
   if float(l/60) > (float(int(l/60)) + 0.5):
    timelabel = (t['length'] / 60) + 1
   else:
    timelabel = (t['length'] / 60)
   title['timelabel'] = "%s mins" % (timelabel)
   title['alang'] = 'en'
   title['slang'] = 'None'
   title['alangs'] = []
   for a in t['audio']:
    title['alangs'].append(a['language'])
   title['slangs'] = ['None']
   for sl in t['subtitles']:
    title['slangs'].append(sl)
   self.titles.append(title)
   self.notify_dispTitle(title)
   
  self.notify_finishScanning()
```

but looking through i see

```

def notify_dispDVD(self, **label**, numtitles):
  pass
```

I did have all this working last night but must have forgotten to save durrr :( now i cannot remember what i did

thanks for the help

---

### Post by Drakx on 2005-09-04
Hi guys

OK im going mad i ran a previous version of the project ok ? then i reran the version (cvs) that ive been working on and no errors nothing it just works can any one give an idea as why one minute it works the next it dont then it does ?


thanks

---

