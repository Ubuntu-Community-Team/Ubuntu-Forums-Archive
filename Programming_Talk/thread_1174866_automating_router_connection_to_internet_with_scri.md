---
title: "automating router connection to internet with scripts"
date: 2009-05-31
forum: Programming Talk
---

### Post by fornix on 2009-05-31
Hi,
I connect to the internet using a router - DLink Dir-300. I have 2 internet connection accounts. When I want to switch between the connections, I have to perform the following operations:
1. I have to go to my browser and go to the webpage of my router [http://192.168.0.1](http://192.168.0.1)
2. Log into the router.
3. Go to status and disconnect current connection.
4. Go to internet settings and change my username, password, servicename and then save changes. 
5. Again go to status and click on connect.

Phew! I want to automate this. Before using the router I used to do all this by using a bash script. And the router does not support telnet interface (Idiots)
Yes I know changing the firmware of the router to something like openwrt may be an option but I am keeping it as my last option.

I would want to write some script which will do all the steps mentioned above. For this the script should be intelligent enough to fill in web forms and click on buttons in a html page.

Which scripting / programming language could do this job fairly easily. If anyone of you could give in your inputs, it will be appreciated.

---

### Post by Habbit on 2009-05-31
If the HTML the router generates is well-formed enough you might be able to load it as XML into a DOM document in Python, then parse it and generate the appropiate requests/responses. This would also work with C# and .NET (look into System.XML and System.Net.HttpRequest/Response)

---

### Post by UbuKunubi on 2009-06-01
I automate my 3G internet connection. I have 2 phones I use as modems, one for my 'normal' surfing, and another which just connects to send security alerts.
To do this I use Xdotool, its easy to call from Python and should do what you want as well.

---

### Post by ssam on 2009-06-01
if you are lucky you may be able to do it with a single wget command, as it can send form answers. it will depend if the web interface is happy to receive the reply to a form without you having requested the form first.

otherwise there are tools designed for benchmarking webservers that can fill in forms.

---

