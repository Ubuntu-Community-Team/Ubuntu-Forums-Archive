---
title: "Printing to Vista Printer - nothing appears at the printer"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by frenchian on 2012-03-01
When I had 32 bit Kubuntu 11.10, I could share the Canon printer on my wife's Vista machine. A couple of days ago, I changed to 64 bit Kubuntu, and I needed to re-install the printer.

I used the "New Printer" option in System settings, and set it as

* Windows printer Via Samba
* smb://tosh/canon270 (same settings as for 32 bit)
* driver is "Cups + Gutenprint (simplified)

The only difference is that I used my own ppd driver before, and this time I'm using the Cups driver

The problem now is when I print something, nothing appears at the printer, even though Cups says the job was completed.

Can anybody help?

Thanks

---

### Post by frenchian on 2012-03-04
> **frenchian said:**
> When I had 32 bit Kubuntu 11.10, I could share the Canon printer on my wife's Vista machine. A couple of days ago, I changed to 64 bit Kubuntu, and I needed to re-install the printer.

I used the "New Printer" option in System settings, and set it as

* Windows printer Via Samba
* smb://tosh/canon270 (same settings as for 32 bit)
* driver is "Cups + Gutenprint (simplified)

The only difference is that I used my own ppd driver before, and this time I'm using the Cups driver

The problem now is when I print something, nothing appears at the printer, even though Cups says the job was completed.

Can anybody help?

Thanks

After much trial and error, it's now working. A simple solution - all it needed was authentication (my Vista ID and password). (I don't remember having to provide those before, but maybe I did - my memory isn't as good as it was....)

The next battle is to try and get the Canon drivers to work, so I can replace the CUPS drivers. A (new to me) process called "force-architecture" apparently.

Cheers

---

