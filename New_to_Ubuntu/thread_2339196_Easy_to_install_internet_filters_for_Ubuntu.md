---
title: "Easy to install internet filters for Ubuntu?"
date: 2016-10-05
forum: New to Ubuntu
---

### Post by vasilios3 on 2016-10-05
Hello.  I am a novice Ubuntu user.  Currently I am using Ubuntu 14.04, and I was wondering if there are step by step instructions or easy to install (via Ubuntu software center) internet filters available.  

Thank you.

---

### Post by &amp;KyT$0P# on 2016-10-06
What kind of internet filter?
What are you trying to achieve with it?

---

### Post by colmax on 2016-10-06
Generally your browser (ie: firefox) has security settings or some plug-ins that can block adds etc
Firewall settings i know very little about sorry
Cheers

---

### Post by leunam12 on 2016-10-08
Opendns

---

### Post by vasilios3 on 2016-10-10
Sorry, I meant to say I am looking for filters that block adult content and are easy to install for a new user.

---

### Post by &amp;KyT$0P# on 2016-10-10
+1 for leunam12 suggestion, [OpenDNS]("https://www.opendns.com/setupguide/?url=familyshield") is probably the simplest option for you.  I don't use it myself but everyone I know who uses it likes it.

NetworkManager menu > Edit connections > (your connection), Edit.  Under IPv4 settings, set "Automatic (DHCP) addresses only".  See where it says "Additional DNS servers"?  Paste in those IP addresses from the link, separated by comma.

You might need to disconnect then reconnect the network for the change to take effect.

---

### Post by mastablasta on 2016-10-11
there used to be something called gnome nanny 

also check here: [SIZE=2]https://help.ubuntu.com/community/ParentalControls
[/SIZE]
i don't support censorship, as i believe in education rather than obscuring things from the young minds. but i understand some institutions might want to do this.

---

### Post by leunam12 on 2016-10-15
It is better to setup OpenDNS at router level if the router allows it, that way all computers are protected. How to do it? it varies according to router manufacturer and model. Search the manual for your particular router to see if there is an option to use fixed DNS

---

