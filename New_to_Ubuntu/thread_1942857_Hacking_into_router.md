---
title: "Hacking into router"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by openation1 on 2012-03-18
Hello everyone. my question is how can I find out who is hacking into my router? I can feel someone is, because I turn my computer off and the lights in my router sometimes are blinking like if someone is using it.....

---

### Post by TAspr on 2012-03-18
Change your password

---

### Post by Holdolin on 2012-03-18
What light is blinking?  While i'm not sure if an attack is making it to your machine, which is a bit harder when it's offline, you are indeed pretty much being pinged by script kiddies on an ogoing basis.  I've looked at the logs in my ipcop, and it's almost scary how many times i've seen my ipcop get hit with probes for all the most common used destination ports.  The key here is, are they getting through.

To that end I would ask, is your system doing any "funny stuff"?  Is it getting slower, or is your internet not as fast as it normally is?

---

### Post by Basher101 on 2012-03-18
preferably use a wpa2-psk encryption with a long password which contains numbers, letters, upper- and lowercase, symbols, and the like. 

I myself know some things about hacking routers (tried mine, failed miserably) so the longer the password, and the more upper- lowercase/symbols and numbers are used, the harder it is to get in.

After doing some math, if you have a 8 character long password,8 characters, plain characters (lowercase and uppercase) or digits = each character in the key could has 26+26+10 (62) possible combinations. So the maximum number of combinations that need to be checked in the bruteforce process is 62 * 62 * 62 * 62 * 62 * 62 * 62 * 62 =  218 340 105 584 896      At about 600 keys per second on my &#8220;slow&#8221; system (laptop), it could take more than 101083382 hours to find the key  (11539 years).  I have stopped the cracking process as my machine is way too slow to crack the key while I&#8217;m still alive&#8230;  So think about this when doing a WPA2 PSK Audit.

---

### Post by openation1 on 2012-03-18
well I've been using ubuntu 11.10 and is doing just fine sometimes it freezes when i use a multimedia application. when I go online it works great, but when I turn off my computer the router sometimes I see is working like when I am online. Like if someone is using it.

---

### Post by uRock on 2012-03-18
It is normal for the NIC and the router to communicate, even when the PC is powered off.

---

### Post by Basher101 on 2012-03-18
if you really think someone is, you can track anyone who is connected with your router via aircrack-ng. But i doubt someone else is using it. Besides, when someone wants to connect to it, they have to first get information from the router, thus your router sends it to them. They then will get a prompt for the password and cannot access your network.

edit: + what[COLOR="Red"] uRock[/COLOR] said

---

### Post by CharlesA on 2012-03-18
> **uRock said:**
> It is normal for the NIC and the router to communicate, even when the PC is powered off.
What he said. If you are that worried, change the admin password, and ensure you are using WPA2 with a strong passphrase.

---

### Post by NikTh on 2012-03-18
Routers sending and receiving packages from providers even if your pc is closed. This is not the correct way to find out who is in your network(if anyone is).
If you want to see that , open you routers page 192.168.?.? you will find that on manual of your router. Then go to wireless page and see how many users are connected to your network . You will see their IP's include yours .

---

### Post by 2bob on 2012-03-18
Hi!
In network settings you have something like "default route" or "gateway address". Type that address in your browser and it will take you to the router webadmin page. Login is usualy "admin" with password "admin" or check with the manufacturer of your router. You'll find a "connected clients" tab somewhere. Anyway, change the default password of the router. The "admin" thing brings you lots of "friends".
Cheerio!
2bob

---

### Post by The Peanut on 2012-03-18
As allot of the other users have said, if you are worried, change your password, or when you go into the password section, there should be a generate automatic password... Basically what that will do, is it will generate a random password using letters (higher case and lowercase - depending on the router) and numbers, they will be in different combinations to ensure the full safety of your router. 

Also, just another thing when I come to think about it, there should be an option under
firewall>ping,to hide your router when being pinged.

Good Luck

The Peanut

---

