---
title: "Sendmail / PHP5 - Rejecting Mail"
date: 2007-07-04
forum: Programming Talk
---

### Post by dreamstalk on 2007-07-04
OVERVIEW:

I'm attempting to build a PHP5 contact form that always submits to the same e-mail address (nightfyre@imagineeverything.com). I did a fresh install of Ubuntu 7.04 and added the sendmail application afterwards.

The script I'm using is one that has worked before on PHP4 so I'm assuming the problem has something to do with the sendmail application.

MAIL ERROR:

Any time I send mail out I receive the following error message in the error in the /var/mail/www-data


   ----- The following addresses had permanent fatal errors -----
<nightfyre@imagineeverything.com>
    (reason: 550-Verification failed for <www-data@webserve.mh.shawcable.net>)
 
   ----- Transcript of session follows -----
... while talking to imagineeverything.com.:
>>> DATA
<<< 550-Verification failed for <www-data@webserve.mh.shawcable.net>
<<< 550-unrouteable mail domain "webserve.mh.shawcable.net"
<<< 550 Sender verify failed
550 5.1.1 <nightfyre@imagineeverything.com>... User unknown
<<< 503 valid RCPT command must precede DATA

ATTEMPTED TROUBLESHOOTING:

I've added the following lines to my /etc/mail/local-host-names file:

localhost
webserve.mh.shawcable.net
imagineeverything.com
nightfyre.ca

I've also ensured that my php.ini file correctly configured for SMTP on the local server:

PHP5 SCRIPT:

//Posted Variables
$email    = "From: " . $_POST["email"];
$comments = $_POST["comments"];

//Preset Variables
$subject = "Form Submit";
$mail_to = "nightfyre@imagineeverything.com";

mail($mail_to, $subject, $comments, $email);


SUMMARY:

I've run through just about every troubleshooting angle I can think of. If anyone has any suggestions it would be greatly appreciated.

---

### Post by runningwithscissors on 2007-07-04
> <<< 550-Verification failed for <www-data@webserve.mh.shawcable.net>
This means that your outgoing mail server does not recognise the address [email]www-data@webserve.mh.shawcable.net[/email] and will not forward any mails coming from it.

One of your mail relay hosts does not recognise this address, I think.

Possible solutions: Use an address that has a mailbox on your ISP's mail server, i.e the address that you normally use to send mail, and relay mail through that. I haven't used sendmail so I don't know how to configure it to do this.

---

### Post by dreamstalk on 2007-07-04
That could be the problem, I'm not using any relay hosts.

I thought sendmail would just use the typical TCP/IP DNS servers to do the name look-up. I'm guessing this means I would have to run bind on the srever?

Just out of curiosity, what MTA do you use? Do you think it would be easier than trying to configure sendmail?

---

### Post by runningwithscissors on 2007-07-04
> **dreamstalk said:**
> That could be the problem, I'm not using any relay hosts.Ah okay, sorry. Thought you were. Which is silly because the error message quite clearly states that the verification failed from imagineeverything.com.

> **dreamstalk said:**
> I thought sendmail would just use the typical TCP/IP DNS servers to do the name look-up. I'm guessing this means I would have to run bind on the srever?Yes, I think you'll have to set DNS up for your domain with an MX record pointing to your mail server so that imagineeverything.com can do a positive lookup.

> **dreamstalk said:**
> Just out of curiosity, what MTA do you use? Do you think it would be easier than trying to configure sendmail?I don't use a mail server and have never set one up. :lol:
I just looked at your error message and tried to make sense of it.
Sorry if the service is less than stellar.

Also, I wouldn't say you should try another MTA, sendmail should do just fine.

---

### Post by tomchuk on 2007-07-04
In your php script add the following anywhere before the call to mail():

```

ini_set('sendmail_from', $_POST['email']);

```

---

