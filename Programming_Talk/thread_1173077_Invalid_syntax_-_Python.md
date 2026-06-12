---
title: "Invalid syntax - Python"
date: 2009-05-29
forum: Programming Talk
---

### Post by P=NP on 2009-05-29
```

import telnetlib
def main():
    host = 192.168.1.110
    tn = telnetlib.Telnet(host, 21, 5)
    tn.read_until('login: ',10)
    tn.write(root + "\n")
    if password:
        tn.read_until("password: ")
        tn.write(password + "\n")

    tn.write("killall rqcamd\n")
main()

```When I run this I get an invalid syntax at the .1 in the IP. Maybe I don't know how to google good enough, but I couldn't find an answer. I know there's more problems than that, but the error is where I'm stuck right now. 

Take it easy, I'm new here ;)

---

### Post by jespdj on 2009-05-29
Well, what is this line supposed to mean:
```
host = 192.168.1.110
```
Should 'host' be a string? The notation 192.168.1.110, without for example quotes or anything, doesn't mean anything in Python. Shouldn't it be this?
```
host = "192.168.1.110"
```

---

### Post by P=NP on 2009-05-29
Thank you! I'm embarrassed to say I just was not paying close enough attention. 

Another question, Do I need to have variables for the user name and password?

---

### Post by imdano on 2009-05-29
Where are the variables root and password coming from in your code?  They don't appear to be defined anywhere.  Or are they supposed to be strings as well?

---

### Post by P=NP on 2009-05-29
I know this must be frustrating for you guys, I appreciate the patience. My question was, do I have to define variables to use for the login and password, or will strings work? Which is the better way of doing things? Also, this line:
```
tn = telnetlib.Telnet(host, 21, 5)
```
Does that create an object (tn)?

---

### Post by The Cog on 2009-05-30
> **P=NP said:**
> I know this must be frustrating for you guys, I appreciate the patience. My question was, do I have to define variables to use for the login and password, or will strings work? Which is the better way of doing things? 
You can either use strings directly like this:
```
tn.write("please" + "\n")
```
or assign strings to variables and use the variables like this:
```
password = "please"
tn.write(password + "\n")
```
The second is more versatile because you can prompt the user for a password, or read it from a file/database. The first is reasonable for a one-off throwaway tool.
> Also, this line:
```
tn = telnetlib.Telnet(host, 21, 5)
```
Does that create an object (tn)?
Yes. It creates an instance of the Telnet class. Telnet() is therefore the class constructor method. In practice, it ends up calling the __init__() method of the newly created instance.

---

