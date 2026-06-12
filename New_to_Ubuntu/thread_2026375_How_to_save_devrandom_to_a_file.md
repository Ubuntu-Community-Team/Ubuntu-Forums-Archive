---
title: "How to save /dev/random to a file?"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by electronbee on 2012-07-15
So, I ask this as I have not figured it out. Other flavors of Linux use RNDCTL which has a -S switch to save the pool. But, Ubuntu does not. 

Is there a way to do this? maybe with a "cat" command or the like?

In case you are wondering, I am using [video_entropyd]("http://www.vanheusden.com/ved/") and I'd like to save the randomly generated numbers.

Thanks...

---

### Post by codemaniac on 2012-07-15
> **electronbee said:**
> So, I ask this as I have not figured it out. Other flavors of Linux use RNDCTL which has a -S switch to save the pool. But, Ubuntu does not. 

Is there a way to do this? maybe with a "cat" command or the like?

In case you are wondering, I am using [video_entropyd]("http://www.vanheusden.com/ved/") and I'd like to save the randomly generated numbers.

Thanks...

In bash there is $RANDOM for you to generate random variables .
Each time this is referenced, a random integer between 0 and 32767 is generated.

---

### Post by codemaniac on 2012-07-15
```
od -An -N2 -i /dev/random
```

The command also extracts a 2 byte decimal integer using od from /dev/random.

---

### Post by electronbee on 2012-07-15
I just turned of the laptop with the random number generator plugged in! DOH!

Is there a way to read out the entire /dev/random into a file?

As a quick background, I'm using Americium-241 from a smoke detector which emits alpha and gamma particle. These particles hit a webcam sensor. If you watch it all you see if a bunch of "white flecks" within the monitoring window as the particles hit the CMOS.

The program I referenced within the first post, takes two images taken at random times, then creates a random number from them. As the particles hit the CMOS randomly each time, it's aid that these number strings are purely random and "cryptographically strong".

So, I wanted to take the entire pool. Or, possibly save the output on a continuous basis over time appended to a file. And then, the next step which I have to look at, is test them against the NIST tests which determine how random the pool actually is.

---

### Post by codemaniac on 2012-07-15
> **electronbee said:**
> I just turned of the laptop with the random number generator plugged in! DOH!

Is there a way to read out the entire /dev/random into a file?

As a quick background, I'm using Americium-241 from a smoke detector which emits alpha and gamma particle. These particles hit a webcam sensor. If you watch it all you see if a bunch of "white flecks" within the monitoring window as the particles hit the CMOS.

The program I referenced within the first post, takes two images taken at random times, then creates a random number from them. As the particles hit the CMOS randomly each time, it's aid that these number strings are purely random and "cryptographically strong".

So, I wanted to take the entire pool. Or, possibly save the output on a continuous basis over time appended to a file. And then, the next step which I have to look at, is test them against the NIST tests which determine how random the pool actually is.

You can always call the above commandline from a loop construct to create a pool of cryptographically strong numbers .

---

### Post by mcduck on 2012-07-15
> **codemaniac said:**
> You can always call the above commandline from a loop construct to create a pool of cryptographically strong numbers .

...in that case you might want to use /dev/urandom instead of /dev/random. 

/dev/random is cryptographically stronger, but will block if the entropy level gets too low, as would happen if you tried to read large amounts of random data from it. /dev/urandom allows reusing data from the pool, so it can produce larger amounts of random data.

(of course you could also just make the loop pause long enough between the reads to allow the entropy to stay at acceptable level and avoid the blocking)

---

### Post by codemaniac on 2012-07-15
/dev/random is high quality entropy, generated from events which are non-deterministic and with "environmental noise". 

**It blocks until enough bits of random data are available. **

Hence it can block for a long time waiting for new user-generated entry to be entered into the system. So you have to use care before using /dev/random .maybe adding appropriate sleep or other means .

/dev/urandom on the other hand isn't as secure, but it's enough for most applications.You are probably better off using /dev/urandom to choose a random seed, and then using a good, fast RNG.

---

### Post by HermanAB on 2012-07-15
Use data definition (dd):
sudo dd if=/dev/urandom of=/dev/bignoise bs=1000 count=1M

---

### Post by electronbee on 2012-07-15
Awesome! I'm learning quite a bit. I had a heck of a time trying to find this via searching on the internet, which is why I came here. 

Quick question, when I write out /dev/random I essentially "empty" that pool and it has to be refilled?

I'll give these a shot tonight. I definitely want to pull from /dev/random as I want the "strong" number sets.

A cron job, calling video_entropyd, every two minutes, would probably suffice to fill /dev/random, followed by writing the data?

---

### Post by codemaniac on 2012-07-16
> **electronbee said:**
> 
Quick question, when I write out /dev/random I essentially "empty" that pool and it has to be refilled?


Yes you are right . When the entropy pool is empty, reads from /dev/random will block until additional environmental noise is gathered .
It will kind of  "hang" when there's no more collected entropy available to generate high-quality random numbers.

---

### Post by electronbee on 2012-07-18
About how fast does it take to generate enough data to fill the entropy pool? Like, seconds or minutes? I was going to have the cron job run the process once every two minutes or so. I'll find out then how fast it fills.

---

### Post by codemaniac on 2012-07-18
> **electronbee said:**
> About how fast does it take to generate enough data to fill the entropy pool? Like, seconds or minutes? I was going to have the cron job run the process once every two minutes or so. I'll find out then how fast it fills.

Depends upon your system's ability to create enough environmental noise .

The Linux kernel generates entropy from keyboard timings, mouse movements, and IDE timings and makes the random character data available to other operating system processes to /dev/random file.

---

### Post by mcduck on 2012-07-18
> **electronbee said:**
> About how fast does it take to generate enough data to fill the entropy pool? Like, seconds or minutes? I was going to have the cron job run the process once every two minutes or so. I'll find out then how fast it fills.

Every two minutes should be OK for a reasonable amount of random data, at least as long as the computer is used for something else at the same time (there needs to be something happening on the machine so that there is something creating the random noise to fill the pool).

The default random pool size for Ubuntu's kernel is 4096  bytes. (of course you might not always have enough random dat in the pool to get that much out of it). If you need anything more than that, or if you need to read random data often, you should use /dev/urandom instead. As instructed in the man page for Linux random devices:
> If you are unsure about whether you should use /dev/random or /dev/urandom,
       then probably you want to use the latter.  As a general rule, /dev/urandom
       should be used for everything except long-lived GPG/SSL/SSH keys.

---

### Post by electronbee on 2012-07-18
So, does the video_entropyd program work with the built in random number generation? Or, does it totally replace it?

---

### Post by mcduck on 2012-07-19
> **electronbee said:**
> So, does the video_entropyd program work with the built in random number generation? Or, does it totally replace it?

First time I even hear aboutr video_entropyd, but based on the descri-ption on the project's wenb site it works with the built-in random system, increasing the entropy in the pool by using data from the web cam.

---

### Post by electronbee on 2012-07-19
The guy also has a server as well to serve random data to other computers, if one likes.

So, I guess the webcam input will allow for more random number generation when the user is away from the computer?

---

### Post by mcduck on 2012-07-20
> **electronbee said:**
> The guy also has a server as well to serve random data to other computers, if one likes.

So, I guess the webcam input will allow for more random number generation when the user is away from the computer?

yes, although even then there has to be something moving in front of the camera, since the random data is generated from *changes* in the images the camera takes. Pointing the camera to look out of the window, for example, should do the trick. And pointing it to an empty room of course doesn't...


(I would personally consider random data coming from a web server pretty much pointless for security purposes. I'd say /dev/urandom would be much better source for random data).

---

### Post by electronbee on 2012-07-20
I'm using some Americium 241 in front of the webcamera which is in a light-proof enclosure. When you look at it normally, like normally through an app, you see pixels go off as the Am241 emits alpha/gamma particles.

Any ways, is there a way to time how fast the entropy pool fills up? Or, posisbly check the status... Maybe by trying to write out /dev/random via a cron job every 5 seconds or so and once is full it will no longer block the write out?

---

