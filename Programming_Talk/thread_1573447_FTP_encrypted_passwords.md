---
title: "FTP encrypted passwords"
date: 2010-09-12
forum: Programming Talk
---

### Post by grantbdev on 2010-09-12
I'm dabbling with FTP connections in **python**. I know that FTP basically shows passwords in plaintext over a network and can be sniffed, and have actually sniffed my own FTP information with Wireshark. 

I want to know if it is possible to send a password encrypted (so sniffers would see the password in say, base64) and then have the password decrypted back to plaintext on the FTP server so it can check to see if it is correct then login. If this isn't outside of impossible, I'd like to know how this could be achieved. 

I know there are things like SFTP and so forward that are much more secure than regular FTP, this is just a little experiment for me to see if I can't add a little selfmade security.

---

### Post by Some Penguin on 2010-09-13
Look into public-key encryption.

---

### Post by Neezer on 2010-09-13
A great alternative to this is using ssh to get SFTP. It is really easy to setup, and then you can use rsa key encryption.

---

### Post by slavik on 2010-09-13
base64 encoded passwords can be decoded with base64 decoder.

public key encryption won't easily work, since you have to negotiate the key trasfer, the suggested solution (sftp) will work as it runs an ssh tunnel for ftp thereby encrypting the entire ftp session. the other alternative is ftps (ftp over ssl) which can be more of a hassle to set up (especially on old systems without proper packages, but it can be done).

---

