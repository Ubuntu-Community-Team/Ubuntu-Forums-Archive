---
title: "Broken pipe?"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-19
After a new install occassionally get an message on reboot " Bytes could not be written: Broken pipe" what does it signify?

Thanks.

---

### Post by Impavidus on 2012-12-19
Technically, it means that the output of one program was written to the input of another program via a so-called pipe. When the second program exited, the first could no longer write to the pipe and on trying so recieved the signal SIGPIPE. It gave an error message and (probably) terminated. I don't know the relevance of this in your case.

---

### Post by Yezinki on 2012-12-19
Thanks Impavidus for trying to explain the technical aspects.

Usually am logged in Pidgin, but I do exit/close it before rebooting......is that the reason?

& my Logitech Quick cam Pro 9000 is always plugged in via usb along with BT dongle even if I am not using them, both usb?

---

