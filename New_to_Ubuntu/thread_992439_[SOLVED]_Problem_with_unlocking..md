---
title: "[SOLVED] Problem with unlocking."
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Schneevvager on 2008-11-24
I received Ubuntu about two months ago and I've been toying around with it. Lately I've created another administrator account and I am unable to unlock the time/date function or any other function for that matter. I discovered this while trying to change the time for a second time.

---

### Post by jemate18 on 2008-11-24
> **Schneevvager said:**
> I received Ubuntu about two months ago and I've been toying around with it. Lately I've created another administrator account and I am unable to unlock the time/date function or any other function for that matter. I discovered this while trying to change the time for a second time.

just click the Unlock button and then type your password

---

### Post by Schneevvager on 2008-11-25
It doesn't give me the option to do that. It tells me it "could not authenticate" or at times doesn't even tell me that (or give me the option to type in my password.). Help is much needed and appreciated.

---

### Post by Furat on 2008-11-25
system -> administration -> users and group 
click in the user then properties 
user privilege 
check if it can administrate the system

---

### Post by Schneevvager on 2008-11-25
It says that neither of the accounts I've created have that privilege. How would I work around that?

---

### Post by unutbu on 2008-11-25
If you managed to create another user, it means that you have an account with root powers. Log in as that user. Open a terminal (Applications>Accessories>Terminal) and type

```
sudo usermod -a -G admin USERNAME
```
substituting the secondary username for USERNAME.
The above command will give the secondary user administrative privileges (the ability to use sudo).

---

### Post by Schneevvager on 2008-11-25
alright, the account you mentioned with root powers, would that be the account labeled root when i check the user groups window? If so then how do I log on to that account. If not, then the account that I created the other account with does not seem to have root powers. As I followed your instructions exactly, and it stated that the account was not in the sudoers file. I'am going to try this with my account I created as well.

---

### Post by Schneevvager on 2008-11-25
Aha! It appears that the account I created had sudo powers, not the one I started with. So now my problem is resolved, thanks for the help and advice.

---

