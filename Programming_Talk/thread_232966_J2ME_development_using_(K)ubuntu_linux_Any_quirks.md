---
title: "J2ME development using (K)ubuntu linux? Any quirks?"
date: 2006-08-09
forum: Programming Talk
---

### Post by kentl on 2006-08-09
Hi!

As a migrated formerly long time Windows user I'm now exclusively using Linux. The distribution of choice for me (at the moment) is Kubuntu 6.06 Dapper.

I'm wondering if I'm equally able to develop J2ME MIDP 1.0 and MIDP 2.0 applications using my new operating system?

For example I'm wondering about vendor specific emulators. I'm pretty new to J2ME development (I've created a small and pretty crappy game for MIDP 1.0) but if I'm not mistaken it works like this. The best way to test an application/game is on the actual device. The second best is to test it using the vendor specific emulator for that device. And the "worst" way to test it is using the general J2ME emulator from Sun.

If I'm correct it leads me to these questions:

[LIST=1]
[*] Is it easy/possible to integrate a real device with the testing process using Linux? That is. To have the updated application/game transfer to the actual phone for testing.
[*] Are the vendor specific emulators available for me to use from Linux as well? Are they of equal quality as those for Windows?
[*] Does the Sun J2ME toolkit work as well in its Linux version as the Windows version?
[/LIST]


Also. If you know how to setup a J2ME development environment using Eclipse in Linux I would be greatful. But the main questions are the ones above.

Thanks for reading this long post. If you have the relevant knowledge and decide to answer some/all of my questions I'll be very greatful.

Best regards
Kent Larsson from Sweden

---

### Post by kentl on 2006-08-13
No one? :(

---

### Post by kostkon on 2006-08-13
1. If the device has a usb interface and acts like usb mass storage device (like many Sony Ericsson mobiles) will be very easy to do it. Additionally, maybe you'll be able to do it with bluetooth. Or with [gnokii]("http://www.gnokii.org/") if your device is a mobile phone, it is supported by the program and you have a cable or irda. Lastly, you can transfer your app through the net to the device.

2-3. I don't have much experience with J2ME in Linux, but [Netbeans]("http://www.netbeans.org/") with the Mobility Pack it's a good overall, out of the box, solution for J2ME development. As fas as Eclipse, there is the [eclipseME]("http://www.eclipseme.org/") plugin, but in general it needs more effort to get it to work for you. I would advice you to give a try with Netbeans. The Mobility Pack page in the Netbeans site has links for vendor specific emulators. Check them, some of them will work in Linux (like the Nokia ones, I think). Netbeans Molity Pack has some already anyway. As far as vendor specific toolkits, from that page I assume that Netbeans supports many devices already, i.e. it doesn't use only the generic *Java Wireless Toolkit* to compile J2ME apps.

The only J2ME thing I did in Ubuntu, when I had a revelant project, was to run the Palm emulator and run a J2ME program into it to test my project. The J2ME app was a client to a Java server and I tested it many times in Ubuntu. But the J2ME client development was mostly done in Windows and the Java server one in Red Hat Fedora at a lab.

I hope I helped you somehow! :)

EDIT: changed one word.

---

### Post by kentl on 2006-08-14
kostkon: Thanks for your reply! I'll reluctantly try NetBeans in a while when I get back into J2ME development. I'm so use to Eclipse that I feel a bit married to it.

---

