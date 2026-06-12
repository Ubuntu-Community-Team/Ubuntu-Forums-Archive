---
title: "Creating service for particular user"
date: 2021-12-03
forum: New to Ubuntu
---

### Post by kilbha on 2021-12-03
Hi community,

I am absolute beginner with ubuntu. I created service to run a piece of code( bash script ). I want to get current active window using script, used xdotool package for this. 

Code to get current active window name is ```
xdotool getactivewindow getwindowname
```. When I run this code in terminal, I am getting the output whatever be the current active window name of **logged** in user. I want to run this script automatically so I created service.

When I copy this code in executable file which gets executed by service I created, It is giving window is null because services are run by **root** and there is no window belongs to root user. Code is trying to get current active window name of root user but I need whoever logged in user current active window name. How can we create service that can be run by particular local user instead of root user?

---

### Post by Tadaen_Sylvermane on 2021-12-03
in the service you can define a user and group field.

```
[Service]
User = root
Group = root
```

Those can be changed. I'm not sure it would work though for the same reason that most commands involving a gui don't work during su. No display variable set.

---

### Post by kilbha on 2021-12-03
Thanks for reply. 

Above settings won't work as per my requirement. By changing above settings, we can enable and disable the service with those users.

I did try for various things to create service per user. 

Please go through below link. If you are able to create service per user, Please share it how can we do it. 

[https://wiki.archlinux.org/title/Systemd/User#How_it_works](https://wiki.archlinux.org/title/Systemd/User#How_it_works)

---

