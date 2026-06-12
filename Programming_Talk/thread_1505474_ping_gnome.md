---
title: "ping gnome?"
date: 2010-06-09
forum: Programming Talk
---

### Post by Sandsound on 2010-06-09
I'm trying to make a fairly simple app in PyGtk.
I using WOL (wake on lan) to turn on my server, and would like to get a confirmation when it's up and running and be able to use is via vnc.

My first idea was to ping the server ip, but the ip is up before the desktop. so my question is, is there a way to "ping" the desktop?
preferable without having to use root.

btw. it's a local server.

---

### Post by Tony Flury on 2010-06-09
There is no way to ping the "desktop", but you could for instance try to open a socket to the server on the correct VNC port. Depending on how VNC works you should get a different response depending on if VNC is ready to run on the serve5.

---

### Post by geirha on 2010-06-09
Use netcat to check if the vnc-port is open. E.g.
```

while sleep 2; do 
  if nc -w 1 -z hostname 5900; then
    break # port's open now.
  fi
done

```

---

### Post by Sandsound on 2010-06-10
Thank you both for your suggestions.

This is my first futile attempt that kind'a works:
```

tid = time.time()

while True:
	if time.time() > tid + 0.20:
		status = ("OFLINE")
		break
	return_value = os.system("ping -c 1 "+ ip)
	if return_value == 0:
		status = ("ONLINE")
		break

```

> **Tony Flury said:**
> There is no way to ping the "desktop", but you could for instance try to open a socket to the server on the correct VNC port. Depending on how VNC works you should get a different response depending on if VNC is ready to run on the serve5.

Not sure how to open a socket?
I can't find a way to read VNC response.

> **geirha said:**
> Use netcat to check if the vnc-port is open. E.g.
```

while sleep 2; do 
  if nc -w 1 -z hostname 5900; then
    break # port's open now.
  fi
done

```

took me a while to figure out that this wasn't Python :-)
"nc -w 1 -z hostname 5900" doesnt seam to return anything?

---

### Post by geirha on 2010-06-10
> **Sandsound said:**
> 
took me a while to figure out that this wasn't Python :-)
"nc -w 1 -z hostname 5900" doesnt seam to return anything?

Sorry, yeah that's posix shell code. I missed the python part. That nc command doesn't output anything, it just returns 0 (true) if the port is open, non-0 (false) otherwise.

---

### Post by Sandsound on 2010-06-10
> **geirha said:**
> Sorry, yeah that's posix shell code. I missed the python part. That nc command doesn't output anything, it just returns 0 (true) if the port is open, non-0 (false) otherwise.

Great :-) just what I need.

this is my final code (the interesting part):
```

serverip = ("192.168.1.10")
tid = time.time()

while True:
	#if not found in 60sec then show error
	if time.time() > tid + 0.60:
		#set statuslabel text
		status = ("OFLINE")
		break
	return_value = os.system("nc -w 1 -z "+ serverip +" 5900")
	if return_value == 0:
		#set statuslabel text
		status = ("ONLINE")
		break

```

I'll upload the final program to my website if anyone should be interested.

---

### Post by geirha on 2010-06-10
Well, you should generally avoid using os.system. python has lots of different modules to do networking tasks. I'm a bit rusty on that part, but the following seems to do what you want:
```

import time, socket
def wait_for_port(hostname, port, timeout=120):
    wait_until = time.time() + timeout # two minutes by default
    s = socket.socket(socket.AF_INET)
    while time.time() < wait_until:
        time.sleep(1)
        try:
            s.connect((hostname,port))
            s.close()
        except socket.error, msg:
            print msg
            continue
        print "connection succeeded"
        return True
    print "timeout"
    return False

```

---

### Post by Sandsound on 2010-06-10
> **geirha said:**
> Well, you should generally avoid using os.system...

It this because of possible problems with portability?

I mostly do small PyGtk apps, so my code is already limited in choice of os.

---

### Post by geirha on 2010-06-10
> **Sandsound said:**
> It this because of possible problems with portability?

I mostly do small PyGtk apps, so my code is already limited in choice of os.

Yes, nc is not portable, you can't expect it to be on every system out there, and it may have a different syntax on other systems. Secondly, it's less efficient to fork and exec a separate process when python can do it natively.

---

### Post by Sandsound on 2010-06-10
> **geirha said:**
> Yes, nc is not portable, you can't expect it to be on every system out there, and it may have a different syntax on other systems. Secondly, it's less efficient to fork and exec a separate process when python can do it natively.

I'll try to keep that in mind for my future projects.

The portability issues doesn't mind me that much (almost everyone I know uses Ubuntu anyway), but my programs have a tendency to get larger and more complex in time, and keeping exec-time to a minimum would be nice.

Thanks for your help :-)

---

