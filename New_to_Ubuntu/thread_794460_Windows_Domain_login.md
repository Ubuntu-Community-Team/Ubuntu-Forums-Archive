---
title: "Windows Domain login"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by logike30 on 2008-05-14
First shot with linux here, learning a lot already. So here is my issue:

Swapped XP with 8.04 on my work laptop. We have a Win 2003 server at work with file shares and print server. With XP I'd login to the domain in order to access all that stuff. I have been reading a lot on samba and active directory to try to figure it all out but I can't get at the printer or the file shares. When I go to places-network I can see our domain and I can see the names of all the computers as well as the server on the network. When I click on the server I just get a blank screen as if there is nothing shared.

So what do I need to do? Is it samba or active directory?

Thanks!

---

### Post by mlentink on 2008-05-14
Neither. You can browse windows-shares natively in Ubuntu, you do not even need Samba for that. But to log on to a Windows Domain, is a bit more complicated. The new 8.04 has a buitl-in tool for that, which I'm still secretly trying out at customers' sites when they aren't looking. You might find more info on it [here]("http://www.likewisesoftware.com/products/likewise_open/index.php")

---

### Post by logike30 on 2008-05-14
Yeah, I was messing around with likewise as well. I'll keep at it.

---

### Post by mlentink on 2008-05-14
> **logike30 said:**
> Yeah, I was messing around with likewise as well. I'll keep at it.

If you find out more, would you mind letting us know?

---

### Post by lazyart on 2008-05-14
You can use sadms to join it to the domain if you want.  I run a domain at home and it surely makes things simple.

---

### Post by MaindotC on 2008-05-14
I don't think you can browse password-protected shares in 8.04 per my sig.  I keep watching bugzilla and launchpad and I've yet to see a resolution.  Hope it works for you!

---

### Post by Loan_Refi on 2008-05-15
I'm having the same problem here not able to see/login to windows folders.

I have Konqueror installed and it works for me until there is a fix for this issue in Ubuntu 8.04LTS I will continue to use Koqueror to connect into windows Server 2003/XP & Vista shared folders.

All I haave to do is open Konqueror, Select Network Folders, Samba Shares, Workgroup or Domain Name 
Then computers are listed - I chose one & I get prompted for my username & password then folders are listed.

I prefer to use the file browser that comes with Ubuntu so I hope this issue gets fixed.

---

### Post by MaindotC on 2008-05-20
Have you guys made any progress the past few days?  I know 8.04 has released some updates - not sure if they're working b/c I'm still using Gutsy.

---

