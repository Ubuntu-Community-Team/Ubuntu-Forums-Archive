---
title: "Disaplay drivers on Ubuntu 12.04"
date: 2018-08-08
forum: New to Ubuntu
---

### Post by its_bigB on 2018-08-08
I've installed ubuntu 12.04 32bit and 64bit OSs, and I can't see hihgher resolutions on display settings. That's running on low resolutions. How can I update the display driver accordingly?

---

### Post by Autodave on 2018-08-08
First off, 12.04 is dead: 18.04 is the newest one.  (12.04 = 2012, April) You need to download and install 18.04 and it will likely solve your low resolution problem.

Can you give us some specs on your machine: especially the graphics card?

---

### Post by Topsiho on 2018-08-08
12.04 was supported until April 2017, and is quite dead now.
So do as Autodave suggests, and you'll probably solve your problem, and can look forward to almost 5 years of computing without problems :)

Topsiho

---

### Post by its_bigB on 2018-08-26
> **Autodave said:**
> First off, 12.04 is dead: 18.04 is the newest one.  (12.04 = 2012, April) You need to download and install 18.04 and it will likely solve your low resolution problem.

Can you give us some specs on your machine: especially the graphics card?

Thank you for the comment.

I'm using 12.04 to maintain some backward compatibility on C++ compilers I'm using for few distributions. Working with 16.04 and everything works fine. Desktop PC I'm using have a display output, and using a VGA converter to connect the monitor.

---

### Post by its_bigB on 2018-08-26
> **Topsiho said:**
> 12.04 was supported until April 2017, and is quite dead now.
So do as Autodave suggests, and you'll probably solve your problem, and can look forward to almost 5 years of computing without problems :)

Topsiho

Yeah, I'm trying the possibilities of migrating to newer version of Ubuntu. For the moment there are limitations. Let's see how it goes. :KS

---

### Post by Topsiho on 2018-08-26
I hope you'll be successful. There is no hope using 12.04, so you'll need to switch to 16.04 (maintained until April 2021) or better still, to 18.04 (maintained until April 2023). The intermediate versions of Ubuntu are only supported for 9 months, so are not an option, to my opinion.

Topsiho

---

### Post by its_bigB on 2018-08-26
> **Topsiho said:**
> I hope you'll be successful. There is no hope using 12.04, so you'll need to switch to 16.04 (maintained until April 2021) or better still, to 18.04 (maintained until April 2023). The intermediate versions of Ubuntu are only supported for 9 months, so are not an option, to my opinion.

Topsiho

Thanks for the quick response. Yes, I wanna too migrate to latest version ASAP, to avoid some of the limitations of C++ because of maintaining backward compatibility. Let's see, hope for the best!

---

### Post by Yellow Pasque on 2018-08-26
> **Topsiho said:**
> There is no hope using 12.04

It depends on the GPU, which the OP did not mention for some reason.

---

### Post by its_bigB on 2018-08-27
> **Temüjin said:**
> It depends on the GPU, which the OP did not mention for some reason.

That's to maintain some backward compatibilities on C++.

---

### Post by Yellow Pasque on 2018-08-27
> **its_bigB said:**
> That's to maintain some backward compatibilities on C++.

What? I was asking what GPU you had. You can look at lspci
```
sudo update-pciids
lspci
```

---

### Post by its_bigB on 2018-08-27
Oh, let me check.

---

### Post by Topsiho on 2018-08-27
There's still no hope using 12.04, if you intend to connect to the internet. As 12.04 is not maintained, you can't update it any more.
If the computer is to be used without any connection to the internet, I think there is no problem at all. If not, then there is a huge security risk. But I don't know how you could install any reliable and good driver without the internet.
So you have two problems to solve:

1. Get rid of 12.04 and replace it with either 16.04, or 18.04
2. If necessary, how to get back your C++ compatibility.

It's a long time since I experimented some with C++, and I remember there was a change in how to use the iostream:

1. you should use <iostream> in stead of <iostream.h>
2 all variables have their own namespace. The variables in the headerfiles that come with the compiler have the namespace std.
3. void main() must now be replaced with int main(), the program has to return an integer.

You understand that I don't write this from the top of my head, but I copy this from a note I pasted in my C++ book, many, many years ago.

It is unwise to us a C++ that is now obsolete, so you'll have to change things anyway, if I'm guessing in the right direction.

But first get rid of 12.04

Topsiho

---

### Post by Yellow Pasque on 2018-08-27
> But I don't know how you could install any reliable and good driver without the internet.

Who said anything about not having an internet connection? And even if there's no internet connection, the OP could put packages on a USB stick.

---

### Post by deadflowr on 2018-08-27
FTR: 12.04 is not fully dead if you have Ubuntu Advantage, which is paid support Canonical offers.
[https://www.ubuntu.com/support/esm]("https://www.ubuntu.com/support/esm")
I have no idea what the eta is how long that support is suppose to go on for.
I'm guessing it's supported until April 2019,
or looks like that from the chart in this page
[https://www.ubuntu.com/about/release-cycle]("https://www.ubuntu.com/about/release-cycle")

---

### Post by Topsiho on 2018-08-27
> **Temüjin said:**
> Who said anything about not having an internet connection?.

I did! I know me very well, so I trust him.

Please read before posting.

Topsiho

---

### Post by Yellow Pasque on 2018-08-27
> **Topsiho said:**
> I did! I know me very well, so I trust him.]

Huh?

> Please read before posting.

I did. You're not making any sense. And to top it off, trying to get the most basic info from the OP apparently requires the Jaws of Life. It's very frustrating and I don't foresee this thread going anywhere, so unsubscribing. Good day and good luck.

---

### Post by its_bigB on 2018-08-28
> **deadflowr said:**
> FTR: 12.04 is not fully dead if you have Ubuntu Advantage, which is paid support Canonical offers.
[https://www.ubuntu.com/support/esm](https://www.ubuntu.com/support/esm)
I have no idea what the eta is how long that support is suppose to go on for.
I'm guessing it's supported until April 2019,
or looks like that from the chart in this page
[https://www.ubuntu.com/about/release-cycle](https://www.ubuntu.com/about/release-cycle)

Unfortunately I don't have a paid support. Just trying to find the drivers freely available.

---

### Post by Topsiho on 2018-08-28
> **its_bigB said:**
> I've installed ubuntu 12.04 32bit and 64bit OSs, and I can't see hihgher resolutions on display settings. That's running on low resolutions. How can I update the display driver accordingly?

We'll start again as things are going in an unwanted direction.

1. You say that you use Ubuntu 12.04. **That is the first thing that you need to change**, as 12.04 is not supported anymore, and using it puts you at risk, whenever you are connected to the internet. Also you then cooperate to make the internet an insecure place to be.
2. Installing Ubuntu 16.04, or better still, Ubuntu 18.04 might solve your problems with your display settings immediately. Ubuntu is second to none in recognizing hardware, especially hardware theat's not the newest of the newest. So please try the latest supported versions, 16.04 and 18.04 are each supported for 5 years. You can try the LiveCD's first, and see how they work with your graphics cards
3. You could always change your graphics cards, taking the old one with you to the shop. I am afraid that if it's an AGP one (if I remember this well) you'll have a problem to get a replacement.
4. If that still doesn't solve your problem, on the internet (which you can now explore safely), e.g. on this forum, you can find solutions how to install an appropriate driver. From within Ubuntu itself. Downloading and installing drivers from elsewhere probably can be done, but it is not the easy road to go. It might work with your card, but does it work with Ubuntu?

As to C++ compatibility, that you mention elsewhere, I already said something about that. C++ changes, and it is hard luck that if you have an old and long and undocumented C++ program, adapting this to the new C++ compiler that comes with the newer distributions, than this may be a problem.

I wish you luck :)

Topsiho

---

### Post by monkeybrain20122 on 2018-08-28
> **its_bigB said:**
> That's to maintain some backward compatibilities on C++.

You can install older or newer gcc and g++ versions in Ubuntu. e.g I have gcc, g++ and gfotran 7 set up as alternative compilers in  Ubuntu 16.04 (default gcc 5.4 is too old to compile some applications and I don't want to upgrade since I have spent much time tuning and hacking my 16.04 to optimize performance and it is damn near perfection)  I installed it in my $HOME by compiling from source. If I can do this with a compiler which is "too new" for the distro chances are you can do same with a compiler which is "too old" (depending on how far back compatibility you need, some older versions of compiler are in the repo and you don't even need to compile)

---

