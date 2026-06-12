---
title: "Is there a bash command to monitor current upload/download speed?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-18
Hi, all:

Is there a bash command of some sort that will display my current upload/download speeds?  Perhaps something like:

Current Upload / Maximum Upload Speed
Current Download / Maximum Download Speed

---

### Post by ggaaron on 2008-11-18
Bash? No. But there is 'nload' application that will probably do what you want.

---

### Post by rampageoberon on 2008-11-18
You can use the 'netspeed' applet or the 'nload' application.

```
sudo aptitude install nload netspeed
```

nload is a command line application where as netspeed you can add to your panel.

Hope thats what you were looking for.

---

### Post by olejorgen on 2008-11-18
What about a nload like app that shows usage per process?

---

### Post by y@w on 2008-11-18
> **olejorgen said:**
> What about a nload like app that shows usage per process?

[http://brainstorm.ubuntu.com/idea/12915/](http://brainstorm.ubuntu.com/idea/12915/)

sudo apt-get install nethogs

---

### Post by tarahmarie on 2008-11-18
I like nload, but I seem to be having some problems getting the output to print properly in my commandwatch plasmoid.  That plasmoid displays the output of a bash command or script.  It's the only one that's given me trouble out of the ten or so similar plasmoids on my desktop.  I've attached a screenshot so you can see the "nload" command working in Tilda.  

Why might nload not display properly in a commandwatch plasmoid when all the other ones do?

---

### Post by rampageoberon on 2008-11-18
> **olejorgen said:**
> What about a nload like app that shows usage per process?

you could use iftop

```
sudo aptitude install iftop
```

---

### Post by tarahmarie on 2008-11-19
I like nload--it just doesn't make pretty output.  

I'm a bash newbie.  How would I go about taking the output of nload and turning it into this really pretty bit of output?

======================================
Network Stats on eth0 at 192.168.1.110

       Upload Speed: xx.x kBit/s
     Download Speed: xx.x kBit/s
======================================


where eth0 is my device, 192... is my IP address on the network, and the up and download speeds are registered as quickly as they are in nload.  I'm guessing it has something to do with awk and echo, but I don't know how to put them together yet.  If I could get something approximating this output, I could fiddle with it til I'm happy.

See, I want to put this command or script into the commandwatch plasmoid, cuz it will look v. nifty.

---

### Post by tarahmarie on 2008-11-28
bump

---

### Post by SeanHodges on 2008-11-28
> **tarahmarie said:**
> I like nload--it just doesn't make pretty output.  

I'm a bash newbie.  How would I go about taking the output of nload and turning it into this really pretty bit of output?

======================================
Network Stats on eth0 at 192.168.1.110

       Upload Speed: xx.x kBit/s
     Download Speed: xx.x kBit/s
======================================


where eth0 is my device, 192... is my IP address on the network, and the up and download speeds are registered as quickly as they are in nload.  I'm guessing it has something to do with awk and echo, but I don't know how to put them together yet.  If I could get something approximating this output, I could fiddle with it til I'm happy.

See, I want to put this command or script into the commandwatch plasmoid, cuz it will look v. nifty.

nload does some weird and wonderful things with the curses library, which enables it to take up the whole terminal screen. This isn't playing nice in your plasmoid. (whether this is a KDE bug or an nload one, I couldn't tell you)

I would abandon nload if I were you. It sounds like you want it to display the information differently, which isn't possible anyway.

Start with this simple command in your commandwatch plasmoid:

```
watch -n 1 cat /proc/net/dev
```

That will output the raw data on the screen, and shouldn't mess up the plasmoid. Next, you could pass /proc/net/dev into something other than the cat program. If you're feeling adventurous, write a script that converts the values into KiB's and draws them exactly where you want them.

Of course there is probably a program that does all this and more (besides nload), but someone else will have to help you there. Personally I would do the above.

---

### Post by tarahmarie on 2008-11-28
What would probably be of the most help is a template of some kind.  Nload gives me the information I want, but hours of playing with awk hasn't helped me figure out what it does or how to get it to display the values I want.  The command you just gave me looks like so much gibberish; at least nload is understandable.  That isn't to say that it might not be useful--it's just that *I* don't know how to use it--or to write the script you suggested.  Writing the script is actually what I was asking for help with; I don't know how to do more than simple scripts yet.

---

### Post by tarahmarie on 2008-11-29
bump

---

### Post by tarahmarie on 2008-12-02
bump

---

### Post by tarahmarie on 2008-12-10
bumpety bump bump

---

### Post by markp1989 on 2008-12-13
bump

---

### Post by tarahmarie on 2008-12-14
@markp1989 LOL

---

### Post by SeanHodges on 2008-12-16
> **tarahmarie said:**
> What would probably be of the most help is a template of some kind.  Nload gives me the information I want, but hours of playing with awk hasn't helped me figure out what it does or how to get it to display the values I want.

I've attached an Awk script that will extract the values from an nload screen dump. I'm not an expert on Awk and I'm sure theres a neater way to do it than this, but it does work. You will need to call it like this:

```
nload -t 0 eth0 | awk -f nload.awk.txt
```

Change "eth0" to match your device. This tells nload to return the output instead of polling repeatedly. To re-instate the polling, you'll need to do it yourself using watch:

```
watch -t "nload -t 0 eth0 | awk -f nload.awk.txt"
```

That is what you will need to put into your plasmoid.

Let me know if you have any problems, or have any questions about the script/command.

---

