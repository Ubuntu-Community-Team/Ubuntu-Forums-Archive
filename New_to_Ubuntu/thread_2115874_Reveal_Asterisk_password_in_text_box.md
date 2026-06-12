---
title: "Reveal Asterisk password in text box"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by ss0007 on 2013-02-14
Hi ,

I have forgotten my password that I gave in Remmina RDP.
I am able to see Asterisk password in "Edit connection" window but I am not able to copy it since its a password field.

Are there any tools in Linux to reveal text boxes in Asterisk chars ?

---

### Post by DuckHook on 2013-02-14
If your password was originally added to your keyring you can decrypt and view it as follows:

1. Use Dash to open "Passwords and Keys".
2. In *Passwords* tab, drill down to Remmina.
3. Properties>Key>Password
4. Click *Show Password* checkbox

Your password should be revealed.

<edit>
Did not notice in my original reply that you are using Feisty Fawn. This version is beyond ancient and the above method will not work with it. Frankly, can't remember back that far and strongly urge you to upgrade as support for 7.04 was dropped years ago. If you are still on 7.04, you have far larger security worries than a forgotten password.
</edit>

---

### Post by ss0007 on 2013-02-15
Thanks DuckHook.
I am using 12.10, have not updated by profile yet :-)

I am wondering if there is tool like in Windows e.x BulletsPassView or Asterisk Logger which reveals the password text in the text field of any window. I just could not find any tools like these in Google.

---

### Post by mcduck on 2013-02-15
I doubt such thing would exist. Anyway, you don't need one, the "Passwords and Encryption Keys" tool mentioned by DuckHook will solve your problem. It's the tool used for managing Gnome's keyring where your password is stored.

---

### Post by ss0007 on 2013-02-16
hmm .. Thanks anyway guys 
Next time I will try to use the keyring :-)

---

