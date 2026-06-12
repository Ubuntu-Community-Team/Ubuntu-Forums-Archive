---
title: "How to make safe my system from any hacker or intruders?"
date: 2023-09-07
forum: New to Ubuntu
---

### Post by neuron51 on 2023-09-07
Hi, I am new to the Ubuntu 22.04 LTS version. Before I used Zorin OS. I love Linux because of its security. However, I am not an expert to most secure my system. So I need a suggestion on how to secure my system from hacker and intruders. Thanks guys.

---

### Post by Rubi1200 on 2023-09-07
Hi and welcome to the forums :-)

Start by reading the security sticky here:
[https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

In general, the following tips would be my recommendations:

1. only install software from the official Ubuntu repositories

2. enable the firewall, which you can do in the terminal with ```
sudo ufw enable
```

3. keep the system updated and choose LTS versions

4. make sure your router/modem is secured

---

### Post by MAFoElffen on 2023-09-07
Security starts with the User. 

Most times it take some user interaction to install something that is infected. Always scan something new for viruses if installing from an untrusted source. 

The first User created in most OS'es, including Ubuntu, is an Administrative User. That way, it gives that user the rights and privilegedes to make changes to the system. There is nothing that says, that you need to use that account, except for maintenance and updates. If you use another non-admin account "daily", that does not have those rights, then changes cannot be made by viruses or other attacks to the system.

You want to be safe, but like surfing the web? Create another user, that is **not an Administrator**. My instructor in Cyber-Security would go so far, in that he personally would creating a special, separate user, that he only used to do online banking, and online bill pays... That is all that user account did from that computer user account... 

Snap Applications introduce a new Security risk factor (I'm sorry to say)... Applications installed by APT, needed admin elevation to install. APT needs digital signing and trusted signing keys for installation. With Snap app's there is now a way to introduce things into the system via non-admin User rights. Install Snap app's only through Snap install and the Snap Store at snap.io. (not outside sources)

Always use one of the main browsers, that may have security built in, or at least the ability to show the address of links, if the cursor is hovered over it, before you select it... 
Be very wary of suspicious links on webpages and emails that seem out-of-sorts. Most people don't know that Firefox contains built-in Phishing and Malware Protection in the browser to try to keep you safe. There are also add-ons/extensions, such as "Total Webshield" that add more protection. 

Security is really multi-fauceted, and not solely the responsibility of the OS, firewalls, or virus protection software. It starts with common sense of the User.

---

### Post by TheFu on 2023-09-07
> **neuron51 said:**
> Hi, I am new to the Ubuntu 22.04 LTS version. Before I used Zorin OS. I love Linux because of its security. However, I am not an expert to most secure my system. So I need a suggestion on how to secure my system from hacker and intruders. Thanks guys.

Take your computer. Unplug it from the wall both power and ethernet.  Remove all storage from the system, so if someone breaks into your home, the computer won't boot.  That's the only way.

I suspect you have slightly more risk tolerance, however.  Yes?  You are willing to accept some risks to have a working, networked, computer that connects to the internet? Yes?  If so, 

[LIST=1]
[*]Get and configure a proper network router. A router is the first line of defense for all networks.
[*]Patch and maintain the router firmware at least monthly.
[*]If you notice the router hasn't been updated in more than 2-3 months, see if it is still supported. If not, buy a new router that is supported OR switch to a more capable router which will tend to have longer support periods.  For example, my router has been maintained since 2014, whereas most consumer routers only get 3-5 yrs of support, before it is time to buy new.
[*]Don't use wifi. If the router has wifi, disable it. Wifi is netoriously non-secure. Problems that existed for 20+ yrs for all wifi protocols have been found. There is a high likeliness that at least 2 other wifi protocol errors exist based on security coding studies.  If the wifi router implementation isn't professionally performed, there could be over 20 wifi protocol errors that are critical, still being carried forward.  
[*]Never enable UPnP or WDS on the router.  These conveniences are anti-security.
[*]Connect your computer to the router using an ethernet cable. 
[*]Follow the "Ubuntu Basic Security" guidelines.
[*]Train all users to read popup dialogs, since all the security settings in the world can be undone by a single users clicking "OK" in a dialog box.  For the 10,000 decisions we make weekly, only 1 mistake can have our systems taken over completely.  If we stay away from nefarious parts of the internet, we can reduce those risks some.
[*] Patch your Ubuntu OS weekly.
[*] Only run LTS releases
[*] Migrate to a new LTS release a few MONTHS before the current release you are using ends support. Never let support lapse.
[*] Setup automatic, daily, versioned, backups.  Test the restore to ensure you are proficient.  Best to take the backup storage with you to some other location for the restore test. You'll learn much about what you forgot to bring or have included in the backups.  I can admit it took me 5 restore attempts and tweaks to what I backed up before I had a solution that was workable and sufficiently efficient on time to backup, time to restore, and storage used.
[/LIST]

---

### Post by grahammechanical on 2023-09-07
From the beginning the Ubuntu developers set out to provide a Linux distribution that was easy to use for non technical users. That does not mean that it is less secure than other Linux distributions. Unlike some distributions we cannot login as an Administrator. When we log in it is as a standard user. We are allowed to work as an Administrator temporarily when running commands entered with the prefix of sudo. Actually, the Administrator account is locked in Ubuntu. This means that if someone gets access to our machine when we are logged in they cannot make any changes to the OS because they do not know our password. Or, do they? So, please add to the list:

Keep your login password secret. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Regards

---

### Post by aljames2 on 2023-09-09
Also, be sure you know what you are doing if  you are, or thinking about, allowing any remote access to your LAN network.  Best to not allow any & have all inbound ports closed.  Otherwise, hopefully you would be using a locally hosted remote access VPN, or at least SSH with key-based authentication.  Even with these, I like to have the server that accepts this inbound traffic set up on a separate subnet at home from the real LAN net.

---

### Post by ian-weisser on 2023-12-14
The [Ubuntu Security Podcast]("https://ubuntusecuritypodcast.org"), episodes 152-154, offers a complete orientation to the topic from a Canonical security engineer, specifically made for new users.

---

### Post by #&amp;thj^% on 2023-12-14
> **ian-weisser said:**
> The [Ubuntu Security Podcast]("https://ubuntusecuritypodcast.org"), episodes 152-154, offers a complete orientation to the topic from a Canonical security engineer, specifically made for new users.
And that's a BIG +1
I Never miss a podcast, even if I have to go back and catch up on one I missed.
A whole boat load of great information to be had.

---

