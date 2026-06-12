---
title: "Need to set password in https://web.xabber.com/ every time I start Brave browser"
date: 2024-07-31
forum: New to Ubuntu
---

### Post by maketopsite on 2024-07-31
Ubuntu 20.04 LTS. No need in openSUSE Leap 15.5. Any idea please ?

---

### Post by TheFu on 2024-07-31
Not sure from your minimal information what you actually want.  Do you want to force a new password to be used every time?
Or do you not want to be forced to login every time?  The words used are quite ambiguous.

Clean out the cookies and "local objects". I.e. only use session cookies.  That should forced logins every time the browser is restarted.

I know nothing about xabber.com, so how they choose to handle password reuse is up to them.  Many sites will expire passwords after a specific period of time. Some use 3rd party authentication, so blocking 3rd party cookies will break logins. OTOH, security + privacy is generally enhanced by blocking 3rd party cookies completely.

---

### Post by maketopsite on 2024-08-01
> **TheFu said:**
> Not sure from your minimal information what you actually want.  Do you want to force a new password to be used every time?
Or do you not want to be forced to login every time?  The words used are quite ambiguous.

Clean out the cookies and "local objects". I.e. only use session cookies.  That should forced logins every time the browser is restarted.

I know nothing about xabber.com, so how they choose to handle password reuse is up to them.  Many sites will expire passwords after a specific period of time. Some use 3rd party authentication, so blocking 3rd party cookies will break logins. OTOH, security + privacy is generally enhanced by blocking 3rd party cookies completely.

Excuse me I didn't expect someone want enter password on every start of browser.

I have to enter password on every start of Brave browser.  I would like Brave remember the password so as I don't have to enter password on every start of Brave browser.

---

### Post by TheFu on 2024-08-01
Most people would use a password manager for this, since trusting any webbrowser's built-in password handling has been proven to be a bad idea.  Now, I prefer to use password manager manually, so I know exactly when passwords are used, but some people like to have them autofill using an extension.  I just don't like browsers to have direct access to my password DB.

**Bitwarden** and **KeePassXC** are on my short list, but lots of people prefer to pay money to use password managers from others, like 1Password or LastPass.  Some sites, like banks are known to block automatic password entry or to add steps like call-backs before the allow access. My bank will provide a small hardware token with a changing password every 60 seconds.  Just be cautious if a bank or other financial institution wants you to use a cell phone authentication.  I don't think those are safe.  The USGovt has removed them from the allowed methods of using 2nd factor authentication for their needs.

A good password manager will change your life.  You'll stop worrying about passwords and every website you log into will have a different, random, passphrase.  You'll use longer passwords too, since 99% of them, you'll never actually type again.  It doesn't matter if a password is 20 characters or 60 characters when a computer is going to enter it for you.   For some of my logins, I also used a random username, so I couldn't tell you many brokerage login if I wanted to. I don't know it. It is random.  A few times in the last 30 yrs, I've had to recite the username to someone at the brokerage company. They think I'm crazy, but are kind enough not to say it. ;)

Also, KeePassXC uses a standardized encrypted file/DB format, so other KeePass compatible password managers can access it too.  It is convenient to have that DB on multiple devices, so I never worry about losing it.  

I'm not a fan of any password manager that stores passwords in the cloud, anywhere. That just seems like a terrible idea to me.  Sure, the math says they are safe, but are they really?  IDK.

---

### Post by currentshaft on 2024-08-01
> **maketopsite said:**
> Excuse me I didn't expect someone want enter password on every start of browser.

I have to enter password on every start of Brave browser. I would like Brave remember the password so as I don't have to enter password on every start of Brave browser.

Brave is based on Chromium so the password dialog you get is likely to unlock your keyring. Usually you can just press Escape to ignore the prompt.

---

### Post by maketopsite on 2024-08-27
> **TheFu said:**
> Most people would use a password manager for this, since trusting any webbrowser's built-in password handling has been proven to be a bad idea.  Now, I prefer to use password manager manually, so I know exactly when passwords are used, but some people like to have them autofill using an extension.  I just don't like browsers to have direct access to my password DB.

**Bitwarden** and **KeePassXC** are on my short list, but lots of people prefer to pay money to use password managers from others, like 1Password or LastPass.  Some sites, like banks are known to block automatic password entry or to add steps like call-backs before the allow access. My bank will provide a small hardware token with a changing password every 60 seconds.  Just be cautious if a bank or other financial institution wants you to use a cell phone authentication.  I don't think those are safe.  The USGovt has removed them from the allowed methods of using 2nd factor authentication for their needs.

A good password manager will change your life.  You'll stop worrying about passwords and every website you log into will have a different, random, passphrase.  You'll use longer passwords too, since 99% of them, you'll never actually type again.  It doesn't matter if a password is 20 characters or 60 characters when a computer is going to enter it for you.   For some of my logins, I also used a random username, so I couldn't tell you many brokerage login if I wanted to. I don't know it. It is random.  A few times in the last 30 yrs, I've had to recite the username to someone at the brokerage company. They think I'm crazy, but are kind enough not to say it. ;)

Also, KeePassXC uses a standardized encrypted file/DB format, so other KeePass compatible password managers can access it too.  It is convenient to have that DB on multiple devices, so I never worry about losing it.  

I'm not a fan of any password manager that stores passwords in the cloud, anywhere. That just seems like a terrible idea to me.  Sure, the math says they are safe, but are they really?  IDK.

Thank you it must save much time.

---

### Post by maketopsite on 2024-08-27
> Brave is based on Chromium so the password dialog you get is likely to  unlock your keyring. Usually you can just press Escape to ignore the  prompt.
Thank you putting password did not help.

---

### Post by currentshaft on 2024-08-27
Ok

---

