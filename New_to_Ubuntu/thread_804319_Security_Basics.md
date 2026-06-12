---
title: "Security Basics"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by jaymacs on 2008-05-23
I have been reading as many threads as I could, so I apologize if I have missed the thread I need.

I want to be sure that I am safe to download on bittorrent/general security.  The whole firewall setup has confused me, I have installed Firestarter and tried others such as Lokkit. When I enter 'ufw status' in the terminal it tells me the firewall is disabled.  Isn't the firewall enabled by default?  I download with Deluge only because it has the blocklist feature which makes me feel safer and less likely to get a letter from my ISP, haha.  I found ipblock to be confusing also.  Is there a setup that I can use that will make me less paranoid?  Any general advice would be helpful, I am sorry I am vague in what I am asking.  I am loving Ubuntu to say the least.

---

### Post by sharks on 2008-05-23
firewall is built by default. if u share anything from windows system , better keep a antivirus.

---

### Post by hyper_ch on 2008-05-23
(1) Antivirus is not needed as the malware targets windows... antivirus could be needed if you want to share data with Windows users and want to protect them - I think they should protect themselves

(2) Firewall is mostly not needed. I assume you have a a modem with integrated router. If so, then you have a firewall on there. If properly configure, there should be no need to configure the firewall in linux - it's different on windows as there is lots of spyware that wants to submit data to the net...

(3) bittorrent - what else would you like to know about security there?

---

### Post by Nepherte on 2008-05-23
(2) The built in firewall IPTables should be enabled by default. Firestarter is merely a front end to configure IPTables. Just be sure to block all incoming connections (unless you want remote access to your computer for example, but that's always a security risk).

(3) Instead of using the built in block tool of deluge, you might want to take a look at Moblock. It does the same thing, but it's not only for bittorrent, it works for everything.

---

### Post by jaymacs on 2008-05-23
I just want to be sure that I am not going to be getting in trouble for downloading off of bittorrent.  Bittorrent is my main concern, what is the best protection in that aspect? Thank you guys for your help.

---

### Post by Nepherte on 2008-05-23
Moblock: [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by styphon on 2008-05-23
> **jaymacs said:**
> I just want to be sure that I am not going to be getting in trouble for downloading off of bittorrent.  Bittorrent is my main concern, what is the best protection in that aspect? Thank you guys for your help.

Trouble as in with the law for downloading illegal files? No firewall will help you there. All the information any law enforcement agency needs will be held by your ISP and the server you download from. Best solution, don't download anything illegal.

---

### Post by hyper_ch on 2008-05-23
> **styphon said:**
> Trouble as in with the law for downloading illegal files? No firewall will help you there. All the information any law enforcement agency needs will be held by your ISP and the server you download from. Best solution, don't download anything illegal.

Or use public wifis

---

