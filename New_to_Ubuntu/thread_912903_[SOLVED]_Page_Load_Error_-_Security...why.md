---
title: "[SOLVED] Page Load Error - Security...why?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by dmurat on 2008-09-07
i try to login to my college's website but i face such an error ```
Secure Connection Failed

      

      
      
      

      
        
        

          

suis.sabanciuniv.edu uses an invalid security certificate.

The certificate is not trusted because the issuer certificate is not trusted.

(Error code: sec_error_untrusted_issuer)

        


        
        



    * This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.


    * If you have connected to this server successfully in the past, the error may be temporary, and you can try again later.  
        

          Or you can add an exception…
```

i used to access this website from windows and its essential for me. what can i do? any idea?

---

### Post by aos101 on 2008-09-07
This is a new feature in Firefox 3 to do with security and SSL (it does the same in Firefox on Windows).  Because the SSL certificate the site sends you is self signed, Firefox comes up with this warning.  

If you want to use the website anyway, click the "Or you can add an exception…" link on the error page then click "Add Exception" -> "Get Certificate" and finally "Confirm Security Exception".  You should then be able to use the website fine.

---

### Post by dmurat on 2008-09-07
i already did it but the problem persists. it still gives "Page Load Error, Secure Connection Failed" even though i add an exception for that site...there were no such problems when using windows (i was a firefox user when using windows too..)
any alternative ways :\ ??

---

### Post by Bölvaður on 2008-09-07
get Opera or Chrome.

But try see if the exception is logged and doesn't disappear after you close firefox

---

### Post by dmurat on 2008-09-07
second thing u said worked just fine. thanks. solved =)

---

