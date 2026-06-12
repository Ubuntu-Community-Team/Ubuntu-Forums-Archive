---
title: "broken ssh connection, causes"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by jackyu on 2012-01-15
I am required to log into a computer cluster at university to do my project work.  I have always used ssh for this without much problem.  

However, recently, I have started noticing something that is hampering my work: the ssh connection often breaks with the message "write failed: broken pipe".  What is peculiar is that this often happens when a lot of stuff is being printed to the standard output, whether it be from the python code I am running, or from the command "qstat" that displays the status of jobs running on the nodes, etc.   

I often hear that the "write failed: broken pipe" message occurs when the ssh session has been idle for too long, so I do not quite understand why this happens when, to me, the terminal appears to be 'busy'.  

What things can make an ssh connection break with the "write failed: broken pipe" message?

Can it happen when the internet is slow?  How do I know if it is the client's or the server's problem (my system administrator tells me it is not the server's in this case)?  Can it be because my internet service provider, which have I have recently switched to, is doing something odd?  Can it be because I have recently moved to a different country?  Or, a new OS on a new computer? :confused: 

Please help!  I really would like to have this resolved so that I can start doing some work...

I am using Oneiric on an ASUS Eeepc 1015PX.

---

### Post by carl4926 on 2012-01-15
> Can it be because my internet service provider, which have I have  recently switched to, is doing something odd?  Can it be because I have  recently moved to a different country?  

Both these, whilst they shouldn't be a problem, nevertheless seem the most likely.

Are you using ssh in a UI or terminal?

---

### Post by Old_Grey_Wolf on 2012-01-15
Whatever the cause, look into the "GNU screen" application. Google on "GNU screen". If you loose your session you can use screen to reconnect to the session. Your program continues to run when the connection is broken. You don't loose your work that way.

It is probably installed already on the university's cluster. Type "which screen" in a terminal to find out.

To install it on Ubuntu, [https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen). Also look at the "Other links" at the bottom of that page for a tutorial of using screen. For Red Hat and other yum based systems, Google on "yum install screen".

Here is another helpful link [http://www.howtoforge.com/linux_screen](http://www.howtoforge.com/linux_screen). At the bottom, "3 My Connection Dropped - What Can I Do?", explains how to ssh to the server and reconnect to the screen session that is still running. It also has instructions for installing on other deb based systems.

---

### Post by jackyu on 2012-01-15
> **carl4926 said:**
> Both these, whilst they shouldn't be a problem, nevertheless seem the most likely.

Are you using ssh in a UI or terminal?
I use it in a terminal.

---

### Post by Old_Grey_Wolf on 2012-01-16
> **jackyu said:**
> I use it in a terminal.

I have used ssh to administer computers half-way around the globe. ssh gets disconnected for various reasons. I have learned how to continue working by using GNU screen. I suggest looking into using it. Your ssh connection may drop; however, you can reconnect to the screen session and continue working.

---

### Post by CharlesA on 2012-01-16
I've seen that "broken pipe" error around the forums before, but I'm not sure what causes it.

Huge +1 to screen from me.. I use it when doing tasks on my server.

---

### Post by sandyd on 2012-01-16
> **jackyu said:**
> I am required to log into a computer cluster at university to do my project work.  I have always used ssh for this without much problem.  

However, recently, I have started noticing something that is hampering my work: the ssh connection often breaks with the message "write failed: broken pipe".  What is peculiar is that this often happens when a lot of stuff is being printed to the standard output, whether it be from the python code I am running, or from the command "qstat" that displays the status of jobs running on the nodes, etc.   

I often hear that the "write failed: broken pipe" message occurs when the ssh session has been idle for too long, so I do not quite understand why this happens when, to me, the terminal appears to be 'busy'.  

What things can make an ssh connection break with the "write failed: broken pipe" message?

Can it happen when the internet is slow?  How do I know if it is the client's or the server's problem (my system administrator tells me it is not the server's in this case)?  Can it be because my internet service provider, which have I have recently switched to, is doing something odd?  Can it be because I have recently moved to a different country?  Or, a new OS on a new computer? :confused: 

Please help!  I really would like to have this resolved so that I can start doing some work...

I am using Oneiric on an ASUS Eeepc 1015PX.
Does your university offer NX? (my former one, UoT, and UoW did, but I practically lived in the cslab, so there was no point...)
If it does, use a NX Client to connect.

---

### Post by Old_Grey_Wolf on 2012-01-16
> **CharlesA said:**
> 
Huge +1 to screen from me.. I use it when doing tasks on my server.

GNU screen is installed by default on several distros; however, many people don't know about it.

---

### Post by jackyu on 2012-01-19
> **Old_Gray_Wolf said:**
> GNU screen is installed by default on several distros; however, many people don't know about it.

Thanks for suggesting Screen.  I did not know about it, and it certainly sounds really useful.  However, I have been using it for the past few days, but it seems that it does not make whatever processes I have running at the terminal survive a 'broken pipe'.  

For example, suppose I run a script at the terminal which submits many many jobs( so it is not a quick process).  If I detach the screen, log out of the university cluster, then log in, and then reattach the screen, the script is still running and submitting jobs.  But if the connection is lost because of a 'broken pipe', when I log back into the cluster and reattach the screen, I see that the script is no longer running, and that not all the jobs I want to submit are submitted (I guess the last job submitted was just before the connection broke). It feels like it only works when I voluntarily break the connection...

I wonder if it is because I need to log into a gateway first before I log into the cluster I acutally work on.  (I need to use ssh twice.)

---

### Post by Lars Noodén on 2012-01-19
I'm not sure how to recreate the error you're seeing so I can test this, but would it help to run screen via [nohup](http://manpages.ubuntu.com/manpages/oneiric/en/man1/nohup.1posix.html)?  In other cases it would allow the process to continue even after a hangup signal is sent so it should work for screen, too.

---

### Post by Old_Grey_Wolf on 2012-01-19
> **jackyu said:**
> 
I wonder if it is because I need to log into a gateway first before I log into the cluster I acutally work on.  (I need to use ssh twice.)

Try ssh to a hop host and run screen. From there ssh to the host doing the work. That way the host doing the work doesn't know screen is involved.

When I use screen it is because I am going through an aggressive NAT firewall that times out the connection when idle for a short time. Under those situations I am making several hops anyway. I didn't think about that.

---

### Post by Lars Noodén on 2012-01-20
> **Old_Gray_Wolf said:**
> When I use screen it is because I am going through an aggressive NAT firewall that times out the connection when idle for a short time.

Try setting [ClientAliveInterval](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) on your server.  That should send packets periodically to see if the client is still connected.  The side effect is that the connection should not get dropped by your aggressive firewall.

---

### Post by Old_Grey_Wolf on 2012-01-20
> **Lars Noodén said:**
> Try setting [ClientAliveInterval](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) on your server.  That should send packets periodically to see if the client is still connected.  The side effect is that the connection should not get dropped by your aggressive firewall.

I know I can do that; however, the servers are set up like that for a reason which I will not discuss. If I changed the ClientAliveInterval in sshd_config, I would have a lot of explaining to do.

---

### Post by Lars Noodén on 2012-01-20
Then you could do it the other way around and go client by client using the [ServerAliveInterval](http://manpages.ubuntu.com/manpages/oneiric/en/man5/ssh_config.5.html) directive in [font=Courier New]ssh_config[/font].  That will do about the same thing but not require any changes to the server.

---

### Post by Old_Grey_Wolf on 2012-01-20
> **Lars Noodén said:**
> Then you could do it the other way around and go client by client using the [ServerAliveInterval](http://manpages.ubuntu.com/manpages/oneiric/en/man5/ssh_config.5.html) directive in [font=Courier New]ssh_config[/font].  That will do about the same thing but not require any changes to the server.

Just because I can do something doesn't mean I should. There are places where a person may work that require people with admin or root abilities to sign agreements to abide by certain rules. Breaking those rules can cause a lot of grief. ;)

I am not the person asking for help anyway. jackyu is the one asking for help.

---

