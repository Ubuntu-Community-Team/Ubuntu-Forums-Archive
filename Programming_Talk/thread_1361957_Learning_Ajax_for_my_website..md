---
title: "Learning Ajax for my website."
date: 2009-12-22
forum: Programming Talk
---

### Post by hockey97 on 2009-12-22
I already read tutorials about it. 

well I am learning it just for one reason. I want to create a function for a button that  once clicked it will fade in a  message box with another button to submit the data.

My question here is that using ajax is it possible that once the  message box gets faded in with another button  that I can talk directly to mysql that once the user clicks the button like a submit button that the message would get stored in the database? 

I don't want a form where when you click submit you redirect the user to another page.

I plan to use jquery if that helps any. 

So the question is would I be able to directly talk to mysql using ajax?

---

### Post by Hellkeepa on 2009-12-22
HELLo!

Not by using AJAX, which is only responsible for communicating with the web server. However, by using a JavaScript framework, like jQuery (or similar), which implements visual effects in addition to AJAX functionality, you can.
You will need a server side script to recieve, validate and store the data, though. JS can't talk directly to the MySQL-server. Or, at least that's something you do not want it to do, if at all possible.

Happy codin'!

---

### Post by shadylookin on 2009-12-22
I don't know about the fade in part, but that can be done with javascript(you shouldn't need to talk to the server to that)

---

### Post by hockey97 on 2009-12-22
ya I know jquery... or javascript can make the visual effects. 


I am just more concern about storing the data.

I don't want to have to refresh the page or send the person to another page.

I want a message box to fade in once the person presses a button. 

Then they type their message and then click send. The send button should send that message to mysql database and store it for the other person to see that message.

I just need to know how I can use javascript/jquery in a way to throw data to the mysql server and have it store it. 

I was thinking to write php code and use ajax with jquery so that when the person clicks the send button it will run the php code and will transfer the data using the post method to the php script and use php to directly talk to mysql.

Would that be possible?

---

### Post by loell on 2009-12-22
that's exactly what you have to do. ;)

call a url in jquery, and probably have it returned with html(with the additional effects for the box).

---

### Post by korvirlol on 2009-12-22
look up jquery:

```
$.ajax
```

this does what you want.

---

