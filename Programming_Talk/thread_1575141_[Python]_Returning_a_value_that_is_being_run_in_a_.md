---
title: "[Python] Returning a value that is being run in a Thread"
date: 2010-09-15
forum: Programming Talk
---

### Post by Pyro.699 on 2010-09-15
Hello, so heres a script ill use to help explain my problem ^^

Firstly, i have modified the Thread function of python, to give myself the ability to forcefully terminate a Thread; among other features.

Thread.py
[php]
import sys, trace, threading 
 
class Thread(threading.Thread): 
    def __init__(self, *args, **keywords): 
        threading.Thread.__init__(self, *args, **keywords) 
        self.killed = False 
     
    def setTimer(self, x): 
        self.t = threading.Timer(x, self.kill) 
        self.t.start() 
     
    def start(self): 
        self.__run_backup = self.run 
        self.run = self.__run 
        threading.Thread.start(self) 
         
    def __run(self): 
        sys.settrace(self.globaltrace) 
        self.__run_backup() 
        self.run = self.__run_backup 
     
    def globaltrace(self, frame, why, arg): 
        if why == 'call': 
            return self.localtrace 
        else: 
            return None 
             
     
    def localtrace(self, frame, why, arg): 
        if self.killed: 
            if why == 'line': 
                raise SystemExit() 
            return self.localtrace 
     
    def kill(self): 
        self.killed = True
[/php]Now, using that as my "Thread" module i have this other snippet of code

[php]
import threading, time, random
class Foo(threading.Thread):
    def __init__(self):
        threading.Thread.__init__(self)
        self.daemon = True
        self.toDo = []
        self.threads = []
        
    def run(self):
        while 1:
            if len(self.toDo) != 0:
                self.threads.append( Thread(target=self.toDo.pop(0)) )
                self.threads[-1].start()
                
                self.threads[-1].setTimer( 10 )
                
            for x in xrange(len(self.threads)):
                if not self.threads[x].isAlive():
                    print "Thread Done, Final Value: %i"%THE_VALUE_OF_Y
                    self.threads.pop(x)
                    break
            time.sleep(0.5)
                
    def add(self, target):
        self.toDo.append( target )
        
def Bar():
    y = 0
    for x in xrange(20):
        time.sleep( random.randrange(5,50) / 10.0 )
        y += random.randrange(0,100)
        
    return y
    
A = Foo()
A.start()

A.add( Bar )

print "Finished\n"
while 1: continue
[/php]As you can see the thread will terminate ***Bar()*** before it has a chance to finish its task. But I am still interested in how far it got; what is the best way for me to figure out what that value "Y" was.

This setup may seem a bit strange, but in its real environment it makes everything much easier. I would be more than happy to provide any other information that may help us come to a solution.

Thanks
~Cody Woolaver

[EDIT]
Something i forgot to mention; i was able to get the value IF the script was able to finish. I did this by modifying Thread.py to include this

(placed at the end of Thread.localtrace)
[php]
if why == 'return' and isinstance(arg, str): 
            self.returnVal = arg
[/php]

Then simply created a "get return value" function and called it from "***Foo()***"

---

### Post by Pyro.699 on 2010-09-15
So, ive done a bit of research and found this neat site. 

[http://www.doughellmann.com/PyMOTW/threading/](http://www.doughellmann.com/PyMOTW/threading/)

It has quite a few unique examples of how to use the threading module. I think what im looking for is [here](http://www.doughellmann.com/PyMOTW/threading/#controlling-concurrent-access-to-resources-with-a-semaphore) but i would still like someone who knows more than me to give me push in the right direction... Again, any help is useful :)

Thanks
~Cody

---

### Post by The Cog on 2010-09-16
In your Bar() loop, you are keeping y private. I think you should get Bar() to save the value somewhere that it can be found. Maybe pass Bar a List to store the value in. Then if you retain a reference to that list yourself, you can "look in the box" any time you want. Of course, there might be concurrency issues, if you look in the box at the same time that Bar() is modifying the contents, so you should also pass Bar a lock that it should use to prevent concurrent access. ```
def Bar(box, lock):
    y = 0
    for x in xrange(20):
        time.sleep( random.randrange(5,50) / 10.0 )
        lock.acquire()
        box[0] += random.randrange(0,100)
        lock.release()
```In fact it would make sense to put the lock in the box next to y. Then when you want to check the y value of a box, just acquire its lock, read y, then release the lock again.

Your code may not be thread safe. The loop that reads the toDo list is running on a different thread to the loop that appends new jobs. This could lead to concurrent list modification by two different threads, which is a big no-no. Even if the Global Interpreter Lock makes sure that concurrent modification cannot happen in the current implementation of cpython, it could happen in future implementations, or if the code ran in other environments such as jython or iron python. You should really use a lock to guard against this by (once again) acquiring the lock before ever appending to the toDo list, and before ever reading from the list.

---

### Post by Pyro.699 on 2010-09-16
Hey, thanks for the reply.

Ill work on including that in my program in a bit but maybe my production code would be a bit different... Here's the layout...

Folder Setup:
```

./src/Plugins/__init__.py
./src/Plugins/a___.py
  <59 other files>
./src/Plugins/z___.py
./src/Logs/
  <a bunch of log files>
./src/MyRunner.py
./src/SeperateFunctions.py
./src/MoreFiles.py
./src/Thread.py

```Each of the files in *./src/Plugins/* contain the same function called **runTask(gbl)** and all have this as a starting line.
[php]
for item in gbl:
    exec("global %s; %s = gbl['%s']" % (item, item, item))
[/php]gbl is passed to the function through *./src/MyRunner.py* and is **globals()**

To run the function from *./src/MyRunner.py* i run this code
[php]
exec("from Functions import %s as taskMod"%pluginName)
self.nowRunning[-1] = Thread(target=taskMod.runTask, args=[globals()])
[/php]Im very aware this is horrible code practice and am actually quite embarassed to have it like this; especially the **exec** part.

All of the functions in *./src/Plugins/* fall under two categories:
```

Will run and stop on its own
Will run indefinitely until forcefully quit

```What im trying to do is get the response's from each of the functions and display them on the screen via *./src/MyRunner.py*. When the code is able to stop on its own, it uses **return** but in the case of the ones that do not stop on their own i was hoping to set a variable as a temporary return value that will be constantly be over written until it is time to exit the thread. When **Thread.kill** is called, before the kill variable is set to true, it would retrieve the variable and store it locally.

Is there something that i could do to *./src/Thread.py* so that i would be able to call:
[php]
self.nowRunning[-1].getRetVal()
[/php]
I will definitely look more into threading.Lock

Thanks a ton :)
~Cody Woolaver

---

### Post by The Cog on 2010-09-16
You can't get a return value from a function until it returns. And all the variables it uses while it is thinking are private to it. If you want to be able to see its progress, I really think you need its cooperation and you need it to write progress information somewhere public - somewhere global or in a container that you give the function. 

Beware that if you kill a thread while it holds a lock, your entire program might freeze because everybody else is waiting for the lock to be released again. You should look at getting your functions to periodically check a flag somewhere that tells them it's time to quit, please. It might make sense to do that at the same time as they update their progress indicator.

---

### Post by Pyro.699 on 2010-09-18
Hey,

So ive added the features you described in [Post #3](http://ubuntuforums.org/showpost.php?p=9852555&postcount=3) and it does work; at times.

What ive done is passed a variable *self.box* which is a dictionary containing the names of all of the scripts. Its default value is a string set to *"< None >"*, in the script that is being run where a return was originally, i have replaced it with this:
```

box['funcName'] = "Some Return Value"
return

```

Sometimes the script will return its proper value, and other times it wont change. The cause of this is completely unknown to me.

On a slightly other note id like to comment on some of the stuff i said in [Post #4](http://ubuntuforums.org/showpost.php?p=9852555&postcount=4). Am i going about this the right way? The setup sounds pretty generic; Basically a single script that has plugins that it is able to run and all of those plugins has access to functions and variables that are defined in the main script.  Basically, what would the most "code safe" way to do this (by which i mean easiest to implement and add new scripts with little to add to each script; it is a pain to alter 60 some files every time i need to alter the way the scripts are run).

Thanks
~Cody

---

### Post by StephenF on 2010-09-18
> **Pyro.699 said:**
> 
To run the function from *./src/MyRunner.py* i run this code
[php]
exec("from Functions import %s as taskMod"%pluginName)
self.nowRunning[-1] = Thread(target=taskMod.runTask, args=[globals()])
[/php]Im very aware this is horrible code practice and am actually quite embarassed to have it like this; especially the **exec** part.

[php]
def obtain_module_object(name):
    module, object = name.rsplit('.', 1)
    return getattr(__import__(module), object)
[/php]
Usage example
[php]
print obtain_module_object('os.path.listdir')('/dev')
[/php]

---

