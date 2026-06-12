---
title: "Cannot add ppa with synaptic"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2013-10-19
Hi,

Whenever I try to add a ppa to synaptic and reload I always get 404 error, however using the terminal with the command "sudo add-apt-repository XXX" and then "sudo apt-get update" the packages are located without problem, afterwards reloading in synaptic has no problem either.

This happens on Ubuntu 13.10. I am wondering if it is a bug in synaptic.

---

### Post by heir4c on 2013-10-19
When you get a 404 error than it don't exist no more or not yet created. (In the last possibility it is not yet compatible with 13.10) 
What ppa will you add?

---

### Post by monkeybrain20122 on 2013-10-19
> **heir4c said:**
> When you get a 404 error than it don't exist no more or not yet created. (In the last possibility it is not yet compatible with 13.10) 
What ppa will you add?

But command line works.

Any random ppa I tried/

---

### Post by heir4c on 2013-10-19
Ok, sorry I misunderstood that.

---

### Post by monkeybrain20122 on 2013-10-19
Seems that somehow synaptic doesn't add the correct line to sources.list. I will do some investigation later. Just wonder why no one seems to experience this as I think synaptic is widely used. 
P.S. After a re install the problem persists.

---

### Post by newb85 on 2013-10-19
I suspect synaptic's user base is shrinking.  Software Center works well for many people's needs, and there are powerful command-line tools for more advanced tasks.

(I do still like to keep synaptic around, but I very rarely use it.)

---

### Post by mc4man on 2013-10-19
Excuse my ignorance but how do you add a ppa thru synaptic?

---

### Post by silvagroup on 2013-10-19
Haven't tried adding with synaptic that is next but when I try to add usiing with add-apt-repository, and get command not found. Installed python-software-properties and software-properties-commons rebooted even and still get command not found error. Tried dropping to su and will not get autehticatication failure after entering password. Seems like it's a super user porblem so sudo is not finding command thereby no command found. Bug maybe?

Ok got into super, dumb on my part forgot had to do sudo -i instead of the Linux su variants, was able to run command, but still shoudl be able to do using sudo shouldn't have to drop to super. Not sure will check maybe something has changed, just upgraded to 13.10 and need to add user to sudo or something like that.

---

### Post by monkeybrain20122 on 2013-10-19
> **mc4man said:**
> Excuse my ignorance but how do you add a ppa thru synaptic?

Basically the same as adding through software-properties-gtk (and USC uses the same interface, I think, but I never use the USC)

---

### Post by mc4man on 2013-10-19
> **monkeybrain20122 said:**
> Basically the same as adding through software-properties-gtk (and USC uses the same interface, I think, but I never use the USC)

Well that may be an issue with software-properties-gtk or software-properties-gtk opened thru synaptic??
What happens  if you try to add a ppa by opening  software-properties-gtk directly?

---

### Post by mc4man on 2013-10-19
Just took a look at "add"ing a ppa thru software-properties-gtk, ie. using an apt line to add one of my ppa's to this install **that wasn't previously added**
Seems a bit pointless & unnecessarily complicated when it's all set up & quite easy to do using add-apt-repository
(all new ppa's just show the add-apt, not Apt line

---

### Post by monkeybrain20122 on 2013-10-19
> **mc4man said:**
> Well that may be an issue with software-properties-gtk or software-properties-gtk opened thru synaptic??
What happens  if you try to add a ppa by opening  software-properties-gtk directly?

Hi, it is very strange. I just tried adding a ppa directly to sofware-propreties-gtk and it worked. I closed synaptic, restarted  it and add another one (a different one, which didn't work before) through synaptic and it is working now!!

I notice the only difference is that, when I added the ppa to software-propreties-gtk via synaptic before, the url that showed up in software-properties-gtk was like "**[http://ppa:launchpad.net/marutter/rrutter/ubuntu](http://ppa:launchpad.net/marutter/rrutter/ubuntu)** saucy main" and it didn't work, now  it is"**[http://ppa:launchpad.net/marutter/rrutter/ubuntu](http://ppa:launchpad.net/marutter/rrutter/ubuntu)** **saucy** main"  and it is working. Notice the bold in "saucy".

---

### Post by monkeybrain20122 on 2013-10-20
I find the same problem with Lubuntu 13.10 32 bit on a different machine. Moreover, this time the work around above didn't work (enter a ppa into software-properties-gtk directly once and then work afterwards just by invoking software-properties-gtk in synaptic) In the case of lubuntu directly entering into software-properties-gtk gets the same error  and 'saucy" is not bold.

---

### Post by monkeybrain20122 on 2013-10-21
This person reported a similar problem. 
[http://ubuntuforums.org/showthread.php?t=2181813&page=2&p=12821745#post12821745](http://ubuntuforums.org/showthread.php?t=2181813&page=2&p=12821745#post12821745)

As I said above, it works now for my Ubuntu 13.04 64 bit but I still can't get it to work in lubuntu.

---

### Post by monkeybrain20122 on 2013-10-22
Anyone?

---

