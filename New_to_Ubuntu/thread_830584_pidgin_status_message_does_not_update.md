---
title: "pidgin status message does not update"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by darthshak on 2008-06-16
hi

i'm using ubuntu hardy 8.04 32-bit on a thinkpad t61. i use pidgin im to chat with my google talk contacts. it was only recently that i found out that my status message is never visible to my online friends. 
for example, if my status is available and my status message is "XYZ", then all my contacts see is "Available". 
is there any restriction on status messages in pidgin that i am not aware of? like number of characters, or whitespaces?
the version of pidgin that i am using is 2.4.1

---

### Post by acidsolution on 2008-06-16
try to add new status from new status available at status bar choice in pidgin 
mine works fine :)

---

### Post by darthshak on 2008-06-16
yeah, well, that is the only way i know for updating status messages too.
that is the whole problem : i can see the updated status message, but my online friends cant.

---

### Post by darthshak on 2008-06-18
come on, dont tell me no one knows what the issue is?
i've searched all over the place for this...

---

### Post by clyodna on 2008-09-06
Well, this might be a little too late but here goes:

I have had the same problem and I've solved it by writing the actual status that I want showing in the Message box of the new status window, not in the Status box. I don't know if this is the best solution but it's how i solved my problem.:)

---

### Post by zzanzare on 2008-09-14
@darthshak
I have had the same problem for a veeeery long time and i haven't found any solution yet. 

Nobody from my contact list (ICQ protocol) is able to see my status message. They can only see Available, but not the message. It doesn't matter if I enter it just by typing after changing the status, or if I save it through the little dialog window. 

I am really surprised that nobody else seems to have this problem..

---

### Post by ne0h on 2008-09-14
Mine works fine. Even I managed to change status message with "Now Playing" from RythmBox after lots (yeah lots) of fighting.

To check what your friends is seeing as status, add your own username(!) in your friendlist! It sounds creepy but this is the only way in Pidgin to see your own status message.

---

### Post by clyodna on 2008-09-14
@zzanzare: actually quite a few people have had this problem before. see here: [http://developer.pidgin.im/ticket/582](http://developer.pidgin.im/ticket/582) . Appart from what I've written earlier I don't know of any other solution to this problem sorry. :(

@ne0h: yes, that is a very handy trick i picked up as well. good for all sorts of things.

---

### Post by khc on 2008-09-14
> **ne0h said:**
> To check what your friends is seeing as status, add your own username(!) in your friendlist! It sounds creepy but this is the only way in Pidgin to see your own status message.

On many protocols you are not allowed to add yourself to the buddy list (MSN, XMPP), so pidgin fakes that. So what you see on your buddy list may not reflect what your buddies see.

---

### Post by zzanzare on 2008-09-15
I tried this:
1.) set my status message to a text like "Does anyone see this text? Please reply", and I have also asked a few people by the way if they can see my status message - no one so far. (not even my brother, who uses the same Pidgin and the same Ubuntu)

2.) when I added myself in my buddy list I could see my status message all right.

3.) I have a few jabber contacts on my Ubuntu Pidgin and they can see my status message all right

4.) I started windows XP in VMWare and installed Pidgin and QIP. Set up another ICQ account. I tested this sequence:

Ubuntu pidgin already started. Status message set to "test"

Started QIP on win - could see only "Online (Connected)"
I logged out and in on my Ubuntu Pidgin - still the same

Started Pidgin on win - could only see "Status: Available"
Logged out and in on my Ubuntu Pidgin - still the same
Set the message "test" on the win Pidgin - the Ubuntu one could only see "Status: Available"

Started ICQ6 on win - could only see the green flower (no text, not even after opening message window)
Set up online message "test" on ICQ - Ubuntu pidgin imediately sees "test: test"

Versions:
Ubuntu uname -a : Linux petenb 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Ubuntu pidgin: 2.4.1 (from ubuntu repositories)
Win pidgin: 2.5.1
QIP: 2005 build 8070
ICQ: 6.0 build 7013

Well.. from this I assume that Pidgin status messages just don't work at all. Is there someone, who can perform this test succesfully?


(I posted this on pidgin forum as well [http://developer.pidgin.im/ticket/582](http://developer.pidgin.im/ticket/582) - thanks for the link, clyodna. Maybe we should continue the discussion there?)

---

### Post by swigrid on 2009-01-16
Hi guys, I just compiled new libs
backup your
/usr/lib/purple-2

download
[http://www.megaupload.com/?d=66FPJ71R](http://www.megaupload.com/?d=66FPJ71R)

and use libs from archive

I compiled on my system, so hopefully it will be working on yours...

---

### Post by khc on 2009-01-17
zzanzare: I believe your problem is specific the the ICQ protocol. There are multiple ways to set the ICQ status message, and I think the issue is we don't do it the way the official client would understand it.

---

### Post by zzanzare on 2009-01-17
> **khc said:**
> zzanzare: I believe your problem is specific the the ICQ protocol. There are multiple ways to set the ICQ status message, and I think the issue is we don't do it the way the official client would understand it.

i'm not so familiar with the icq protocol, neither how the official client handles messages (if differently from the protocol...). But as I said, the problem exists even between Pidgin on Ubuntu machine and another Pidgin on another Ubuntu machine.. which definitely does not concern the official client.

Anyway.. with the majority of users having the official client, shouldn't Pidgin just "learn" the way the official client would understand?

---

### Post by anasofiapaixao on 2009-03-22
> **khc said:**
> On many protocols you are not allowed to add yourself to the buddy list (MSN, XMPP), so pidgin fakes that. So what you see on your buddy list may not reflect what your buddies see.

What? I can see myself just fine on WLM, only can't chat with myself. Pidgin isn't faking anything - at least when it comes to showing myself on the contact list.

I have the exact same problem, and was wondering exactly how come so little people have complained about it (for what it looked like from my googling). I tried saving a status too, and it doesn't work - in both cases my personal message appears for... five seconds? and then it's gone. Besides, I still don't get why in the world after those same five seconds, when I'm not Away/Busy, my system tray icon changes to Invisible when I am actually online.

---

### Post by khc on 2009-03-27
I believe the problem with status messages on ICQ is fixed with pidgin 2.5.5, which will come with Jaunty

---

### Post by khc on 2009-03-27
> **anasofiapaixao said:**
> What? I can see myself just fine on WLM, only can't chat with myself. Pidgin isn't faking anything - at least when it comes to showing myself on the contact list.

I have the exact same problem, and was wondering exactly how come so little people have complained about it (for what it looked like from my googling). I tried saving a status too, and it doesn't work - in both cases my personal message appears for... five seconds? and then it's gone. Besides, I still don't get why in the world after those same five seconds, when I'm not Away/Busy, my system tray icon changes to Invisible when I am actually online.

Please describe your problem in full. Which protocol are you having problem with? If it's just ICQ, I think it's fixed in 2.5.5.

---

### Post by zzanzare on 2009-03-28
> **khc said:**
> I believe the problem with status messages on ICQ is fixed with pidgin 2.5.5, which will come with Jaunty

i can confirm that icq 6 can see my status messages all right with pidgin 2.5.5 (compiled from sources). So can another pidgin on windows. Qip (build 8092), however, only shows away/online/etc.. but not the text of my status message. But I can live with that;-) Thanks

---

### Post by khc on 2009-03-29
> **zzanzare said:**
> i can confirm that icq 6 can see my status messages all right with pidgin 2.5.5 (compiled from sources). So can another pidgin on windows. Qip (build 8092), however, only shows away/online/etc.. but not the text of my status message. But I can live with that;-) Thanks

QIP is always a weird beast, nothing much we can do about that...

---

### Post by FirstByté on 2009-12-03
> **khc said:**
> I believe the problem with status messages on ICQ is fixed with pidgin 2.5.5, which will come with Jaunty

Sorry to be resuscitating a dead thread.

But I still have this issue on my Pidgin 2.6.2.

I have two yahoo accounts setup. Anytime I change my status, only one of them changes. I've tried going to account management "Ctrl + A" editing the specific account status, still no good.

It's either the icon changes or the status of both account don't even get changes at all.


my temporary workaround for now:

What ever status type I wish to setup, such as Away, Busy etc, I'll choose it first then I'll go to custom messages.
Then I'll enter the status I want.


At the moment its failure to always use my predefined status causes me a lot of unwanted disturbances!

---

