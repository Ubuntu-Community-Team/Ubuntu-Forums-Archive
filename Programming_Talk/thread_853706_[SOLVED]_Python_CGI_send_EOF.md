---
title: "[SOLVED] Python CGI send EOF"
date: 2008-07-08
forum: Programming Talk
---

### Post by themusicwave on 2008-07-08
Hey everyone,

I need to send an e-mail with Python CGI.  I know that I need to send and End Of File at the end of the e-mail.  I know on Linux this is Crtl-D.  What I am wondering is what string do I append to my file to add the EOF?

Thanks,

Jon

---

### Post by ghostdog74 on 2008-07-08
how are you sending the email? are you using smtplib? show some code

---

### Post by pmasiar on 2008-07-08
CGI does send email. CGI will accept form parameters, and use one of many email-related modules to send email, right? Which module you use?

---

### Post by themusicwave on 2008-07-09
Sorry about being so vague in the previous post, I was pretty tired when I wrote it.

Anyways,

I am trying to send it using smtplib.  What I have done is tried to take an example I got off the web that used user input and turn it into a callable e-mail library for myself.

Here is the little example script I pulled off the web:
[PHP]
#!/usr/bin/python

import smtplib

def prompt(prompt):
    return raw_input(prompt).strip()

fromaddr = prompt("From: ")
toaddrs  = prompt("To: ").split()
print "Enter message, end with ^D (Unix) or ^Z (Windows):"

# Add the From: and To: headers at the start!
msg = ("From: %s\r\nTo: %s\r\n\r\n"
       % (fromaddr, ", ".join(toaddrs)))
while 1:
    try:
        line = raw_input()
    except EOFError:
        break
    if not line:
        break
    msg = msg + line

print "Message length is " + repr(len(msg))

server = smtplib.SMTP('localhost')
server.set_debuglevel(1)
server.sendmail(fromaddr, toaddrs, msg)
server.quit()
[/PHP]

That one works perfectly, but obviously relies on user input to function.  What I basically want to so is simply create a function that I can easily call to send e-mails(perhaps one exists) like so:

sendemail(to,from,subject,message)

This is my attempt at it, which doesn't work:
[PHP]
#!/usr/bin/python

import smtplib
import cgi
import cgitb; cgitb.enable()
 
def sendemail(to,fromAddr,subj,msg):
	
	#Add From
	outMsg = "From:".join(fromAddr).join("\r\n")
	
	#Add To
	outMsg.join("To:")
	
	addrStr =""
	for addr in to:
		if len(addrStr) > 0:
			addrStr.join(",")
		
		addrStr.join(addr + "\r\n")
	
	#Add Subject
	outMsg.join("Subject:" + subj + "\r\n")
	
	#Add Message
	
	outMsg.join("\r\n" + msg + "\r\n")

	#print "Sending:" + outMsg
	server = smtplib.SMTP('localhost')
	server.set_debuglevel(1)
	server.sendmail(fromAddr, to, outMsg)
	server.quit()
	
if __name__ == "__main__":
	toSend = []
	toSend.append("mygmail@gmail.com")
	sendemail("myemail@mydomain.com",toSend,"Mail test", "This was sent by my new function!")
[/PHP]

It gives me an error code saying administrative permission denied, I think the code is 555 or 550.  I can;t SSH into the server to get the exact message now.

So where did I go wrong?

---

### Post by themusicwave on 2008-07-09
I also should mention that the my Hosting [Blue Host]("http://www.bluehost.com") only supports Python 2.3, with no upgrade plans.  So everything I use has to be Python 2.3.  This annoys me of course, because they advertise support for Python, they just leave out the version.

They will install any additional Python 2.3 modules for me though.

---

### Post by themusicwave on 2008-07-09
I got it to work, here is the code incase anyone ever needs it:

[PHP]
#!/usr/bin/python

import smtplib
import cgi
import cgitb; cgitb.enable()
 
def sendemail(to,fromAddr,subj,msg):


    #Add From
    outMsg = "From:" + fromAddr + "\r\n"
    
    #Add To
    outMsg += "To:"
    
    addrStr =""
    print type(to)
    
    for addr in to:
        if len(addrStr) > 0:
            addrStr += ","
        
        addrStr += addr
    addrStr += "\r\n"

    outMsg += addrStr
    #Add Subject
    outMsg += "Subject:" + subj + "\r\n"
    
    #Add Message
    
    outMsg+="\r\n" + msg + "\r\n"
    print outMsg
    #print "Sending:" + outMsg
    server = smtplib.SMTP('129.179.0.16')
    server.set_debuglevel(1)
    server.sendmail(fromAddr, to, outMsg)
    server.quit()
    
if __name__ == "__main__":
    toSend = []
    toSend.append("addy@domain.com")

    sendemail(toSend,"addy@domain.com","Mail test", "This was sent by my new function!")

[/PHP]

---

### Post by thornmastr on 2008-07-09
If you are happy with the solution to your problem, please mark your thread as solved.

Robert

---

