---
title: "Removing users"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by stevedore on 2008-05-07
Hi all,

I've just installed Hardy Heron and now whenever I turn on my computer I need to login in as a user and give my password - which is annoying for my partner who can never remember my password and this can't log on. When I had the previous distribution I never needed to log on as a user and give a password.  How do I get rid of the user identity and skip the log-on stage when turning on the computer?  I've tried deleting the user identity but when I restart the computer I am still asked to log on and am back to where I started.

thanks :)

---

### Post by hyper_ch on 2008-05-07
That can be set somewhere in your system / login manager... not sure where that is in gnome but have a look around and explore the settings ;)

---

### Post by kesman on 2008-05-07
Why don't you just create a new account for your buddy?

---

### Post by tamoneya on 2008-05-07
system->administration -> login window
go to the security tab and setup an automatic login.

---

### Post by Aearenda on 2008-05-07
You can't do anything on Linux without logging on with a recognised username. Some distros just do this automatically, as 'root'. Ubuntu does not, because this is insecure. However, you can tell the system always to log on a given non-root user.

Assuming you haven't really deleted your admin user, you need to go to system->administration->login window, supply your password, then go to the 'security' tab, check 'enable automatic login' and select the user. That's it!

If you have deleted your only admin user, there's more to do - let us know if this is the case.

---

### Post by stevedore on 2008-05-07
Thanks, creating a new user won't get around the problem of her perpetually forgetting passwords.

---

### Post by lswest on 2008-05-07
Well, you can set up an automatic login on the PC, however, if she plans to run anything as root she would need to know your password, maybe set her up an account with a password that is something she can easily remember?

---

### Post by stevedore on 2008-05-07
Excellent thanks Aearenda and tamoneya!

---

### Post by Xiong Chiamiov on 2008-05-07
> **stevedore said:**
> Thanks, creating a new user won't get around the problem of her perpetually forgetting passwords.
In reality the problem is that Microsoft has trained people to not use passwords.  I believe they are required now in Vista, but most people are very bad at remembering passwords of any sort because they never have had to.  That's why I think it's a good idea to force them to enter a password to login; the only reason I don't is because I'm sudo-ing crap all the time so I'll never forget it.

---

