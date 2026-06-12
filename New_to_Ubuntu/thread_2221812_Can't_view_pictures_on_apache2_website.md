---
title: "Can't view pictures on apache2 website"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by lars4 on 2014-05-03
I can't view any of the pictures (background, and a few others) on my apache2 website. I built the site in kompozer and pointed all the pictures in the right directories but from tests on all my computers they don't show up! Its weird though, because when i click on the html file it shows the pictures. Can someone please help?

-Lars

---

### Post by lars4 on 2014-05-03
Bump

---

### Post by sammiev on 2014-05-03
Hi lars4, only bump once every 24 hrs due to the timezones and members living in all parts of the world. ):P

---

### Post by mcduck on 2014-05-04
Make sure all the picture URL's are relative to the page location, not absolute paths (as in "pics/somefile.png" rather than "/var/www/pics/somefile.png"). And also check the permissions of the image files, they need to be accessible by Apache (which runs as it's own user).

If that's not enough to get things working, please give an example of the html code on the site you are having problems with and I'm sure we'll b bale to figure it out... :)

---

