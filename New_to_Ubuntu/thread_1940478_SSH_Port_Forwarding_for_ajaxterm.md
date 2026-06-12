---
title: "SSH Port Forwarding for ajaxterm"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2012-03-13
Hey,

Ajaxterm is an application that creates a terminal session in a web browser. When it has been installed and configured, you can access it from the local machine in your browser from:

[http://localhost:8022](http://localhost:8022)

It cannot be accessed from outside, unless I do some SSL configuring, which I don't wanna get into. I have used ssh port forwarding to access the machine, <ajaxtermMachine>, from <myLocalMachine> by using the following:

```
ssh -L 8022:localhost:8022 kurtis@<ajaxtermMachine>
```

Then, I go into a browser on <myLocalMachine> and enter:

[http://localhost:8022](http://localhost:8022)

and it works.

QUESTION:
I would like to know if it would be possible for me to ssh forward from a <thirdMachine> so that anyone can:

http://<thirdmachine>:8022

then get the page from <ajaxtermMachine>. I think there might be issues because ajaxterm must be accessed by using localhost:8022. I have tried the following from <thirdMachine> with no luck:

```
ssh -L 8022:localhost:8022 kurtis@<ajaxtermMachine>
```

and when I went to http://<thirdMachine>:8022 from <myLocalMachine> I would expect to see the terminal, but it doesn't work. But it will work if I go to [http://localhost:8022](http://localhost:8022) in a browser on <thirdMachine> 

Any help with this would be awesome.

Thanks,
Kurt

---

### Post by jkurtisr32 on 2012-03-13
> **jkurtisr32 said:**
> Hey,

Ajaxterm is an application that creates a terminal session in a web browser. When it has been installed and configured, you can access it from the local machine in your browser from:

[http://localhost:8022](http://localhost:8022)

It cannot be accessed from outside, unless I do some SSL configuring, which I don't wanna get into. I have used ssh port forwarding to access the machine, <ajaxtermMachine>, from <myLocalMachine> by using the following:

```
ssh -L 8022:localhost:8022 kurtis@<ajaxtermMachine>
```

Then, I go into a browser on <myLocalMachine> and enter:

[http://localhost:8022](http://localhost:8022)

and it works.

QUESTION:
I would like to know if it would be possible for me to ssh forward from a <thirdMachine> so that anyone can:

http://<thirdmachine>:8022

then get the page from <ajaxtermMachine>. I think there might be issues because ajaxterm must be accessed by using localhost:8022. I have tried the following from <thirdMachine> with no luck:

```
ssh -L 8022:localhost:8022 kurtis@<ajaxtermMachine>
```

and when I went to http://<thirdMachine>:8022 from <myLocalMachine> I would expect to see the terminal, but it doesn't work. But it will work if I go to [http://localhost:8022](http://localhost:8022) in a browser on <thirdMachine> 

Any help with this would be awesome.

Thanks,
Kurt


Wow, I'm totally closing this. This doesn't use HTTPS in the current config (which is why I would need to configure SSL) so it would be unsecured if someone used HTTP to connect to <thirdMachine>.

Thanks anyways.

Sincerely,
Dumbass

---

