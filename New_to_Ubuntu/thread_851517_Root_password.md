---
title: "Root password"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Vossibear on 2008-07-06
Hi @all

At first. I#m new and I am a pupil from Germany. My English is very bad. Sorry for the mistakes in my Question.

I have installed ubuntu for the first time and I wanted to run su in the terminal. But the answer is: "Fehler bei Authentifizierung" in English : "Mistake at the Authentification" (I think it is the translation ;) )

Sudo does work well.

Thanks

---

### Post by lisati on 2008-07-06
Heißen Sie willkommen zu Ubuntu

---

### Post by Xerp on 2008-07-06
Any specific reason you want to use su rather than sudo? Sudo really is the way forward!

---

### Post by esbo on 2008-07-06
> **Vossibear said:**
> Hi @all

At first. I#m new and I am a pupil from Germany. My English is very bad. Sorry for the mistakes in my Question.

I have installed ubuntu for the first time and I wanted to run su in the terminal. But the answer is: "Fehler bei Authentifizierung" in English : "Mistake at the Authentification" (I think it is the translation ;) )

Sudo does work well.

Thanks

Not too sure what you are saying.

Have you tried entering your password?

---

### Post by spiderbatdad on 2008-07-06
use ```
sudo -i
```

or ```
sudo -s
```

for a root session.

For single commands: ```
sudo <command>
```

By default, the root password is locked, and should remain locked for security reasons.

---

### Post by lamego on 2008-07-06
You should not use root, please read:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Vossibear on 2008-07-06
I did not set a root password at the installation, but I thought it would be the same password as the password of my first user.

And that does not work:

But If you think it is not necessary to login at root I will do so too ;)

But I want to know the root PW and that is the way to trie ...

---

### Post by mcduck on 2008-07-07
There is no root password, and that'a also the reason why "su" doesn't work (as it's asking for root password, not your own user's password like "sudo" does).

---

### Post by Vossibear on 2008-07-07
So I wont be able to run su forever? ;)

However ... sudo is enough

---

### Post by mcduck on 2008-07-07
> **Vossibear said:**
> So I wont be able to run su forever? ;)

However ... sudo is enough

True, "su" doesn't work. But "sudo -i" gives you the same result, opens a root shell, so you can use that instead.

---

### Post by rogier.de.groot on 2008-07-07
I always just use "sudo su -" without setting the root password.
No offence, but I get real tired of typing 'sudo' every time in commands like "sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get clean". Though I usually just solve that with a shell script so I can say "sudo update.sh" instead.

---

### Post by ByteJuggler on 2008-07-07
"sudo" remembers your password for some period of time, so you don't have to type it on every invocation of it.  You can configure this period of time too.

---

