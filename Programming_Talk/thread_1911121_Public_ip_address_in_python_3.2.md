---
title: "Public ip address in python 3.2"
date: 2012-01-18
forum: Programming Talk
---

### Post by prismctg on 2012-01-18
HOW can i find public ip address using python 3.2 ... i m novice :(

---

### Post by surfer on 2012-01-18
what do you mean by 'public ip address'? the ip address of your machine? this you can get with the following:
```
import socket
print(socket.gethostbyname(socket.gethostname()))

```

---

### Post by Tony Flury on 2012-01-18
@prismctg - see also - in reply to the question you posted there.
[http://ubuntuforums.org/showpost.php?p=11621043&postcount=6](http://ubuntuforums.org/showpost.php?p=11621043&postcount=6)

@surfer - that will work if your client PC has been allocated a public address. If you are sitting behind a NAT router, then this will return the address that the NAT router has assigned - which will be valid on the network behind the NAT router (i.e. in your home or office), but which is not your public address.

---

### Post by prismctg on 2012-01-18
@tony [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp) is not working ....... [File moved-http://www.whatismyip.com/faq/automation.asp]

---

### Post by Sworddragon on 2012-01-18
> **prismctg said:**
> HOW can i find public ip address using python 3.2 ... i m novice :(

There is no absolute secure way of getting the public ip address without using external informations. I recommend you to get your ip address from a public site.

---

### Post by pbrane on 2012-01-18
> **prismctg said:**
> @tony [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp) is not working ....... [File moved-http://www.whatismyip.com/faq/automation.asp]

its changed to, [http://automation.whatismyip.com/n09230945.asp]("http://automation.whatismyip.com/n09230945.asp")

try this, it works in 2.7
```

from urllib import urlopen
print urlopen('http://automation.whatismyip.com/n09230945.asp').read()

```

EDIT:
It looks like in 3.2 you have to use
```

urllib.request.urlopen('http://automation.whatismyip.com/n09230945.asp').read()

```

[http://docs.python.org/py3k/index.html]("http://docs.python.org/py3k/index.html")

---

### Post by prismctg on 2012-01-18
@phrane thnx :)

---

