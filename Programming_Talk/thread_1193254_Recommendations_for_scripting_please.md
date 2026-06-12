---
title: "Recommendations for scripting please"
date: 2009-06-21
forum: Programming Talk
---

### Post by mtbsoft on 2009-06-21
Hi all,

Just wanting a little advice about best choice of scripting languages please...

I recently signed up to prepaid mobile broadband (12Gb quota over a 12 month period, with 3) for when I am unable to use my client's or work's wireless.  I'm wanting to create a small script which I can use in conky to show my bandwidth usage so that I don't run out without warning - all automatic communication with 3 is stupidly via SMS(!), not email.  

I've set up vnstat to monitor the mobile connection and can get at the vnstat data in monthly (or raw) format but I need to add the values up then deduct it from my total allowance, finally formatting it for conky.

So, before I start down the track of writing the script, I'd appreciate advice on the most suitable scripting language for the job - I've been writing software for well over 20 years but mainly using a certain large monopoly's software (hangs head...) so have little coding experience in Linux.

I'm not wanting anyone to do the job for me - I'm looking forward to the task as it'll be the first real development (albeit small) I've done on Linux (which I've been using for two years).  

I'd just like someone to suggest the better/best language to start looking at so I don't spend too long using the wrong one, before realising my mistake.

I'm guessing at Python, based on my experience with conky, but any advice will be much appreciated.

---

### Post by x22 on 2009-06-21
recommend "awk"--well designed for parsing lines, adding up
the numbers, doing arithmetic, and the formatted printing of
reports.  

small, powerful, and easy to use

---

### Post by mtbsoft on 2009-06-21
> **x22 said:**
> recommend "awk"--well designed for parsing lines, adding up
the numbers, doing arithmetic, and the formatted printing of
reports.  

small, powerful, and easy to use

Excellent.  Had a quick look at some on-line resources and I can see what you mean, looks just the ticket.

Thanks for that.

---

### Post by mali2297 on 2009-06-21
When you have finished the script, please share it. I would be interested in the solution.

---

### Post by cubeist on 2009-06-21
The new version of conky (1.7.1) supports native lua scripts, but I cannot endorse it because I have never scripted with it.  But, it appears to be a fairly powerful language.

---

### Post by soltanis on 2009-06-21
awk is the cheap and easy way to tie unix utilities together, perl might also suit you if the script becomes too big/complex for awk. Good choice.

---

### Post by mtbsoft on 2009-06-22
Right, well that wasn't too hard after all - awk is nice, I like it!

The awk script is as follows:

```
($1 == "totalrx") { totrx += $2; tot += $2 } 
($1 == "totaltx") { tottx += $2; tot += $2 } 
END { printf "Rx: %6.3fGb     Quota to 16-4: %6.3fGb     Tx: %6.3fGb\n", totrx / 1024, (11575 - tot) / 1024, tottx / 1024}
```

...where the 11575 figure is my current remaining quota (Mb, to be used by 16-4) - I have reset the vnstat values for my ppp0 connection so the two now coincide. The printf statement is formatted to print 57 characters wide as this will nicely slot into my conky display...

```
${if_empty ${exec python ~/Scripts/ppp0.py}}${color #CC0000}3 MOBILE (${addr ppp0}) ${color steel blue}${hr 2}${color #CC0000}
Down: ${downspeed ppp0}kB/s ${alignr} Up: ${upspeed ppp0}kB/s
Total: ${totaldown ppp0} ${alignr} Total: ${totalup ppp0}${alignr}
**${exec vnstat --dumpdb | awk -F\; -f ~/Scripts/vnstat.awk}**
${upspeedgraph ppp0 20,195 333333 cc3333} ${alignr}${downspeedgraph ppp0 20,195 333333 cc3333}${color #000000} 

```

Hope this is useful to others, it would be fairly easy to adapt to a monthly plan rather than an annual one like I have.  Please feel free to critique my solution - I'm more than happy to learn better ways to do this (but be gentle!).

---

### Post by soltanis on 2009-06-22
How does that program keep track of your total bandwidth usage (does it dump numbers to an output file when it finishes executing, or does it start over every time?)

---

### Post by mtbsoft on 2009-06-22
> **soltanis said:**
> How does that program keep track of your total bandwidth usage (does it dump numbers to an output file when it finishes executing, or does it start over every time?)

vnstat does all the work via a cron job, I just tap into the data with my script - read all about vnstat [here]("http://freshmeat.net/projects/vnstat/").

That said, running the thing via conky for a while has shown a problem - for some reason, the output from vnstat is not being suppressed all the time and is appearing in the conky window... back to the drawing board!

edit: the problem appears to be with the awk script, it seems to work the first few times (run manually from a terminal windows) then decides to list all lines despite matching the correct ones.  Hmm...

---

### Post by ghostdog74 on 2009-06-22
awk is supposed to do what it should, provided you give it the correct pattern to match. check your output that is passed to awk.

---

### Post by mtbsoft on 2009-06-23
> **ghostdog74 said:**
> awk is supposed to do what it should, provided you give it the correct pattern to match. check your output that is passed to awk.
Oh don't get me wrong, I'm certain the the error lies with me, I just can't see it at the moment.  

I've checked both halves independently from one-another and am simply getting inconsistent results - I just need to do a little more investigation to see why the pattern seems to match sometimes and not the others.

---

### Post by mtbsoft on 2009-06-23
Ah well, go figure, it's working now.  

I think I must have managed to get a non-printing character in there, either in the awk or the conky script which broke things - I updated them both to add parameters to the awk script (for debugging) and the problem went away.  Can't reproduce it now.

The new version of the script takes the remaining quota and the end date as parameters, passed in via the conky exec call...

```
/totalrx;/ { totrx += $2; tot += $2 } 
/totaltx;/ { tottx += $2; tot += $2 } 
END { printf "Rx: %6.3fGb     Quota to **" enddate "**: %6.3fGb     Tx: %6.3fGb\n", totrx / 1024, (**quota** - tot) / 1024, tottx / 1024}
```

...and...

```
${if_empty ${exec python ~/Scripts/ppp0.py}}${color #CC0000}3 MOBILE (${addr ppp0}) ${color steel blue}${hr 2}${color #CC0000}
Down: ${downspeed ppp0}kB/s ${alignr} Up: ${upspeed ppp0}kB/s
Total: ${totaldown ppp0} ${alignr} Total: ${totalup ppp0}${alignr}
${exec vnstat --dumpdb | awk -F\; -f ~/Scripts/vnstat.awk **enddate="16-4" quota=11575**}
${upspeedgraph ppp0 20,195 333333 cc3333} ${alignr}${downspeedgraph ppp0 20,195 333333 cc3333}${color #000000} 

```

---

