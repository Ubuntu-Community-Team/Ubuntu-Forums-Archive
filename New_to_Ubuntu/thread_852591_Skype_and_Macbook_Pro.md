---
title: "Skype and Macbook Pro"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by speedemonV12 on 2008-07-07
hey, i have just installed skype on my macbook pro, and had no problems doing the install, but when i try to make a test call, and it tells you to speak, and then it will play it back, i do not hear anything, i went into options, and then sound devices, and tried everyone of them for sound in, and could not get the test call to work. I am on a macbook pro. 
Any ideas what to do ?

thanks!

Fixed the issue... done..

---

### Post by joshsmith on 2008-07-08
so tell us what you did

---

### Post by ppo on 2008-11-23
FYI...
MacBook Pro Santa Rosa with Ubuntu 8.10.

Go in Options > Sound Devices:
  Sound In: HDA Intel (hw:Intel, 1)
  Sound Out: HDA Intel (hw:Intel, 0)
  Ringing: default device (default)

Click on the "make a test call" button.
You should hear a voice saying something like "Hello, welcome to the call service of Skype..."

If it's not working, try maybe the other combinations for Sound In/Out.

---

