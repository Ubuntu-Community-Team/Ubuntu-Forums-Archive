---
title: "How do i get a webpage to send local telnet commands?"
date: 2010-08-30
forum: Programming Talk
---

### Post by geekyhawkes on 2010-08-30
Hello;

I am trying to make a webpage that when links are pressed sends telnet commands, is this possible?  The page itself will be hosted on the machine that I would like the telnet commands sending to, but it would be nice to have an option to connect to another machine if its not too difficult to achieve.

Thanks for any help, I seem to going no where fast with this at the moment!

Andy

---

### Post by worseisworser on 2010-08-30
I think your best bet is to split your web-application in two; a client-part and a server-part.

The server part generates the HTML for the client (web-browser), while at the same time using standard socket programming to send telnet commands to whatever server/ip you point it to.

---

### Post by geekyhawkes on 2010-08-30
Sounds like the solution im after, problem is this is outside my experiance.  Can you give me a steer how i would achieve this?   (I can knock up html but dont really know where to start on the server side of socket programming, should be an interesting lesson when I get started!)

---

### Post by geekyhawkes on 2010-08-30
And as i look at it, this might be the project i need to get me learning python 3?  Or can i get this done with just html?

---

### Post by worseisworser on 2010-08-30
> **geekyhawkes said:**
> And as i look at it, this might be the project i need to get me learning python 3?  Or can i get this done with just html?

Yeah, you can't really do much server-side with just HTML.

---

### Post by fct on 2010-08-31
You can knock up something like a web interface using a scripting language like PHP which takes care of things on the server side.

Read the manual on [www.php.net](www.php.net) , might get you some ideas while you learn.

---

### Post by geekyhawkes on 2010-08-31
Thanks, im part way through learning python so im going to try and get it up and running that way first.  If i have no luck with python then i will look at php i guess.

Thanks, this is my first project like this and i havent really coded anything useful for years!  Not going to be a quick project i think!

---

### Post by mendhak on 2010-08-31
There's a [telnet class](http://cvs.adfinis.ch/co.php/phpStreamcast/telnet.class.php?Horde=c999ccb49c17f45e8dd6e86fd037cf7d&r=1.2) that someone has written in PHP.

You could then use this sample script:

```

<?php 
//-------telnet.class.php usage example--------- 
                $telnet = new telnet; 
// Next line is for logging.   
//By default you need to create a folder called /log and give it the  
//rights your webserver is running. 
                $telnet->setLog(1,"mylog"); 
                $telnet->set_host("myhost.myplace.com"); 
//You need to set the prompt to what you know its going to be, 
//then call wait_prompt...which waits for what you just set 
                $telnet->set_prompt("Password: "); 
                $telnet->connect(); 
                $telnet->wait_prompt(); 
                $telnet->write("mypassword"); 
//Have to change the prompt...in my example this is the  
//prompt that a pix will change to after loggin in. 
                $telnet->set_prompt("pix> "); 
                $telnet->wait_prompt(); 
                $telnet->write("en"); 
                $telnet->set_prompt("Password: "); 
                $telnet->wait_prompt(); 
                $telnet->write("enable_password"); 
//When you go into enable mode in a pix the prompt changes 
                $telnet->set_prompt("pix# "); 
                $telnet->wait_prompt(); 
                $telnet->write("shun " . $shun_address); 
                $telnet->wait_prompt(); 
                $telnet->write("clear xlate"); 
                $telnet->wait_prompt(); 
                $telnet->write("write mem"); 
                $telnet->wait_prompt(); 
                $telnet->write("exit"); 
                $telnet->disconnect(); 
?>
```

Note that the telnet class itself makes use of fsockopen which is part of PHP.

Have a look at the [fsockopen](http://us.php.net/fsockopen) page.  It gives you sample code and there's user-contributed code too (where I found the above).  

If this looks overwhelming to you, start with the simplest PHP possible.  You'll quickly see that you can have your code in <?php ... ?> in the page that you load.  So something like the above would go into one of these boundaries.  So start with the usual [Hello World example](http://php.net/manual/en/tutorial.firstpage.php).

---

