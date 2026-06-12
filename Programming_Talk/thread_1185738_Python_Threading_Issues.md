---
title: "Python Threading Issues"
date: 2009-06-12
forum: Programming Talk
---

### Post by cmat on 2009-06-12
I'm working on a program that stacks images using PIL. I made a GUI with wxPython. The operation is done in a thread so it doesn't lock up the GUI and allows the user to cancel the operation at any time. The problem I'm having is with the behaviour of the thread interacting with the GUI. I have code in the thread updates a progress bar on my frame, it doesn't work. Also there is a long delay when the file is being saved that locks the GUI. The reset tool bar function takes a good few seconds to kick in.

In general, how do I make the progress bar work properly? and how do I prevent the file save operation from locking my GUI? and more importantly how can I maintain clear communication between the thread and my GUI? 

```
class LayerImages( threading.Thread ):

    def __init__ ( self, parent, paths ):
        self.paths = paths
        self.parent = parent # Pointer to parent object
        print self.parent
        threading.Thread.__init__ ( self )
        self.abort = False
    
    def run( self ):
        # Create a blank image with the same properties of the images to be
        # stacked.
        baseImage = Image.open( self.paths[0] )
        average = Image.new("RGB", baseImage.size, "black")
        
        i = 0
        
        while i < len( self.paths ) and not self.abort:
            print("Stacking image " + str(i + 1) + " of " + str(len( self.paths )))
            im = Image.open( self.paths[i] )
            
            alpha = 1.0 / ( i + 1 ) 
            average = Image.blend(average, im, alpha)
            
            i += 1
        
        average.save("/home/cmat/Desktop/TEST.png", "PNG")
        
        print("OPERATION COMPLETE")
        
        self.parent.ResetToolBar()

    def abortThread ( self ):
        self.abort = not self.abort
```

Right now I'm just using print to give information about the status of the operation.

---

### Post by slavik on 2009-06-12
there is never a time when two threads in Python are being simultaneously executed.

---

### Post by soltanis on 2009-06-13
I thought Python started using posix threads on Linux (hence, yes, two threads can be executing at once, on a multi-core system)

---

### Post by kripkenstein on 2009-06-13
Yes and no. Python uses threads, but it also has the GIL, which prevents two threads from accessing Python at once (two threads can run at once, if they are *not* accessing Python - like if they are executing code inside a Python extension module written in C).

However, this shouldn't be an issue, as the Python runtime will switch between threads, giving the illusion of parallel execution of threads (but without the performance ;)

I'm not familiar with wxPython, but I am guessing the reason this doesn't work as you want is something to do with wxPython.

---

### Post by cmat on 2009-06-13
wxPython has something called "delayedResult" which allows the execution of code and prevents the GUI from freezing. Didn't work so I wrote my own thread for the algorithm and it ended up giving me the same problems.

---

