---
title: "discarding command line output"
date: 2008-01-25
forum: Programming Talk
---

### Post by ayampanggang on 2008-01-25
Can't find the exact appropriate forum for this, but
how do i prevent a CLI program from outputting to the terminal?

for example when im using tcpdump or arpspoof it ouputs the packet it grabs to the terminal

i don't want that and i don't want to save the packet either, i want to just discard the output (sorta like sending them to /dev/null)

i have tried to do this:
arpspoof -t 192.168.0.1 192.168.0.2 > /dev/null and
arpspoof -t 192.168.0.1 192.168.0.2 & > /dev/null

none of them work

thank you for your help :)

---

### Post by LaRoza on 2008-01-25
Try running it in the background? I am not sure exactly what you want.

---

### Post by ghostdog74 on 2008-01-25
> **ayampanggang said:**
> 
i don't want that and i don't want to save the packet either, i want to just discard the output (sorta like sending them to /dev/null)

why would you want to do that? the purpose of tcpdump is for you to view packets for analysis. please describe your use case. If not, you can just run tcpdump with -o option ( i think , pls check the man page for the correct optoin that outputs to file ). You can view the output file later

---

### Post by geirha on 2008-01-25
> **ayampanggang said:**
> arpspoof -t 192.168.0.1 192.168.0.2 > /dev/null
That one redirects stdout to /dev/null

> **ayampanggang said:**
> arpspoof -t 192.168.0.1 192.168.0.2 & > /dev/null
Almost. Remove the space between & and >. That will redirect stdout and stderr to /dev/null.

And if you only want to redirect stderr to /dev/null, use "2> /dev/null".

---

