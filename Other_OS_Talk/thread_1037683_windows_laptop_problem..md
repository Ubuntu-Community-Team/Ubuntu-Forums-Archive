---
title: "windows laptop problem."
date: 2009-01-12
forum: Other OS Talk
---

### Post by hockey97 on 2009-01-12
Hi, I have a problem. I have a windows xp os laptop.

I have IE7 and firefox3 installed.

So far I can't get any website. I mean my wireless internet connection is good. I got all bars.

I got the connection. I can download files from other computers on my home network. I just can't use the web browsers to find websites.

what should I do???

---

### Post by hivelocitydd on 2009-01-12
Its problem with ur internet connection only.check it properly

---

### Post by hockey97 on 2009-01-12
I doubt it's the internet connection. 

the laptop has 2 network cards. One is a ethernet card and the other is a wireless card. I connected the wireless card to my router. It shows that the signal is good. It was also connected successfully. 

When I open IE7 or firefox3. I would  type in [www.google.com](www.google.com) and it will take a long time then I get an error that [www.google.com](www.google.com) dosen't exist make sure you type the name right and try again.

I get that for every site. Yet I am still able to download files from my desktop computer that I installed a web server. 

I hosted anti-virus programs and downloaded it to that laptop.

I rand the anti-virus...anti-malware, and anti-spyware. I found a huge number of viruses,malware,spyware. I found about 865 so far and it still is running finding more and more.

I am guessing that the viruses and malwares and spywares are causing the web browsers to not grab websites???

I am just guessing but would like some input on what you think it could be.

If you really think it's the internet connection how should I test to make sure it's the internet connection???

and if it's the internetconnection then how do I fix it and why am I able to download from a webserver on my own network?

---

### Post by wolfen69 on 2009-01-12
do windows key+r, type in: sfc /scannow

it will ask for the original disc. put it in and continue. this will fix any borked windows files and should get you back online.

---

### Post by hockey97 on 2009-01-12
ok thanks... one problem... this is a friends laptop they have xp home... I at my home have my own copy.. I have windows xp pro... would this make any difference?

also do you mean to go to start and then hit run and type that in?? if so I just tried and it gave me a error.

Update: Ok I just open the command prompt and type that in... it showed a window checking protected windows files.

---

### Post by chamber on 2009-01-12
You could try pinging a site and see what happens then.

---

### Post by hockey97 on 2009-01-12
I did a ping and it says cannot find host name.. I tried [www.google.com](www.google.com)

Also I tried that one suggested above... I did it in command prompt and I only get a window saying that it will make sure that all windows files are secure and protected.  I has a bar and at the end the window disappears and it dosen't even ask for the windows cd.

did I do it wrong?

---

### Post by chamber on 2009-01-12
what about ipconfig?  What comes up then? Have you tried tracert too?

---

### Post by hockey97 on 2009-01-12
yes I tried that too the ipconfig... it shows that it got a ip address and looks like it is connected.

I did a ip config all. My router is working fine since this computer I am using to post this works.

The browsers still don't work nore any anti-virus updates. It can't connect to the internet.

that sfc/scannow finished and never asked for the windows xp cd.

anything else I could do?


how can I fix this??

yes I tried the tracert [www.google.com](www.google.com)  and I got unable to resolve to host.

UPDATE: ok I read around googled around and found something to try.

in the browser I type in googles ip address and it works. I can get the google page.

I just can't use [www.google.com](www.google.com) in the browser.

---

### Post by hockey97 on 2009-01-12
ok, so right now the laptop can only get websites just by the ip address.

I need to type ip adresses in order to get to websites.

What needs to be fixed to be able to tyep in the name.

like [www.google.com](www.google.com) not the ip address.

any ideas how to fix it? she had macaffee on her computer that firewall which I deleted. I also turned off windows firewall.

any suggestions I could try to fix the problem? I can even ping to the websites ip address but can't with the host name.

so I could write like 204.64.207.4 and I would get the website but if I type something like [www.google.com](www.google.com) I get a host not found... a error saying that the name must be wrong and try again.

so I can get to the websites only by putting their ip addresses.

my anti-virus dosen't work because the updates are updated by going to the host name... like [www.avg.com](www.avg.com)

which dosen't work.

How would someone fix such a thing?

UPDATE: I just tried to flush the dns which I got to flush it but yet same problem.

---

### Post by hockey97 on 2009-01-12
ok, it seems that the laptop is not connecting to the dns servers.

is there anything I can do to fix this? I mean my other computers use the same dns server and it works but why this laptop can't connect to it?

I done a nsloop up and it failed... It said something about unknown dns server. and then it spits out the same dns servers ip address as whats in my router status.

anything I could do to fix such a thing?

it seems like some dns files are missing.. is there any way I can overright the dns files of windows xp? the ones the resloves to a dns server?

---

### Post by mips on 2009-01-12
Try a different DNS server like OpenDNS, **208.67.222.222** and **208.67.220.220** configure them manually.
[https://www.opendns.com/smb/start/](https://www.opendns.com/smb/start/)

Something is wrong with your DNS settings or your computer is simply not getting the correct settings.

---

### Post by hockey97 on 2009-01-12
I tried that dns server and I still have the problems.

I don't think it's the settings. I currently on all the computers on my network have that same dns ip which is from our ISP. and we have not trouble.

it's just my friends laptop is not taking that ip nore the one you gave.

I think some files must be missing or something.

the nslookup just shows cannot find dns server.

the settings look fine to me.I used the same ones with my other computers just the static ip is not the same as any computer on the network.

any other ideas I should look for.

the problem is with dns that is the only problem the laptop is facing.

---

### Post by wolfen69 on 2009-01-12
backup any files and reinstall?

---

### Post by hockey97 on 2009-01-12
well my friend dosen't make backups. So I am stuck.

if there is a way where I can just over write the files that would handel the communcation with the dns servers that would hopefully work.

I think the dns server files that communicates with the dns server might of got currpted.

---

### Post by mips on 2009-01-14
> **hockey97 said:**
> well my friend dosen't make backups. So I am stuck.

if there is a way where I can just over write the files that would handel the communcation with the dns servers that would hopefully work.

I think the dns server files that communicates with the dns server might of got currpted.

I think he meant **backup all her data & email then reinstall windows**.

You could try booting of the windows cd and selecting the repair option but I have no idea what that does to the data.

---

### Post by hockey97 on 2009-01-28
ok thanks. She didn't mind that I didn't fix it. She told me it only works when you use a hard wire connection. 

So I done that and it was fine.

It's just the wireless she can't get the dns servers. 

So I am guessing it's her drive I think she or her other friends installed the wrong drive so it works but dosen't work properly.

so I might later down the road have to fix it for her. They want me to setup their router next. So that's the next project.

So thanks for the help. I will have to see if it's the drive that is not the proper version.

---

