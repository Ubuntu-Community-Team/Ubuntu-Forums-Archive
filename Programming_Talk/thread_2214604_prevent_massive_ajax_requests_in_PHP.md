---
title: "prevent massive ajax requests in PHP"
date: 2014-04-02
forum: Programming Talk
---

### Post by chuchi on 2014-04-02
Hi everyone!!
 

 Maybe this is a stupid question.
 

 Let's suppose I have a login system for users, and that logged users can insert posts of texts using Ajax requests on the data base. A logged user can use Firebug to post a big amount of posts on the data base.  
 

 How can I prevent this? To prevent a user to use client side JavaScript to post a big amount of Ajax requests. I am using PHP as the server language.
 

 I could use a CSFR token, but once the user has the token in the client side, she/he could use the token to perform thousands of Ajax requests.
 

 Thank you very much!!

---

### Post by s.fox on 2014-04-02
Hello,

I am not 100% sure I understand your question, but I would look at doing the checks server side with php.  Perhaps you can check the number of database inserts associated with a particular token or session id.  You might need to adapt your table structure to do this.

Sorry if I have not been of much help.

---

### Post by chuchi on 2014-04-02
Hello s.fox!
 

 Thank you very much for your quick answer!  
 

 Yes, it is what I am looking for. I have read some solutions on the web, and I have just found this:
 

 [http://stackoverflow.com/questions/10466241/new-csrf-token-per-request-or-not](http://stackoverflow.com/questions/10466241/new-csrf-token-per-request-or-not)
 

 Maybe it is what I am looking for. They say about generate a new token per Ajax request, so one user can not perform several requests with the same token.
 

 Anyway I will take a deeper look at this.

---

### Post by s.fox on 2014-04-02
> **chuchi said:**
> Hello s.fox!
 

 Thank you very much for your quick answer!  
 

 Yes, it is what I am looking for. I have read some solutions on the web, and I have just found this:
 

 [http://stackoverflow.com/questions/10466241/new-csrf-token-per-request-or-not](http://stackoverflow.com/questions/10466241/new-csrf-token-per-request-or-not)
 

 Maybe it is what I am looking for. They say about generate a new token per Ajax request, so one user can not perform several requests with the same token.
 

 Anyway I will take a deeper look at this.

You're welcome, you might also want to add in some simple javascript to limit the number of times your submit button can be clicked with some logic checks.  This client side measure can of course be overcome by any determined individual and is not reliable.

---

### Post by chuchi on 2014-04-02
Definitely. The client measures are not what I am looking for. You know you can use firebug to write JavaScript code, and thus perform Ajax requests in a loop and inserting thousands of rows in the data base.

---

### Post by s.fox on 2014-04-02
> **chuchi said:**
> Definitely. The client measures are not what I am looking for. You know you can use firebug to write JavaScript code, and thus perform Ajax requests in a loop and inserting thousands of rows in the data base.

Whenever I do anything that takes user input and puts it into a database table I always use try to protect myself both client and server side.  You don't loose anything by having both.

I assume you are reading about mysql_real_escape_string extension, although if memory serves it might be depreciated in php 5.5.0

---

### Post by chuchi on 2014-04-02
Yes I always perform client side checks in JavaScript, but now I am in the scenario where a bad user wants to use Firebug to insert thousands of rows.  

 

 I am using PDO extension with prepared statements. I have read it is more secure than mysql_real_scape_string. Do you think so? I am not an expert in backend in PHP.

---

### Post by s.fox on 2014-04-02
> **chuchi said:**
>  I am using PDO extension with prepared statements. I have read it is more secure than mysql_real_scape_string. Do you think so? I am not an expert in backend in PHP.

I am not an expert on security either, but I have looked on [php.net and mysql_real_scape_string]("php.net/mysql_real_escape_string") is being depreciated and they are recommending the MySQLi or PDO_MySQL extension be used.

---

### Post by ofnuts on 2014-04-02
It's not a matter fo Firebug/Javascript. This can be scripted in any language the user fancies. And AJAX request is just a HTTP request.

You can't avoid doing the checks on the server. Possible counter-measures:
[LIST]
[*]add a delay in your answer: a half-second delay will be barely noticed by normal users, but will slow down code
[*]keep a "last request" time stamp for each user, and reject requests that come within some delay (20-60 seconds)
[*]lock out users after X posts per hour/day
[/LIST]

---

### Post by SeijiSensei on 2014-04-02
How about just adding a table to the database that logs the number of requests per token?  Then when the next request arrives, you check to see if the total exceeds some ceiling and inform the user that the limit has been reached.  You could also arbitrarily bump persistently annoying users off the system by refusing to authorize their credentials at login.

Are you concerned about the number of POSTs or their lengths as well?  For the latter, just check the length of the request and complain if it is too long.  You might want to add the cumulative number of bytes posted to that database table as well as count the number of requests.

---

### Post by chuchi on 2014-04-03
HI **[COLOR=#000000]SeijiSensei! I think your proposal is very good, I will give it a try![/COLOR]**

 

 **[COLOR=#000000]Thank you very much to all of you![/COLOR]**

---

