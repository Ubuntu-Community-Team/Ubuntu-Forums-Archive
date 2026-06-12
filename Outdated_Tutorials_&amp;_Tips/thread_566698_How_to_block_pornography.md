---
title: "How to block pornography"
date: 2007-10-03
forum: Outdated Tutorials &amp; Tips
---

### Post by nitep on 2007-10-03
You can use OpenDNS ("http://www.opendns.com/") to block porn, phishing, domains such as some chat rooms etc. to keep your computer safe for your children, grandchildren etc. This an off site filter so it will not slow your computer like on site filters such as netnanny and DansGuardian web content filtering.  

When your computer goes to a website, the name has to be translated to an IP (internet protocol address). OpenDNS can do this faster than your ISP. (internet service provider) For them to do this the DNS addresses in your computer have to be changed to 208.67.222.222 and 208.67.220.220 as this is the IP of OpenDNS so OpenDNS will process the translation.

When you first go to OpenDNS will ask you to choose your operating system from a list so that they can tell you how to put those DNS addresses in your computer.

You can now open an account with them. 
Then click on their networks tab and click on add this network.
The next step is to click on their settings tab to choose what level of undesirable web page blocking you want. You will be given a list and you can tick all the options.

You can also block domains. For example if your children are using a chat website where you think an adult could lure them to a liason, then you can block access to that website etc. You should also block the domains images.google.com and images.search.yahoo.com . Although you can set these browsers to safe search, any child can reset that.

Your computer also has an IP given to you by your ISP. If you have broadband then you will probably have a static IP which you will see in your OpenDNS settings when you set up a network. Your job is now done.

If your ISP gives you a dynamic IP as most do with dial up then your IP changes whenever you connect to your ISP. OpenDNS can only recognise your computer from the IP it has stored with your account so here is where it gets a little difficult.

With a dynamic IP you have to get a program ("http://www.opendns.com/support/dynamic_ip_downloads/") that will run on your computer to check your computer IP and when it changes, notify OpenDNS so they know who you are and can use your blocking information. When set up this is all automatic.

If you run into trouble then you can get more help at the OpenDNS forum ("http://forums.opendns.com/") where you can see questions and answers from other people and ask your own questions. 
_____________________________________________________________________
To get OpenDNS to work with Ubuntu set the DNS servers to OpenDNS instead of the DNS servers that are provided from your ISP. Keep a copy of your original values for step 20 if you want to undo your new settings at a later date.
These are
208.67.222.222
208.67.220.220

The instructions are at
[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)
===========================================================================
The following information was kindly supplied by  Simos Xenitellis

If you keep losing these new DNS settings (as I did) then a quick fix is to set the values of /etc/resolv.conf to what we need, as follows

sudo gedit /etc/resolv.conf
   
edit the numbers to  208.67.222.222 and 208.67.220.220  save and close the editor and then run

sudo chattr +i /etc/resolv.conf

This command will make the file read-only so you wont lose the values. 
===========================================================================
If your ISP gives a dynamic IP then you need a program to update your IP at OpenDNS.
A good one is Inadyn.

The following will download the source code for Inadyn and compile it on your computer.

Do the following in a terminal. You can copy these commands and paste them in the terminal one at a time.

1. 
wget [https://www.opendns.com/support/ddns_files/inadyn.source.v1.99.zip](https://www.opendns.com/support/ddns_files/inadyn.source.v1.99.zip)

2. 
unzip -a inadyn.source.v1.99.zip

3. 
cd inadyn.source.v1.99/

4. 
sudo apt-get install build-essential

5. 
sudo apt-get install libcurl3-openssl-dev

6. 
make

7. 
gedit inadyn.conf
here put your OpenDNS information (username, password) the alias is ignored. Also add the line 

--background

Make sure on the OpenDNS settings at OpenDNS you enable "Set Up a Dynamic IP".

8. 
sudo cp inadyn.conf /etc/
sudo cp bin/linux/inadyn /usr/local/bin/

9. 
/usr/local/bin/inadyn

Once you run step 9, you will get the result.

INADYN: Started 'INADYN version 1.99' - dynamic DNS updater.
I:INADYN: IP address for alias 'Office' needs update to '1.2.3.4'

(If not look in the logfile to see the output, see 19. below)

This means that you can run manually and correctly this process. 
===========================================================================
To have Inadyn start automatically when you connect to your ISP. 

11. 
sudo gedit /etc/network/if-up.d/inadynsvc

12.(Copy and paste the following into the editor)

#!/bin/sh

if [ ! -x /usr/local/bin/inadyn ]; then
        exit 0
fi

if [ ! -r /etc/inadyn.conf ]; then
        exit 0
fi

if [ "$METHOD" = loopback ]; then
        exit 0
fi

# Terminate any existing inadyn services running.
/usr/bin/killall -TERM inadyn

/usr/local/bin/inadyn

exit 0


13. Save and exit the editor

14. 
sudo gedit /etc/network/if-post-down.d/inadynsvc

15. (Copy and paste the following into the editor)

#!/bin/sh

if [ ! -x /usr/local/bin/inadyn ]; then
        exit 0
fi

if [ ! -r /etc/inadyn.conf ]; then
        exit 0
fi

if [ "$METHOD" = loopback ]; then
        exit 0
fi

# Terminate any existing inadyn services running.
/usr/bin/killall -TERM inadyn

exit 0

16. Save and exit the editor

17. To make these files executable

sudo chmod 755 /etc/network/if-up.d/inadynsvc
sudo chmod 755 /etc/network/if-post-down.d/inadynsvc


18. If you are using dialup then do these further 2 steps

sudo cp /etc/network/if-up.d/inadynsvc /etc/ppp/ip-up.d/inadynsvc
sudo cp /etc/network/if-post-down.d/inadynsvc /etc/ppp/ip-down.d/inadynsvc

19. To see if inadyn is responding after connecting, click on System-->Administration-->System Log
Then, from all logs, click on /var/log/user.log, and the last entries should mention how inadyn is doing.
===========================================================================
20. To remove inadyn if you do not want it in the future do the following.
sudo rm /etc/network/if-up.d/inadynsvc
sudo rm /etc/network/if-post-down.d/inadynsvc
sudo rm /etc/ppp/ip-up.d/inadynsvc
sudo rm /etc/ppp/ip-down.d/inadynsvc
sudo rm /usr/local/bin/inadyn
sudo rm /etc/inadyn.conf 
sudo chattr -i /etc/resolv.conf
sudo gedit /etc/resolv.conf
   and change the OpenDNS values to your original DNS values as supplied by your ISP.

---

### Post by FrozenFlame22 on 2007-10-05
Fantastic tutorial! Thanks for the very detailed and easy steps!

---

### Post by lisati on 2007-10-30
Thanks.

---

### Post by rkdss on 2009-02-24
To simplify the installation, inadyn could be find in the repositories since Ubuntu Dapper

[COLOR="Red"]EDIT[/COLOR]: at least at this time (Intrepid Ibex) the version of inadyn available in the repos (1.96-1) doesn't support the --secure parameter so the compilation is still needed. Also, to view at syslog the activity of the process the parameter --syslog is required

---

### Post by Martje_001 on 2009-02-26
Thank you :). Wonder how good it works, though.

---

### Post by kamitsukai on 2009-02-26
I do like opendns but i noticed that when using BBC Iplayer that I got alot of error messages and a couple of "sorry you must be a UK resident to watch this" (or something along those lines)

---

### Post by mugg326 on 2009-03-03
Thank you very much for the detailed tutorial!

---

### Post by Normalex on 2009-12-22
[LIST]
[*]If your router supports DynDns service then set it up.
[*]Create OpenDNS account.
[*]Then use the same OpenDNS credentials to connect to [www.dnsomatic.com](www.dnsomatic.com) and activate your DynDNS account/network there.
[*]Everything works without any software installation.
[/LIST]

---

### Post by x.knight on 2009-12-22
i use squid with dansguardian it is awesome it is not only block prono but also blocks all useless things like downlands etc etc please try its awesome

as far as opendns is concern i feel its slow down browsing speed

---

