---
title: "Installation process hangs at &quot;Who are you?&quot; stage"
date: 2015-08-12
forum: New to Ubuntu
---

### Post by buddy123 on 2015-08-12
While trying to install Ubuntu desktop on my laptop, after I fill in the user & password settings, It simply hangs forever.
at start it seems like its reading from CD, after a long while it stops and nothing happens since that point on.
the cursor is "thinking" and thats it.
Any suggestions? I thought perhaps its CD issue, so I burned it again, from different iso.
then I tried to use the same iso as Virtual Machine and it worked like a charm.

---

### Post by howefield on 2015-08-12
Unacceptable characters in the information ?

I'm sure it isn't but just ruling out the obvious.

---

### Post by buddy123 on 2015-08-12
Sure, thats reasonable :-)
Nothing special there, no
username is simply my name in lowercase and so password is also something silly

---

### Post by Topsiho on 2015-08-12
Why is the password something silly, because your username is simply your name in lower case?
Password should be entered by you yourself (twice), and be constructed by you, such as "oNC9ytA6" (an example which now, however, is useless, as everybody can see this). At least 8 characters, more is better.

A reason the install halts might be that there is not enough room on the partition you use for the install. I was thinking the CD might be the culprit, but this seems not to be so.
Is the memory in your computer OK. You might use the memtest to check this, let it run at least a few hours (or a number of complete passes). If no errors are found this memory is probably OK.

---

### Post by buddy123 on 2015-08-17
True, Its not that silly as my name, of course not, I just meant - Its not the issue probably. Its a mixure of upper-case, lower-case and numbers. not too short.

I honestly dont know the reason why it happened. I tried everything - Re-burning the image, boot from CD, boot from DOK..Nothing helped
I did run memory scan for around 3 hours, nothing came up.

Eventually I downloaded the 15.04 version and it worked well.
Very strange, but atleast its behind me.

---

### Post by Topsiho on 2015-08-17
It's very strange indeed.
1) Your 14.04 CD (DVD) is OK as it worked in the Virtual Machine
2) Your way of doing things is OK as the 15.04  works OK, also the hard disk seems OK

3) the memory seems OK

I apologize for reading your

>  username is simply my name in lowercase and so password is also something silly  not correctly: I guess between so and password a , was needed :)



Did you install 15.04 in the same partition as you tried to install 14.04?
If not, maybe the partition for 14.04 is too small.

Do you realise that 15.04 is only maintained for 9 months (until January 2015)?

Topsiho

---

### Post by buddy123 on 2015-08-17
Well, 
what should I do then?
Does it mean that within 9 months there'll be no more updates available? seems bad...:-\

The entire setup is the same, my disk is the same, I went trough the installation without determining myself the paritions so it goes around 50GB for root and the rest for /home, and around 30GB for swap (this is what I see happens on 15.04 anyway)
I will try again with Kubuntu. I'll report soon.

no apologize needed, I did mistakenly let it seem so :)

---

### Post by howefield on 2015-08-17
> **EranYanay said:**
> Well, 
what should I do then?
Does it mean that within 9 months there'll be no more updates available? seems bad...:-\

It means 15.04 goes end of life January 2016 meaning you have 3 months after 15.10 comes out to upgrade if you wish to continue running a supported release. There isn't anything bad about it, it is the way it is, Long Term Support releases come out every 2 years and are supported for 5 years, the last one was 14.04 and the next is 16.04. The interim releases coming out at 6 month intervals and have 9 months of support.[/QUOTE]

---

### Post by Topsiho on 2015-08-17
> Well,
what should I do then?
Does it mean that within 9 months there'll be no more updates available? seems bad...:-\

It is exactly that. Only the LTS-versions (every two years) are maintained for 5 years, the intermediate versions only for 9 months.

So I suggest to use your present install to get a bit used to Linux and Ubuntu, Kubuntu and other versions, and after January decide what you want and install the 16.04 LTS-version.

You might also try the different tastes of Mint, and, who knows, Suse, Fedora (I used to use Fedora, long ago, but (then) the Fedora fora were very unfriendly). The KDE-desktop of Suse seems to be superior to the way it is implemented in Kubuntu. An example: In Dutch, the translations in the latter are sometimes borked (I am a Dutch translator for KDE).

You are in a very interesting phase of exploration, use it :)

Topsiho

---

### Post by buddy123 on 2015-08-17
In that case, why should I care. I dont mind upgrading in a few months.
and as I was advised from a different Thread I opened here, I created separate partition for my / (root) folder, so, when I come to upgrade, my /home folder is on a different partition, so it would be pretty easy. I'll just have to install some apps again.

Thanks :-)

---

