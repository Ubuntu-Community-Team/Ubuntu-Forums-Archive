---
title: "Howto: Run bash shell commands from within Python"
date: 2010-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by paulmilliken on 2010-06-23
The subprocess module can be used to call command-line programs from within Python.  However, the syntax is long-winded and hard to remember.  A convenient simple python script that can save you time is:

```
def bash(cmd,cwd=None):
    '''runs a command in the bash shell'''
    print(cmd)
    retVal = subprocess.Popen(cmd, shell=True, \
        stdout=subprocess.PIPE, cwd=cwd).stdout.read().strip('\n').split('\n')
    if retVal==['']:
        return(0)
    else:
        return(retVal)

```

Example uses are:

```
bash('convert myFile.png myFile.jpg')
```

and

```
myFileList = bash('ls *.jpg',cwd='myDirectory')
```

---

