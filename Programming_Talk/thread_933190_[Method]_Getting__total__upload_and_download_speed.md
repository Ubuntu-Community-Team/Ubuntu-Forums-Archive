---
title: "[Method] Getting _total_ upload and download speeds"
date: 2008-09-29
forum: Programming Talk
---

### Post by Pyro.699 on 2008-09-29
Hello,

Would it be possible, using either java or python, to get the total number of kilobytes being sent to/from the host computer? An example could be how transmission shows the total speed of the combined downloads, is there a way to get the speed (like that) for all programs. Another question is how to get the total in/out for the current session.

[B](Down: xxx kb/s | Up: xxx kb/s)
(In: xxx MB | Out: xxx MB)
[/B]
Thanks
~Cody Woolaver

---

### Post by Zugzwang on 2008-09-29
Answer: Well, it depends. You cannot get the "combined download speed for all programs" since you cannot determine from outside whether some program is using its connection to download some stuff does something else with its connection (like streaming some media, etc.).

You can, however, get some statistics for network connections. Look at what you can get in "/proc/net". Maybe there's something in there for you.

EDIT: Have a look at "/proc/net/dev".

---

### Post by Pyro.699 on 2008-09-29
I dont mind if its data such as webpage loading, streaming, msn chats (as small as they may be), downloads, ANYTHING.

I looked under /proc/net/dev_snmp6/wlan0 and didnt really find anything. I couldn't run it as an application, and there wasnt anything inside the file.

Edit:
In short, you know when you have the "System Monitor" on the panel, and you can have one that displays network useage. I would like a decimal representation of that

---

### Post by Asham on 2008-09-30
you can try analyzing the output from ifconfig. it contains bytes sent and received. I'm not sure if or how you it is possible to get the std output into a program however. if it is then perhaps you could use watch -n 1 ifconfig to get an update each second?

---

### Post by m10 on 2008-09-30
hint: the netspeed applet does that for u.. (sudo apt-get install netspeed)
i don't know how to do it while coding urself though..

---

### Post by Pyro.699 on 2008-10-05
I tried to use netspeed although i was unable to get it working properly with the apt-get. In order to run it i have to type **/usr/lib/netpeed/netspeed_applet2** and then its output is nothing, it just idols.

Ifconfig displays the total bytes sent and recieved but has no information about the information being recieved within a certian inverval. I could try taking 2 ifconfigs, get the line with the total bytes sent and recieved, and then devide them to get the differance within that interval.

Im still looking for any soloution to this ^^

Thanks
~Cody Woolaver

---

### Post by snova on 2008-10-05
Firstly, you can't get rate information without at least two snapshots. So do whatever you do to get the amount, wait a little while, and then do it again. Then speed is Different in Amount Transferred / Time Interval, unless it's the other way around :).

As for actually getting the data in the first place, it seems as if the /proc/net/dev file contains useful information. Read the contents of the file and pull out the appropriate bits.

An alternative is to fetch the source code to another program that needs transfer information (ifconfig is the obvious one to try, but it seems to work on a per-connection basis, which I don't think is what you want) and extract the useful bits of code.

---

### Post by Pyro.699 on 2008-10-05
The data in /proc/net/dev is nothing, the file is empty
> 
cody@Charmander:~$ echo < /proc/net/dev

cody@Charmander:~$ 


So the best method would be to take the data from ifconfig and find the speed through that? Is there anyway to narrow down the output from ifconfig? right now i just use **ifconfig wlan0**

Thanks
~Cody Woolaver

---

### Post by Kevbert on 2008-10-05
If you just want what you've displayed in bold you could use the [[COLOR="Red"]Net Monitor Screenlet[/COLOR]]("http://gnome-look.org/content/show.php/Net+Monitor?content=72013"). You can manually reset it whenever you want.  Also the python code is there.
If you just want an approximate figure you can use the System Monitor.

---

### Post by snova on 2008-10-05
How do you know the file is empty? Run *this* instead:

```
cat /proc/net/dev
```

echo won't do anything. It prints its arguments.

---

### Post by Pyro.699 on 2008-10-05
How would this be done in python? because i am fimilar with that language

Thanks a lot
~Cody Woolaver

---

### Post by snova on 2008-10-05
Read in the entire file into a list of lines. Discard the extra lines. Take the important one and split it at spaces, then index the resulting list to get the useful numbers. Wait a few seconds (I've no idea how to do that), and then repeat. Then you should have your data.

---

### Post by Asham on 2008-10-06
Doesn't ifconfig offer hooks of some kind? 
Something like:
```
on_inet_package_received() #notify listeners
```

Polling is usually the last resort.

---

### Post by snova on 2008-10-06
I don't think anything more complicated than polling is necessary in this context. It's just to get the download speed. Polling is probably the way to go, since you need to capture its status at two points- and updating state via hooks would be rather complicated.

On the other hand, if ifconfig offers a method to get rate information, then use it! But if it gets that information by reading /proc/net/dev, then why bother? It might safeguard against kernel API changes, I guess...

---

### Post by Asham on 2008-10-07
I was reading to much into the question. For this purpose there is nothing wrong with polling. I agree with you there. 

On the other hand, if I wanted to get asynchronous updates, would I have to talk to the kernel then? Or how would I registering a listener? Sorry for stealing the focus of the thread.

---

### Post by snova on 2008-10-07
I have no idea. I didn't even know about the existence of /proc/net/dev before yesterday.

---

