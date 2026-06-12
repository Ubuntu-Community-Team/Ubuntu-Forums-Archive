---
title: "Redirect output-stream from command in Python"
date: 2012-07-24
forum: Programming Talk
---

### Post by DarkAmbient on 2012-07-24
Hi!

Building a GUI / Quickly project manager.. Trying to read the output of a sub-process (in real-time). I've manage sort of, but the output doesn't show until after the process has been terminated.

How can I manage this but in real-time? This is my code, I've shorten it down to the essential parts...


Output.py
```
    def run_and_get(self, *args):

        try:

            # spawn a new process, connect to its output and error pipes        
            pipe = Popen(args, stdout=PIPE, stderr=PIPE)
        
            # print the output lines as they happen
            while True:
                
                self.enditer = self.textbuffer.get_end_iter()
                
                stdout = pipe.stdout.readline()
                stderr = pipe.stderr.readline()
                
                if not stdout and not stderr:
                    break
                else:
                    if stdout:
                        self.textbuffer.insert(self.enditer, stdout)
                    if stderr:
                        self.textbuffer.insert(self.enditer, stderr)
                    
        except OSError as e:
            print "Popen OSError: " + str(e) + ", arguments: " + str(args)
        except ValueError as e:
            print "POpen ValueError: " + str(e) + ", arguments: " + str(args)
```

Window.py
```
    def __init__(self):
        self.appoutput = Output()
        self.appoutput.set_textview_destination(self.tvoutput)
        self.x = self.appoutput.run_and_get

    # run command
    def on_brun_clicked(self, widget):
        self.x('quickly', 'run')

```

---

### Post by spjackson on 2012-07-24
Output to a pipe is buffered by default. You need to force the program you are calling to unbuffer its output. Since 'quickly' is a python script, you can use 'python -u' - but check the man page because this flag has other implications.

So instead of calling 'quickly run', you need 'python -u /usr/bin/quickly run'.

---

### Post by DarkAmbient on 2012-08-03
> **spjackson said:**
> Output to a pipe is buffered by default. You need to force the program you are calling to unbuffer its output. Since 'quickly' is a python script, you can use 'python -u' - but check the man page because this flag has other implications.

So instead of calling 'quickly run', you need 'python -u /usr/bin/quickly run'.

Hiya! Thanks for you response, and sorry for the time taken to reply, been busy lately. 

I've tried your suggestion calling "python -u /usr/bin/quickly run". I'm sorry to say it made no difference.. been trying some new ways today to solve this... all with the same result, ie. output comes after main-app closes... no matter if it's within a console or to some textview-buffer. 

Read up some on multithreading... been trying my way forth.. this is what I got so far. The class Processor creates 2 new threads, Writer and Reader. Writer read lines from the subprocess's stdout and put it in a queue, Reader reads the Queue and discard the job/item/line (if i got it right?). Might point out that I'm not sure I got everything right.. Don't quite understand threading w/ conditions just yet. So I would be thrilled if I could get a pointer or two! :)

In mainfile i call this:

```
self.processor = Processor(self.tvbuffer) # provide buf to print too
self.processor.run(['python', '-u', '/usr/bin/quickly', 'run'])
```

And this is the Processor-file and it's 3 classes. The Processorclass is furthest down:

EDIT: I've split up the classes into 3 codeblocks over here so it will be easier to read.

Writer:
```
#!/usr/bin/env python -u

class Writer(threading.Thread):
    """
    Stacks the queue
    """

    def __init__(self, condition, output, queue):
        """Constructor.

        @param condition condition synchronization object
        @param output stdout from subprocess invoked in Processor
        @param queue thread stacks queue with lines read from output
        """
        
        threading.Thread.__init__(self)
        self.condition = condition
        self.output = output
        self.queue = queue
    
    def run(self):
        """Thread run method"""
        
        while True:
            
            for line in self.output:
                self.queue.put(line)
            
            if self.queue.qsize() > 0:
                self.condition.acquire()
                print 'condition acquired by %s' % self.name
                print 'condition notified by %s' % self.name
                self.condition.notify()
                print 'condition released by %s' % self.name
                self.condition.release()
            else:
                print "queue is empty"
                
            time.sleep(1)
```

Reader:
```
class Reader(threading.Thread):
    """Read from queue"""

    def __init__(self, condition, queue, textbuf):
        """
        Constructor.

        @param condition condition synchronization object
        @queue the output-queue
        @textbuf textview's buffer, will print output to this
        """
        threading.Thread.__init__(self)
        self.condition = condition
        self.queue = queue
        self.textbuf = textbuf
    
    def run(self):
        """Thread run method"""
        
        while True:
            self.condition.acquire()
            print 'condition acquired by %s' % self.name
            while True:
                
                try:
                    line = self.queue.get(timeout=.2) # timeout in seconds on get
                except Queue.Empty:
                    break
                else:
                    #line = self.queue.get_nowait() # same as .get(False)

                    # test-print the current line...
                    print "line is " + line

                    #self.textbuf.insert(self.textbuf.get_end_iter(), line)

                    self.queue.task_done()
                    
                break
                print 'condition wait by %s' % self.name
                self.condition.wait()
                
            print 'condition released by %s' % self.name
            self.condition.release()
```

Processor:
```
class Processor:

    def __init__(self, textbuffer):
        '''Constructor
        
        @textbuffer the buffer where the output will get to in time..
        '''
        self.buf = textbuffer
    
    def run(self, cmd):
        '''
        invoking this then a subprocess is initiated using the provided cmd
        
        @cmd a tuple with the command to be called via a freshly baked subprocess
        '''
        
        p = subprocess.Popen(cmd, 
                             stdout = subprocess.PIPE, 
                             stderr = subprocess.STDOUT, # merge
                             bufsize = 1, # I see no different between 0 or 1 
                             close_fds = 'posix' in sys.builtin_module_names)

        con = threading.Condition()
        que = Queue.Queue()
        
        t1 = Writer(con, p.stdout, que)
        t2 = Reader(con, que, self.buf)
        
        t1.name = "Writer"
        t2.name = "Reader"

        t1.daemon = True
        t2.daemon = True
        
        t1.start()
        t2.start()
        
        # by using join the main-app freeze...
        # by not using join, output show after main-app is finished, hmm
        #t1.join()
        #t2.join()
        
        del t1, t2
```


If you check furthest down in the provided code.. the t1/t2.join calls.. I'm not sure what they mean entirely. Ive commented on what happens when i Use them vs not using them.

---

