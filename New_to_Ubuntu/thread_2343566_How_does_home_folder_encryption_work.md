---
title: "How does /home folder encryption work?"
date: 2016-11-17
forum: New to Ubuntu
---

### Post by laggger164 on 2016-11-17
The title says pretty much everything.

I have Ubuntu installed on my USB drive and I have installed some things on it, mostly in the /home folder.
I cannot notice any slowdowns when accessing those programs that I have installed. But that might be because I have a USB 3.0 drive connected to a USB 2.0 port. (still pretty fast tho!)

I did install one without encryption before and it was really close if not identical in performance.

Does anybody know how it actually works then? How it encrypts when it encrypts and the same for decryption?

I did try to google it, but either I am not understanding it, or there isn't any relevant information that I want.

Thanks a lot for the information!

---

### Post by mastablasta on 2016-11-17
it encrypts when you shut down the PC i believe (on logout). think of it as a locked box. you unlock it do your work, put stuff inside and then lock it on exit from your account.

---

### Post by laggger164 on 2016-11-17
> **mastablasta said:**
> it encrypts when you shut down the PC i believe (on logout). think of it as a locked box. you unlock it do your work, put stuff inside and then lock it on exit from your account.
Thanks a lot for the explanation. It really seems too quick to me, how can I test if it is actually encrypted?

---

### Post by kpatz on 2016-11-17
It doesn't encrypt and decrypt the entire volume every time you log in/out.  When you log in, it uses your password/passphrase to decrypt the encryption key used to decrypt data in the volume.  Data is then decrypted on the fly when read and encrypted when written.  When you logout, it just wipes the encryption key from memory, effectively locking the volume.

---

### Post by mastablasta on 2016-11-18
as for test - boot form live USB/DVD and try to open a file (if you can find one).

---

### Post by HermanAB on 2016-11-18
Most processors have special instructions that speed up encryption.  The performance loss to encryption is only about 2 to 3 percent, which is not noticeable.

---

### Post by davehenson on 2016-11-24
> **kpatz said:**
> It doesn't encryp    st and decrypt the entire volume every time you log in/out.  When you log in, it uses your password/passphrase to decrypt the encryption key used to decrypt data in the volume.  Data is then decrypted on the fly when read and encrypted when written.  When you logout, it just wipes the encryption key from memory, effectively locking the volume.

good question and even better answer.  So if we want to ALSO extend that ability to external (usb) drives and such, what would one use? I'm reading on LUKS (with dmcrypt tools) and also veracrypt but I'm not sure either would have that same ease of functionality. 

(I didnt open a new thread as this is the same topic and I didnt want to create a thread that was already on topic)

---

