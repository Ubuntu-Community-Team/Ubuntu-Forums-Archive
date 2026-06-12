---
title: "Telling Display Manager (gdm) to launch xwindow app"
date: 2010-06-11
forum: Programming Talk
---

### Post by alibaba163 on 2010-06-11
Hello,
       Can anyone tell me how can I tell my gdm to launch xwindow app (e.g xeyes) at login screen. 

Please note: i want application to be running(available) at login screen NOT after user has logged in (login screen is the screen where we enter username and password)

I am running ubuntu 9.04

Any help will be appreciated.

Regards,

Lepeord.

---

### Post by whiteychs on 2010-06-11
I'm not sure this is possible out of the box. You'd have to have another X session running as GDM is just waiting for a user to login and redirects it. GDM locks that X session as far as i know.


You could look into hacking a GDM theme and inserting xeyes...

---

### Post by alibaba163 on 2010-06-11
Hacking into gdm is actually something i want. I want to know how gdm launches "login screen" may be it is script running in /etc/init.d/gdm but that apparantly does not  have any reference to lauch login screen window.

Please remember i want my app to be available at login screen window.

Regards.

---

### Post by soltanis on 2010-06-11
Not sure if this is possible; gdm probably doesn't allow you to launch apps into the login window, maybe for security reasons, or maybe because right now gdm is just not that configurable.

I'm sure if you edited the gdm source you could add this functionality.

---

### Post by alibaba163 on 2010-06-11
Could you please suggest where is gdm source code. I can try playing with it. See if changine source code could do the trick!!

---

