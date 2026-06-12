---
title: "Returning PHP output to client but keeping thread open"
date: 2012-01-08
forum: Programming Talk
---

### Post by dazman19 on 2012-01-08
Hi,

I want to be able to keep my thread running in my server, somehow and send ajax posts to it. 

Generally when PHP executes, it only returns the stdout when it finishes the execution. I need a program that holds open an infinite loop and dependant on what the script sends back, The user can make choices to send posts to it to allow it to perform actions. The reason for this is it opens a socket and needs to read/write XML to the socket. I also need it to time out after about a minute. 

I was thinking about writing a CGI program, but I dont know the best way to deal with this issue. Languages I am competent with is C/C++ Java and PHP.

I prefer to use PHP and Java as they are the two languages I know the best, but I will brush the dust off my C++ text and use it if necessary although my libraries are somewhat limited.

What do you think?

---

### Post by Sworddragon on 2012-01-09
I have written such a similar script. The user can render a Minecraft worldmap and he will see the progress of the tool (c10t). I'm using an infinite loop which is checking if the connection has been closed and if not reading the current output from c10t, calculating what has already been sended and sending the rest. ob_flush() and flush() will help you to send the output after every loop.

To got the output from c10t I have called before the loop another script with proc_open. It calls with proc_open c10t and is storing the output in a file. At least it ensures a correct closing of all opened processes.

Don't forget to let the loops sleep a little after every execution to not waste a huge amount of cpu time. The advantage is that this solution is not dependent of JavaScript which may not be activated in the browser of the client.

---

