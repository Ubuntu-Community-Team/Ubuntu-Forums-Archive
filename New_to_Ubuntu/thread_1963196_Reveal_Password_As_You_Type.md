---
title: "Reveal Password As You Type?"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Andavane on 2012-04-22
I wonder if there's anything you can do, briefly to reveal the letter you're typing when you're entering passwords, before it disappears. This option is already there for Android devices, and Android is I understand a Linux variant.

I find it invaluable on my phone and it would be a great benefit in ubuntu for people like me, who type their letters in with a special stick and am not always sure whether I've hit the correct letter. So I'm frequently having to retype my password.

After all, I use my laptop in a chair in the corner and the only person who sees is the budgie.

Regards, John

---

### Post by matt_symes on 2012-04-23
Hi

> **Andavane said:**
> I wonder if there's anything you can do, briefly to reveal the letter you're typing when you're entering passwords, before it disappears. This option is already there for Android devices, and Android is I understand a Linux variant.

I find it invaluable on my phone and it would be a great benefit in ubuntu for people like me, who type their letters in with a special stick and am not always sure whether I've hit the correct letter. So I'm frequently having to retype my password.

After all, I use my laptop in a chair in the corner and the only person who sees is the budgie.

Regards, John

You can use password feedback in your sudeors file. It will display a star (*) when you type a character. This may help.

Open a terminal and type...

```
sudo visudo
```

Enter your password. Change the line.

```
Defaults        env_reset
```

to

```
Defaults        env_reset, pwfeedback
```

Press ctrl + o to save and ctrl + x to exit.

I know of no way to achieve exactly what you are asking though.

Kind regards

---

### Post by zombifier25 on 2012-04-23
If you're using IBus (in order to type foreign language) you can have the said effect when IBus is activated.

---

