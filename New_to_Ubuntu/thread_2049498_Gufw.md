---
title: "Gufw"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-08-28
I use Gufw firewall. I find it so simple that i get confused to configure it. :) can any one direct me to a very basic tutorial for configuring it. Actually i do not understand its configuration interface. I find some ports being shown as "closed" and not "stealth" in the shields up test. How do i make these changes ?

---

### Post by jerome1232 on 2012-08-28
firstly if your computer is connected to a router then that's what shields up is testing, not your computer so changing your firewall configuration won't have any affect on the results. 

secondly closed is rejecting packets, "stealth" silently drops them, either one still means you're not accepting traffic on that port

---

### Post by 3dmatrix on 2012-08-29
> **jerome1232 said:**
> firstly if your computer is connected to a router then that's what shields up is testing, not your computer so changing your firewall configuration won't have any affect on the results. 

secondly closed is rejecting packets, "stealth" silently drops them, either one still means you're not accepting traffic on that port

Thanx for your reply. I am not behind a router and i know the meaning of stealth and closed and that is why i would prefer to convert the closed in to stealth - if possible,

.

---

### Post by jerome1232 on 2012-08-29
> **3dmatrix said:**
> Thanx for your reply. I am not behind a router and i know the meaning of stealth and closed and that is why i would prefer to convert the closed in to stealth - if possible,

.
 
Deny is a silent drop (stealth)
Reject sends a reject packet (closed)

If you still need clarification perhaps you can put up a screenshot of your gufw config to see what it is you have setup and to help identify any misconfiguration.

---

### Post by Ms. Daisy on 2012-08-29
Here's my favorite GUFW tutorial, makes it seem really easy.
[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

It's a matter of heated debate usually, but IMO there's no benefit to have "stealthed" ports instead of "closed." Here's one of those debates so you can decide for yourself:
[http://ubuntuforums.org/showthread.php?t=1916336](http://ubuntuforums.org/showthread.php?t=1916336)

If you decide that you'll die without "stealth" ports then that thread gives you a quick tutorial on how to do it.

---

### Post by 3dmatrix on 2012-08-31
Thanx Daisy,
I recently upgraded to 12.04 so busy with some tweeking. Will go through those tuts soon :)

---

### Post by 3dmatrix on 2012-09-01
> **Ms. Daisy said:**
> Here's my favorite GUFW tutorial, makes it seem really easy.
[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

It's a matter of heated debate usually, but IMO there's no benefit to have "stealthed" ports instead of "closed." Here's one of those debates so you can decide for yourself:
[http://ubuntuforums.org/showthread.php?t=1916336](http://ubuntuforums.org/showthread.php?t=1916336)

If you decide that you'll die without "stealth" ports then that thread gives you a quick tutorial on how to do it.

Very informative links  :)

---

### Post by 3dmatrix on 2012-09-02
I made the following changes in my UFW settings :

Status: active

To                         Action      From
--                         ------      ----
53/udp                     ALLOW OUT   Anywhere
80/tcp                     ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
53/udp                     ALLOW OUT   Anywhere (v6)
80/tcp                     ALLOW OUT   Anywhere (v6)

-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

sudo ufw default deny

Shields Up reports :

Results from scan of ports: 0-1055

    0 Ports Open
    0 Ports Closed
 1056 Ports Stealth
---------------------
 1056 Ports Tested

ALL PORTS tested were found to be: STEALTH.

TruStealth: PASSED - ALL tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

But it also reported some reverse DNS error :
Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. It seems contradictory and did not used to happen earlier.

Is there any other change that needs to make things more secure ?

---

### Post by 3dmatrix on 2012-09-03
Any sugession ?

---

### Post by Ms. Daisy on 2012-09-03
> **3dmatrix said:**
> Any sugession ? On what?  Your configuration looks good to me.  Ping is useful when you need to troubleshoot, so IMO it doesn't kill anyone to leave it enabled.  

If you follow the UFW tutorial I posted earlier, there's a section where you could use IPTables instead of UFW to drop ICMP messages, if it's super important to you.

---

### Post by 3dmatrix on 2012-09-03
> **Ms. Daisy said:**
> On what?  Your configuration looks good to me.  Ping is useful when you need to troubleshoot, so IMO it doesn't kill anyone to leave it enabled.  

If you follow the UFW tutorial I posted earlier, there's a section where you could use IPTables instead of UFW to drop ICMP messages, if it's super important to you.

I would like to know, earlier i never had to do anything 'special' to stop the ping responce. So why is it happening that way now ?

Moreover, i would also like to know how i could save the configuration file of GUFW and again reuse it whe ever needed in future ?

---

### Post by Ms. Daisy on 2012-09-03
There are probably 50 different ways to save the current configuration of UFW.  One simple way is this: you can open a terminal, type in 
```
sudo ufw enable && sudo ufw status
```
and then copy the output into a text file.

---

### Post by 3dmatrix on 2012-09-03
> **Ms. Daisy said:**
> There are probably 50 different ways to save the current configuration of UFW.  One simple way is this: you can open a terminal, type in 
```
sudo ufw enable && sudo ufw status
```
and then copy the output into a text file.

After (say) while tweeking the config goes messed up then how do we restore the last best config back ? Is there any way of just replacing the config file ?

---

