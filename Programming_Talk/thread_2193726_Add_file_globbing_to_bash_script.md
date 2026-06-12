---
title: "Add file globbing to bash script"
date: 2013-12-14
forum: Programming Talk
---

### Post by EddyNigma on 2013-12-14
Hi folks,
I'm trying unsuccessfully to add file globbing to a basic shell, I've been at it for a feckin ages and although I can glob the files in the current directory I can't get it done properly with user input, ie ls *.py.
All I can do is an if statement and then glob the entire directory. Any help here would be really appreciated.

---

### Post by ofnuts on 2013-12-14
The syntax of Bash ain't what it used to be :)

This said, in Unix the globbing is done by the shell. When you enter:
```
somecommand *.ext
```

the shell does the globbing before calling the command so it's exactly as if you entered:
```
somecommand file1.ext file2.ext file3.ext
```

And in your code you execute the commands without doing the globbing, so all the command sees as an argument is "*.ext" which isn't the name of an existing file.

---

### Post by EddyNigma on 2013-12-15
Thanks ofnuts, I've got it working, kind of. I can now glob files, I've added a redirection function too but for some reason simple commands that worked earlier like ls and cat seem to have stopped. Am I doing anything obviously wrong here?

---

### Post by ofnuts on 2013-12-15
What are the (cmd, argv) arguments you end up passing to os.execv()?

PS: use [code] tags to bracket you code (or the '#' icon in the toolbar)

---

### Post by EddyNigma on 2013-12-15
> **ofnuts said:**
> What are the (cmd, argv) arguments you end up passing to os.execv()?

PS: use ```
 tags to bracket you code (or the '#' icon in the toolbar)
The cmd is the user input and the argv is the parsed input. Thought my code looked sloppy alright.
So I have me program doing what I want but I have one small bug that's ruining my day/night. Everything works fine but when I read or write to a file I need to type exit a load of times to get out of the program.

Any ideas?
[code]
# Very basic Posix shell
import os
import sys
import readline
import shlex
import glob

prompt = "sh>> "

def copyright():
  sys.stderr.write("""
Copyright (C) 2012-13 
This program comes with ABSOLUTELY NO WARRANTY; This is free
software, and you are welcome to redistribute it under certain
conditions; Type "copyright" or "license" for more information.
""" + "\n")
  return True


def globbing(cmd):
  for i in range(0, len(cmd)):
    if '*' in cmd[i]:
      cmd.extend(glob.glob(cmd[i])) 
      temp = cmd[i] 
      cmd.remove(temp)
      sys.stderr.write(cmd[i])

def save(cmd):
  number = len(cmd)-1
  check = argv[number]
  if os.fork() == 0:
    fd = os.open(cmd[2], os.O_CREAT | os.O_TRUNC | os.O_RDWR)
    os.dup2(fd, 1)
    print(cmd[0])
    os._exit(1)
  elif check == '&':
    return
  else:
    os.wait()

def read(argv):
  number = len(argv)-1
  check = argv[number]
  if os.fork() == 0:
    #fd = os.open(argv[2], os.O_RDONLY)
    #readvar = os.dup2(fd, 0)
    a = open(argv[2], "r") 
    line = a.readline() 
    while line: 
      print (line )
      line = a.readline() 
    a.close() 
    return
  elif check == '&':
    return
  else:
    os.wait()


# Parsed splitting of input into constituent arguments
def parse(cmd):
  cmd = shlex.split(cmd)
  for c in cmd:
    if '*' in c:
      globbing(cmd)
    elif '>' in c:
      save(cmd)
    elif '<' in c:
      read(cmd)
  return cmd

def internal(argv):
  cmd = argv[0]
  if cmd == "copyright":
    return copyright()

  return False

# Execute an execute command (i.e. run a  program on disk)
# If this succeeds it never returns
def execute(cmd, argv):
  try:
    os.execv(cmd, argv)
  except OSError: pass

def call(argv):
  number = len(argv)-1
  check = argv[number]
  if os.fork() == 0:
    if '<' in argv:
      0 
    elif '>' in argv:
      0
    else: 
      cmd = argv[0]
      if '/' in cmd:
        # Relative or absolute path specified
        execute(cmd, argv)
      else:
        for dir in os.getenv('PATH').split(':'):
          # Keep trying each directory in PATH until we find it
          execute(dir + '/' + cmd, argv)

      # If we get here then execution has failed
      sys.stderr.write('Unrecognised command: ' + cmd + '\n')
      os._exit(1)
  elif check == '&':
    return
  else:
    os.wait()

# Read, print, eval, loop (REPL)
copyright()
while True:
  try:
    cmd = ""
    cmd = input(prompt).strip()
    if cmd == "":
      # Empty command so just prompt again
      pass
    elif cmd == "exit":
      # Exit the shell
      break
    else:
      argv = parse(cmd)
      if not internal(argv):
        call(argv)
  except EOFError:
      # User has pressed Ctrl-D
    break
```

---

### Post by ofnuts on 2013-12-16
> **EddyNigma said:**
> The cmd is the user input and the argv is the parsed input.

Yes, and what do they look like exactly in your tests? What are the actual strings you see?

---

### Post by EddyNigma on 2013-12-16
> **ofnuts said:**
> Yes, and what do they look like exactly in your tests? What are the actual strings you see?
Depends what I type in. An input example would be cmd = "I like cake" and when parsed it would be argv = ['I' , 'like' , 'cake']. I'm pretty sure they're not my problem though.

My last issue is that I'm stuck in a loop when trying to exit. I'm not sure how I've gotten in the loop in the first place as I have breaks and returns in the proper places(I think). This only happens after read from or writing to a file.

---

### Post by ofnuts on 2013-12-16
Without digging too much in your code:

- I'm surprised redirection works at all... I don' t see you removing the <> nor the file names from the command args. Plus that's not how it works... you don't have to read/.write the file... you open it, dup2() the handle to your stdin/out, and then exec() the command, that will inherit the files already open and read/write to them. If you only handle < and > this can be done in the child process after the fork, bt if you want to handle pipes you have to create the pipe(s) before the forks (because each side of the pipe will be used by a different forked process).
- "number = len(argv)-1;   check = argv[number]" could be replaced by the more pythonic "argv[-1]"
- If you have several like-named commands in the various path directories, you are going to execute them all. But execvp() could take care of everything.


PS: "I'm pretty sure they're not my problem though.". Famous last words...  in a couple of programming careers I've seen :)

---

### Post by EddyNigma on 2013-12-16
> **ofnuts said:**
> 
PS: "I'm pretty sure they're not my problem though.". Famous last words...  in a couple of programming careers I've seen :)

Sentence is open to interpretation I suppose. I'll reword it as I'm retty sure it's not the problem though. Thanks for the time ofnuts, I got it working in the end. I moved the read/write function calls to a different function(doubt this helped) and put in an os._exit(1) after each. I've to run a test.rb file and it passes on all but the write function. The test file runs this run('echo redirection > outfile.txt'), but the file contents are blank. Although if I run the command $echo redirection > outfile.txt from the terminal, all is good.

---

### Post by ofnuts on 2013-12-16
> **EddyNigma said:**
> Sentence is open to interpretation I suppose. I'll reword it as I'm retty sure it's not the problem though. Thanks for the time ofnuts, I got it working in the end. I moved the read/write function calls to a different function(doubt this helped) and put in an os._exit(1) after each. I've to run a test.rb file and it passes on all but the write function. The test file runs this run('echo redirection > outfile.txt'), but the file contents are blank. Although if I run the command $echo redirection > outfile.txt from the terminal, all is good.

See my remarks about doing the I/O redirection (and test your stuff with things less trivial than "echo" or "cat").

---

