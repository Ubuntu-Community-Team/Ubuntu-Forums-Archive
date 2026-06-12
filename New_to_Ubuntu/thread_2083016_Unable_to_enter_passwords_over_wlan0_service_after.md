---
title: "Unable to enter passwords over wlan0 service after upgrade to 12.04"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by Songspirit on 2012-11-11
I upgraded to Ubuntu 12.04 LTS Nov 6 after I noticed what I thought  might be a security problem with web account passwords (I was running an  old version of 11.)

Afterwards I noticed the following items. 

1)   Several Errors due to my Nvidia driver and power management of my ASUS  computer (ACPI, Avahi-daemon, pciehp sending multiple error messages). 
    
2)  When I entered passwords online the website did not seem reload or try  to send info out. I was concerned because a https was not being  loaded.   Instead an error "System Program Error" message appeared  instead.  If i clicked report it asked for my sudo password for access  to logs (which I probably stupidly entered.. but then nothing happened.)  

 3) I added a sys monitor "GKrellM System Monitor" and noticed a  LOT of traffic on Sr0.  ?? what is this?  Google search indicates a DVD  drive, perhaps?  but I don't even have a disk in the drive. 

   4) A friend suggested I add EtherApe which I did.  When I hit enter on a  webpage to submit a password --the page changes.. (for example if I am  trying to go to facebook.com. htpps.facebook.com shows up on etherape.   When I click enter it changes to lax02s01-in-f1-le100.net,  evan.roth.com, [www.169.sedoparking.com](www.169.sedoparking.com), srv6.paul.activeminds.net, or  ae-1-60.edge7.Frankfort1.level3.net )    Can a cell phone be on a  network?  My cell phone address listed on my network as a node ??? by  etherape?  Is this even possible ????- it's not a smartphone. Just a  cheap tracfone and an old one at that.

  If I change my password  using a friends computer I can sign in on their computer.  If I try my  computer I can sign in once.  Then it won't work from mine or their  computer.   I am concerned because I do work from home and need to sign  onto the work server.  I don't feel like I can safely do that.

5)  In addition, in the logs I noticed these cryptic lines.  "The canary  thread is apparently starving." "________(my wlan0) has security, and  secrets exist.  No new secrets needed."
SCPlugin-Ifupdown: init!  ...(many more lines here looks like  if than loop.. if used then  redirects devices.. else it sets up a UVD link?? and joins a  worldcast.      	 	 	 	   Activating service name='org.freedesktop.PackageKit'  and adds something called udisks.   


Anyhow my questions are: 



Why am I unable to connect to to places online (2 days in a row - seems to work once.)  



Is it possible I have been compromised (or am I just paronoid because I don't understand linux?) 



And (sorry unrelated, mostly)  how do I exit vim?  Q won't work.  


Thank  you for you time and putting up with reading a bunch of what is  probably random nonsense from a beginner.  Please let me know if  additional information and/or specifics can be of help.  (I can post  rest of log if needed.)

---

