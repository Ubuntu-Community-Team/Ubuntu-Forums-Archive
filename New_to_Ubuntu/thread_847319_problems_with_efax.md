---
title: "problems with efax"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-07-02
I can't send a fax via efax.

Here is the information that I get.

Can anyone tell me what I am doing wrong?

Socket running on port 9900
efax-0.9a: 10:06:49 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 10:06:49 opened /dev/ttyS1
efax-0.9a: 10:06:49 failed page /home/server/Desktop/fax.ps.001
efax-0.9a: 10:06:49 Error: fax device write: Input/output error
efax-0.9a: 10:06:51 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 10:06:53 Error: fax device write: Input/output error
efax-0.9a: 10:06:55 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 10:06:55 sync: dropping DTR
efax-0.9a: 10:06:55 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 10:06:55 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 10:06:58 Error: fax device write: Input/output error
efax-0.9a: 10:07:00 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 10:07:00 Error: fax device write: Input/output error
efax-0.9a: 10:07:00 Error: fax device write: Input/output error
efax-0.9a: 10:07:00 sync: sending escapes
efax-0.9a: 10:07:00 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 10:07:00 Error: fax device write: Input/output error
efax-0.9a: 10:07:00 Error: fax device write: Input/output error
efax-0.9a: 10:07:01 Error: fax device write: Input/output error
efax-0.9a: 10:07:03 Error: fax device write: Input/output error
efax-0.9a: 10:07:05 Error: sync: modem not responding
efax-0.9a: 10:07:05 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 10:07:05 finished - unrecoverable error

---

### Post by mjlee105 on 2008-07-02
i am also a newbie, but it looks to me like your attempt to fax is trying to open a path to a physical fax modem, not to a efax virtual printer that is connected to the internet.  are you pointing your self to the right device.  and do you have the ability to upload faxes to efax. are you using just the reader or do you have the plus program?

just looked at the efax page, and the way you send a fax is via you email,  receipeints fax number and then an efax domain name.  then you attach what you want to fax.

---

### Post by saskatchewan on 2008-07-02
You are right, I was trying to open a path to a physical fax modem.  I do not have the plus program.

How do I get hooked up with theh this virtual printer?

---

