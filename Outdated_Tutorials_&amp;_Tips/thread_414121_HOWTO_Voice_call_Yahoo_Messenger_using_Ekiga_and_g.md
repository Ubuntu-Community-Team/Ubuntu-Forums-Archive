---
title: "HOWTO: Voice call Yahoo Messenger using Ekiga and gtalk2voip service."
date: 2007-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by loell on 2007-04-19
[SIZE="3"][B]This simple howto is just a recreation of a tutorial found at  
 [http://www.gtalk2voip.com/gtalk_service_yahoo.shtml]("http://www.gtalk2voip.com/gtalk_service_yahoo.shtml") through Ekiga[/B]
[/SIZE]

[B][COLOR="Red"][SIZE="3"]1. Configure your ekiga.[/SIZE]  [/COLOR]

for beginners register an account through  [http://ekiga.net]("http://ekiga.net"), ekiga setup wizard will guide you through the process. but any sip account/provider will do.[/B]



[B][SIZE="3"][COLOR="Red"]2. Calling a yahoo messenger user[/COLOR][/SIZE]

  now you can call a yahoo messenger user, by just typing the username in the sip address bar like this [COLOR="Red"]someuser_at_yahoo.com@yahoo.gtalk2voip.com[/COLOR] or [COLOR="Red"]someuser%yahoo.com@yahoo.gtalk2voip.com [/COLOR] [/B] ie ```
 john_at_yahoo.com@yahoo.gtalk2voip.com or john%yahoo.com@yahoo.gtalk2voip.com  
```




[B][SIZE="3"] [COLOR="Red"]3. The catch: yahoo messenger user must accept a buddy invitation from gtalk2voip[/COLOR][/SIZE]  
submit the YM username to [www.gtalk2voip.com](www.gtalk2voip.com) 
the YM user must accept the buddy invitation from gtalk2voip service in order to recieve the call from your sip network. so before calling, [COLOR="Red"]advice user to accept the invitation[/COLOR] [/B] the name of gtalk2voip buddy will look like this **gtalk2voipXXX@yahoo.com** where XXX is a number, ie ```
gtalk2voip005@yahoo.com
```[COLOR="Red"]** after the user accepts the invitation, he/she can answer your call and the next time you call.**[/COLOR]



*** the YM user can always remove the gtalk2voip buddy if the user wishes not to recieve calls through this gateway **

*** This howto is also apliccable to  any sip based softphones **

  gizmo even integrates this service with version 3.0 and perhaps onwards.

*** the service is free**

---

### Post by chakkaradeep on 2007-04-20
Thanks for the tip.

By any chance, do you know how to enable voice chat for gtalk ? Is that possible using ekiga ?

---

### Post by loell on 2007-04-20
it can't be done, as ekiga is sip base softphone only, you can try tapioca and jabbin.
though through gtalk2voip service can also let you call to a gtalk and msn user, using ekiga and other sip base softphones, more info at  

[http://www.gtalk2voip.com/faq.shtml]("http://www.gtalk2voip.com/faq.shtml")

---

### Post by chakkaradeep on 2007-04-20
> **loell said:**
> it can't be done, as ekiga is sip base softphone only, you can try tapioca and jabbin.
though through gtalk2voip service can also let you call to a gtalk and msn user, using ekiga and other sip base softphones, more info at  

[http://www.gtalk2voip.com/faq.shtml]("http://www.gtalk2voip.com/faq.shtml")

Thanks loell , sure will look into that ! :)

---

### Post by loell on 2007-04-20
you're welcome :)

---

### Post by ftmichael on 2007-05-12
Is this for voice only?  Is there a way to do video the same way?  My partner's using Windows and both NetMeeting and the new Windows version of Ekiga are giving us loads of trouble.  Yahoo messenger works great, but I use Gyach for that and it sops up all my resources.

Michael

---

### Post by loell on 2007-05-12
yes, theres no video as yahoo video and msn video conferencing do not comply with standard SIP , while ekiga does. i also know about the memory leak that gyachi had in its webcam capabilities, the library/component that causes it has already been fixed, unfortunately it was not inlcuded in ubuntu 7.04. 

but you can also try kopete.

---

### Post by rajeev1204 on 2007-05-12
super duper howto and link loell !

Gtalk was only reason i had to occassionally boot to windows because i chat with my sister in UAE where skype (actually VOIP) is banned and somehow gtalk only works .

But now i can configure ekiga to talk to a gtalk user heh ( I hope i got this right ! )


thanks a million LOELL .



regards

rajeev

---

### Post by loell on 2007-05-12
i'm glad that you find this useful, if for some reason you want to make it easier to instant message and call gtalk users ,  you can also use gizmo 3.0 for linux maybe it will be out in the coming weeks, though you can also test the 3.0 linux beta.

---

### Post by kostkon on 2007-06-06
Many thanks!!!

---

### Post by loell on 2007-06-06
your welcome :)

if you could give feedback to the voice quality, whenever you'll try this.

whether its good or bad, that would be nice ;)

---

### Post by Songwind on 2007-06-12
I just tried it and the person on the other end got a "no voice signal detected" error and Yahoo ended the call.

---

### Post by loell on 2007-06-12
this is maybe a problem with gtalk2voip gateway, i'll make a thread in their forum..  if you could join the discussion then much better.

---

### Post by loell on 2007-06-13
hi songwind,

  try this settings , in edit menu --> preferencess --> audio codecs

  disable/uncheck all audio codecs except pcmu codec.

 and try calling again.

---

### Post by Manasia on 2007-07-09
I just tried this and the person I am calling does get the buddy invite it goes straight to their voicemail. 

They are on a dialup system, and I am behind a firewall, any suggestions?

---

### Post by loell on 2007-07-09
i think this could be a problem from gtalk2voip  service , 

can you call your freind from the official YM without a problem? despite that he's on a dail-up and behind firewall?

---

### Post by Manasia on 2007-07-10
Hey loell,

Yes I can call him from the Official YM client with no issues. He also uses windows 98, and the latest version of messener.

Manasia

---

### Post by loell on 2007-07-10
i emailed  the gtalk2voip team about this, since we have the same issue even in gizmo phone , he asked for Yahoo ID's to check thier logs, it turns out that one of the yahoo account that i call is tagged as MSN account , hence when i call , it is not passed to the YM user and just goes directly to the mail.

their suggested fix is to tell the Y! user to remove the buddy "gtalk2voipXXX@yahoo.com" where X represents a number,
then re-invite/ re-submit  the username at [http://www.gtalk2voip.com/](http://www.gtalk2voip.com/), then try to make a call again.

---

### Post by Manasia on 2007-07-10
Ok Loell kewl, his yahoo ID if u want to have them check it is [email]Alkebulan47@yahoo.com[/email]. 
I will have him remove the buddy when he logs back in. Thanx a million.

---

### Post by andoty_jazz on 2007-09-10
Thank you so much Ma'am.

I just tried it this very hour/day. I does work for me however I could hear the background sound louder than the user's voice. 

But anyway, I am very much thankful that it did work for me using Ubuntu Feisty.

A million thanks again Ma'am.

:popcorn:

---

### Post by loell on 2007-09-10
> **andoty_jazz said:**
> Thank you so much Ma'am.

I just tried it this very hour/day. I does work for me however I could hear the background sound louder than the user's voice. 

But anyway, I am very much thankful that it did work for me using Ubuntu Feisty.

A million thanks again Ma'am.

:popcorn:



no problem sir,

 

> 
taga- davao pud diay ka.

 btw, barako  ko sir :lolflag: 


---

### Post by andoty_jazz on 2007-09-10
> btw, barako ko sir 

Waaa....

Sorry Sir.

Yup. Dabawenyo ko. Nistorya lng ko inamerkano para kasabot tanan. hehehe. :lolflag:

Anyway, thanks. Tried your post on [Gyachi/GyachE]("http://ubuntuforums.org/showthread.php?t=431290&page=15"). Enjoy kaayo. Everythings working. 

Ubuntu Rocks. :guitar:

---

### Post by ekricyote on 2007-09-23
Will the advice in this thread help me make PC-to-phone calls?

---

### Post by loell on 2007-09-24
with ekiga, yes you certainly can.

---

### Post by 417 on 2007-09-29
I followed the instruction, but was unable to talk:

the other partner can receive the call
he can establish the connection
but after connecting he hangs up and receive this message:

 no voice signal can be detected!

any idea?

---

### Post by loell on 2007-09-29
yeah, this is a codec negotiation problem, tell the user to restart his/her yahoo messenger, then call again.

---

### Post by medomedo on 2007-10-26
Thanks loell and everyone,

I am experiencing sevral problems:

When I try to make a call via Twinkle, I get:
Sat 00:11:41
Line 1: call failed.
404 User not found

When I use kphone I get connected for 10 sec, then I can not hear anything from the other side. Though packet stream is still folowing.

When I use ekiga, I get connected but the sound is too choppy to the extend that I shut it down. This choppiness is know issue with ekiga so you can ignor it.

---

### Post by loell on 2007-10-26
hi, since you've already tried a couple of voip apps,

may I ask, have you tried gizmo project? i think its much easier to use and the sound quality is good, the steps mentioned here are already automated. :)

---

### Post by medomedo on 2007-10-27
Hi loell,

Using Gizmo, I had to manually adjust the mic level to get good connection. I was able to make three conversations, around 5 min each.

The session is dropped then automatically.

---

### Post by loell on 2007-10-27
just call back again ;) , even in YM, this does happen.

---

### Post by medomedo on 2007-10-27
Thanks loell,

I want to share this:

YAHOO! sip:user_at_yahoo.com@yahoo.gtalk2voip.com
GTalk: sip:user_at_domain.com@gtalk.gtalk2voip.com
MSN:   sip:user_at_domain.com@msn.gtalk2voip.com

---

### Post by anuban on 2008-02-10
Thanks a lot for the great info in this thread.
I was able to make call to my friend on Yahoo using Ekiga. I will try others later.
Good info...
Thanks again...

Anurag Bansal
[http://anuragbansal.blogspot.com:popcorn:](http://anuragbansal.blogspot.com:popcorn:)

---

### Post by WhiteHorse on 2008-12-13
I can't seem to get MSN to work with Ekiga through gtalk2voip. Has anyone had success with MSN? If not, is there a program that works? I've tried Amsn and it always fails. God I hate Microsoft and their users!!!!!

---

### Post by loell on 2008-12-13
> **WhiteHorse said:**
> I can't seem to get MSN to work with Ekiga through gtalk2voip. Has anyone had success with MSN? If not, is there a program that works? I've tried Amsn and it always fails. God I hate Microsoft and their users!!!!!

try asking at

[gtlak2voip forum]("http://www.gtalk2voip.com/forum/board_show.pl?bid=2")

---

