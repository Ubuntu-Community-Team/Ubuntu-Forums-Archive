---
title: "Selectively slow Ubuntu"
date: 2022-05-04
forum: New to Ubuntu
---

### Post by hakelm on 2022-05-04
After 6 years I had to discard my Ubuntu 16.04 and made a fresh installation of Ubuntu 20.04.
To my surprise some programs are painfully slow.
I  noticed that my favorite browser Opera didn't behave normally.  It can  take up to 10 seconds to enter a single character in the search field.
The same applies to Thunderbird.
Other programs like Firefox, VMware player and Libre Office are snappy and behaves normally.
Programs run in the terminal like Maxima behaves at full speed. 
To get an idea of what is going on I installed Vivaldi, Konqueror and MS Edge. They all behave in the same dreadful way.
The only browser I have tested that behaves normally is Firefox.
I can live with Firefox but somehow I must fix Thunderbird.
Can anyone please tell me what is going on?
H

---

### Post by TheFu on 2022-05-06
No way to know from the description. We need some facts.

Check the system log files for any errors or warnings or stack dumps.
Check that network performance is as expected. A slow DNS can impact any tools that use DNS lookups.  Firefox started using their own DNS about 18 months ago, which, if you don't specifically disable it, could be why FF is still fast and other browsers are slow.

Also, I've had terrible slowness from FF because I don't have IPv6 enabled anywhere on my home network. There's a specific hidden setting in FF to get it to drop IPv6.  Since FF is fast for you, this is not the issue, but something similar may be at work with other programs.

LTS releases don't have patches for 6 yrs. They get 5 yrs of standard, no-hassle, support.  Also, you may find that your old hardware isn't ready for the demands of 20.04 Gnome3 desktop.  There are other, lighter, desktops which could be a better choice, depending on the hardware.

If you need help deciding what your hardware could/should have for DE, run and post **inxi -Fxz** command + output. That provides a summary. inxi isn't pre-installed, so update, then install the package using whatever package manager you like.

Thunderbird act funny on 1 of my systems when I should have rebooted after a new release was installed or a new kernel was installed, but forgot.

* Check the system logs.
* Check the networking.
* Please provide an overview of the hardware using the command above.

---

### Post by hakelm on 2022-05-07
Thanks. 
I [COLOR=#202124][FONT=arial]initially[/FONT][/COLOR] installed 22.04 and couldn't get it to work properly (VMware etc,) so I settled for 20.04 but that was even worse with terrible performance but I could get  VMware and other programs to to work but some where very hesitant and slow. So I tried a do-release-upgrade to 22.04 and so far everything seems okay and snappy.
H

---

### Post by keylowmike on 2022-05-10
I installed Ubuntu 22.04 on my Ol' Reliable (Dell Latitude D820) and I had problems with sluggish performance and Firefox wasn't working at all.  I found that my hardware just couldn't handle the software, so I installed Lubuntu 22.04 and it works great.  

The reason i bring this up is because you mentioned that you've got six years of service out of 16.04.  Your hardware might need a lighter OS that doesn't bog it down, or in my case a web browser doesn't even boot up.  I do suggest to try Lubuntu 22.04 ;).

---

### Post by hakelm on 2022-05-11
Thanks.
I believe my hardware is in order, Intel I7+16GB of ram. My previous post is wrong. Also 22.04 misbehaved. I also think that I found the culprit, it is probably the drivers for my Radeon 290 GPU. Disabling the GPU removed the problem. But there where other problems with 22.04 so I swapped it for 20.04 which now runs satisfactorily but wo GPU.
H

---

### Post by keylowmike on 2022-05-12
> **hakelm said:**
> Thanks.
I believe my hardware is in order, Intel I7+16GB of ram. My previous post is wrong. Also 22.04 misbehaved. I also think that I found the culprit, it is probably the drivers for my Radeon 290 GPU. Disabling the GPU removed the problem. But there where other problems with 22.04 so I swapped it for 20.04 which now runs satisfactorily but wo GPU.
H

Have you tried reinstalling the Radeon 290 drivers in 20.04, see if it's compatible?

---

