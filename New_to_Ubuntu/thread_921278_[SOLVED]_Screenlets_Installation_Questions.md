---
title: "[SOLVED] Screenlets Installation Questions"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-16
I installed Screenlets from the repositories and learned today that it is about 4 versions behind the one available online. So I want to install the new one. Three questions:

1) I'm new to Linux. Does one typically need to remove an older software version before installing a new one?

2) Regarding Screenlets specifically... is it best to blow everything away and start clean with the new version?

3) Does anyone have a weather screenlet working? I can never seem to connect (I'm in the US). What's the correct way to enter your location?

Thanks.

---

### Post by prshah on 2008-09-16
> **bobsmith2 said:**
> 
1) I'm new to Linux. Does one typically need to remove an older software version before installing a new one?

2) Regarding Screenlets specifically... is it best to blow everything away and start clean with the new version?

3) Does anyone have a weather screenlet working? I can never seem to connect (I'm in the US). What's the correct way to enter your location?



1) Yes, you should uninstall the old one (from the repositories), and then install the new one. It's not typically required for all software, but in the case of (repository-version) screenlets, it's an exception, and required.

2) Yes, specially in the case of (repository version) screenlets, it is. Maybe not for future updates.

3) The weather screenlet is "broken" because of a change in the SOAP url for weather.com. You can [correct it manually]("http://ubuntuforums.org/showthread.php?t=784053"), or, if you put in the newer version, it will work just fine.

---

### Post by bobsmith2 on 2008-09-16
Thanks prshah. That is exactly what I needed.

---

