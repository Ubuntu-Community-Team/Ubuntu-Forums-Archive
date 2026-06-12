---
title: "Lubuntu netbook freeze problem"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by RAJASD on 2011-10-12
IF U CAN C THIS LINK, U CAN UNDERSTAND MY PROBLEM:
[http://forum.lxde.org/viewtopic.php?f=8&t=31374](http://forum.lxde.org/viewtopic.php?f=8&t=31374)

(reason for posting this here is there are lot of coming to this forum)

thanks...

---

### Post by demeter on 2011-10-12
try this:[http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178), it did solve my freeze problem with my G475

---

### Post by RAJASD on 2011-10-12
@ meter
i'm using lubuntu...mine is hp mini will this work for me?
u had similar problem like me?

---

### Post by wildmanne39 on 2011-10-12
Hi, that is the same link I was going to give you, so you should try it.

Also some people have solve this issue by upgrading there kernel.
Thank you

---

### Post by RAJASD on 2011-10-13
Hi friends...
i did it as  u said...
but the process is differ from acer to hp.
i tell you what i did correct me if any error exist...

=>i found BIOS setup in f10 not in f2 as per the post.
=>system configuration->boot option
=>internal network adopter boot
=>it fixed as disabled,i enabled it.
=>i saved it and exit.

last 24 hours no problems. i have a doubt when i turn on the machine new message showing like 
"this product covered by intel"
some serial numbers appearing and
"exit PME ROM"
"failed media" earlier i havent come across such msg in 
starting up.i think it is because of change network boot.
will this msg affect netbook?
computer is not my cup of tea.so help me.

thanks:)

---

### Post by amjjawad on 2011-10-13
Raja,

Had something to tell you but I keep forgetting that.
Have you checked your BIOS? Have you checked the booting devices? somehow, I suspect that you are booting form a network device? if I remember correctly, some users here on this forum have managed to fix similar issues but different machines and it was Ubuntu not Lubuntu but that shouldn't be a problem since the concept is the same.

Please double check that.

Make sure your machine boots first from internal HDD. Or at least from USB then HDD. I think you are using HP mini so there is no CD-Drive there.

---

### Post by amjjawad on 2011-10-13
Oh and one more thing. You need to learn how to be patient ;)

Sending Private Messages won't get you the answer faster, trust me!

---

### Post by RAJASD on 2011-10-13
> **amjjawad said:**
> Oh and one more thing. You need to learn how to be patient ;)

Sending Private Messages won't get you the answer faster, trust me!

haha ok ok...
sorry friend...
but u tell me "u bought ur first machine...and it doest work
properly.hw wud u feel?"

---

### Post by amjjawad on 2011-10-13
> **RAJASD said:**
> haha ok ok...
sorry friend...
but u tell me "u bought ur first machine...and it doest work
properly.hw wud u feel?"

Never mind ;)

Well, I feel you but that should motivate you and encourage you to search, search and search until you manage to find the answer :)

IMHO, nothing is better than this.
Beside, not to worry, you have some good friends here who are willing to help so relax :D

---

### Post by RAJASD on 2011-10-13
> **amjjawad said:**
> Raja,

Had something to tell you but I keep forgetting that.
Have you checked your BIOS? Have you checked the booting devices? somehow, I suspect that you are booting form a network device? if I remember correctly, some users here on this forum have managed to fix similar issues but different machines and it was Ubuntu not Lubuntu but that shouldn't be a problem since the concept is the same.

Please double check that.

Make sure your machine boots first from internal HDD. Or at least from USB then HDD. I think you are using HP mini so there is no CD-Drive there.
@ammjwad

pls read my earlier post which how i chage the bios.give me
feedback.
i have san disk pen drive...it works well with my netbook...
how to check booting devices?

hav gd day:)

---

### Post by amjjawad on 2011-10-13
> **RAJASD said:**
> @ammjwad

pls read my earlier post which how i chage the bios.give me
feedback.
i have san disk pen drive...it works well with my netbook...
how to check booting devices?

hav gd day:)

How close your BIOS to mine:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]


Concept is the same but I know your BIOS will be slightly different.

Point is: make sure the first device to boot from is your HDD or USB. Try to disable booting from Network or at least set that as a third choice.

---

### Post by RAJASD on 2011-10-13
did as u said...

---

### Post by RAJASD on 2011-10-13
> **amjjawad said:**
> How close your BIOS to mine:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]


Concept is the same but I know your BIOS will be slightly different.

Point is: make sure the first device to boot from is your HDD or USB. Try to disable booting from Network or at least set that as a third choice.

@ammjawad
hi...

i did as u said...
pls check out the ealier order of priority
1.usb cd rom(but i don have cd port)
2.network adopter(i think this is u mentioned)
3.usb diskette/usb hd
4.notebook hd
5.usb floppy

i changed into this following order:
1.notebook hd
2.usb diskette/usb hd
3.usb floppy
4.network adopter
5.cd rom(last priority bcos no cd port)
any other correction anna?

earlier i enabled network adopter boot.
should i disable it?

patiently waiting anna;)

---

### Post by amjjawad on 2011-10-13
> **RAJASD said:**
> @ammjawad
hi...

i did as u said...
pls check out the ealier order of priority
1.usb cd rom(but i don have cd port)
2.network adopter(i think this is u mentioned)
3.usb diskette/usb hd
4.notebook hd
5.usb floppy

i changed into this following order:
1.notebook hd
2.usb diskette/usb hd
3.usb floppy
4.network adopter
5.cd rom(last priority bcos no cd port)
any other correction anna?

earlier i enabled network adopter boot.
should i disable it?

patiently waiting anna;)


Ok, we are trying to test and see which setup is going to be helpful, deal? so this is not permanent. Anyhow, you can change it any time you want. For example, when you want to install or re-install, you need to set your BIOS to boot from USB Drive then Internal HDD.

Anyway, try to keep the network enabled. Let's see what difference that will make. 
If the freezing still happening then try to disable it.

---

### Post by RAJASD on 2011-10-13
> **amjjawad said:**
> Ok, we are trying to test and see which setup is going to be helpful, deal? so this is not permanent. Anyhow, you can change it any time you want. For example, when you want to install or re-install, you need to set your BIOS to boot from USB Drive then Internal HDD.

Anyway, try to keep the network enabled. Let's see what difference that will make. 
If the freezing still happening then try to disable it.

deal:)

im not gonna disturb u anymore.
ill let u kno if any problem.

one personal question bcos im apparently seeing u people
work so hard in this forum...
how u people and ubuntu family earn from this opensource and free os project? 
u seem friendly so tat im asking u...(if it is confidential..no need...sorry)
bye anna...tak care:)

---

### Post by amjjawad on 2011-10-13
> **RAJASD said:**
> deal:)

im not gonna disturb u anymore.
ill let u kno if any problem.


I didn't say don't disturb you, I just want you to post here because sending PM will not help others to learn from our mistakes and take our advices ;)

The Forum is for everyone and everyone is encouraged to share and contribute and this is how our community will grow bigger and **better**. It's always the quality not the quantity.


> one personal question bcos im apparently seeing u people
work so hard in this forum...
how u people and ubuntu family earn from this opensource and free os project? 
u seem friendly so tat im asking u...(if it is confidential..no need...sorry)
bye anna...tak care:)
Although it's OFF-TOPIC :P but it's ok, feel free to ask whatever comes to your mind ;)

For me, I'm jobless and have no source to earn money from. I'm planning to move to another country to start a new life there. Life is hard and harsh.
I'm not sure about other people so can't talk on their behalf. However, we are all here volunteers. Linux deserves some of our time so I won't hesitate to spend sometime here :)

---

### Post by RAJASD on 2011-10-13
> **amjjawad said:**
> I didn't say don't disturb you, I just want you to post here because sending PM will not help others to learn from our mistakes and take our advices ;)

The Forum is for everyone and everyone is encouraged to share and contribute and this is how our community will grow bigger and **better**. It's always the quality not the quantity.



Although it's OFF-TOPIC :P but it's ok, feel free to ask whatever comes to your mind ;)

For me, I'm jobless and have no source to earn money from. I'm planning to move to another country to start a new life there. Life is hard and harsh.
I'm not sure about other people so can't talk on their behalf. However, we are all here volunteers. Linux deserves some of our time so I won't hesitate to spend sometime here :)

i understand bro.i will keep on update.so that i can do my part
to linux.:D

off-topic
i surprised by your answer.everybody may not like u as large hearted.i pray to god for your new life.
all the best anna:)

---

### Post by wildmanne39 on 2011-10-13
Hi amjjawad, it appears since the OP used the link that he/she has had no more freezing yet.
Thank you

---

### Post by amjjawad on 2011-10-13
> **RAJASD said:**
> i understand bro.i will keep on update.so that i can do my part
to linux.:D

Yes, keep us updated and by the way, Lubuntu 11.10 is out :D

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

> 
off-topic
i surprised by your answer.everybody may not like u as large hearted.i pray to god for your new life.
all the best anna:)

I really appreciate that!
God bless you and thanks a lot for your nice words :)

---

### Post by amjjawad on 2011-10-13
> **wildmanne39 said:**
> Hi amjjawad, it appears since the OP used the link that he/she has had no more freezing yet.
Thank you

Yes, thanks a lot my Ninja Friend :D
In case something goes wrong, we both will be notified :)

---

### Post by RAJASD on 2011-10-14
> **wildmanne39 said:**
> Hi amjjawad, it appears since the OP used the link that he/she has had no more freezing yet.
Thank you

> **amjjawad said:**
> Yes, thanks a lot my Ninja Friend :D
In case something goes wrong, we both will be notified :)

no bros...it does freeze.today i had freezing prob
2 times when i was in chromium..

problem is not fixed for wifi button also as it does freeze when turn off the button...
for ur kind info network adopter is in enabled state only..

any other options?

---

### Post by wildmanne39 on 2011-10-14
Hi, it would probably be best to install the new version that just came out because my next recommendation is to upgrade to the new kernel, I can give you directions to do that but you will also install the new kernel if you install the new version of lubuntu.

However I can not recommend doing an upgrade you should do a clean install. 

I upgraded last night and it was all messed up, I also have a clean install that is working great.
Thank you

---

### Post by amjjawad on 2011-10-15
I think I'm out of ideas at the moment and I'd suggest to go for Lubuntu 11.10 too. It has Kernel version 3 and if the current issues has anything to do with the Kernel then Lubuntu 11.10 may fix that.

---

### Post by amjjawad on 2011-10-15
> **wildmanne39 said:**
> However I can not recommend doing an upgrade you should do a **clean install**. 

I upgraded last night and it was all messed up, I also have a clean install that is working great.
Thank you

Although I have never used "Upgrade" option but I totally agree with my friend here.

JUST make sure to backup your important files in case you'll go for that.

---

