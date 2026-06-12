---
title: "PPP dial-up long time to connect - waiting for prompt"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by jvolzer on 2008-09-26
I've downloaded and installed GNOME-PPP on Ubuntu 8.04 to dial into the Internet using my cell phone on Verizon. I've been able to get it to connect, but it takes a long time.  It displays "waiting for prompt".  If I click "view log" and watch the process, I see that it pauses for a long time at "Carrier detected.  Waiting for prompt".  Eventually it gives up and shows "Don't know what to do!  Starting pppd and hoping for the best.  starting pppd."  Then I see all the IP address stuff and all is well.

Is there a way to change the delay so it doesn't sit there at wait for some prompt that it apparently never receives and just move right onto starting pppd anyhow?  I know from doing this same process under Windows that it should be able to connect and be ready to go in just a few seconds.  This delay really drives me crazy.

---

### Post by cmnorton on 2008-09-26
Have a look at the options file in /etc/ppp. As I recall using vpn connections, there are ppp parameters you can tweak.

---

### Post by NoReflex on 2008-09-26
Hello!

I too experienced the same delay using Huawei e220 on Vodafone. In KPPP it worked fine (there was no delay). At least it works :D.

Best wishes,
NoReflex

---

### Post by jvolzer on 2008-09-26
Cmnorton, I've scoured the options file in the /etc/ppp folder and I can't find anything that seems to be related to that particular setting or delay.

NoReflex, I'm just learning my way around GNOME (and Linux in general), so I don't think I want to switch to KDE just for this.  Besides, I'm trying this on two laptops, one of which is an eeePC, so I'm using Ubuntu-eee with the GNOME interface that's optimized for the small screen.  I'd like to keep both laptops in the same environment.

Any other ideas?

---

### Post by cmnorton on 2008-10-01
I've seen access to options that would handle what you describe, and I believe they're defined in the /etc/ppp/options file.

---

### Post by jvolzer on 2008-10-01
> **cmnorton said:**
> I've seen access to options that would handle what you describe, and I believe they're defined in the /etc/ppp/options file.

Yes, there are a lot of options in that file.  As I said, I've scoured it.  I don't see anything related specifically to that time out though.

---

### Post by AClark on 2008-10-01
It says here:

[https://help.ubuntu.com/community/dialupmodemhowto/setupdialer](https://help.ubuntu.com/community/dialupmodemhowto/setupdialer)

that Stupid mode will start pppd immediately

sounds like it might be what you need

In the Gnome-ppp gui under setup then options there is a box you can check labeled "ignore terminal strings (stupid mode)

don't know for sure but worth a try.

Good luck

---

### Post by jvolzer on 2008-10-03
> **AClark said:**
> Stupid mode will start pppd immediately

sounds like it might be what you need

In the Gnome-ppp gui under setup then options there is a box you can check labeled "ignore terminal strings (stupid mode)


YES!  That's exactly what I'm looking for!  It works beautifully.  I can now connect to the internet within a matter of seconds after clicking connect in gnome-ppp.  And there wasn't even a need for editing files.  Thank you!

---

### Post by c5froa on 2009-06-01
Okay so for me... the way i found to stop wvdial from waiting for prompt was to simply add 'Stupid Mode =on' to my /etc/wvdial.conf file.
Now my connection starts and is connected within 2 seconds..
This is my wvdial.conf contents:

[Dialer three]
Modem = /dev/ttyUSB0
Baud = 460800
Stupid Mode = on
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","3netaccess"
Username = 0
Password = 0
Phone = *99***1#


Hope that helps :)

---

