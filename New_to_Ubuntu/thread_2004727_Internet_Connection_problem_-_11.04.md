---
title: "Internet Connection problem - 11.04"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by syteanric on 2012-06-16
Hello everyone Apologies if this is already posted, ui have looked around but not been able to find it

I am looking for a little help with internet connection problems, first a little information regarding my system which may help

3.0 ghz Pentium 4

2 GB Ram

using neat gear WG111v3 Wireless USB dongle

running Ubuntu 11.04natty Narwhal 2.14 (I think).38

I am using the standard network tool that comes "Out of the box" so to speak.

the problem i am having, The system seems to think that I am not connected to the internet when it is showing a connection fine. when i connect to a web site in firefox it says "looking up" in the window before coming up with the Page Not Found screen after a while.

The internet seems fine at first boot of the computer for the day and seems to stay connected for around 10-15 minutes before the problems i am having. I have tried a few fixes and i will mention them now to ensure we dont go over old ground:

1: Reconnecting - this works for about 1 minute then stops
2. Rebooting - this has a terrible result and once i have entered my password into the keyring seems to not recognise i am connected to the internet at all
3 using different browsers, Arora, Chrome and Firefox - to be fair Arora works, but very slowly, chrome and firefox either work fine for a few minutes or fail to find the page i am looking for.
4. I run no firewall
5. system test - the results here are interesting, when i run system test it tells me i have no Internet connection on my system at all, this is the opposite!

The problem has been occuring for a couple of months. I know a little bit about Ubuntu and Linux and will occasionally try new things and be adventurous, howevr I havent done anything relating to online settings or the internet through the terminal or otherwise.

I am stumped as to why this is happening and am hoping you can all offer some kind of fix, as above it worked like a dream for so long and now just seems to not work at all....

last tidbit of info - i have a windows (Yuck!) duel boot on my system, which i am using now to post this, the internet works no problem but does occasionalyl drop out just due to the cheap  Dongle i use. I NEVER had the problem on ubuntu until about 2 months ago.

I cant watch youtube videos, Download files for work etc as the internet just isnt recognised on ubuntu. I need my computer as i work as a sports coach so need to download rosters, training schedules etc.. its getting t the point this is not possible.. Help!

Thanks in advance!:)

---

### Post by rdsnc on 2012-06-16
Just a guess here,  but it sounds like you may be having DNS issues.
Open a command window and type

ping 74.125.45.101
if it works, try 
ping google.com
and see if the DNS server does its job and translates the URL into an IP address.

If you want to try a different DNS server, try calling your ISP and get a couple of DNS Server addresses, and put them (at the top) in  /etc/resolv.conf.

---

### Post by syteanric on 2012-06-17
seems ok now, thanks RDSNC, if it breaks again i will contact my ISP.

i wonder why it was ok only a few weeks back though.

---

