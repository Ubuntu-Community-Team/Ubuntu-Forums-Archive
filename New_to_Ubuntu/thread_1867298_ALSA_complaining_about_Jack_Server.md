---
title: "ALSA complaining about Jack Server"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by HolyDonut on 2011-10-22
What is a jack server? 

When I google the problem, I keep finding references to jackd and qjackctl but I don't want to install those. I don't need them right?

But every time I run a program that plays sound I get this error:

espeak hello
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

audacity
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

It's not so annoying when I try to run audacity, but it hangs espeak for a bit. 

How do I get rid of this error? I got it to go away before, but I had to reinstall Ubuntu and I can't remember what I did.

I'm using Natty Narwhal 11.04

---

### Post by HolyDonut on 2011-10-23
I fixed the problem.

I installed jackd (sudo apt-get install jackd).

Then I added this command to my startup programs: jackd -d dummy

Now the errors are gone.

---

