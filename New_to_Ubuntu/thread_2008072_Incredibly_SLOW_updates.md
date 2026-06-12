---
title: "Incredibly SLOW updates"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by markless on 2012-06-22
Hello Everyone,

I have been trying to install updates for Ubuntu Lucid 10.04 and I am getting a download speed of 900 B/s. Very very slow. i've also had this issue with Natty when I was running it, but I decided to go back to Lucid. 

Can someone tell me why this would be happening?

Thanks,
-Mark-

---

### Post by jmore9 on 2012-06-22
I just about 2 hours ago did a clean install and it took over an hour for the downloads to complete .  I have a very fast internet conn. so it usually takes about 12 to 15 minutes,

Don't know what was going on.

---

### Post by markless on 2012-06-22
> **jmore9 said:**
> I just about 2 hours ago did a clean install and it took over an hour for the downloads to complete .  I have a very fast internet conn. so it usually takes about 12 to 15 minutes,

Don't know what was going on.



My internet connection is fine. I'm able to download music or anything else pretty fast. I don't know if it is the repositories in Lucid or what, but it's literally crawling at about... 400 B/s now.

I have no idea why.

---

### Post by wildmanne39 on 2012-06-22
Hi, change the server that you download your updates from that usually helps.
Thanks

---

### Post by Elfy on 2012-06-22
Try stopping the update process if it is still downloading.

Settings at the bottom of the update manager - in the Ubuntu Software tab - Download from - change the serrver.

If you pick other there is an option to pick best server.

Do that and then start the update again.

---

### Post by markless on 2012-06-22
> **wildmanne39 said:**
> Hi, change the server that you download your updates from that usually helps.
Thanks



Hi,

I tried that a couple of times, but it still displayed the same message for every server i chose.

It would say that it is either now longer available or has been moved, or something along those lines.

I'm really stuck on this one.

---

### Post by markless on 2012-06-22
> **Elfy said:**
> Try stopping the update process if it is still downloading.

Settings at the bottom of the update manager - in the Ubuntu Software tab - Download from - change the serrver.

If you pick other there is an option to pick best server.

Do that and then start the update again.



I get the same exact message as when trying to update with Natty 11.04.


"No suitable download server was found"
"Please check your Internet connection."

However, when downloading music or anything else, I have a 800 - 1500 Kb/s rate.

---

### Post by Elfy on 2012-06-22
Are you using a proxy?

---

### Post by shubham1 on 2012-06-22
i think i got it you should use a good download server this happens when you choose an download server and it stops working what i recommend is open ubuntu software center and then open edit > software sources then choose Main server and then check it if it works then try to choose the best server near you or let ubuntu choose it then if it works keep it or else stick to main server

---

### Post by Elfy on 2012-06-22
> **shubham1 said:**
> i think i got it you should use a good download server this happens when you choose an download server and it stops working what i recommend is open ubuntu software center and then open edit > software sources then choose Main server and then check it if it works then try to choose the best server near you or let ubuntu choose it then if it works keep it or else stick to main server

We've done this ...

---

### Post by markless on 2012-06-22
They are correct, "shubham1". I tried using different servers as well as resetting it back to "Main Server". i'm still just getting the super slow update download speed. It's just a little odd that even though I choose it's "Best Server for you" option to detect one, it still does not work.

Thanks,

---

### Post by Elfy on 2012-06-22
Please answer post #8.

---

### Post by markless on 2012-06-22
> **Elfy said:**
> Please answer post #8.

My apologies. That is a negative, on the proxy. I haven't setup anything like that.

Thanks,

---

### Post by markless on 2012-06-25
Any other suggestions?

Thanks,

---

### Post by wildmanne39 on 2012-06-25
Hi, are you sure it is only updates, does all other downloads and loading of web pages seem fine?
Thanks

---

### Post by markless on 2012-06-25
> **wildmanne39 said:**
> Hi, are you sure it is only updates, does all other downloads and loading of web pages seem fine?
Thanks

Yes. It's specific for the ubuntu updates only. Anything else I down load has a normal DL time.

---

### Post by wildmanne39 on 2012-06-25
Hi, I did some research and the only thing I found was to try different mirrors which is the servers until you find one that is faster, and it could be that it may not be the closet one to you.
Thanks

---

### Post by markless on 2012-06-25
> **wildmanne39 said:**
> Hi, I did some research and the only thing I found was to try different mirrors which is the servers until you find one that is faster, and it could be that it may not be the closet one to you.
Thanks
 
I've gone through A LOT of the servers available. I live in Ohio, so I can't possibly just get a slow server connection since everything else that I dl is fine. If you happen to have any server recommendation, I'd appreciate it.

Thanks,

---

### Post by wildmanne39 on 2012-06-25
Hi, mine just says server for the United States and it is fast.

Do you have any third party ppa's installed maybe that is holding up the process.

Run:
```
sudo apt-get update
```
from the terminal and watch if anything in particular is slowing down the process, maybe it can be removed if it is a third party ppa.
Thanks

---

### Post by markless on 2012-06-25
> **wildmanne39 said:**
> Hi, mine just says server for the United States and it is fast.

Do you have any third party ppa's installed maybe that is holding up the process.

Run:
```
sudo apt-get update
```
from the terminal and watch if anything in particular is slowing down the process, maybe it can be removed if it is a third party ppa.
Thanks

Actually, now that you mention it, I could have third party ppa. However, if they are there i do not know how to remove them since i don't ever remember updating ppa's. 

Should I just remove them through "sudo gedit /etc/apt/sources.list" ?


Thanks,

---

### Post by wildmanne39 on 2012-06-25
Hi, it is best to open synaptic>settings>repositories>othersoftware and just uncheck the ppa's from third party sources but run the command from the terminal first and see what is going on.
Thanks

---

### Post by markless on 2012-06-25
Thanks. I'll give it a shot and post results.

Thank you,

---

### Post by markless on 2012-06-25
See image for the "Other Software" list.

i'm not exactly sure which ones to uncheck/check.

---

### Post by wildmanne39 on 2012-06-25
Hi, uncheck the last three and see if that improves your speed.
Thanks

---

### Post by markless on 2012-06-25
Seems to be doing the same thing. Very very slow load. I ran the update manager for the updates and it was dl'ing at a whopping 300-1000 B/s.

Here was the terminal output for running "sudo apt-get update"


```
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Reading package lists... Done
```


I'm not sure if anything stands out, but if so, let me know.

Also, i don't know if it does help, but I only have to dl 120MB worth of updates apparently. 

Thanks guys,

---

### Post by CharlesA on 2012-06-25
I checked my lucid box and it updated ok:

```
Fetched 13.1MB in 26s (486kB/s)   
```

Have you tried going to software sources > Download from: > Other > Select best server ?

---

### Post by markless on 2012-06-25
> **CharlesA said:**
> I checked my lucid box and it updated ok:

```
Fetched 13.1MB in 26s (486kB/s)   
```

Have you tried going to software sources > Download from: > Other > Select best server ?


Yeah I have. I get the same thing every time. Which doesn't make sense since everything I download, will go at about 1.5 MB/s.

See attachment. 

Thanks,

---

### Post by markless on 2012-06-25
Am i doing something wrong?

---

### Post by CharlesA on 2012-06-25
Odd. The select best server goes off ping.

Have you run the test at speedtest.net?

---

### Post by wildmanne39 on 2012-06-25
Hi, to be honest I have no further suggestions.

---

### Post by CharlesA on 2012-06-25
> **wildmanne39 said:**
> Hi, to be honest I have no further suggestions.
Sameish, it seems to point to a problem with the internet in general and not the ubuntu servers to me.

---

### Post by markless on 2012-06-26
I'll try to dl the updates at a different location with internet and let you all know of the outcome. 

Thanks,

---

### Post by drmrgd on 2012-06-26
This may be irrelevant and something that you guys have already considered, but using the default server on lately has been really slow for me too.  Occasionally, it'll timeout when running apt-get update, which is not normal for me at all.  When I tried to click the "Select Best Server" button, it actually gave me a server from France, which I doubt will be routinely the best for me as I'm on the East Coast of the US.  I had a look here:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

and looking at the list for the United States, the mirror at the Argonne National Lab (mirror.anl.gov), it looks like they have a heck of a connection pumping the data out over there, so I chose that mirror, and it seems to have dramatically improved my apt-get update query.  

If my experience is similar to yours, I would recommend manually selecting another mirror and trying a few to see if you can get a better result.  I just ran apt-get update from the ANL mirror, and got my usual 13.3 MB in 29s.  So, it seems to still be working well for me.

---

### Post by cmcanulty on 2012-06-26
I had same problem until I unchecked the sources code repositories

---

### Post by markless on 2012-06-27
> **drmrgd said:**
> This may be irrelevant and something that you guys have already considered, but using the default server on lately has been really slow for me too.  Occasionally, it'll timeout when running apt-get update, which is not normal for me at all.  When I tried to click the "Select Best Server" button, it actually gave me a server from France, which I doubt will be routinely the best for me as I'm on the East Coast of the US.  I had a look here:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

and looking at the list for the United States, the mirror at the Argonne National Lab (mirror.anl.gov), it looks like they have a heck of a connection pumping the data out over there, so I chose that mirror, and it seems to have dramatically improved my apt-get update query.  

If my experience is similar to yours, I would recommend manually selecting another mirror and trying a few to see if you can get a better result.  I just ran apt-get update from the ANL mirror, and got my usual 13.3 MB in 29s.  So, it seems to still be working well for me.


I would personally like to thank you, sir. This has been bothering me for weeks. I switched the server to the one that you have suggested and it's cruisin' right along. Thank you very much.

And also, thank you everyone else for your suggestions as well. I really do appreciate it.

Thanks,
-Mark-

---

### Post by wildmanne39 on 2012-06-27
Hi, glad you got it sorted, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

