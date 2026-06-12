---
title: "Python question on subprocess"
date: 2010-04-11
forum: Programming Talk
---

### Post by Ali Kante on 2010-04-11
Hi,

I've just programmed some Python code and as a newbie I was wondering, how to sort a file out of Python.

I tried it with the subprocess command, but without any useful result.

Here's the code:

```

subprocess.Popen('sort file.txt -o file_sort.txt', shell=True, stdin=subprocess.PIPE, stdout=subprocess.PIPE)

```Any ideas why that won't work? :confused:

---

### Post by Bodsda on 2010-04-11
> **Ali Kante said:**
> Hi,

I've just programmed some Python code and as a newbie I was wondering, how to sort a file out of Python.

I tried it with the subprocess command, but without any useful result.

Here's the code:

```

subprocess.Popen('sort file.txt -o file_sort.txt', shell=True, stdin=subprocess.PIPE, stdout=subprocess.PIPE)

```Any ideas why that won't work? :confused:

Hmm, works fine for me, what errors are you getting?

```

bod@bod-linux:~$ cat file.txt 
z
y
x
w
v
u
t
s
r
q
p
o
n
m
l
k
j
i
h
g
f
e
d
c
b
a
bod@bod-linux:~$


```
```

>>> import subprocess
>>> subprocess.Popen('sort file.txt -o file_sort.txt', shell=True, stdin=subprocess.PIPE, stdout=subprocess.PIPE)
<subprocess.Popen object at 0xb76e28ac>
>>> exit()
bod@bod-linux:~

```
```

bod@bod-linux:~$ cat file_sort.txt 
a
b
c
d
e
f
g
h
i
j
k
l
m
n
o
p
q
r
s
t
u
v
w
x
y
z
bod@bod-linux:~$ 

```

Bodsda

---

### Post by Ali Kante on 2010-04-11
Damn... :oops:

ok, works for me, too after I separated the code from the rest of the program. It doesn't work inside my program, so I have to find out, what's wrong with that.

Thank you!

---

### Post by Ali Kante on 2010-04-11
My mistake was that the subprocess call was called before all threads finished. Now I'm looking for a way to wait for all subthreads to finish.

---

### Post by StephenF on 2010-04-12
> **Ali Kante said:**
> My mistake was that the subprocess call was called before all threads finished. Now I'm looking for a way to wait for all subthreads to finish.
```

a = subprocess.Popen("/usr/bin/sleep 5", shell=True)
a.wait()

```
It waits.

---

### Post by Ali Kante on 2010-04-13
I've found a better solution with join(). If anyone is interested, here's a piece of code that pings my server inside my lab in the fastest way:

```

#!/usr/bin/python
import subprocess
import threading

# ping function
def ping(ip, fp):
    command = "ping -c 1 " + ip
    # call the bash command
    process = subprocess.Popen(command, shell=True, stdout=subprocess.PIPE) 
    #give it some time to execute 
    process.wait()    
    result = process.stdout.read()
    # look if a ping was successful    then write it to the file
    if result.find("1 received") > 0:
        fp.write(ip + '\n')

# main program
def main():
    threads = []
    fp = open('result', 'w')
    fp.write("* Pinging all servers in my lab *" + '\n')

    for hosts in range(1,254):
        ip = "192.168.1." + str(hosts)    
        t = threading.Thread(target=ping, args=(ip,fp))
        threads.append(t)            
        t.start()

    # close the file, but first wait till all threads finish
    for i in range(0,253):
        threads[i].join()
    fp.close()

    # last but not least, sort the result
    process =  subprocess.Popen('sort result -o result_sorted', shell=True, stdin=subprocess.PIPE, stdout=subprocess.PIPE)    

if __name__ == '__main__':
    main()


```

---

