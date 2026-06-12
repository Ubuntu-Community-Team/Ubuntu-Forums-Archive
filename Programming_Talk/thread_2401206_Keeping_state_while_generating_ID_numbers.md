---
title: "Keeping state while generating ID numbers"
date: 2018-09-15
forum: Programming Talk
---

### Post by trilobite2 on 2018-09-15
Hi all - 

 I have a Python coding question.  I want to generate consecutive "ID numbers" - this is for a "toy scheduler" that will schedule jobs to be run. 

Anyway, here's the code that I've written so far -  
```
 

#  toysched - a "toy" job scheduler. 
#  Author - mooseman 
#  This code is released to the public domain. 
#  "Share and enjoy...... :) "  


import datetime, itertools


# Helper function to generate job IDs 
def makeid():
  num = 0
  yield num
  num += 1
      

# Scheduler class. This holds jobs
class scheduler:
  def __init__(self):
    self.scheduledict = {}
    
  def add(self, job):
    self.scheduledict.update({job.jobid: job.detailslist})
    
  def update(self, id, dict):
    if id in scheduledict:
      scheduledict.update(dict)
    else:
      print "That jobid is not in the schedule."                                    
              
  def remove(self, id):
    if id in scheduledict:
      del scheduledict[id]
    else:
      print "That jobid is not in the schedule."                                                            
    
  def show(self):
    #print [ k,v for (k,v) in self.scheduledict ]    
    print list(self.scheduledict.viewitems())  
               

#  A job class 
class job():
  def __init__(self):
    self.nextid = makeid().next()   
    self.jobdict = {}      
    self.jobname = None 
    self.jobid = None  
    self.predepslist = [] 
    self.postdepslist = [] 
    self.execpath = None 
    self.execname = None    
    self.hold = "N" 
    self.groupslist = [] 
    self.freq = None 
    self.runtime = None
    self.detailslist = []      

  def create(self, name):
    self.jobname = name
    self.jobid = self.nextid  
    makeid().next() 
    self.detailslist = [self.jobname, self.predepslist, 
         self.postdepslist, self.execpath, self.execname, 
         self.hold, self.groupslist, self.freq, self.runtime]  
    self.jobdict.update({self.jobid: self.detailslist})    
              
  def show(self):
    #print [ k,v for (k,v) in self.jobdict ]     
    print list(self.jobdict.viewitems()) 
                          

# Create a couple of jobs 
job1 = job()
job1.create("FOO-BAR-BAZ")

job2 = job()
job2.create("MOOSE-SQUIRREL-BEAVER")

s = scheduler()
s.add(job1)
s.add(job2)
s.show()


``` 

I want to generate job IDs that increase by 1 for each new job created, so some kind of "keeping state" seems to be needed. 
Anyway, that isn't happening and I'm only getting the second job printed by the scheduler.   

I hope someone can help. Many thanks in advance -  bye for now - 
- trilobite

---

### Post by spjackson on 2018-09-15
[https://code-maven.com/slides/python-programming/static-variable](https://code-maven.com/slides/python-programming/static-variable)

---

### Post by trilobite2 on 2018-09-15
> **spjackson said:**
> [https://code-maven.com/slides/python-programming/static-variable](https://code-maven.com/slides/python-programming/static-variable) 

Hi spjackson!  Thanks very much for that - that'll do the trick nicely!  

Thanks again, bye for now :)   
- trilobite

---

