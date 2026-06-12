---
title: "Web Server Security"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by Romeo3t on 2011-09-19
Hello all!

I'm going to school for system administration and figured I would study a bit more by setting up some lamp stack applications and such. I recently set up a web server using my home connection and after a few hours of figuring out what was what got it up and running using apache. 

I was told that running a webserver(without knowing what you are *completely* doing) can be very dangerous security wise but after trying to do a bit of research I can't find exactly why. 

I was hoping someone would be nice enough to explain(or point me to somewhere that does) some of the security risks of running a web server from your home connection and dangers it can pose to your network. 

**tl;dr:** What are some security risks of running a webserver from home with a simple apache setup.

---

### Post by Dangertux on 2011-09-19
I'm not really sure that running a web server in particular is any more of a security risk than running any other service in your home. In fact if you're using Apache I'm actually inclined to say there are certainly worse things you could be running.

That being said, some of the reasons why running a home server could be a security risk are as follows.

1 -- Home servers are usually port forwarded, or not properly placed in a DMZ (data management zone, not that thing that SOHO routers pass off as a DMZ). This causes a couple of problems, if the server DOES become compromised it has access to the systems in your internal network and can be used as a pivot point to compromise those systems. Particularly due to the fact that you're likely managing said server from your home machine the level of trust between the server and your machine is higher, making it more of an easy target. 

2 -- Web server's that are run at home are often poorly secured (ie: no WAF, no application confinement [apparmor/selinux], no IDS host based or otherwise), and have weak credentials.

3 -- Home web server's often contain poorly coded web content with vulnerable web applications running on them. (more on this in a moment)

4 -- Home server's are often great attack platforms for attacking other targets (due to the fact that most of them are running either poorly configured SSH, any type of FTP, or both)

5 -- Home servers usually end up as a repository for projects, and are rarely treated as production machines. Thus they end up running a lot of poorly confined easily exploited services. A home web server can quickly turn into a file server, print server, web server, dns server, email server and home media server, solely because its owner can only afford that machine ; and they are a technology enthusiast.

Now back to Web applications, in my personal opinion in terms of the LAMP stack, MOST of the software in that set is fairly mature, and reasonably secure. The Apache foundation is VERY on top of security updates , minus whatever that was where they ignored CVE-2011-3192 for 4 1/2 weeks (granted it was just a denial of service).

That being said the security of the actual service itself can not account for the content you place on your site. Many people host personal blogs, business sites, and whatever else using content management systems such as Drupal, Joomla, or Wordpress. These CMS'es tend to be a breeding ground for XSS, CSRF and SQL injection vulnerabilities. Most individuals who host a home web server either do not have the knowledge or resources to properly audit and validate the code in those applications. Particularly when it comes to blogs and wordpress. Most people will just pick the addons they think are cool and call it a day. Most of those addons are HORRIBLY coded and wrought with vulnerabilities. A vulnerable web application in conjunction with a poorly configured database server can lead to a complete system compromise very quickly. The average home server owner doesn't take these into account. So on average home web servers are considered less secure.

From a physical security standpoint a home web server obviously has certain drawbacks as well. For instance, the fact that it's not in a "secure" datacenter. It's not set up on failover power supplies, and it's probably not properly backed up. It's also likely sitting in someone's garage so any child with access to a 2x4 can steal it. 

So imo a home web server is not innately less secure minus the physical security aspects (unless you live in a bunker). However, they just tend to be less secure due to lack of information and understanding about the technology being implemented.

---

### Post by Romeo3t on 2011-09-19
Thank you very much. That was well written and informative. 

From what you have said it doesn't seem like running a webserver just for my testing purposes is very dangerous at all.

From what I have learned it seems that if I just be careful not to be completely stupid with configurations, I should not be compromised. 

I think I should be all set on all your points except the selinux and application confinement. I will need to do some more research on that front. 

Just to ask a quick question though. I thought apache did a form of application confinement for you. By not running with root credentials. So that it is only allowed to access certain files.(I might be misunderstanding the definition of application confinement)

Thanks again!

---

### Post by Dangertux on 2011-09-20
> **Romeo3t said:**
> Thank you very much. That was well written and informative. 

From what you have said it doesn't seem like running a webserver just for my testing purposes is very dangerous at all.

From what I have learned it seems that if I just be careful not to be completely stupid with configurations, I should not be compromised. 

I think I should be all set on all your points except the selinux and application confinement. I will need to do some more research on that front. 

Just to ask a quick question though. I thought apache did a form of application confinement for you. By not running with root credentials. So that it is only allowed to access certain files.(I might be misunderstanding the definition of application confinement)

Thanks again!

I'm glad you liked it. I wouldn't say it's overly safe or overly dangerous. It really just depends on the risk level you can assume. So unless you're processing financial transactions or top secret government data on your home network I would say you're probably fine ;-)

If you're using Ubuntu as your server of choice I would suggest using Apparmor over SELinux, you could use either however Ubuntu ships with Apparmor, and generally the profiles are a little bit easier to create (in my opinion). 

As far as application confinement goes there are a couple of things to keep in mind.

1 -- Always least privileges needed. No matter what your application, whether it's a web server or a video game, it always should have only the least amount of privileges it needs to accomplish it's job. Your assumption about Apache is correct, the Apache parent process is started as root, however, the child processes that actually serve out the hits run as another user. (specifiable at compile time or in the configuration).

2 -- There are other types of confinement like Application level firewalls, these are things like Apparmor and SELinux. They work to prevent the dreaded "0 day exploit" from being effective by limiting what the application they are confining can do. They enforce strict limits on what abilities the application has (networking, what hardware they can access, etc) as well as where the application can read, write, view and modify files. These work as a second level of protection. For instance, say you were to exploit an Apache server with the Mod_isapi dangling pointer buffer overflow. You would only be able to execute code as the unprivileged user, however this is enough to pass kernel level shellcode to escalate privileges all the way to root. This is where Apparmor and SELinux come in, you would have limited the ability to do this prior to the exploit. Thus even the unprivileged user could not escalate. It's more of a "backup plan" then a solution. Think of them as very advanced chroot prisons. (that's very simplified and not the best example)

Another important note in terms of service security is that MOST packages shipped by default with the major distributions are compiled with Stack Protection. This prevents arbitrary code from being injected into memory in the case of a successful exploit. So they effectively reduce what could be catastrophic to a denial of service. (It's important to use this option when compiling your own software).

Of course you also have ASLR which attempts to randomize executable memory to prevent successful exploitation as well. You have a lot of factors on your side when dealing with web server security. 

Which is why the focus is moving to web based applications. Web based applications are far less protected and usually far more vulnerable then the actual service itself. This is where things like Intrusion detection and web application firewalls come in. 

Things like Snort can analyze incoming traffic and match it against a variety of signatures to determine if it is malicious in nature. Web application firewalls do the similar but on a less broad scale. They focus on attacks targeting solely web content. These are things like SQL injection, remote or local file inclusion, code disclosure, XSS, CSRF, etc. You can install a web application firewall for apache in the form of mod_security. It is a very complicated module itself and is highly customizable although you can get a basic rule set from OWASP.

For more info on mod_security check out this link [http://www.modsecurity.org/](http://www.modsecurity.org/)

Also bodhi.zazen one of the admins here wrote a decent tutorial about mod security although it's a little dated now you can read it here [http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

Hope this helps, and good luck with your endeavors.

---

### Post by Romeo3t on 2011-09-20
I'm blown away. All this is extremely interested. I'm excited to learn more. Thank you so much. You have been a huge help.

---

### Post by Dangertux on 2011-09-20
Glad I could be helpful. There are many helpful people on this forum. So as you progress and learn there should always be someone to help you with the next task at hand :-)

---

