---
title: "How to know if I am connected?"
date: 2007-06-30
forum: Programming Talk
---

### Post by Matodo on 2007-06-30
Hello

I need to write a script that do a command if I am connected or do another if I am not.

I only know one way to make sure if I am connected or not: to ping a website.
But I don't know how to exploit this command.

Can you please help me? An if-statement would be enough.
Thank you.

---

### Post by woodr0w on 2007-06-30
Need to understand the questing a bit more, asking if your connected to the internet? or local ? , either or im sure ifconfig, or netstat in console would give you the information you require.
Hope this helps sir.

---

### Post by gpolo on 2007-06-30
You could do something overkill like this:

```

import socket

def connected():
    remote = ("www.google.com", 80)
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    try:
        s.connect(remote)
    except socket.gaierror, e:
        return "No, you are not connected."

    return "Nice, you are connected."

if __name__ == "__main__":
    print connected()

```

---

### Post by Matodo on 2007-07-01
> Need to understand the questing a bit more, asking if your connected to the internet? or local ?
To the internet.
Thanks for your help

gpolo: I tried to execute the script  but it didn't work for me. It gives me this error message:
```
./test: line 3: syntax error near unexpected token `('
./test: line 3: `def connected():'
```
Any idea?

Thank you in advance

---

### Post by Dancingwllamas on 2007-07-01
Are you trying to run the script he provided in bash or python? The script he provided is a python script, which may be your problem.

---

### Post by Matodo on 2007-07-01
Now it works
Thank you

---

