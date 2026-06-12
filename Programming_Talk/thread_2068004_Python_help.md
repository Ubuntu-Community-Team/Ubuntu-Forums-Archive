---
title: "Python help"
date: 2012-10-08
forum: Programming Talk
---

### Post by prismctg on 2012-10-08
[CODE/]from sys import platform
from os import system ,listdir
import subprocess
def Platform():
    if platform == "win32":
        system("notepad")
    elif platform == "linux2" or "linux":
        subprocess.Popen("gnome-terminal -e nano", shell=True)

def main():
    Platform()
    a=listdir()
    length=len(a)
    print(length,a)
if __name__ == "__main__":main()][/CODE] ; In that code how can i capture when text editor is closed ? so is there any way to capture editor close signal ? actually i want to run listdir() after editor is close

---

### Post by surfer on 2012-10-08
subprocess.call() (check [http://docs.python.org/library/subprocess.html]("http://docs.python.org/library/subprocess.html")) waits for the process to finish.

---

### Post by Bachstelze on 2012-10-08
Never mind...

---

