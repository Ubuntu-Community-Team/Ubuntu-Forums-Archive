---
title: "firefox browser won;t connect to wireless"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by cebowlin on 2013-11-04
ddownloaded ubuntu, burned a live cd, and booted up to sample the os without installing onto the windows 7 system.  Firefox works fine in Windows 7, but while useing the ubuntu live cd, Firefox doesn't connect.  it keep asking for a password, which I don"t know.  any solutions

---

### Post by ajgreeny on 2013-11-04
Asking for a wireless password or some other "user-type" password?  What is the actual password request saying?

---

### Post by cebowlin on 2013-11-04
needs authentication passwords or encryption keys

---

### Post by coffeecat on 2013-11-04
Firefox is not asking for the encryption key. The network manager app is asking for your wireless network WPA passkey so that the operating system can connect to your wireless network. The same thing would happen in Windows if you tried to connect to a wireless network before you had configured the system with the WPA passkey. 

You say you don't know the password. If this is your wireless router, who configured Windows for you? Is this your wireless router? If it came pre-configured from your ISP, is the passkey printed on the under-surface?

---

### Post by K7AAY on 2013-11-04
And, if you install Chromium or some other browser, does the same problem occur?

---

### Post by cebowlin on 2013-11-04
Thanks everyone, I finally figured the problem out.  Being an 80 year old man having moved in with my daughter, who set the wireless up, and i did not want to bother her at work, I was able to get the key to allow firefox to go.  thanks much

---

### Post by coffeecat on 2013-11-04
@cebowlin, I'm glad you've solved this. Just so that you know. In the live session when running from the CD, all configurations are stored in volatile memory, so when you power down they will be lost. You will have to enter the passkey if you boot up a new live session.

---

