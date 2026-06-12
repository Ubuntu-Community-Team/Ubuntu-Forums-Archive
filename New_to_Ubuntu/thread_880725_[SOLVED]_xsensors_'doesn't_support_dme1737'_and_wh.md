---
title: "[SOLVED] xsensors 'doesn't support dme1737' and white screen"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by rbjscv on 2008-08-05
OK, that may not be quite right, as I got so disgusted I deleted the program and lm-sensors also.  Lm-sensors gave me a listing of all sorts of info including dme1737; and of course I did this from the command line.  But I want a graphic to leave running as I'm suspecting some sort of failure coming.  Xsensors couldn't get past the dme1737 problem; all I got was a blank screen.  

I tried commenting out the offending line in sensors3.conf- same thing. And I commented out the offensive term in etc/modules.  My motto:  When confused try anything that doesn't make sense.

Next step was to uncomment all refernces to DME1737: same error msg with white screen.

Please go easy on me as I'm only a 7 week old Ubuntu.

---

