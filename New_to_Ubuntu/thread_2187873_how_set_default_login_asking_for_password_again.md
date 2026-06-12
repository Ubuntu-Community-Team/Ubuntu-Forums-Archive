---
title: "how set default login asking for password again?"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by fatharraxman on 2013-11-14
I want to set my login screen (greeting screen or GUI) to the default setting, which asks for password befor let me login, I dont know how did I messed it out, now running saucy, it just can show me the list of desktop environments, but after I chose the environment I want, I just click and login directly, then after I login to the descktop another message pop out asking me to type my keyring password.
 I wounder if me inserted GPG (or PGP not sure) key from previous system did that, any how, I just want the normal default login back, any help please? step by step for a newbie> terminal prefered

---

### Post by steeldriver on 2013-11-14
You need to set a password for the account. You can either use the 'Login Options' section under the System Settings --> User Accounts GUI tool, or use the passwd command

For your own account
```
passwd
```

For somebody else's account (assuming your account is a member of sudo)
```
sudo passwd *username*
```

---

### Post by cmcanulty on 2013-11-14
or system settings-user accounts-unlock-turn off auto login

---

### Post by stefbeukers on 2013-11-14
System Settings - User Accounts - 'Unlock' - Switch 'Automatic Login'

---

### Post by fatharraxman on 2013-11-14
I have used all those in vien guys need something deep it is a real tough problem

---

### Post by fatharraxman on 2013-11-14
System Settings>User Accounts> pressing "Unlock" but is not responding as all other "Unlock"s in this laptop right now nor the terminal commands change anything, they change the password in terminal but still the same exat above mentioned drama

---

### Post by fatharraxman on 2013-11-14
I found this answer by [Arthur Tan]("http://askubuntu.com/users/149453/arthur-tan")  :[INDENT]   > Run the following command in terminal:[INDENT]```
sudo gpasswd -d username nopasswdlogin
``` substitute your username for username.[/INDENT]
[INDENT]

[/INDENT]
[/INDENT]

  It solved my problem [Here]("http://askubuntu.com/questions/211084/how-do-i-get-ubuntu-to-ask-me-for-a-password-at-login-again")

---

