---
title: "Firefox3 (internet) slows Ubuntu"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Frenske on 2008-06-30
Every time I use Firefox 3 (last ubuntu-version) and have heavy internet traffic (sites with some pictures or down/up-loading files), Hardy Heron comes to grinding stop. The mouse moves slow and erratic and opening programs and even typing command lines is annoyingly slow.

Is there remedy for this? It never happened before upgrading to HH. I know it is not really a high spec computer but connectivity should not affect the computer performance I guess.

I am not sure this is related to Firefox 3 or internet traffic general.


Specs: 2.66GHz P4 with 1G RAM, Nvidia 6600GT and wireless broadband.

---

### Post by hyper_ch on 2008-06-30
open a terminal

run
```

sudo apt-get install htop

```

run
```

htop

```

leave the terminal open.... use FF... when you notice that performance issue again, have a look at the terminal... it should tell you what is using your cpu.

---

### Post by sayakb on 2008-06-30
FF is a bad resource hog. It uses up large amount of memory when you work with multiple tabs or keep it running for long. You may create a small panel launcher that would kill firefox and bring ir back up again..

---

### Post by Frenske on 2008-06-30
Oops ... I should have posted this question when using my computer at home. My 8GB quad core at work can roundhouse kick Chuck Norris while finding the answer to the meaning of life in 0.0012s ... and does use CentOS.
I guess we will have to wait till I get home.

---

### Post by lukjad on 2008-06-30
> **Frenske said:**
> Every time I use Firefox 3 (last ubuntu-version) and have heavy internet traffic (sites with some pictures or down/up-loading files), Hardy Heron comes to grinding stop. The mouse moves slow and erratic and opening programs and even typing command lines is annoyingly slow.

Is there remedy for this? It never happened before upgrading to HH. I know it is not really a high spec computer but connectivity should not affect the computer performance I guess.

I am not sure this is related to Firefox 3 or internet traffic general.

This is a well known problem (at least to me). Try this:

> Speed up Firefox with these tweaks
Computers February 25th, 2005

Does Firefox seem way slower than Internet Explorer to you? Well it certainly is out of the box. I&#8217;m not sure why they don&#8217;t make the following settings default but check these out. They may change your opinion of the browser.

firefox_icon.jpg

Type &#8220;about:config&#8221; in your firefox address bar.

Search for the following settings:

1. network.http.pipelining
Set to true
2. network.http.pipelining.firstrequest
Set to true
3. network.http.pipelining.maxrequests
Set to 32
4. network.http.proxy.pipelining
Set to true
5. nglayout.initialpaint.delay
Set to 0

Its very likely that you won&#8217;t have an entry for network.http.pipelining.firstrequest. Thats ok. Just add one.

Right-click on the preferences list, select &#8216;New&#8217; then select &#8216;Boolean&#8217;

On the first prompt, type:
network.http.pipelining.firstrequest

On the second prompt, set it to &#8216;true&#8217;

Its also likely that you won&#8217;t have an entry for nglayout.initialpaint.delay

Right-click on the preferences list, select &#8216;New&#8217; then select &#8216;Integer&#8217;

On the first prompt, type:
nglayout.initialpaint.delay

On the second prompt, set it to &#8216;0&#8242;

Thanks to MatthewHSE and rise2it of WebmasterWorld for these settings. Thanks to rona for heads up on the nglayout.initialpaint.delay also not being present. Firefox is way faster for me and has enabled me to finally bail on IE.

How does it help? These are Matthew&#8217;s words:

    Enabling the pipelining features allows the browser to make multiple requests to the server at the same time. The &#8220;maxrequests&#8221; is the maximum number of requests it will send at once. I&#8217;ve heard that 8 is the most it will send at once, but setting it higher won&#8217;t hurt, just in case. The initialpaint.delay is the length of time (in milliseconds) after the server response before the browser begins to paint the page.
Source:

[http://www.tonyspencer.com/2005/02/25/speed-up-firefox-with-these-tweaks/](http://www.tonyspencer.com/2005/02/25/speed-up-firefox-with-these-tweaks/)

Here's another (similar) link:

[http://tamnn.wordpress.com/2008/01/23/how-to-speed-up-mozilla-firefox-3-30x/](http://tamnn.wordpress.com/2008/01/23/how-to-speed-up-mozilla-firefox-3-30x/)

While your mucking around in the about:config you might want to check out the about:robots and about:mozilla. I think these last two will really help your stress levels. ;)

Hope this helped!

---

### Post by Frenske on 2008-06-30
Nah ... the about:config did not work. 'top' showed that the CPU % for firefox went up to 90%, although it was difficult to see because of the choppiness. Memory did not seem to go up about 12%. 

Seems to me that Firefox 3 is having a huge footprint on my system.

---

### Post by lukjad on 2008-06-30
> **Frenske said:**
> Nah ... the about:config did not work. 'top' showed that the CPU % for firefox went up to 90%, although it was difficult to see because of the choppiness. Memory did not seem to go up about 12%. 

Seems to me that Firefox 3 is having a huge footprint on my system.

Have you tried Seamonkey? It's basically a faster, slicker version of Firefox. I now tech gurus who swear by it except for the most highly dangerous and ad full of sites.

---

### Post by Famicommander on 2008-06-30
The latest version of Opera is the way to go if you ask me. Opera 9.5 comes standard with many things which Firefox requires and add-on for and it's generally faster and less resource-intensive.

---

### Post by roachk71 on 2008-06-30
There's another FF configuration option. Since IPv6 hasn't quite gone mainstream yet, Firefox performance could be improved considerably by disabling IPv6 DNS lookups:

Open about:config again, and change the **network.dns.disableIPv6** value to **true**. This should speed things up quite a bit.

---

### Post by d41m40u on 2008-07-17
You're not the only one.  Mine does the same exact thing, but I can't rightly remember when it all started.  Pretty recently, I'm sure.

Anyhow, I tried all of the remedies here and none of them seemed to work.  At all.

Has anyone found anything to help, or is this a mozilla bug?  I'm very tempted to roll back to 2.0

---

