---
title: "Periodically Check Website"
date: 2009-04-07
forum: Programming Talk
---

### Post by DaanVB on 2009-04-07
Hi there,

I'm building my first web application and I need to be able to periodically retrieve data from another website and put in my data base. After searching for a while, cron seems like the simplest option, but my host doesn't support it. So I was wondering if there are other options.

Python might be an option, as far as I understand you can write continuously running programs with it as opposed to PHP for example (the only language I know). And my host supports it.

I'm an amateur and I really have no idea how you would deal with a problem like this. I don't even know how I would get a python program running on my host's server. Maybe that's not even possible, and by python support they might mean just the scripting capabilities (the same functionality PHP offers). I have no idea what I'm talking about, though (tried a very simple script to just print "hello", which didn't work...). Meanwhile I'll get back to learning python basics, in case it will be useful.

Thanks for taking the time to read this!

---

### Post by Eeve on 2009-04-07
You might want to have a visitor hitting the site trigger the running of your script. check if the minimum amount of time has passed since the script was last run, if so, run it before you serve up the page to the visitor or, run it concurrently. If cron is not an option. This only works if the time the script runs doesn't matter.

---

### Post by DaanVB on 2009-04-08
That last part is the problem, it needs to update every 24 hours, whether a user has been to the site or not.

I just figured I'd type in "free host cron jobs" at google, and I found a whole webpage with free hosts that allow them... I feel pretty dumb for not trying that before. Anyway, is cron the best option for this sort of thing? I'm trying to learn, and not just get my site up and running as fast as possible.

I've also tried a bit of python, got the python publisher working on my local test server. Now I understand how some websites seem to have all their dynamic content in "directories". I always thought that was weird. It's very different from PHP, pretty interesting way of doing things. I wish I could set up my own server but that seems pretty dangerous, especially with no IT background whatsoever.

---

### Post by mcla0203 on 2009-04-08
> **DaanVB said:**
> That last part is the problem, it needs to update every 24 hours, whether a user has been to the site or not.


Maybe try something like this and leave the script running?

```
#!/usr/bin/python

import time

def 

##define the function recurse
recurse():

	i = 0
 
	secs = 24*60*60

	#while its still the current day, sleep
	
	while(i < secs):

		time.sleep(1)

		i = i + 1

		j = 24*60*60 - i

		print("Seconds passed: " + str(i)+ "   ---   Seconds remaining: " + str(j));


	#Write code to update the file here.
	
	return recurse()




recurse()

```

---

### Post by johnl on 2009-04-08
I doubt that your host will allow you to run a python script in the way you want to -- more likely they simply support mod_python for apache, allowing you to use it like you use php.

Here's a simple hack:

Create a page on your website in php that does what you want to do. It can do some sanity checking on how often it runs, etc.

Create a cronjob on your local machine to hit that page every 24 hours using wget/curl/whatever.

It's not the cleanest solution, but it would work :)

---

### Post by Reiger on 2009-04-08
> **DaanVB said:**
> Python might be an option, as far as I understand you can write continuously running programs with it as opposed to PHP for example (the only language I know). And my host supports it.

Well, I doubt that your host would support you adding daemons to its server. I mean if they don't support cron why would they offer support for something which can ultimately be your own Python cron? With Python support they probably mean you can use Python instead of PHP to the same ends if your are so inclined.

However if the host allows you to install PHP extensions (or it already has) you can use APC to store a flag:

[php]
function cacheRoutine() {
 $myflag = apc_fetch('myflag');
 $ttl = 60; // time to live in the cache.
 if($myflag === false) {
  /* Connect to external site and do the data processing... Store results in db or perhaps even in the APC cache itself... ?
   */
  apc_store('myflag',true /* or some other value which does not yield false on boolean conversion */, $ttl);
 }
 // resume normal script execution.
}[/php]

If you make sure that cacheRoutine() is the first function to be called for any page request (that uses the data which requires caching) you will essentially can essentially 'hitchike' your cron job as a PHP function.

EDIT: If caching with APC is out of the question the good old modulus operator can save the day:
[php]
$ttl = 50; // some time to live in seconds.
$trigger = 4; // arbtitrary value.
if( (strtotime('now') + 1) % $tll == $trigger ) {
 // do everything you need to do...
}
[/php]
EDIT: If the update really must take place regardless of whether someone visits the site or not, then a local cron job is the way to go.

---

### Post by DaanVB on 2009-04-09
Thanks for all the replies and tips! I guess it's best that I just get a host that supports cron, I'm using a free host anyway so switching isn't a big problem. The hitch hiking methods aren't reliable. I'm not sure a host will let a script run indefinitely, they don't let you do that with PHP, so I'd guess it's the same with python. And running cron jobs from my personal computer isn't a great idea either, since it would have to be on all the time and it would defeat the whole purpose of having a host!

I've already found one that does, and the person that runs it seems very approachable so he might also allow some way to get data from other sites (something free hosts hate!) Thanks again for all the help, and at least now I know cron is the way to go. :)

---

