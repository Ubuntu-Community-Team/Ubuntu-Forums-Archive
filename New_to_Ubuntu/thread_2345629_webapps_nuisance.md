---
title: "webapps nuisance"
date: 2016-12-06
forum: New to Ubuntu
---

### Post by yazdzik-k on 2016-12-06
Dear friends,
 
Behaviour: upon closing a browser,  cpu use increases for about a minute,  causing fans to run,  &c.

Observations:  system monitor shows "unity web apps" using 12% of cpu
                       killall unity-webapps-messaging-host  stops hysteria

skylake, 16G ram,  etc,  so this is not a low power system, 
Linux xxxxxx 4.8.0-30-generic #32-Ubuntu SMP Fri Dec 2 03:43:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

How do I completely rid my life of unity web app integration,  since it is nothing I would ever want, need use,  or think part of a rational system?

(since removing unity web apps entirely would remove unity tweaks,  I removed components using apt-cache one by one.  offender was unity-chromium extension)

Best,
M

---

### Post by Jeroen_Mathon on 2016-12-06
Hey Yazdzik,

Have you tried following the instructions in the following article?
[http://askubuntu.com/questions/214755/how-can-i-remove-unity-web-apps](http://askubuntu.com/questions/214755/how-can-i-remove-unity-web-apps)

There they explain that you can run 
`gsettings set com.canonical.unity.webapps integration-allowed false` to fully disable unity webapps.

Can you try following their instruction for me?

---

### Post by yazdzik-k on 2016-12-06
Dear J,

Thank you very much for your kind reply.  Actually,  that is where I got the basic information.  

Editing gconf or dconf did not solve the issue,  but, yes,  I did begin by changing "authorisation allowed" and getting rid of pre-authorised domains"

this had the same effect as disabling them via the unity tweak tool,  to wit,  none.

There is probably something buggy in the chromium hook,  either on the web app integration or chromium itself,  which allows a continued seek after the parent has been closed.

(yes,  I miss the simple old days where anyone could find the son-of a file in linux distros......;) )

Gratefully,

M

---

### Post by Jeroen_Mathon on 2016-12-06
Hey Yazdzik,

Have you tried using firefox or Vivaldi(The spin off of chrome)

---

