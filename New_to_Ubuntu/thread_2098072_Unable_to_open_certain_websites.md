---
title: "Unable to open certain websites"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by fodilein on 2012-12-25
Since a couple of days I have the problem not be able to open any websites with the end of hu. Any other ending (org. com. de ...etc) are problemless to open . I didn't change anything (or I don't know about) on anything, reset the Firefox but it still doesn't use. I'm not even able to go to the hungarian ubuntu forum and ask there.  I use ubuntu 11.10 and mozilla firefox. 
Do have somebody an idea what can it be? Thanks forward!

---

### Post by offgridguy on 2012-12-25
Welcome to the forum,  have you tried a different browser, or do you wish to stay with firefox ?

---

### Post by monkeybrain2012 on 2012-12-25
> **offgridguy said:**
> Welcome to the forum,  have you tried a different browser, or do you wish to stay with firefox ?

Why do you assume that other browsers would work? It is not a Firefox problem, I just visited ubuntu.hu with FF. See screenshot.

---

### Post by jockyburns on 2012-12-25
Are you sure that the sites your trying to access , have not been closed down for Christmas? I know one of the forums I use, "Shuts down for essential maintenance." (An excuse they use meaning there's no one to moderate the forum for a few days)

---

### Post by Zill on 2012-12-25
fodilein:  ubuntu.hu also works OK here (UK) with Firefox v17.0.1.
[LIST=1][*]Are you posting to this site (ubuntuforums.org) with the same PC and browser you are having problems with?
[*]Can you access ubuntu.hu from any other PC you have available or is this problem common to multiple machines?[/LIST]

---

### Post by fodilein on 2012-12-25
Thanks for the replies and thanks for the welcome!
 Well Offgridguy I've tried to download the Chrome as an other browser but I can not  My software centre doesn't do anything and wenn I click on it doesn't open. (That would be a next post for problemsolving but maybe are the two things in relation. )
The hungarian sites related the browser doesn't open any sites with hu, so it's not about just some hungarian sites.  I don't know if it does something to it but I'm in the UK but all my online banking, mailings etc. are hungarian and it's a big problem for me if I can not come to them. 
To reply your question Zill, yes this is the PC (Notebook) where I post now, and which whom I having the problem. 
Do you have guys more ideas?

---

### Post by Zill on 2012-12-25
> **fodilein said:**
> ...The hungarian sites related the browser doesn't open any sites with hu, so it's not about just some hungarian sites.  I don't know if it does something to it but I'm in the UK but all my online banking, mailings etc. are hungarian and it's a big problem for me if I can not come to them...
Maybe your ISP is blocking direct access to hungarian sites for some reason.

I suggest you try accessing ubuntu.hu via a proxy server and see if this works.

An easy way is to open [ixquick]("https://www.ixquick.com") and then enter "ubuntu.hu" in the search box.  Don't click on the highlighted result "ubuntu.hu" but instead click on the "proxy" link at the bottom of the entry.  This should then open "ubuntu.hu" via the ixquick proxy server.  Please then advise if this works or not.

---

### Post by fodilein on 2012-12-26
Thank you Zill, with the ixquick under proxy I can enter the sites! So I'm a step forward with your help. But the use of this is unfortunately limited as I can not enter the forums, the mail etc. so the main problem is not yet solved. And since yesterday I can not reply on this forum, I try it now again!

---

### Post by fodilein on 2012-12-26
It has succed now as you see!

---

### Post by holycow131415 on 2012-12-26
It would be worth a try to unplug your modem and router to refresh your dns.

---

### Post by Zill on 2012-12-26
> **holycow131415 said:**
> It would be worth a try to unplug your modem and router to refresh your dns.
A good suggestion.

fodilein:  [LIST=1]
[*]Which ISP are you using?
[*]Which DNS servers are you using?
[*]Are the DNS addresses held in your router or are they configured within your Ubuntu system?
[/LIST]

---

### Post by fodilein on 2012-12-26
You are good:-).  Do you tell me what is the ISP and the DNS? Where can I find them to identify? And how can I unplug my modem?  (An absolut beginner, who bought a Notebook and got one with Linux, and I can not go back to the shop as it was in Hungary and I'm sitting in England). 
Thanks forward for your patient!

---

### Post by Zill on 2012-12-26
> **fodilein said:**
> ...Do you tell me what is the ISP and the DNS? Where can I find them to identify? And how can I unplug my modem?
The Internet Service Provider (ISP) is the service you use to connect to the internet.  When you sign-up to an ISP you will be given a username and password, together with other details such as the IP addresses for the Domain Name Servers (DNS) that provide the routing for your internet traffic.

If you are connecting via a DSL router this information is best held within the router.  However, there are other options such as retaining this information within the Ubuntu configuration.

It will help if you advise *exactly* how you are connecting to the internet.  Do you use your own DSL connection (with your own ISP account) or are you using a public wifi access point?

---

### Post by fodilein on 2012-12-27
Hi Zill, 
I use the internet per wi - fi and I see hier datas like 802.11 WiFi (eth1) and under IPv4 the IP adress, Broadcast, DNS Nr etc. I work for different clients and wenn I arrive somewhere I get a key for the Wifi so its not my own wifi.  Does help this info?

---

### Post by Zill on 2012-12-27
fodilein:  As you seem to be using different wireless access points it is *possible* that the DNS servers defined by their router(s) may not be the best choice for you.

Accordingly, I suggest you should specify the DNS servers you wish to use and, unless you have any other preference, I believe you should get good results with the Google DNS servers 8.8.8.8 and 8.8.4.4

These *can* be defined via the Network Manager (right-click and edit the connections) but I believe it is best to define the DNS servers in the /etc/resolv.conf file.

First, open a terminal (Ctrl-Alt-t) and make a backup of your existing /etc/resolv.conf file:
```
sudo cp /etc/resolv.conf /etc/resolv.conf_bak
```
Then open the /etc/resolv.conf file for editing:
```
sudo nano /etc/resolv.conf
```
Delete any existing line(s) beginning "nameserver" then add the following two lines:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
Hit Ctrl-o to save the file and then Ctrl-x to exit the nano editor.  Then reboot your Notebook and test your new DNS is working by trying to access various websites (including Hungarian ones!)

If you have any problems you can always revert to the original /etc/resolv.conf file by entering the following code into a terminal:
```
sudo cp /etc/resolv.conf_bak /etc/resolv.conf
```
Please let us know if this works.

Caveat:  I do not use "Network Manger" myself, nor the Google DNS servers, so I am happy for my advice to be corrected or improved by other, more knowledgeable, users.

---

### Post by fodilein on 2012-12-27
Good evening Zill, 
thanks for the detailed description, but I've got  stopped at the first code. After I have given in, I've got the reply '  command not found' (I've tried more time of course). Do you have an idea  why it doesn't accept the code?

---

### Post by mrjava on 2012-12-27
The fact that you can open .hu domains through a proxy but not via regular browsing means either your ISP blocks .hu domains, or some sort of security software you have blocks them.

Check with your ISP to see if there is a list of blocked domains available.

---

### Post by Zill on 2012-12-27
fodilein:  Please open a terminal (Ctrl-Alt-t) and then copy and paste the command in and hit enter:
```
sudo cp /etc/resolv.conf /etc/resolv.conf_bak
```
Then copy everything in the terminal and paste it back to this thread so that we can see what is happening.  Note that you should be asked for your password as we have used the "sudo" prefix.

It will make the terminal output more readable here if you highlight the text in the post editing screen and then wrap "CODE" tags around the text using the "#" icon.

---

### Post by Zill on 2012-12-27
mrjava:  It appears that the OP is *not* using his own ISP but is using various wifi access points.
> **fodilein said:**
> ...I work for different clients and wenn I arrive somewhere I get a key for the Wifi so its not my own wifi...

---

### Post by fodilein on 2012-12-28
[COLOR=DarkRed][COLOR=Black]Thank you Zill, but I'm afraid there is something wrong with my system. It doesn't accept the password and doesn't do anything.  [/COLOR]

dell@dell-Latitude-D410:~$ sudo cp /etc/resolv.conf /etc/resolv.conf_bak
[sudo] password for dell: 
dell@dell-Latitude-D410:~$ 
[/COLOR]
I think I'll have to change the operation system, it seems for me very complicated. But thanks again for your help !

---

### Post by Zill on 2012-12-28
> **fodilein said:**
> Thank you Zill, but I'm afraid there is something wrong with my system. It doesn't accept the password and doesn't do anything...
There is nothing wrong with your system.  When you enter your password you just type the password and nothing will appear on the screen.  With Linux systems, when a command runs successfully there is no output.  A response will only be given if an error occurs.  So, no problem so far.  :-)

If you want to prove that the last command ran successfully just enter the following code:
```
ls /etc/resolv.conf*
```
This should now list your original /etc/resolv.conf file *and* the new /etc/resolv.conf_bak backup file.

Please now continue to edit the /etc/resolv.conf file as described in my post [#15]("http://ubuntuforums.org/showpost.php?p=12424437&postcount=15") above.

---

### Post by fodilein on 2012-12-29
[COLOR=DarkRed][COLOR=Black]Hi Zill again!
I've got some new hope from your last suggestion, but it didn't bring the expected result. Some difference to the previous state, if I put the name of a hungarian site in, it starts to search but doesn't find. (Previously I've got right the yellow sign without searching).

My terminal looks now like thist: 
Do you have maybe an other idea what could I try? 
[/COLOR]
GNU nano 2.2.6           Fájl: /etc/resolv.conf                               

nameserver 8.8.8.8
nameserver 8.8.4.4

















                              [ 2 sor beolvasva ]
^G Súgó      ^O Mentés    ^R Beolvasás ^Y El&#337;z&#337; old.^K Kivágás   ^C Pozíció
^X Kilépés   ^J Sorkizárás^W Keresés   ^V Köv. old. ^U Beilleszté^T Helyes-e?
[/COLOR]

---

### Post by Zill on 2012-12-29
fodilein:  As a test, please see if you can open the Hungarian news site [Népszabadság.hu]("http://nol.hu/") with your web browser.

If this fails then please enter the following code into a terminal:
```
ping nol.hu -c5
```
Then enter the following code into a terminal:
```
ping 62.77.131.89 -c5
```
Please post back the full output of both tests.

---

### Post by Zill on 2012-12-29
> **fodilein said:**
> ...My terminal looks now like thist: 
Do you have maybe an other idea what could I try? 

GNU nano 2.2.6           Fájl: /etc/resolv.conf                               

nameserver 8.8.8.8
nameserver 8.8.4.4

                              [ 2 sor beolvasva ]
^G Súgó      ^O Mentés    ^R Beolvasás ^Y El&#337;z&#337; old.^K Kivágás   ^C Pozíció
^X Kilépés   ^J Sorkizárás^W Keresés   ^V Köv. old. ^U Beilleszté^T Helyes-e?
Just to check...
The screen you have shown is the "nano" editor screen.  You do need to [COLOR="Red"]save[/COLOR] the edited file (/etc/resolv.conf) and this is done by hitting the Ctrl-O keys.  You should then [COLOR="Red"]exit[/COLOR] the "nano" editor by hitting the Ctrl-X keys.

You need to then reboot your computer to restart using the new DNS servers.

It might be helpful if you post back the contents of the /etc/resolv.conf file and the original (now a backup) file.  Enter the following two commands into a terminal and then post back the full results of both commands.
```
cat /etc/resolv.conf
```
```
cat /etc/resolv.conf_bak
```

---

### Post by fodilein on 2012-12-30
[COLOR=DarkRed][COLOR=Black]Hi Zill, 

I had again the problem, that I was unable to reply and now I try again: hier ist terminal: 
[/COLOR]
dell@dell-Latitude-D410:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
dell@dell-Latitude-D410:~$ cat /etc/resolv.conf_bak
# Generated by NetworkManager
domain home
search home
nameserver 192.168.0.1
dell@dell-Latitude-D410:~$ 

[/COLOR]

---

### Post by fodilein on 2012-12-30
test

---

### Post by Zill on 2012-12-30
> **fodilein said:**
> ...
I had again the problem, that I was unable to reply and now I try again: hier ist terminal: 

dell@dell-Latitude-D410:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
dell@dell-Latitude-D410:~$ cat /etc/resolv.conf_bak
# Generated by NetworkManager
domain home
search home
nameserver 192.168.0.1
dell@dell-Latitude-D410:~$
My post [#15]("http://ubuntuforums.org/showpost.php?p=12424437&postcount=15") requested that you *add* the new nameservers to the /etc/resolv.conf file.  This means that the other original lines should remain in the file.

I suggest you use the nano editor to edit /etc/resolv.conf again, this time making sure that it now looks like the following:
```
domain home
search home
nameserver 8.8.8.8
nameserver 8.8.4.4
```
Note that the line "# Generated by NetworkManager" simply means that the file can *possibly* be overwritten by the NetworkManager utility.  The "#" means that Linux should ignore the line as it is simply a comment.

The computer should be rebooted for these changes to take effect.

Could you then please run the tests I described in my post [#23]("http://ubuntuforums.org/showpost.php?p=12427543&postcount=23").

---

### Post by Calinou on 2012-12-30
If you get no error message, then it worked. The password is not shown for obvious reasons.

Also, if you think Linux is too complicated for you, then go back to your Windows 8.

---

### Post by fodilein on 2012-12-30
Hi Zill, I try to post the terminalresult the whole time, but I'm unable to post it. It comes the same failsign as in the case of the hungarian sites. Does it play a roll maybe, that the Firework setting jumps for the manual proxy setting, without that I touch it. If ÍI can shot it out accidently I can post hier, otherwise not.

---

### Post by fodilein on 2012-12-30
[COLOR=#8b0000][COLOR=black]Zill: to the post 23[/COLOR]
[/COLOR]
[COLOR=#8b0000]
[/COLOR]
[COLOR=#8b0000]dell@dell-Latitude-D410:~$ ping nol.hu -c5
PING nol.hu (62.77.131.89) 56(84) bytes of data.
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=1 ttl=56 time=75.2 ms
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=2 ttl=56 time=72.0 ms
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=3 ttl=56 time=73.3 ms
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=4 ttl=56 time=72.2 ms
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=5 ttl=56 time=71.6 ms

--- nol.hu ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 71.619/72.877/75.219/1.342 ms
dell@dell-Latitude-D410:~$ ping 62.77.131.89 -c5
PING 62.77.131.89 (62.77.131.89) 56(84) bytes of data.
64 bytes from 62.77.131.89: icmp_req=1 ttl=56 time=73.1 ms
64 bytes from 62.77.131.89: icmp_req=2 ttl=56 time=80.0 ms
64 bytes from 62.77.131.89: icmp_req=3 ttl=56 time=71.8 ms
64 bytes from 62.77.131.89: icmp_req=4 ttl=56 time=72.1 ms
64 bytes from 62.77.131.89: icmp_req=5 ttl=56 time=82.2 ms

--- 62.77.131.89 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 71.835/75.902/82.277/4.361 ms
dell@dell-Latitude-D410:~$ 

[/COLOR]

---

### Post by Zill on 2012-12-30
> **fodilein said:**
> dell@dell-Latitude-D410:~$ ping nol.hu -c5
PING nol.hu (62.77.131.89) 56(84) bytes of data.
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=1 ttl=56 time=75.2 ms
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=2 ttl=56 time=72.0 ms
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=3 ttl=56 time=73.3 ms
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=4 ttl=56 time=72.2 ms
64 bytes from lb2-hb.ringier.hu (62.77.131.89): icmp_req=5 ttl=56 time=71.6 ms

--- nol.hu ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 71.619/72.877/75.219/1.342 ms
dell@dell-Latitude-D410:~$ ping 62.77.131.89 -c5
PING 62.77.131.89 (62.77.131.89) 56(84) bytes of data.
64 bytes from 62.77.131.89: icmp_req=1 ttl=56 time=73.1 ms
64 bytes from 62.77.131.89: icmp_req=2 ttl=56 time=80.0 ms
64 bytes from 62.77.131.89: icmp_req=3 ttl=56 time=71.8 ms
64 bytes from 62.77.131.89: icmp_req=4 ttl=56 time=72.1 ms
64 bytes from 62.77.131.89: icmp_req=5 ttl=56 time=82.2 ms

--- 62.77.131.89 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 71.835/75.902/82.277/4.361 ms
dell@dell-Latitude-D410:~$ 
These ping tests indicate that the DNS for nol.hu *is* being resolved - although I am puzzled by the references to lb2-hb.ringier.hu.  This *may* be due to translation problems between English and Hungarian.  However, as the IP address 62.77.131.89 is resolved I guess it should work OK.

So, did you manage to open the site [http://nol.hu]("http://nol.hu") with your web browser?

---

### Post by fodilein on 2012-12-31
Dear Zill, 
thank you very much for your help. Unfortunately this doesn't work and I loose now the patient to try again, so I'll let to install an MS Windows. A pity, I liked the ubuntu, but I would need more time to learn to understand this if I need some correction and at the moment I don't have this time. 
I wish you a happy new year 2013!

---

### Post by Zill on 2012-12-31
> **fodilein said:**
> Dear Zill, 
thank you very much for your help. Unfortunately this doesn't work and I loose now the patient to try again, so I'll let to install an MS Windows. A pity, I liked the ubuntu, but I would need more time to learn to understand this if I need some correction and at the moment I don't have this time. 
I wish you a happy new year 2013!
I am sorry that this did not work for you.  The "ping" tests showed that your Ubuntu installation *is* resolving the Hungarian website nol.hu so this should have opened up correctly with your web browser.

It is possible that other Ubuntu users here may be able to give more advice on what else to try and I am sure that, with time, your Ubuntu system would work correctly.

However, as you have decided to install MS Windows, I can just wish you the best of luck with this and hope that this does resolve your difficulties.

Thank you for the good wishes and I wish you too all the best for 2013.

---

