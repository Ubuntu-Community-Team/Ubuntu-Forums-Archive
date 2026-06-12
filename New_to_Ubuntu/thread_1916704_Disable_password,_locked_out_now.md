---
title: "Disable password, locked out now"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by steprock on 2012-01-28
Hey guys. I have got Ubuntu 10 on my son's laptop - which has been terrific so far - but he's hit a snag.

Apparently, he was running on Admin and was tired of logging in, so he went to the Users page and told me he hit "disable password"

Now, he can't log in to Admin, even using his old password. If I log in as Guest and look at Users, the Admin account is listed as Disabled.

What gives? I'd appreciate any advice.

---Total Linux newb alert.---

:::: End solution was to reinstall from scratch ::::

---

### Post by sudodus on 2012-01-28
Welcome to the Ubuntu Forums,

There is a good tutorial about your problem in this link
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/resetpassword_[/COLOR]]("http://www.psychocats.net/ubuntu/resetpassword")

If you cannot restore contact with his present user, you can create a new one according to this link
[[COLOR="red"]_https://help.ubuntu.com/community/AddUsersHowto_[/COLOR]]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by Rodney9 on 2012-01-28
Re-Set Password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Rodney

---

### Post by steprock on 2012-01-28
Thanks muy mucho for the information.

I can get into Root and run that password reset, but it gives me an error when I try to reset the PW:

"Authentication token manipulation error. password unchanged"

I am currently trying to hunt down info on superuser permissions, which might be the issue, and considering wiping out Linux and reinstalling it...the nuclear option.

Any input would be welcome. Thanks again.

---

### Post by sandyd on 2012-01-28
> **steprock said:**
> Thanks muy mucho for the information.

I can get into Root and run that password reset, but it gives me an error when I try to reset the PW:

"Authentication token manipulation error. password unchanged"

I am currently trying to hunt down info on superuser permissions, which might be the issue, and considering wiping out Linux and reinstalling it...the nuclear option.

Any input would be welcome. Thanks again.

The account was disabled. Add his account back to /etc/shadow
```
nano /etc/shadow
```

---

### Post by steprock on 2012-01-29
Thanks Sandy.

I've no idea what to do once I'm in there - total newb, after all.

I do see that there is a user name "admin" with a looooong line of code after it. The "guest" accounts, by comparison have a much shorter amount of code.

I'm trying to research and see how to add that account back in again.


EDIT: Seems to be set to Read-Only at any rate.

---

### Post by steprock on 2012-01-29
Well...that's one way to fix the problem. I reinstalled from the USB stick using the on-screen instructions; namely, to reinstall from scratch. I tried reinstalling and keeping data, but the touchpad and mouse weren't working and I was getting tired of fighting with it.

Also, I've set up a User account for the kiddos.

Thanks for the input, all.

---

