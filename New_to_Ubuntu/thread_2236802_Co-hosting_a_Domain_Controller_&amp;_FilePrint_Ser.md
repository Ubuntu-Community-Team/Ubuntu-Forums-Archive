---
title: "Co-hosting a Domain Controller &amp; File/Print Server"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by Dark_Joat on 2014-07-29
Greetings,

I'm new to Ubuntu and some limited experience with Linux in general, but I have successfully installed Server 14.04 on an PC and set it up as a Domain Controller in a proof of concept test. I'm going to be deploying it in a small non-profit environment that historically has had a peer-to-peer Windows environment.

My next phase is to deploy the environment on an HP Proliant ML310 G5 as soon as the box arrives. I have been playing with a Dell PowerEdge 700 and while waiting, I've been thinking of how I would setup the environment with multiple machine using Windows OS in an enterprise environment.

My basic question is, "since I am using the server version (no GUI), can I utilize the box for both PDC roles as well as file & print services?" On a Windows box it's doable, but not recommeded (at least for small environments). I am wondering if that it still the case or is it acceptable to co-host those function on the same box given the low overhead.

I have the two servers and I think I can get them both up and running and talking to each other after looking at the web-lore, but a single box would be easier to manage with my limited donated time.

I've just started combing the forums and I did look for a thread addressing this topic, but it didn't jump out at me with 10 minutes of looking. Hopefully this is not a frequent repeat.

Thanks.

---

### Post by Dark_Joat on 2014-08-01
So, I have been digging around in my *copious* amount of spare time and found this on Samba's [AD DC HOWTO]("https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO"):

> [COLOR=#000000][FONT=sans-serif]While a Domain Controller is running our full file server, and can act quite well as a File Server, it is suggested that organisations run a distinct file server to allow upgrades of each without disrupting the other. It is also suggested that medium-sized sites should run more than one DC. And so it makes sense to have the DCs distinct to any file servers that may use the Domain Controllers. Also using distinct File Servers avoids many issues around the Winbindd internal to the Active Directory Domain Controller.[/FONT][/COLOR]

So now the question is, do I make the DC the faster computer or do I make the file/print server the faster computer. My thoughts are make the file/print server the beefier one as it will most likely see more traffic. Make the older, less powerful computer the authentication server. Thoughts?

Should I keep the profile folders on the DC? I know that I will need to follow up with [making the file server a member server]("https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server").

Any input or Ubuntu watchouts would be appreciated? Can I follow [Samba documentation]("https://wiki.samba.org/index.php/Main_Page")?

I am really hoping to keep the setup and managemnt fairly simple as I will be handing this over to someone (I don't know who yet) in a year or so. With that in mind, do I try to implement a DFS or just plan on using separate \\server\paths for the necessary settings? 

Regards.

---

### Post by Dark_Joat on 2014-08-01
Oh, will I have any issues running 32 bit on one machine (tenttively the older server) and 64 bit on the newer?

---

