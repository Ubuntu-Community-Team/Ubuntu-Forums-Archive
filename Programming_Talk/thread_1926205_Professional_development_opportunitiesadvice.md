---
title: "Professional development opportunities/advice?"
date: 2012-02-15
forum: Programming Talk
---

### Post by FamousAmos on 2012-02-15
I'm a software engineer, about 4 years out of university(BS in computer engineering), and have an interest in networking .  I'd like to find classes/seminars/training/etc. that I can take to develop my skills, but searching on google hasn't been very fruitful.  Most of my search results are for university courses/programs, which are out of reach at the moment.  Does anyone have any tips on how to search for development opportunities?  

Also, if anyone has any career advice for someone like me, who'd eventually(years down the line) like to be a networking expert/specialist?  That would be highly appreciated.

---

### Post by r-senior on 2012-02-16
I'm not clear ... are you looking for a job or a training course to help you get a job?

If you are looking for a training course, do you mean a short, focussed course, e.g. 4-5 days? Or are you looking at a long-term course with a qualification at the end?

Are you prepared to pay for training?

---

### Post by juancarlospaco on 2012-02-16
If you are interested in Networking you MUST have CCNA, 
if you want to be an expert, also take a Juniper course.

I dont understand what are you looking for..., 
a job?, a course?, want to be NetAdmin? or Programmer?

---

### Post by FamousAmos on 2012-02-16
Sorry for not being clear - I am already employed as a programmer, have been for about 4 years.  I'm not looking for a job, I'm looking for short, focused courses that can help me expand my skills.  Thanks for the recommendations of CCNA and Juniper, I appreciate that!

---

### Post by haqking on 2012-02-16
> **juancarlospaco said:**
> If you are interested in Networking you **MUST have CCNA**, 
if you want to be an expert, also take a Juniper course.

I dont understand what are you looking for..., 
a job?, a course?, want to be NetAdmin? or Programmer?

Must ?

if using Cisco products maybe, not much use to you in a non cisco environment.

As for Juniper making you expert, hardly and depends what Juniper cert you take, a JNCIA-JUNOS would only be equivalent of CCNA so not making you an expert

There are much higher levels within Cisco if you want to be a "Cisco" expert like CCIE.

Networking is a broad subject covering many areas, depends what area you are interested in.

---

### Post by juancarlospaco on 2012-02-16
> **haqking said:**
> Must ?

if using Cisco products maybe, not much use to you in a non cisco environment.

As for Juniper making you expert, hardly and depends what Juniper cert you take, a JNCIA-JUNOS would only be equivalent of CCNA so not making you an expert

There are much higher levels within Cisco if you want to be a "Cisco" expert like CCIE.

Networking is a broad subject covering many areas, depends what area you are interested in.

meh, c'mon, you are smart, he said like "something to start with"
Anyways Cisco IOS CLI can be used for (random) example on Vyatta.
The level depends on him, and the availability, i.e. at the place i live theres nothing more than CCNA courses.

When he goes into basic cisco or juniper or whatever he will see the higher levels and make his way.

---

### Post by karlson on 2012-02-23
> **juancarlospaco said:**
> meh, c'mon, you are smart, he said like "something to start with"
Anyways Cisco IOS CLI can be used for (random) example on Vyatta.
The level depends on him, and the availability, i.e. at the place i live theres nothing more than CCNA courses.

When he goes into basic cisco or juniper or whatever he will see the higher levels and make his way.

If you are planning on supporting it it then yes.  If not then Stevens' books will do as a starting point.

---

### Post by karlson on 2012-02-23
> **FamousAmos said:**
> I'm a software engineer, about 4 years out of university(BS in computer engineering), and have an interest in networking .  I'd like to find classes/seminars/training/etc. that I can take to develop my skills, but searching on google hasn't been very fruitful.  Most of my search results are for university courses/programs, which are out of reach at the moment.  Does anyone have any tips on how to search for development opportunities?  

Also, if anyone has any career advice for someone like me, who'd eventually(years down the line) like to be a networking expert/specialist?  That would be highly appreciated.

What are you planning to do?  Run Cables?  Install Switches? Support Switches and Routers? Develop Communication layer for applications?  Develop Client-Server applications?

---

### Post by FamousAmos on 2012-02-28
> **karlson said:**
> What are you planning to do?  Run Cables?  Install Switches? Support Switches and Routers? Develop Communication layer for applications?  Develop Client-Server applications?

Communication layer for applications, client-server applications, that sort of thing.

---

### Post by Some Penguin on 2012-02-29
> **FamousAmos said:**
> Communication layer for applications, client-server applications, that sort of thing.

Honestly?  I'd say -- don't.  Unless you're looking at highly specialized situations e.g. where minimizing power consumption is critical or where high-speed reliable routing of communications between a massive number of end-points is an issue...

There are plenty of relevant frameworks and libraries that make this not where most teams should be spending much time -- [Jersey]("http://jersey.java.net/nonav/documentation/latest/user-guide.html"), [Apache HTTPComponents]("http://hc.apache.org/"),[Jackson]("http://jackson.codehaus.org/"), [Thrift]("http://thrift.apache.org/"), [protocol buffers]("http://code.google.com/p/protobuf/")...

---

