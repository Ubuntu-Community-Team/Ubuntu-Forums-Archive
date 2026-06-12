---
title: "How to switch between users ?"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by Akhj on 2012-09-05
Hello,

I am using Ubuntu 12.04 LTS (32 bit). When i am using terminal sometime i must have to use ```
sudo -i
``` for root privilege.
But then if i wish to switch back to another user, i don't know the command. Any help will be highly obliged. 

Thanks & Regards

---

### Post by steeldriver on 2012-09-05
```
exit
```

will get you out of the sudo -i shell back to your original user; and

```
su *newuser*
```

will switch to a different user

---

### Post by Lars Noodén on 2012-09-05
If you've run [font=Courier New]sudo -i[/font] then you can get back the the previous user by pressing ctrl-d or else typing [font=Courier New]exit[/font].

If, as the regular user, you wish to expire sudo's capabilities before it times out anyway you can enter [font=Courier New]sudo -k[/font] or [font=Courier New]sudo -K[/font]

Or, if you want to just test something as another user but go back to working as root right after that, then you can use [su](http://manpages.ubuntu.com/manpages/precise/en/man1/su.1.html). e.g. [font=Courier New]su -l  *akhj* [/font]  That will make you become the other user until you type exit, at which point you'll return to being root.

---

### Post by Akhj on 2012-09-05
THanks a Ton @ : **steeldriver** & [B]Lars Noodén :)
[/B]

---

