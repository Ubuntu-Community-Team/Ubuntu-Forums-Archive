---
title: "Asus B560M"
date: 2023-10-01
forum: New to Ubuntu
---

### Post by lowlevel0-0 on 2023-10-01
I am new to ubuntu 22.04 LTS. I am using Asus B560M plus wifi motherboard. But in the website they have no option to download their driver for linux.
What can i do now. I also try ubuntu Software.


Even try most of the youtube method.

My audio,wifi not working even my Sata is not showing.

Is there any option to install those drivers?

---

### Post by jeremy31 on 2023-10-01
If you have internet access using ethernet or USB tethering to a smart phone in terminal do ```
sudo apt update
sudo apt install inxi
inxi -Fxxzc0
```
Post results

---

### Post by lowlevel0-0 on 2023-10-01
Ok.then what can i do for sata and audio?

---

### Post by jeremy31 on 2023-10-01
The results I asked for are needed to answer that question

---

### Post by lowlevel0-0 on 2023-10-01
Ether cable working ok in my device.

---

### Post by MAFoElffen on 2023-10-02
According to ASUS here: [https://dlcdnimgs.asus.com/websites/global/aboutASUS/OS/Linux_Status_report_202111.pdf](https://dlcdnimgs.asus.com/websites/global/aboutASUS/OS/Linux_Status_report_202111.pdf)

They said that that motherboard has been supported by Ubuntu since release 20.10. 

There are some caveats: 

[LIST]
[*]You cannot do Intel Optane. It has to be disabled in the BIOS and the module physically removed.
[*]It needs to be an 11th gen Intel CPU = Not 10th Gen. Even though the socket, board and chipset says it supports 10th Gen Intel, doing so disables a lot of things for the chipset... Like the ability to support 4th gen PCI ( and m.2 NVMe), limits the memory types that are compatible of use with it... Support for Turbo Boost... The second M.2 slot will be disabled if the CPU is not 11th gen... Etc, etc, etc.
[*]Secure Boot needs to be disabled.
[*]The SATA Mode needs to be st to AHCI.
[/LIST]
Support for AX210e has been there since kernel 5.10... 

Please come up with a list of what is not working. Either post the results of inxi like was requested, or run the [Ubuntu 'system-info' script]("https://github.com/UbuntuForums/system-info") from a LiveUSB and post the URL of where the report uploads to a pastebin. The later, if ran with the '--details' startup option will tell us which CPU, what version of BIOS, etc, in much detail, so we can see what is going on.

---

### Post by lowlevel0-0 on 2023-10-02
Asus 560M didnt support any of destro.

As per list.

---

### Post by coffeecat on 2023-10-02
@lowlevel0-0, you have been asked three times now for more information. Either the output of the terminal commands described in post #2, or the output of the system-info script as described in post #6. You have ignored all these requests from volunteer users trying to help you. Without that information, no one can give you the help you need.

---

### Post by MAFoElffen on 2023-10-03
> **lowlevel0-0 said:**
> My audio,wifi not working even my Sata is not showing.

In Asus'es support site, they have drivers for Windows, not Linux. So? What drivers do you think you need from Asus? 

You have told us the motherboard and what version of Ubuntu you installed. That is all. That leaves a big void. And every time we ask you for something, you come back with a half-sentence quip about how ASUS did not provide you with drivers...

I don't think you understand what any of us has said. Either that or you are ignoring us on purpose. 

Please reread post #6.

I need information from you in any of the forms asked. Why? Because i can't read your mind. I want to help you get things going, but I can't. I know the motherboard, but I need to know what else is there, and how it is setup.

I know the 'system-info' script's report will fill in many of the blanks to provide me information, for me to help you. I know the limitations of that motherboard, and what affects it. If I ask you for information, there are reasons why I am asking.

The drivers are already there, in Ubuntu 22.04, that support that motherboard, storage disks, the WiFi device that it has, and the sound controller. I said that, and explained briefly (summarized) in Post #6. _I will not say anything more until I know what else is there_. 

I am not going to guess or recommend a solution until I know it is sound and will work for your situation. Nor will I play games back and forth, trying to 'extract' information from you. [I]There is no emotion in that. Those are just the facts. 

"Help us help you."[/I]  If you cannot do that, or are not willing to accept our help, then I will go on to help someone else who needs help.

You have not said enough to us to judge your experience level and skills, for us to determine how we need to explain things to you. Without that, I will just have to assume that you are a complete new user, so I do not skip over any details. Sound fair to you?

Let's go on. Waiting for information from you.

---

