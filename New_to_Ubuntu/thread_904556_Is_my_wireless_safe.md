---
title: "Is my wireless safe"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Badoxide on 2008-08-29
Hello,All

Well for you ubuntu gods please go easy on the slaps here. I would like to ask if I may I have a router that I can run both wireless, and wired. Not all to sure that's what you call it.

Anyways my question is this how safe is it to run wireless, and wired I ask because all was going great with the setup I had till a friend of mine asked the magic words well if your running wired, But the wireless is running at the same time. Couldn't someone find a way in to your box.

At first I didn't put much into what he had said. But the more I ran it that way the more I have been feeling uneasy about my setup should I even be thinking about this.

Does anyone know of a way to disable the wireless part when not using it other then having to goto the web site to login, and do this.


NOTE:

Yes I know you can run both at the same time without a problem. What I need to find out is when I run the laptop wired. There is no option on the router its self to disable the wireless part. Well that's not 100% true there is, but it only last for about say 5Mins. What I need is to have a way to disable it till I need it again.

Thank you

Badoxide

---

### Post by roundidiot on 2008-08-29
Do you have WPA security set up for your wireless router?

---

### Post by nicedude on 2008-08-29
First if your router is not holding the settings you put in it then that is bad. When you turn wifi off it should stay off. Please give me the model # and brand of your router and what firmware version you are using in it and I will try and see if your model has an updated firmware that addresses that issue.

In general when you say how secure is wifi it all depends on how you set it up.

WEP - I will break in to your network in 5 minutes, although all that allows someone to do is then map your network and look for vulnerabilities to exploit or they could try logging on to your router as the admin, but if you chose a strong password for your routers logon then that should be ineffective.

WPA (preshared key)- this depends on how you set it up. All attacks on WPA involve capturing a handshake between a valid client and the router and then trying various methods to crack the captured handshake to produce the key. If you use a short passphrase then a bruteforce or dictionary attack against a captured handshake might succeed in a short amount of time. If however you pick a very strong passphrase that includes CAPS and lowercase along with numbers and special characters then only a rainbow tables attack against a capture has chance of success and this is kinda a pretty advanced type of attack the 99% of idiots trying to mess with your wifi will not have in their trickbag. Just remember that with WPA all an attacker has to do is bump you off the router with a special command and then your PC will reauthenticate with the router instantly which lets the attacker capture the handshake data he needs, then he can go home and does not have to be near your wifi in order to do the actual hacking of your key because he has the encrypted packet he needs.

In general though use WPA ( don't turn off broadcasts on your router as that does not help for security and can cause you more problems with having your wifi work properly ) and use a very strong 20+ digit passphrase and you will be fine against all but the most proficient wifi crackers and even they might have to use a machine of theirs for days or weeks working on cracking your key even with rainbow tables to do it with.
 And it won't be worth it for them to do so as since less skilled crackers can get a WEP key in around 5 minutes and there are tons of WEP connections still in use, so they will choose a easier target for their malfeasance.


Hope that helps you understand a little and please post the model router or investigate your routers firmware yourself as I think you will find that there is a newer one than the one that is currently loaded in the device.

PS one way to really make wifi unusable is that if it has a removable antennae that is removable then by all means remove it and then run a wifi scanner like 15 feet away in your house and see if you can even get a signal.

nicedude

---

### Post by Badoxide on 2008-08-29
Hello.Guys

Thanks for your time on this. First have a safe weekend ;) 

@ roundidiot

Yes I am running it with that security set up, and all is working great.

Thank you

@ nicedude

Yes its running the latest firmware I haven't had one problem other then my friend opening his mouth he is always doing this to me, I am at the point that each time he comes over I just run around hiding my stuff. As I said all was great tell he started running his, big mouth about how safe this would be to do.

Also I made sure to run it WPA and using a 20+ digit pass phrase, for login, and I think its a 30+ pass phrase,for the router not all to sure it maybe a bit less will check it out.

Thank you for talking the time here.

Badoxide

---

### Post by nicedude on 2008-08-29
If you did all that then you can forget it is on for the most part as you would be not a very attractive target to attack and anyone so doing will only get frustrated :-)

Do note though that some of the funniest wifi attacks can be done without knowing the key. Like sometimes I will start deauthing one of my friends nearby at random intervals and watch them smack and cuss their windows PC as being a piece of junk. I did it one day until I just busted a gut at their frustration :-)

Only do this deauth attacks to your good friends though as to pull up outside starbucks and do it would be funny but also pretty rude :-)

---

### Post by ilrudie on 2008-08-29
I run dd-wrt on a linksys wrt45gs and it has an option where when you hit the "Linksys" button (which generally has no use under dd-wrt) it turns the wireless radio off.

---

### Post by wolfen69 on 2008-08-29
i guess it also depends on how paranoid you are, where you live, what's on your computer, etc. i dont keep any personal information on my pc's and live in a "good" neighborhood. i know most of the people around here, and as far as i know, there are no uber geeks here. i just go with wep and dont worry it.

---

### Post by hyper_ch on 2008-08-29
listen to nicedude :)

---

### Post by Badoxide on 2008-08-29
Hey.Guys

Thanks

@ nicedude

Yes I had one hell of a time with the support People telling me, what a bad idea it was to use these long type of passwords. I don't get it you think they had paid, for it.

He he well my friend I'd like to do the same, but at only 4'9" if some of them came after me, it would turn out to be a bad day for sure.

@ wolfen69

Not much of anything on here, but what there is I paid for you follow. Have a safe weekend.

@ ilrudie

Sorry you ran dd-wrt not to sure what that is. May I ask for more info from you on this please.

Safe weekend to all.

B-O

---

### Post by hyper_ch on 2008-08-29
dd-wrt is an alternate firmware that operates routers... mostly it can be run on buffalo and linksys routers.

It offers you a lot more options than the default firmware.

I used it for quite a while until I discovered tomato-wrt - it has, IMHO, a much nicer QoS setup than dd-wrt.

---

### Post by Badoxide on 2008-08-29
Hi.hyper_ch

Thanks

Would you happen to have a link or two at hand if, so may I ask that you post them, for me ;) to go have a look at.

As aways thanks.

B-O

---

### Post by ilrudie on 2008-08-29
[http://www.dd-wrt.com/](http://www.dd-wrt.com/)

Its been really good for me.  Nice interface and very powerful.  Never tried tomato but I've heard its good.  As far as QoS dd-wrt has iproute2 so you can do a whole lot more than the web gui allows if you know what you are doing.  I've been happy with the QoS though.  For some ideas/instruction on what to do with iproute2: [http://lartc.org/](http://lartc.org/)

---

### Post by tkaed on 2008-09-04
> **nicedude said:**
> 

In general though use WPA ( don't turn off broadcasts on your router as that does not help for security and can cause you more problems with having your wifi work properly ) 



Hello, 

In every wireless safety guide I've read they all suggest turning off your broadcast to give less of a chance of people finding you. I've had my broadcast off, but can you explain to me why keeping it off is a bad thing?

Thanks for your time.

---

### Post by hyper_ch on 2008-09-05
Tomato WRT:  [http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

> **tkaed said:**
> but can you explain to me why keeping it off is a bad thing?
It doesn't add any security to your wireless. Hence you take a measure that you think that makes it more secure and instead it doesn't do anything.

---

### Post by Bucky Ball on 2008-09-05
[QUOTE=nicedude]pull up outside starbucks and do it would be funny but also pretty rude[/QUOTE]

Well, we thought Starbucks were pretty rude here in Australia serving what they call coffee. We just didn't buy it and what do you know, they packed their bags and shut up shop. There ain't no Starbucks in Aus anymore. :)

---

### Post by adult swim on 2008-09-05
small hijack/
has anyone ever tried running tomato or ddwrt on a linksys wrt300n?
/end hijack

---

### Post by MarlonDean on 2008-09-05
As long as you don't use WEP and rather WPA it should be safe. I suggest using MAC address filtering aswell on your router, that would allow only certain machines to use the network. Please note that it is still possible to crack WPA and to fake a MAC address, but this is the safest way I know of

---

### Post by hyper_ch on 2008-09-05
> **adult swim said:**
> small hijack/
has anyone ever tried running tomato or ddwrt on a linksys wrt300n?
/end hijack

did you check if your router is supported by those firmwares?

---

### Post by hyper_ch on 2008-09-05
> **MarlonDean said:**
> I suggest using MAC address filtering aswell on your router

Mac address filtering is as secure as hiding the SSID.

---

### Post by bangmalley on 2008-09-05
> **adult swim said:**
> small hijack/
has anyone ever tried running tomato or ddwrt on a linksys wrt300n?
/end hijack

check it [here]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Linksys")

---

### Post by adult swim on 2008-09-05
> **bangmalley said:**
> check it [here]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices#Linksys")

you sir, have given me a a reason to stay up and mess with things! :guitar:

---

### Post by adult swim on 2008-09-05
last hijack/
if i brick this thing, is there a point of return?
/im done i swear!

---

### Post by hyper_ch on 2008-09-05
by altering the firmware on any device you might render it useless.

---

