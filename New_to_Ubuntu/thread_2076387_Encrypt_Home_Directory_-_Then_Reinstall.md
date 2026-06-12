---
title: "Encrypt Home Directory - Then Reinstall?"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by held7over on 2012-10-25
Ubuntu 12.10 is installed in primary partion / and my personal data is stored in primary /home.

I have never had an encrypted home directory before. What happens if I need to reinstall Linux?  

Do I automatically loose my personal data?

And if not, do I have to reinstall linux with the home directory encrypted again in the case of needing to reinstall?

Thanks! :)

---

### Post by sandyd on 2012-10-25
> **held7over said:**
> Ubuntu 12.10 is installed in primary partion / and my personal data is stored in primary /home.

I have never had an encrypted home directory before. What happens if I need to reinstall Linux?  

Do I automatically loose my personal data?

And if not, do I have to reinstall linux with the home directory encrypted again in the case of needing to reinstall?

Thanks! :)

What kind of home directory encryption you are talking about?

a) The one during the partitioning stages of installation (encrypted home partition)
b) The one during the User setup stage of installation. (Encrypted home directory)

Also a few more things:

If your /home is on the same partition as /root, reformatting the drive will delete everything.

If you are using the encrypted home directory setup, there is a password it asks you to set when you first boot up, and get to the desktop. That password can be used to decrypt your home directory. Once it is decrypted, all your files can be accessable. :) . I suggest you do this on LiveCD.

Then, you can reinstall and place all your files back.

---

### Post by held7over on 2012-10-26
The OS and my personal data are in separate partions.

I thought it was the one that encrypted the home directory....but, maybe I missread it. It randomly generated a "suggested" passphrase which I accepted.

However, when I boot up, I am only asked for my User password, not the encryption passphrase.

I just tried accessing my / directory on the hard drive using the LiveDVD and nautilus. No problem getting into /. 

However when I try accessing the home directory via Nautilus, it promptly tells me "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "user".....and it doesn't ask me for my passphrase.

Am I using the LiveDVD working though Nautilus correctly?

Does this sound like I picked encryption for the /home directory or the entire partition?

---

### Post by CaptainMark on 2012-10-26
You have chosen to encrypt your home directory probably through the user setup section of the installation process, this is the suggested method. If you're asking how to reinstall ubuntu then its simple, you can run a live cd and select install, use the same partitioning setup you have now (usually its safe to use the option "replace ubuntu 12.04 with ubuntu 12.10" or similar) then as long as you select the option to encrypt the home folder again in the user setup and use exactly the same password then your data should be safely carried across to a new install 

Just to be certain though: There is no 100% safe way to ensure no data loss when re-installing/re-partitioning/upgrading so be sure you always make a total separate backup of your important files and completely remove them from your computer during any maintenance

---

### Post by CaptainMark on 2012-10-26
Whoops duplicate posts

---

### Post by Wim Sturkenboom on 2012-10-26
> **CaptainMark said:**
> Just to be certain though: There is no 100% safe way to ensure no data loss when re-installing/re-partitioning/upgrading so be sure you always make a total separate backup of your important files and completely remove them from your computer during any maintenance
Totally agree; if something can fail, it will when you least expect it. Make backups (and validate them) and you'll never have to worry.

---

### Post by held7over on 2012-10-26
Not to worry, I have everything backed up on other computers. It's simply the time to transfer across my network that is the deterient. 

Thanks! That procedure for upgrading or reinstalling was what I was sweating....and I couldn't seem to find the information I needed googling. I now have the confidence to do the reinstall.

I appreciate your time! Thanks!

---

