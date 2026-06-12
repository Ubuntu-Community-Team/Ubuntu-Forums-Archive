---
title: "smtp Mail for use in bash"
date: 2007-02-20
forum: Programming Talk
---

### Post by corosus on 2007-02-20
Hi 

I'm getting into bash scriptng a bit and i am looking for a command/program that will alow me to send  out mail from my pc thru the smtp server provided to me by my ISP?? 
Ideally something that would also allow me to forward a few pop-emails to my gmail account, but this is not a requisite.

I tried both mailx and sendmail but i can't seem to get them configured properly

thank you

---

### Post by dwblas on 2007-02-20
Try Exim4.  It's simple to set up and does everything that I want.  It's in the repos.  I don't really use bash anymore, Python has gradually replaced it, so can't help you with bash, but this simple Python script will show how smtp is done.```
def SendMail( msg ) :
   try :
       fromaddr = "<root@localhost>"
       toaddrs  = "<user_name@your_computer's_name>"

       # The actual mail send
       server = smtplib.SMTP('localhost')
       server.sendmail(fromaddr, toaddrs, msg)
       print server.verify( toaddrs )
       server.quit()

   except:
       print "sendmail error"
    
##=========================================================================
if __name__ == '__main__':
    SendMail( "SendMail test message" )
```

---

