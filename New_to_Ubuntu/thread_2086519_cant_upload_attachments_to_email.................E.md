---
title: "cant upload attachments to email.................ERROR 400"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by SayakBiswas on 2012-11-21
Hello Linux users


This is my first time on any kind of forum, so please bear with me,

My problem is that i cannot send attachments with my gmail/corporate email accounts.
This is an ubuntu issue as it works fine in windows 7 64 bit.

my error is HTTP Error 400 Bad request

while sending attachments it uploads partially then stops at "waiting for mail.google.ca".....while using firefox 16 or chrome 23.

Atleast opera 12.11 gives me the error 400 message.

i had installed kernel 3.6.6 to test, but the issue persisted and i lost my proprietary audio drivers, so i purged it.

thunderbird also fails to attach to emails.

google chrome plugins: stealthy, https, ad-block
opera: none
firefox: default ones only

[I]also submitting this post took a lot of time and retries...
...stuck at "waiting for ubuntuforums.org......" or "connected to ubuntuforums.org......" 
[/I]

I need your help cause it would be a shame to switch back to Win7 for this little issue.
and frankly, I'm in love with linux. where else can i play my flac audio at floating piont bitrates

I'm not a linux expert like you guys, but i've been testing ubuntu  since 10.10 and finally decided to jump ship with 12.04, and i just dont wanna go back.

My system:
ubuntu 12.04 64 bit (default kernel)
phenom II x4 965
8 gb ram
radeon hd 6950 (with proprietary catalyst 12.10 drivers)
realtek 8810e onboard lan (with proprietary drivers)
realtek alc889 onboard audio (with proprietary drivers)

---

### Post by cwsnyder on 2012-11-21
Is this a problem with all attachments, or only some attachments?  Are you sure the _same_ attachments work in Windows with the same email provider?  If so, which browser are you using in Windows?

---

### Post by newb85 on 2012-11-21
Could be an issue with security measures you've put in place, like firewalls or antivirus scanners.

---

### Post by cwsnyder on 2012-11-21
I was thinking more the size of the attachments.

---

### Post by SayakBiswas on 2012-11-21
did some further tests, very small(<100 bytes)   .txt files are being sent but not much else.

turned off ufw but no effect

and i tried live booting 12.04 lts and 12.10 CDs and tried the attachments from there.....did'nt work

in windows, same attachment worked through same email provider(google)

i was using internet explorer (default/not updated) with windows7/64

PS:  its not that i cant attach at all...........it takes me 45-50 minutes, a  lot of attempts and even more patience to attach a ~20KB .xls file in gmail.

---

### Post by cwsnyder on 2012-11-21
It sounds to me as if your ISP is throttling your upload speed severely.  I know on my DSL connection I get 3Mb/sec downloads, but only about 0.5Mb/sec on uploads according to [http://www.speedtest.net](http://www.speedtest.net) .

---

### Post by SayakBiswas on 2012-11-21
> **cwsnyder said:**
> It sounds to me as if your ISP is throttling your upload speed severely.  I know on my DSL connection I get 3Mb/sec downloads, but only about 0.5Mb/sec on uploads according to [http://www.speedtest.net](http://www.speedtest.net) .


+1 ^^

yes Exactly, you're right.
@ speedtst, i got 15 ms ping, 1.4 mbps down....but the upload test failed to even connect...

---

### Post by CharlesA on 2012-11-21
> **cwsnyder said:**
> It sounds to me as if your ISP is throttling your upload speed severely.  I know on my DSL connection I get 3Mb/sec downloads, but only about 0.5Mb/sec on uploads according to [http://www.speedtest.net](http://www.speedtest.net) .
This bit. I would contact the ISP and inquire.

---

### Post by SayakBiswas on 2012-11-21
yeah but inquire about what exactly? i mean, what do i ask them?? I'm sure they are not very linux savvy.

And the thing is, it works in windows, so this has to be a settings/config mismanagement basically.

---

### Post by CharlesA on 2012-11-21
> **SayakBiswas said:**
> yeah but inquire about what exactly? i mean, what do i ask them?? I'm sure they are not very linux savvy.

And the thing is, it works in windows, so this has to be a settings/config mismanagement basically.
Have them run a line test. If speedtest cannot even connect to do an upload, that might be why it isn't working.

Have you tried checking from a livecd? I doubt it is the install itself, but it couldn't hurt.

---

### Post by SayakBiswas on 2012-11-21
> **CharlesA said:**
> Have them run a line test. If speedtest cannot even connect to do an upload, that might be why it isn't working.

Have you tried checking from a livecd? I doubt it is the install itself, but it couldn't hurt.


yes i did try from the livecd, both 12.04 and 12.10, it did'nt work :(


finally, got a upload rating, 0.14 mbps......

---

### Post by CharlesA on 2012-11-21
I would still contact the ISP and ask them to do a line test to see if it is your connection, or if they just don't play nice with a *nix machine.

---

