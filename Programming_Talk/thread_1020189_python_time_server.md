---
title: "python time server"
date: 2008-12-23
forum: Programming Talk
---

### Post by zzzPOOHzzz on 2008-12-23
i am trying to write a time server in python, and when trying to write the time received to the clients clock it is changing the time i input as 12:00:00
i'm kind of embarassed to post all the code because it's really sloppy, I just keep adding stuff and testing my outputs and stuff so here's part of it
```

t = time.strftime('%m/%d/%Y %X', recvstamp)
print t +" :variable t"
os.system("date -s " + "\"t\"")
print t +" :variable t"
print "Clock Set!"
```
and the output (not using sudo so i actually can't change the clock, i don't want to keep setting it back from 12:00:00)

```

12/23/2008 22:04:38 :variable t
date: cannot set date: Operation not permitted
Mon Dec 22 12:00:00 EST 2008
12/23/2008 22:04:38 :variable t
Clock Set!

```

again, i'm not worried about the "cannot set date" part, just why it changes it to 12:00:00.  if i run just the date command with the same thing in my code, it would set it to the right time, but not in the script

sorry if this doesnt make sense, just kinda flustered at the problem and not sure how to describe it

---

### Post by catchmeifyoutry on 2008-12-24
> **zzzPOOHzzz said:**
> i am trying to write a time server in python, and when trying to write the time received to the clients clock it is changing the time i input as 12:00:00
i'm kind of embarassed to post all the code because it's really sloppy, I just keep adding stuff and testing my outputs and stuff so here's part of it
```

t = time.strftime('%m/%d/%Y %X', recvstamp)
print t +" :variable t"
os.system("date -s " + "\"t\"")
print t +" :variable t"
print "Clock Set!"
```
and the output (not using sudo so i actually can't change the clock, i don't want to keep setting it back from 12:00:00)

```

12/23/2008 22:04:38 :variable t
date: cannot set date: Operation not permitted
Mon Dec 22 12:00:00 EST 2008
12/23/2008 22:04:38 :variable t
Clock Set!

```

again, i'm not worried about the "cannot set date" part, just why it changes it to 12:00:00.  if i run just the date command with the same thing in my code, it would set it to the right time, but not in the script

sorry if this doesnt make sense, just kinda flustered at the problem and not sure how to describe it

Hi, I think I understand what you mean. You have a quoting problem and missing + operators, look at the following lines:
[PHP]
print "date -s " + "\"t\"" # [WRONG] prints 'date -s "t"', t is part of the string
os.system("date -s " + "\""+t+"\"") # [OK] this is probably what you meant
os.system('date -s "'+t+'"') # [GOOD] this is less confusing to read, no escaping needed
os.system('date -s "%s"' % t) # [GOOD] without using string concatenation
[/PHP]

In other words, the system command you executed was: date -s "t"
which, if you enter it in a terminal, is indeed interpreted as an illegal date specification, thus it uses some other default date.
Also, notice how syntax highlighting above immediately reveals how in the first line the 't' is part of the string (as in your code), while in the other lines 't' is a variable not part of the string.
I suggest you use a text editor which provides syntax highlighting to quickly spot such mistakes (gedit and most code editors do have this option).

Best, and merry christmas :)

---

### Post by zzzPOOHzzz on 2008-12-24
awesome, it works perfectly now... thanks for actually explaining it too so i know what i did wrong instead of just giving me the code and saying have at it
i really appreciate this!

---

### Post by zzzPOOHzzz on 2009-07-07
i'm resurrecting this thread because i need a little more help...
i'm making it so i can put this on any system and it will identify its own ip address without hardcoding it into the script, i am not a python guru by any means, my teacher made us hop into without teaching any of it to us whatsoever...
but i found this to identify it
>>> s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
>>> s.connect(("192.168.1.100",80))  #this is going to be the staticip for the server
>>> print s.getsockname()
('192.168.1.104', 44522) #my ip on the local network
>>> ipaddy = s.getsockname()
>>> print ipaddy
('192.168.1.104', 44522) #figured this would be a good way to store my IP


now... how do i isolate the text inbetween the quotes (192.168.1.104)
if i can do that, i can probably get this down perfectly how i want to.

---

### Post by zzzPOOHzzz on 2009-07-07
bump

---

### Post by ajsquared on 2009-07-08
> **zzzPOOHzzz said:**
> i'm resurrecting this thread because i need a little more help...
i'm making it so i can put this on any system and it will identify its own ip address without hardcoding it into the script, i am not a python guru by any means, my teacher made us hop into without teaching any of it to us whatsoever...
but i found this to identify it
>>> s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
>>> s.connect(("192.168.1.100",80))  #this is going to be the staticip for the server
>>> print s.getsockname()
('192.168.1.104', 44522) #my ip on the local network
>>> ipaddy = s.getsockname()
>>> print ipaddy
('192.168.1.104', 44522) #figured this would be a good way to store my IP


now... how do i isolate the text inbetween the quotes (192.168.1.104)
if i can do that, i can probably get this down perfectly how i want to.

Are you just trying to get the first element of the tuple?  If so, all you need to do is ipaddy[0].

---

### Post by zzzPOOHzzz on 2009-07-08
> **ajsquared said:**
> Are you just trying to get the first element of the tuple?  If so, all you need to do is ipaddy[0].

awesome... thanks it works perfectly

---

### Post by zzzPOOHzzz on 2009-08-16
well i'm back at this project again, now i'm trying to run this script from a virtual ubuntu OS on a win7 pc... maybe i should post this elsewhere, but how can i get my network to pick this up... because it gives me an offline ip address, 10.0.xxx.xxx,

---

### Post by Bodsda on 2009-08-16
> **zzzPOOHzzz said:**
> well i'm back at this project again, now i'm trying to run this script from a virtual ubuntu OS on a win7 pc... maybe i should post this elsewhere, but how can i get my network to pick this up... because it gives me an offline ip address, 10.0.xxx.xxx,

I am unsure exactly but if you are running in a VM I suggest checking what ubuntu thinks your IP is (ifconfig) and also check if the VM software is setting an IP so that the guest and host can communicate.

---

### Post by zzzPOOHzzz on 2009-08-17
> **Bodsda said:**
> I am unsure exactly but if you are running in a VM I suggest checking what ubuntu thinks your IP is (ifconfig) and also check if the VM software is setting an IP so that the guest and host can communicate.


i said it thinks my ip is 10.0.xx.xx i dont remember the exact numbers atm, and how do i set it up so i can get the guest and host to communicate?

---

### Post by zzzPOOHzzz on 2009-08-19
bump. any help?

---

### Post by jeffathehutt on 2009-08-19
Which VM software are you using?

If you can connect to a web page from the Ubuntu VM, then your network is working properly.  If you can't browse web sites, you will need to set up a connection in the VM software, but the specific steps are different for each VM software.

---

### Post by zzzPOOHzzz on 2009-08-20
i'm using virtual box. yeah i can connect to the web... i need to connect to the virtual OS directly from over the network though is what i'm tryijng to say

---

### Post by zzzPOOHzzz on 2009-08-21
bump

---

### Post by zzzPOOHzzz on 2009-09-02
well, just to get this client working i installed a 2nd virtualbox OS
now heres my problem...
i'm sure its simple, but i'm pretty noob to python.
i've got my IP saved into a variable... called myip (creative, huh?)
now, when i need to send my own ip address to the
[PHP]
sock.connect(("192.168.56.101",80)
ipaddy = sock.getsockname()
myip = ipaddy[0]
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.bind(("192.168.56.102", 8881))
[/PHP]
i need my "myip" variable to go into where i have 192.168.56.102

if you're wondering why i have it do that, it is so i can just throw this program up on any computer and have it discover it's own ip address rather than having to hard code every single ip address into every computers certain file (and if i don't have static IP's)

i've tried a few things, like using quotes, not using quotes, using + signs i just cant get it to work

---

### Post by zzzPOOHzzz on 2009-09-02
bump... any help?

---

### Post by zzzPOOHzzz on 2009-09-04
unfortunately another bump...

---

### Post by Arndt on 2009-09-04
> **zzzPOOHzzz said:**
> well, just to get this client working i installed a 2nd virtualbox OS
now heres my problem...
i'm sure its simple, but i'm pretty noob to python.
i've got my IP saved into a variable... called myip (creative, huh?)
now, when i need to send my own ip address to the
[PHP]
sock.connect(("192.168.56.101",80)
ipaddy = sock.getsockname()
myip = ipaddy[0]
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.bind(("192.168.56.102", 8881))
[/PHP]
i need my "myip" variable to go into where i have 192.168.56.102

if you're wondering why i have it do that, it is so i can just throw this program up on any computer and have it discover it's own ip address rather than having to hard code every single ip address into every computers certain file (and if i don't have static IP's)

i've tried a few things, like using quotes, not using quotes, using + signs i just cant get it to work

I probably misunderstand the question, but doesn't this code do what you want?

```
ipaddy = sock.getsockname()
myip = ipaddy[0]
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.bind((myip, 8881))

```

---

### Post by zzzPOOHzzz on 2009-09-04
> **Arndt said:**
> I probably misunderstand the question, but doesn't this code do what you want?

```
ipaddy = sock.getsockname()
myip = ipaddy[0]
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.bind((myip, 8881))

```

ok i swear i tried that before... i must have typed something wrong, sorry for wasting your time :(

edit: oh yeah.... thanks ;)

---

### Post by Hanratty on 2009-09-04
A Time server implemented in Python, developed for use at my job site, but opened up to the public for further improvement(s) & feature set changes.

---

### Post by zzzPOOHzzz on 2009-09-05
> **Hanratty said:**
> A Time server implemented in Python, developed for use at my job site, but opened up to the public for further improvement(s) & feature set changes.
what?

---

