---
title: "enable threads in php"
date: 2013-08-28
forum: Programming Talk
---

### Post by chuchi on 2013-08-28
Hi everyone!!
 

 I am developing a concurrent websocket server in PHP. I prefer to implement it using pthreads rather than using fork to create new processes, because the server is supposed to handle thousands of connections. Threads are lighter than processes.

 

 But when I execute this code:
 

 ```

 <?php
 class My extends Thread {
     public function run() {
         /** ... **/
     }
 }
 $my = new My();
 var_dump($my->start());
 ?>
 
```
 

 I get this error:
 

 ```

 PHP Fatal error:  Class 'Thread' not found in /home/user/htdocs/example/server.php on line 3
 
```
 

 Why?? How can I get pthreads working in PHP??
 

 By the way, do you have another suggestions to implement the concurrent server??
 

 I am using Ubuntu 12.04 64bits
 

 Thank you very much!

---

### Post by spjackson on 2013-08-28
> **chuchi said:**
> I am developing a concurrent websocket server in PHP.

Why? Although I do use PHP, I would not regard it as appropriate for this purpose. I would choose any of C, C++, Java, Python in preference to PHP for this.

If you wish to persist, then it matters which version of PHP you are using and how you installed it. As I understand it, the default Ubuntu package is not built with the relevant options to support pthreads. See [here]("http://stackoverflow.com/questions/14081444/how-to-use-pthreads-php-extension-in-ubuntu") and the [manual]("http://www.php.net/manual/en/pthreads.requirements.php") for more information.

I haven't used pthreads with PHP and have no desire to, but hopefully the above will give you some clues.

---

### Post by chuchi on 2013-08-28
Hi [**[COLOR=#000000]spjackson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1128302")!! Thank you very much for your response. I am not sure if I am able to use C, C++, Java or python on my webserver, I will check it and your links.
Thanks a lot!

---

### Post by chuchi on 2013-08-28
Hello spjackson. You know?? I am much more comfortable with multithreading in C or Java, like you said.
 

 But I am in trouble trying to find some web hosting with php-mysql, and with the possibility to open a server socket (C or Java). Do you know any web hosting with this features?
 

 Thank you very much

---

### Post by Crusty Old Fart on 2013-08-28
> **chuchi said:**
> ...trying to find some web hosting with php-mysql, and with the possibility to open a server socket (C or Java). Do you know any web hosting with this features?...
If you haven't done so already, you might want to take a look at bluehost.com or hostmonster.com, both of them are owned by the same outfit. If you don't find what you're looking for on their website, don't hesitate to give them a call. They put real live human beings on the other end of the line and the wait times are remarkably short.

Good luck,

Crusty

---

### Post by SeijiSensei on 2013-08-28
You might be able to invoke a socket listener written in C using Apache's [cgi-bin interface]("http://httpd.apache.org/docs/2.2/howto/cgi.html").  I don't know how many web hosting providers support cgi-bin scripts these days for security reasons.  

It sounds to me like you would be better off renting a virtual machine from someone like [Linode]("http://www.linode.com/"), where you could run your own C- or Java-based daemon to create the socket, and run Apache and an SQL server as well.

---

### Post by chuchi on 2013-08-28
First of all, thank you very much to all of you. I will give a try at your suggestions.
 

 I think I will implement the server using Java, just in case we would need to change to a another OS webserver. If I develop the socket server in C, we would have to reprogram the whole socket server if we had to change the OS of the server.
 

 Do you think it would be a good idea to develop in JAVA?
 

 Thanks a lot!

---

