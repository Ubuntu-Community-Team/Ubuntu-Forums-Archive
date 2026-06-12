---
title: "Can't run Tor browser bundle."
date: 2012-07-22
forum: New to Ubuntu
---

### Post by Sematary on 2012-07-22
First, I do love the Ubuntu OS but I've come across one of those situations where I can't "just do" what I want to do and no matter how I try to solve it, the problem remains. 

In this instance...

I want to use TOR for my browsing. TOR is already running as a service in 12.04 (excellent).
I install Vidalia (so far so good)

I run Vidalia (now the problems start)

Vidalia detected that the Tor software exited unexpectedly.

I installed the TOR bundle on my Win 7 machine - works like a charm.
I'm protected. Linux - not so much. Can't get it to work. Totally frustrated. I just want the damn thing to work. Why are there so many hoops and why is it that sometimes, no matter what you do, you just can't get stuff to work?

---

### Post by Hadaka on 2012-07-22
perhaps this will be of some help.

[https://www.torproject.org/docs/debian-vidalia.html.en](https://www.torproject.org/docs/debian-vidalia.html.en)

---

### Post by DanR01 on 2012-07-22
I would suggest using the tor browser bundle for Linux.

Uninstall vidalia and the tor package if you have them installed via the repos as the packages seem to conflict with each other.

---

### Post by krustenBrot on 2012-07-22
The Browser Bundle works without a single problem. At least for me.

The good thing is, Ubuntu ( or OSS in general ) is **free**. What means you do not have to pay for using it, try it, use it if you like, and if not do not use it. :)

---

### Post by jonnyboysmithy on 2012-07-22
I installed the firefox plugin for tor, worked like a charm. I can't remember if I had to specifically install other things (vidalia etc..) but the plugin worked like a charm. Perhaps try that?

---

### Post by mastablasta on 2012-07-22
there are also linux distrubutions that are more protected than just having TOR. For example Liberte LInux is quite good.

---

### Post by Sematary on 2012-07-22
> **Hadaka said:**
> perhaps this will be of some help.

[https://www.torproject.org/docs/debian-vidalia.html.en](https://www.torproject.org/docs/debian-vidalia.html.en)

I tried that but when I attempted to export the key it failed. Everything else seemed to go alright. Still no happiness. :-(
lol

I'm sure I'll figure it out.
I'm going to be purchasing a vpn from BTguard anyway to replace the proxy service from them that I've been very happy with so that is probably the way to go.

---

### Post by Sematary on 2012-07-22
> **jonnyboysmithy said:**
> I installed the firefox plugin for tor, worked like a charm. I can't remember if I had to specifically install other things (vidalia etc..) but the plugin worked like a charm. Perhaps try that?

I downloaded it - couldn't figure out how to install it. Maybe I was too tired last night. I'll plug away at it another time.

---

### Post by Sematary on 2012-07-22
I think some of the point of my post has been lost. I'm the type that is willing to plug away at a problem till I either find a solution (more often than not) or find an alternate solution (sometimes) or simply give up (occasionally). This is not true of the average person. In order for the average person to be completely happy with Linux, it will have to work as easily as Windows does - which is to say, you should be able to get what you want, install it, and have it work.

---

### Post by DanR01 on 2012-07-22
I agree that Linux can require more effort than Windows. IMHO I think that the rewards are probably greater though.

As regards your specific problem - installing Tor, the solution is to use the browser bundle. The method suggested here:

[https://www.torproject.org/docs/debian-vidalia.html.en](https://www.torproject.org/docs/debian-vidalia.html.en)

is no longer recommended.

You can download the bundle for Linux here: 

[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)
 and follow the instructions.

If you run into problems I would be happy to try and help.

Regards

---

### Post by cwsnyder on 2012-07-22
If you are really paranoid, I mean concerned about your browsing privacy :-p, even straight TOR isn't really enough.  Look into browsing using a Live CD or USB with TOR, such as [https://tails.boum.org/](https://tails.boum.org/) for Tails Linux, which is a Debian derivative.

---

### Post by Zill on 2012-07-22
> **Sematary said:**
> I think some of the point of my post has been lost. I'm the type that is willing to plug away at a problem till I either find a solution (more often than not) or find an alternate solution (sometimes) or simply give up (occasionally). This is not true of the average person. In order for the average person to be completely happy with Linux, it will have to work as easily as Windows does - which is to say, you should be able to get what you want, install it, and have it work.
You might find this link helpful...

[Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by ub07 on 2012-07-22
> **Sematary said:**
> I think some of the point of my post has been lost. I'm the type that is willing to plug away at a problem till I either find a solution (more often than not) or find an alternate solution (sometimes) or simply give up (occasionally). This is not true of the average person. In order for the average person to be completely happy with Linux, it will have to work as easily as Windows does - which is to say, you should be able to get what you want, install it, and have it work.

Linux is not for everyone. Indeed, you have to be willing to put in an effort to get things working the way you want. But it is very rewarding because you almost always learn something and the result is very much your own system. That's why you see everyone here having sometimes very different problems ... once the problems are ironed out and you've customized it to your liking, the system is uniquely yours. You don't get that with Windows. Everyone's Windows system is nearly identical.

---

### Post by uRock on 2012-07-22
Back on topic,

I was having the same problem with Vidalia and Tor. I had to chown to do the following via the terminal,```
cd /var/run/tor
sudo chown username:username control.authcookie
```The above command made the user(insert your username into the command) the owner of the control.authcookie so that it can run properly. After doing this, I used the terminal to launch the downloaded Tor browser, which is located in my Downloads folder,```
cd Downloads/tor-browser_en-US/ && ./start-tor-browser
```You may first need to make the start-tor-browser executable which is done by **cd**ing to the directory holding the file, then using the **chmod +x** command.

I changed the title of the thread in hopes of answering your question instad of arguing over frustrations.

---

### Post by jonnyboysmithy on 2012-07-22
If you're still interested in installing the plugin, it can be found on this page: [https://www.torproject.org/torbutton/index.html.en](https://www.torproject.org/torbutton/index.html.en)
Quoting from the page> **Expert Install (Stable):** Click to [install from this website]("https://www.torproject.org/dist/torbutton/torbutton-current.xpi").

---

### Post by patriciu25 on 2013-05-25
Had the same problem and I was very frustrated by it. I managed to get tor browser working. **Just drag the "start tot browser" file to the opened terminal and then press enter**. That's how it worked in my case. Tried anything else without results.

---

### Post by RoyBinder1972 on 2013-05-25
using TOR in linux ubuntu is much more easy than in windows:
1. install "foxy proxy" in your firefox" browser
2. open the command line and type "apt-get install tor"
3. after installing config firefox using "foxy proxy" to 127.0.0.1 , port 9050 , and use sock 4.
thats it!

---

