---
title: "Two noobish python programming questions"
date: 2011-01-08
forum: Programming Talk
---

### Post by piwacet on 2011-01-08
Hi.  I'm trying to write a simple multi-threaded  application, where I create a class that inherits from the Threading  class.  I'm confused on two points: 
 
1.)  Each time I create a thread (instance of the aforementioned class),  is the scope of the local variables isolated to each individual thread?   In other words, my class's run() method contains statements such as  'for item in list' - I don't want one thread's 'item' variable getting  confused with another threads 'item' variable.  I want 'item' to be  strictly local to the individual thread (class instance).  The  alternative is to define 'self.item' in the __init__ method, and use  that instead, but that becomes cumbersome for a complicated run()  method. 
 
2.) Can the __init__ method of a class actually define it's own local  functions to be used only during the __init__ method?  I've defined a  class whose __init__ method actually defines some instance variables by  reading data out of a file, and the __init__ method has defined brief  routines for reading lines from a file: 
 
```
class Backup_Filesystem_File_Data: 
        def  __init__( self, path, file ): 
                self.metadata_path_and_file_name = os.path.join(path, file) 
                self.string = '' 
 
                def read_line_of_metadata_file(): 
                        try: 
                                self.string = fd.readline().rstrip('\n') 
                        except: 
                                return 'UNKNOWN' 
                        return self.string 
 
                self.file_md5sum = read_line_of_metadata_file()
```Instances of this class are created simultaneously by multiple threads,  and again, I'm hoping the the file descriptor 'fd' stays local to each  instance. 
 
I've actually tried all of this, and it seems to be working, but I'd hate to get bit later if I've made a mistake. 
 
Thanks in adavance!

---

### Post by unknownPoster on 2011-01-09
As far as your first question is concerned, threads share the same memory. In order to prevent deadlocks or race-conditions you may want to look into implementing locks for your threads. If I remember correctly the python Threading module already has a lock data-type along with functions for locking and releasing.

I'm not sure that I completely understand your second question so I'll let someone else look into that.

---

### Post by The Cog on 2011-01-09
Yes and yes.

1: 
An instance's local variables are distinct from other instance's local variables. If you are multithreading, you should be careful about letting other threads get hold of these variables - if you store a loop counter in this.loopcounter for instance, it could then be used by another thread that has a reference to the insance by reading instance.loopcounter. 

But you seem to have a good handle on the problem. So yes, for item in list gives you a new item variable, distinct from any other threads running the same code.

2:
Nested definitions do seem to work in python, just as you describe. I wasn't aware of the possibility until recently, but it is legitimate.

---

### Post by piwacet on 2011-01-10
Thanks everyone!  Appreciate your time.

---

