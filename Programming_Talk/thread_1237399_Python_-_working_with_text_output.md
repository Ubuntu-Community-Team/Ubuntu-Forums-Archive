---
title: "Python - working with text output"
date: 2009-08-11
forum: Programming Talk
---

### Post by thirddeep on 2009-08-11
I am trying to create a python script to check if a service / node is up in a cluster.

The output of the clustat command looks like this :
```
[root@blade01]# clustat
Member Status: Quorate

  Member Name                Status
  ------ ----                ------
  blade01                    Online, Local, rgmanager
  blade04                    Offline
  blade06                    Online, rgmanager
 

  Service Name         Owner (Last)     State         
  ------- ----         ----- ------     -----         
  blade04_gfs_services (unknown)        stopped         
  blade01_gfs_services blade01          started         
  blade05_gfs_services blade05          started         
  blade11_gfs_services blade11          starting        

```

The state I am currently pulling the status out with the following :

```

def grep(string,list):
        expr = re.compile(string)
        return filter(expr.search,list)

pipe = os.popen('/usr/sbin/clustat')
output = pipe.readlines()

SERVICE = grep("".join(argument), output) 
# grep is returning a list, so I have to fudge it to get what I want.
SERVICE = str(SERVICE)
SERVICE = SERVICE.split()
SERVICE = SERVICE[1:-1]

if SERVICE[2] == 'started':
......

```

(I got that grep function somewhere on the net)

This works, but it is ugly as hell and I cant extend it much.  For example, I want to check if the cluster is quorate :

```

print str(grep("".join('Quorate'), get_output())).split()[2:]

```

Will return :

```

["Quorate\\n']"]

```

I just want the word, not the newline and brackets.

I don't expect anyone to do this for me, but I would love someone that knows python to help me on the right path :-)

Thd.

---

### Post by ghostdog74 on 2009-08-11
you can use this method

```

f=0 #initialize flag
for line in pipe.readlines():
    line=line.strip()
    if "Service" in line: 
        f=1
        continue
    if f and not "----" in line:
        print line 
        # the rest you do yourself

```

---

### Post by thirddeep on 2009-08-11
ghostdog74,

That is so much simpler.  No grep, no fudging the output, and I can use it anywhere I want.

Thank you very much :)

Thd.

---

