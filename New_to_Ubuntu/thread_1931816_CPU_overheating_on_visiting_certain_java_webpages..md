---
title: "CPU overheating on visiting certain java webpages."
date: 2012-02-26
forum: New to Ubuntu
---

### Post by sbnwl on 2012-02-26
I noticed a cpu overheating problem just when I opened [_this page_]("http://www.exampleproblems.com/wiki/index.php/Fourier_Series") in firefox. A small message in bottom left side says "applet started". I opened the same page in Google Chrome, and the same result.

The "top" command shows cpu 743% busy.
It is abnormal/unacceptable. I just did "killall java" in terminal and cpu comes down to 5%. 
**What the problem is with java?**
The power drains like a hell. Heating, and fan runs at full speed. 

> Intel corei7 2670QM 2.2GHz, Ubuntu 11.10 64 bit, Gnome3, firefox, and Java Version 1.6.0_23 from Sun Microsystems Inc, as per [_http://javatester.org/version.html_]("http://javatester.org/version.html")

---

### Post by mcduck on 2012-02-26
First, any actual overheating (as in CPU temperature exceeding safe limits, instead of just heavy CPU usage) is *always* a hardware problem, due to insufficient cooling. All computer hardware is made to be able to handle sustained full load, and heat sinks, coolers etc. are designed to handle that thermal load. Failing to do so is an hardware issue, not software problem, and usually related to dust or incorrectly attached fans or heatsinks, not sufficiently appled thermal paste between the components, or sometimes simply manufacturing defects.

What comes to the web site, you might want to ask it's developers. ;) The page throws a JavaScript error, and indeed simply disabling JavaScript is enough to remove the high CPU use...

---

### Post by pqwoerituytrueiwoq on 2012-02-26
which version of java are you using? in my experence the open souce versiondoes not work as well as the official version of java

if the app still works you can use the CPU scaling applet to lower your cpu's clock speed

@mcduck
it can be a configuration issue if you are overclocking

---

### Post by sbnwl on 2012-02-26
_*@pqwoerituytrueiwoq*_
According to what I checked in synaptic, the java version is: > 6b23~pre11-0ubuntu1.11.10.2_*@mcduck*_
It is unlikely a hardware issue, cause It is a Branded Netbook, and I have tested even with Electronic Art's latest window based game through wine, and also some heavy computational FE simulations. Only then it goes to such heated levels. 

**My point is how can a simply browser component be such heavy on a core i7 QM 2.2 GHz CPU? Should it be?**

---

### Post by mcduck on 2012-02-26
> **pqwoerituytrueiwoq said:**
> 
@mcduck
it can be a configuration issue if you are overclocking
Isn't that a bit of nitpicking? :D And even then it would be a hardware issue, not software problem.

But I see your point. And of course I meant *any normal situation where the hardware is used as it's intended to be used*.

---

### Post by mcduck on 2012-02-26
> **sbnwl said:**
> _*@pqwoerituytrueiwoq*_
According to what I checked in synaptic, the java version is: _*@mcduck*_
It is unlikely a hardware issue, cause It is a Branded Netbook, and I have tested even with Electronic Art's latest window based game through wine, and also some heavy computational FE simulations. Only then it goes to such heated levels. 

**My point is how can a simply browser component be such heavy on a core i7 QM 2.2 GHz CPU? Should it be?**

sure I believe it does get hot, but that isn't the same as *overheating*. Does the system crash or behave unstable in any way? Do you get any errors, or is the CPU speed throttling down due to overheating? If not, then it's not overheating. ;) And if it is, then it's a hardware problem (in case of a new machine that would either be a manufacturing defect or faulty design)

And yes, even a simple piece of code can be extremely heavy task for a computer to run. That's maths for you. A simple logical or mathematical problem can require lots of work to solve. And since there clearly is bugs in the site's  code (based on the JavaScript errors) it isn't doing what it's supposed to do, and that can always lead to problems.

---

### Post by lovinglinux on 2012-02-26
Indeed the page uses 100% CPU and temperature goes from 56 to 80 degrees celsius on a i5 processor here. The problem occurs with Firefox and Chrome, but not with Opera.

---

### Post by pinguinhood on 2012-02-26
I had a similar problem on my Hp dv5-1080 with Ubuntu amd64. In my case the problem was the flash plugin. I had to install the original adobe's one. Has the web-page some flash content?

---

### Post by alegomaster on 2012-02-26
The reason why your cpu usage is high is probably due to poor programming by the website owner.

---

### Post by lovinglinux on 2012-02-26
> **pinguinhood said:**
> I had a similar problem on my Hp dv5-1080 with Ubuntu amd64. In my case the problem was the flash plugin. I had to install the original adobe's one. Has the web-page some flash content?

No there is no flash involved. It is a java issue.

---

### Post by sbnwl on 2012-02-26
@lovinglinux
> Indeed the page uses 100% CPU and temperature goes from 56 to 80 degrees  celsius on a i5 processor here. The problem occurs with Firefox and  Chrome, but not with Opera.

Really you tried it with opera also? It's rather interesting that opera is showing different than chrome or firefox :-?....

---

### Post by sammiev on 2012-02-26
Using FF here and only reached 50c on this addie with Sun Java. I never tried the java your using.

---

### Post by lovinglinux on 2012-02-27
> **sbnwl said:**
> @lovinglinux


Really you tried it with opera also? It's rather interesting that opera is showing different than chrome or firefox :-?....


Strike that. It was some configuration in the Opera profile. When I open that page on a clean Opera profile, it also exhibits the same issue.

---

