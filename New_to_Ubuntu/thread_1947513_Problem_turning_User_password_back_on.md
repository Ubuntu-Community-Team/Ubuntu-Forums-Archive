---
title: "Problem turning User password back on"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by Agnosticvigor on 2012-03-26
I recently turned my password off so that I wouldn't have to enter it in every time I start my laptop. I tried to install a theme that I downloaded and I get prompted for a password. It isn't my old password. I'm not sure what the password it is asking for is. So I go back in to turn my password back on and it will not let me without unlocking user accounts. Which I can not do because I do not know the password it is asking for. I tried changing it in through the grub menu from the root shell prompt but after I confirm my new password it gives this message
                                  passwd: Authentication token manipulation error
                                  passwd: Password Unchanged


Please any help will be greatly appreciated.

---

### Post by wildmanne39 on 2012-03-26
Hi, is this how your tried to do it?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thanks

---

### Post by Agnosticvigor on 2012-03-27
Yes it is only instead of giving me the message  [COLOR=Red]password updated successfully[/COLOR]  I get the message            [COLOR=Red]Authentication token manipulation error[/COLOR] [COLOR=Black]and [COLOR=Red]password unchanged[COLOR=Black]. I really appreciate your interest  [/COLOR][/COLOR][/COLOR]in trying to help me.

---

### Post by jerome1232 on 2012-03-27
Check that / isn't mounted read only when you are in recovery mode

```
mount -o remount,rw /
```

Then try changing the password.

---

### Post by Agnosticvigor on 2012-03-27
> **jerome1232 said:**
> Check that / isn't mounted read only when you are in recovery mode

```
mount -o remount,rw /
```Then try changing the password.
Thank you so much it was mounted read only. This fixed my problem.

---

### Post by Agnosticvigor on 2012-03-27
Should I change it back to read only?

---

### Post by jerome1232 on 2012-03-27
No, once you reboot everything will be as it should be.

---

### Post by wildmanne39 on 2012-03-27
Hi, I am glad you git it fixed , please use thread tools to mark the thread solved.
Thanks

---

