---
title: "safely store password with python"
date: 2011-09-25
forum: Programming Talk
---

### Post by sam81 on 2011-09-25
I'm writing an application in python3 and pyqt4. The application needs to send email through the smtplib. I would like to store the password to authenticate on the server safely. I'm a total noob in encryption. I've tried hashing the password, but it doesn't seem to work. The following example works if I give the password in plain text to the server.login() function, but it doesn't work if I hash it before. What can I do?

```
import smtplib
import email.utils
from email.mime.text import MIMEText
import hashlib

passwd = "mypass"
passwd = bytes(passwd,'utf-8')
passwd = hashlib.sha1(passwd).hexdigest()

# Create the message
msg = MIMEText('This is the body of the message.')
msg['To'] = email.utils.formataddr(('Recipient', 'example2@gmail.com'))
msg['From'] = email.utils.formataddr(('Sender', 'example@gmail.com'))
msg['Subject'] = 'Simple test message'

server = smtplib.SMTP("smtp.gmail.com", 587)

try:
    server.set_debuglevel(True)

    # identify ourselves, prompting server for supported features
    server.ehlo()

    # If we can encrypt this session, do it
    if server.has_extn('STARTTLS'):
        server.starttls()
        server.ehlo() # re-identify ourselves over TLS connection

    server.login("example@gmail.com", passwd)
    server.sendmail('example@gmail.com', ['example2@gmail.com'], msg.as_string())
finally:
    server.quit()

```

---

### Post by simeon87 on 2011-09-25
SMTP sends passwords in plain text so sending the hash won't match the plain text password that is expected on the server. Basically, you'd be comparing the hash to the plain text password. You'd have to use a more secure version of SMTP to support logging in with hashed passwords. I don't know what those protocols are called though, you'd have to search for that.

---

### Post by merlin371 on 2011-09-25
you could use [SMTPS]("http://en.wikipedia.org/wiki/SMTPS") which is pretty much SMTP with SSL on it

Also have a look at this thread

[http://ubuntuforums.org/showthread.php?t=664382](http://ubuntuforums.org/showthread.php?t=664382)

---

### Post by sam81 on 2011-09-25
Thanks for the suggestions! Encoding and decoding using base64 seems to work, but as far as I understand this only makes the password non human-readable. If you know more secure methods to do this stuff, please, let me know.

---

### Post by merlin371 on 2011-09-25
> **sam81 said:**
> Thanks for the suggestions! Encoding and decoding using base64 seems to work, but as far as I understand this only makes the password non human-readable. If you know more secure methods to do this stuff, please, let me know.

only way would be some encryption that needs a password to be decrypted. If you store something on the computer without the need to enter a password to unlock it, it will always be unsafe.

---

### Post by simeon87 on 2011-09-25
> **sam81 said:**
> Thanks for the suggestions! Encoding and decoding using base64 seems to work, but as far as I understand this only makes the password non human-readable. If you know more secure methods to do this stuff, please, let me know.

You need to use a hashing function, not base64.

---

### Post by cgroza on 2011-09-25
You must use some SHA algorithm, not the base64 function.

---

### Post by Bachstelze on 2011-09-25
If the password must be transmitted to the server in clear text and you don't want to ask it to the user every time, then you must store the password in clear text (or some obfuscated version of it like base64) in the code. There's no way around it. If you tore a SHA hash, then the program will not be able to transmit it in clear text to the server.

---

### Post by sam81 on 2011-09-26
> **Bachstelze said:**
> If the password must be transmitted to the server in clear text and you don't want to ask it to the user every time, then you must store the password in clear text (or some obfuscated version of it like base64) in the code. There's no way around it. If you tore a SHA hash, then the program will not be able to transmit it in clear text to the server.

Thanks. I have the impression you're right. Unfortunately I can't ask the user the password. The application serves to run experiments. There are two types of users, the experimenter (who manages the app and knows the password), and the experimental subject (who doesn't know the password). I want the app to send some data/info while the experiment is running. Therefore the experimenter is not there when this is happening. In other words, I do need to store the password somewhere.

Do you know how kwallet or the gnome-keyring store user passwords? I know there is a python library that lets you use kwallet or gnome-keyring, but it's not available on python3, so I can't use it now.

---

### Post by Rich43 on 2011-09-27
Can try porting above libraries with 2to3 or read their source.

---

