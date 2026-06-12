---
title: "Creating facebook analog live messenger etc"
date: 2009-03-15
forum: Programming Talk
---

### Post by micdhack on 2009-03-15
Hello people,
i want to create a live service for a site like facebook's. basically instant updates, messenger. As far as i could debug facebook, it has an ajax script that run continually with a timeout of 60 seconds. When the scripts times out (probably from the server), ajax from client retries the request. This way the client side can hear for any new messages at any time. When i new message is to be delivered the side script instead of timing out it sends data to the client side, the client's scripts process it and starts a new sidescript request which starts a new cycle of waiting for something to be delivered.

As far as my programming knowledge goes this is not something extremely difficult but still im not sure if my way is the most effective. Personally i would create a sidescript:
```
<?php
$a=1;
while ($a<60) 
{
do_all_my_checks_for_messages();
sleep(1)
$a++;
}
?>
```
And then i would create a javascript which would do request using ajax.

This way we dont have a lot of request to the server from the client which would cause flooding but im not sure if there is an other way.
For example maybe there is a function in php that im missing and i could skip while with something like $someobject->wait_for_message();
Less loops, less processing power.
Also i dont know if this could be achieved with another language. Any ideas?

---

### Post by cabalas on 2009-03-15
You might want to take a look at this: [http://nzjrs.github.com/facebook-notify/](http://nzjrs.github.com/facebook-notify/) it is a facebook applet for gnome, while it doesn't do what you are wanting to it could be a good place to start from.

---

### Post by drubin on 2009-03-15
> **cabalas said:**
> You might want to take a look at this: [http://nzjrs.github.com/facebook-notify/](http://nzjrs.github.com/facebook-notify/) it is a facebook applet for gnome, while it doesn't do what you are wanting to it could be a good place to start from.

That lib doesn't help with regards to chat. That uses the FaceBook application framework that doesn't provide access to chat/IM

Take a look here [http://coderrr.wordpress.com/2008/05/06/facebook-chat-api/](http://coderrr.wordpress.com/2008/05/06/facebook-chat-api/)

---

### Post by micdhack on 2009-04-03
Thanks for the help people. That was exactly what i was looking for. :)

---

