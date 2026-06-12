---
title: "Howto: Install Ubuntu on an external hard drive on an Acer Aspire laptop"
date: 2008-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by daltonlaffs on 2008-06-07
The following are the steps I took trying to get Ubuntu onto an external drive on an Acer Aspire 5100 laptop (although it should work on any other computer about the same way).

PLEASE NOTE, these ARE the steps I took... which means there ARE MISTAKES that are fixed later. Please read through so that you don't make the mistakes I did, this is my actual process I'm recording!

1) Buy a MyBook 320GB hard drive at Wal-Mart (by Western Digital) for ~$100

**NOTE: The next step is only necessary if you need wireless internet access through a router**

2) Buy a Zonet wireless card (your Aspire's built-in wireless IS NOT compatible with Ubuntu)

3) Follow the MyBook's [[color=red]sarcasm[/color]]extremely difficult[[color=red]/sarcasm[/color]] installation instructions to get it working in Windows Vista.

4) [COLOR=red]DO NOT USE THE ZONET CARD[/COLOR], Windows can and will mess up its internal settings.

5) Once the MyBook is working, attempt to format it to NTFS. When the format is just A LITTLE BIT done, purposefully end the format to corrupt the drive. I know it sounds stupid, but it *works*.

6) Download the latest version of Ubuntu (8.04 at the time of writing) as a LiveCD.

7) Write the ISO to a CD, I used a CD-RW. Most Aspire laptops come with NTI CD Maker, so use that if you have it.

[COLOR=Silver]8)[/COLOR] *[COLOR="Silver"]This step was a mistake. If you're trying to reproduce this, skip to step 9.[/COLOR]* Restart your laptop to find that the BIOS won't load from CDs. Reenter Windows in frustration.

9) Go into the CD with windows to bring up the Ubuntu menu inside Windows.

10) Choose to use the LiveCD (I think the top option) and use the 3rd option (to get help with startup).

11) It will rewrite your BIOS to allow booting from the LiveCD on startup.

12) Restart again and load the LiveCD.

13) Boot into "normal install" (first button on CD menu).

14) Enter GParted and find your new 320GB hard disk.

15) There should be 1 partition with an "unknown" format. Delete the partition and apply it.

16) Close GParted and restart. Go back into the normal install like before.

17) Hit Install on your Ubuntu desktop.

18) Answer the questions as normal until it asks you where to install it to.

19) Choose to take up the entire 320GB drive.

20) Install Ubuntu as normal, you don't need to change any of the advanced settings.

21) When complete, reboot into the new GRUB bootloader and choose to start Ubuntu.

22) It will start from your external HD and boom, you have Ubuntu!

**NOTE: If you DON'T want wireless internet access, skip to step 29**

23) Shut down and put your Zonet card in. Go back into Ubuntu.

24) In Ubuntu, go to the network options.

25) Set your computer's built-in wireless device to 'roaming mode' if you haven't already.

26) Set your Zonet card to manual configuration. Enter your router's SSID and choose "Automatic DHCP configuration" in the dropdown list.

27) Apply these and let it change the interface.

28) Start Firefox, and with any luck, you're connected now!

29) Enjoy!


Ask questions if you have some, I'll do my best to answer.

---

### Post by causeitsme on 2008-06-10
> **daltonlaffs said:**
> T

2) Buy a Zonet wireless card (your Aspire's built-in wireless IS NOT compatible with Ubuntu)



Sorry, I have to disagree, although it took me some time to get it working.

I too have an Aspire 5100. It has the Atheros ar2413 chipset.

The driver can be found [http://www.atheros.cz/]("http://www.atheros.cz/") . When you click the checkmark under Linux and at the ar2413 chipset you will download "madwifi-0.9.4.tar.gz"

That one did the trick for me. (Although I had to learn all about sudo and make and such as that, 'I'm a noob, if you hadn't guessed').

I also then had to follow these instructions... [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") as I wasn't getting a password prompt.


Anyway, I saw what you'd said about the built-in card not working and felt I had to say something, they do work. At least mine, and from what I've seen others are getting theirs to work as well.

Otherwise, great post, I'd been wanting to do that with an external HD and that's just the ticket. Thanks.

---

