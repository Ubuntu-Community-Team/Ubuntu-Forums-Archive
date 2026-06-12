---
title: "Setting a good password"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by hebdave on 2014-04-28
Hi I am not sure whether this is related to the thread but it does involve commands. I just typed sudo passwd to try and change my root password. It will not let me change it even though I enter the new password and it seems to acknowledge it as okay even. My password was a little weak hence the need for change. I wondered if I instead entered the original password when I first installed Ubuntu to see if that was 'needed one' instead to then change to a new password after. I am trying to change the password that I use when I do sudo apt-get update for example. I read the Ubuntu documentation and it seems to suggest there is another password not including the keyring password - perhaps a 'user' password  ? It is certainly confusing me at present hence me asking again about this. I did use character symbols in the new password change so perhaps thats the problem ? Thanks all I appreciate you time and help.

---

### Post by lisati on 2014-04-28
I've moved your post to its own thread, because it's not directly related to the software centre. 

There is some information about sudo, admin privileges, root passwords and the like at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Jim_Kajder on 2014-04-28
Ubuntu is different from other Linux operating systems in that the root account password is locked, and you cannot login as root. I would worry about using character symbols in a password, seems like you might make a mistake entering them. Personally I think a long pass phrase (14+ characters of words strung together) makes a decent password, and is not hard to remember.

---

### Post by HermanAB on 2014-04-29
Government recommendations are 12 characters with complexity or more than 12 characters without complexity.

The best thing you can do is to install KeepassX on Linux, Keepass on Windows and KeepassDroid on your phone, put the database on Dropbox or Copy.com and start using it for all your passwords.

---

### Post by mastablasta on 2014-04-29
dropbox? it's unencrypted.... although the keepass is encrypted.

---

### Post by open2reason on 2014-04-29
hebdave,
Length, strength and complexity all contribute towards a strong password / pass phrase, the article from Stanford University illustrates just that point [URL="http://arstechnica.com/security/2014/04/stanfords-password-policy-shuns-one-size-fits-all-security/"]http://arstechnica.com/security/2014/04/stanfords-password-policy-shuns-one-size-fits-all-security/
[/URL]

---

### Post by bapoumba on 2014-04-29
> **hebdave said:**
> Hi I am not sure whether this is related to the thread but it does involve commands. I just typed sudo passwd to try and change my root password. It will not let me change it even though I enter the new password and it seems to acknowledge it as okay even. My password was a little weak hence the need for change. I wondered if I instead entered the original password when I first installed Ubuntu to see if that was 'needed one' instead to then change to a new password after. I am trying to change the password that I use when I do sudo apt-get update for example. I read the Ubuntu documentation and it seems to suggest there is another password not including the keyring password - perhaps a 'user' password  ? It is certainly confusing me at present hence me asking again about this. I did use character symbols in the new password change so perhaps thats the problem ? Thanks all I appreciate you time and help.

To change a user password, you do not need sudo, just use ```
passwd
``` in a terminal from the user session you are looged in. [http://manpages.ubuntu.com/manpages/trusty/man1/passwd.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/passwd.1.html)

---

### Post by hebdave on 2014-04-29
Okay thanks all I have now changed it much appreciated :p

---

