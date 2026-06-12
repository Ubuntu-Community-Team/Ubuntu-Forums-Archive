---
title: "How to add email subject in this Python script ?"
date: 2012-02-13
forum: Programming Talk
---

### Post by prismctg on 2012-02-13
```
 import smtplib
# Credentials
username = input("Enter your Gmail id : ")
password = input("Enter your Gmail password : ")
#from and to 
fromaddr = username + "@gmail.com"
toaddr = input ("Type your destination email address: ")
msg = input("Type your message: ")
# The actual mail send
server = smtplib.SMTP('smtp.gmail.com:587')  
server.starttls()  
server.login(username,password)  
server.sendmail(fromaddr,toaddr, msg)  
server.quit()
```

---

### Post by Tony Flury on 2012-02-13
Have you actually read the documentation on smtplib ?

[http://docs.python.org/library/smtplib.html](http://docs.python.org/library/smtplib.html)

I think the answer is to ensure that you construct your message so that it contains the subject - follow the links from above and you quickly get to : 

[http://docs.python.org/library/email-examples.html#email-examples](http://docs.python.org/library/email-examples.html#email-examples)

And look the first example does what you need.

---

### Post by ofnuts on 2012-02-13
Instead of setting "msg" from some raw text input, you make it an RFC2822-compliant mail body with subject and other useful headers using the [email package]("http://docs.python.org/library/email.html#module-email")

---

### Post by prismctg on 2012-02-13
Thank you ofnuts and tony :)

---

