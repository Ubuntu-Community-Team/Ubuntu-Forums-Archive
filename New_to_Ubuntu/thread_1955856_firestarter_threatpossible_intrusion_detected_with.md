---
title: "firestarter threat/possible intrusion detected with chkroot/rkhunter"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by williamchan on 2012-04-10
Hi all. Forgive me as I am new. I got the firestarter firewall gui deal app. I know its jsut a interface for the real firewall. I noticed there is a constant blocked ip from south korea on several ports with the length of the most being 60 seconds. first it was in the service bar as http-alt, then unknown, then telnet, then http, then unknown.

It shows these as blocked. Should I be concerned. It shows them as 2 serious threats. Why am I getting this? What makes me of interest? keep in mind the source ip changes but goes back to korea on each one.

in this I ran the chkroot and rkhunter. I did not have any roots or malware as it shows none not found etc but the typical so called false positive warning of 
/usr/bin/unhide.rb
/usr/bin/curl

group and account check says password found. I assume this is normal?

the system boot check gives this:
checking for local host name [FOUND]
checking for system startup files [FOUND]
checking system startup for malware [NOT FOUND]

system config checks:
checking for SSH config file [FOUND]
checking if SSH root access is allowed [WARNING]
SSH Protocol vl [NOT ALLOWED]
running syslog daemon [FOUND]
sys log config file [FOUND]
syslog remote logging allowed [NOT ALLOWED]

Basically all the checkers show the same info and false positves i researched into already except I am unsure of the /usr/bin/unhide.rb /usr/bin/curl It also shows listed number of files checked with that number then under the Suspect files 2.

Shows no rootkits or malware. I am assuming im safe but making sure. ANy thoughts?
Now I did do the unhide command in one of the root kit scans. I am not sure if the /usr/bin/unhide.rb has anything to do with that?

If needing further let me know and ill get on that pc and paste here the scans etc. but overall what do you think? I apologize just little concerned bc that south korea threat keeps being blocked. Now my firestarter did at one point have a ip address allowed at boot up and i dont know if a update did it or what. this was my concern. I also had shattery graphics at the screen but it has done this before on fresh installs not connected to net, but this time had text it appeared in it. but things look fine now.

thanks
Will Chan

---

### Post by williamchan on 2012-04-10
I believe I am safe after more checking as found false positives that been listed. But any thoughts and what can  I do to better the security of ubuntu?

---

### Post by Cheesemill on 2012-04-10
> **williamchan said:**
> I believe I am safe after more checking as found false positives that been listed. But any thoughts and what can  I do to better the security of ubuntu?
Start with this sticky from the Security Discussions forum:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

