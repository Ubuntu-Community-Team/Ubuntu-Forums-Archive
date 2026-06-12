---
title: "Python run process get output"
date: 2011-04-26
forum: Programming Talk
---

### Post by DBQ on 2011-04-26
Hi everybody. I am having a problem in python.  I would like to use python
to run two programs at the same time: e.g. time ls.  I want my python script to get the output of both commands.  Currently I am using code like this

```

cmd = ["time","ls"]

         process = subprocess.Popen(cmd, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
 
         process.wait()
         out = process.stdout.readline()


```

However, I am getting output for ls, but not time.  Any ideas?

---

### Post by DaithiF on 2011-04-26
set cmd to be a single string 'time ls' and add the parameter shell=True to the Popen call, e.g.:

```
p = subprocess.Popen('time ls', shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE)

```

---

### Post by Arndt on 2011-04-26
> **DBQ said:**
> Hi everybody. I am having a problem in python.  I would like to use python
to run two programs at the same time: e.g. time ls.  I want my python script to get the output of both commands.  Currently I am using code like this

```

cmd = ["time","ls"]

         process = subprocess.Popen(cmd, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
 
         process.wait()
         out = process.stdout.readline()


```

However, I am getting output for ls, but not time.  Any ideas?

'time' writes to stderr, so you should look in process.stderr.readline()

---

