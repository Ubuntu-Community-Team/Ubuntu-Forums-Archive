---
title: "cant connect to POP server - strange behavior"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by jbkott on 2008-10-09
I need to check my work email on the road so I am attempting to setup Thunderbird. I have entered all the account settings as instructed by our IT folks but I get "Failed to connect to server mail.*.com" (* substituted for real). The following is as far as I am at this point...

1) Can't ping the mail server from Ubuntu machine (get "unknown host mail.*.com" in terminal)
2) Can ping the mail server from a windows machine - got IP adress
3) Can ping the ip address of the mail server in Ubuntu without problem
4) Substituted the ip address into Thunderbird setup and now get different Thunderbird error - "failed to connect to server"

Please note that both the Ubuntu machine and the windows machine are on the same network (currently) and obtain all network settings via DHCP.

I must admit I am at a loss. Any help would be greatly appreciated. Thanks!

---

### Post by Mark_in_Hollywood on 2008-10-09
Can you surf the 'net at all? Or is that a problem to the Thunderbird/Email? I'm sorry to answer your question with a question, but I need more info.

---

### Post by roger_1960 on 2008-10-09
Hi

Are you trying to send pop mail using your work mail server while you are at home?  If so, it wont work unless you are connected to your work network.  (You should be able to pick up mail from your work server)

---

### Post by LowSky on 2008-10-09
I know it could be anything but I bet it is something simple like a mispelled address. Please cheack the adress again, putting a space in the name or after a period might be throwing it off. Alsocheck with It about which port is to be used. and that you entered your address correctly

[http://www.freeemailtutorials.com/mozillaThunderbird/setupEmailAccount.cwd](http://www.freeemailtutorials.com/mozillaThunderbird/setupEmailAccount.cwd)

---

### Post by jbkott on 2008-10-09
No problem browsing. Double checked what I entered doesn't look like there are any errors. POP server is exposed so I can access anywhere.

Got it partially, not sure why. Did nslookup on POP server and got

Non-authoritative answer:
mail.*.com	canonical name = mail1.*.com.
Name:	mail1.*.com
Address: *.*.*.*

Since I ran this it seems to work. Not sure why. Seems like Ubuntu/Thunderbird or the DNS server can't go down this DNS rabbit hole unless pushed? Strange.

---

