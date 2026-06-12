---
title: "Problem with Python Callback Timer Class"
date: 2009-11-01
forum: Programming Talk
---

### Post by briansykes on 2009-11-01
Hi there, i'm receiving an error from python when i try to use a callback timer class i get the TypeError: 'module' object is not callable,  The class is below along with the callback function it's supposed to call and the main function.

ttimer class:
```
class ttimer():
  
  def __init__(self, interval, retry, cbfunc, cbparam=[]):
    self.is_start=False
    self.is_end=False
    
    # doing my thread stuff now.
    thread.start_new_thread(self._callback,(interval,retry,cbfunc,cbparam,))
    
  def Start(self):
    self.mytime=time.time()
    self.is_start=True
    self.is_end=False
    
  def Stop(self):
    self.mytime=time.time()
    self.is_start=False
    self.is_end=True
      
  def IsStop(self):
    if self.is_end:
      return True
    else:
      return False
            
  def _callback(self,interval,retry,cbfunc,cbparam=[]):
    """ This is the private thread loop, call start() to start the threading timer."""
    self.retry=retry
    retry=0
    
    if self.is_end:
      return None
      
      while True:
        if self.is_end:
          break
        if self.retry==-1:
          pass
        elif retry>=self.retry:
          break
            
        if self.is_start:
          #check time
          tmptime=time.time()
          if tmptime >=(self.mytime + interval):
            cbfunc(cbparam) # callback your function
            self.mytime=time.time()
            retry+=1
          else:
            pass
        time.sleep(0.01)
            
    self.is_end=True

```

dummy_cb and main:
```
def dummy_cbf(param=[]):
  print "hello %-12s %s" % (param[0], time.strftime("%H:%M:%S"))
    

def main(argv=None):
  print "Enter quit to exit"
  timer  =ttimer (0.5, 5, dummy_cbf, ["linux"])
  timer.Start()
  
  while 1:
    time.sleep(0.001)
    cmd=raw_input()
    if cmd=="quit":
      timer.Stop()
      if timer.IsStop():
        sys.exit(0)
    else:
      print "Enter quit to exit"
```

The interpreter says its on this line in the main function:

```
timer  =ttimer (0.5, 5, dummy_cbf, ["linux"])
```

---

### Post by dwhitney67 on 2009-11-01
I do not get any errors when I run your (incomplete) code.

However, I did not get the desired effect because of a bug, that apparently stems from Pythons idiotic indentation policies.

```

  def _callback(self,interval,retry,cbfunc,cbparam=[]):
    ...
    if self.is_end:
      return None

      while True:
        if self.is_end:
          break
        if self.retry==-1:
          pass
        ...

```
Note how the while-loop is part of the if-block.  I bet that is not what you wanted.

P.S.  In the future, please post complete code.  That means, include all statements necessary for the program to run.

---

