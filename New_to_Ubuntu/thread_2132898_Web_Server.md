---
title: "Web Server"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by burge38 on 2013-04-06
Hi I run raveskool.com
Recently in the last week my hosting provider deleted my ecommerce folder for containing files construe to be archiving and in the TOA it says archiving of files is not permitted on our servers .
Point being I thought I would build a Linux web server  .
After researching I decided on Ubuntu 12. And apache2. Used an old 1.2 desktop and set it up for a trial run after 30 hours I had it running stable and serving my site.
With this I brought a server configured a 1tb raid0 and repeated the process (A LOT MORE DIFFICULT THIS TIME I MIGHT ADD) Again I hit the forums sorted all the problems out have it running at moment stable 32 hours.
What I cannot understand is the speed of files being downloaded now I have not tested download speed on this yet I thought I would ask if there&#8217;s some script I need to use to speed up the process or is it down to my fiber optic connect and what is the maximum download speed a home server can hope to achieve, that is outside world downloading from my server.
[http://192.168.1.35/ravesite/shop/](http://192.168.1.35/ravesite/shop/)
kind regards
[removed email] Sending emails from my shop admin to customers not working what email client should the server be running

---

### Post by Kirboosy on 2013-04-06
Welcome to the Forums! Hopefully I can answer your question and its easy to understand.
[B]
Speed Questions[/B]
The maximum upload speed of your home server is dependent on the service agreement you have with your ISP. At my house I get 55Mbps down and 6 Mbps up. If I switched contracts of service I could go to a much faster package. Say 55 Mbps down and 25 Mbps up, however the price jump is crazy. The most important number to you when you are running a webserver is the upload speed. Download speed isn't needed as much. The only time you will use download speed on the webserver is when someone is uploading files to it. You might need a business level contract in order to get faster upload speeds. 

All depends on your area and ISPs. You could run a speedtest from speedtest.net or a similar service to see what currently your speeds look like. 


**Mail Portion**
Are you sure you can send emails at all from the webserver? I would recommend using [thunderbird]("https://www.mozilla.org/en-US/thunderbird/") or evolution for a client. Also webmail would be a viable option for easy access when you aren't on your regular systems.


Hope that helps.

~Caboose

---

### Post by burge38 on 2013-04-06
I installed send mail but still not managed to sort it

---

### Post by burge38 on 2013-04-06
so a 100 mb file would only take 9.22 seconds it use to take 6 minutes on my host service provider still I can live with that obviously the more connections the slower it be

---

### Post by burge38 on 2013-04-06
I fixed it I just had not filled out files right all done now cheers

---

### Post by burge38 on 2013-04-06
Every part site working ok but I failed on making my ip address that the world sees static thought I had but when router reset I lost connectivity with web

---

### Post by burge38 on 2013-04-07
Night mare this is ,<br> 1. right my ISP lets port 80 be forwarded <br>2. ISP DNS servers not listed hidden from public view no reference on web to them<br>3. I managed to sneakily Acquire DNS servers, IPV4, and the ip range subnet <br>4. cant find tutorial clear enough to follow in creating a static ip address for the world to see so I can add my domain name to it<br> some divine intervention needed all help on this matter much appreciated in advance .<br>kind regards <br> last question how come I can not press enter for new line and html tags don't work. No offence intended but this is by far the worst forum input system I have ever seen kind regards

---

### Post by lisati on 2013-04-07
> **burge38 said:**
> Last question how come I can not press enter for new line and html tags don't work. No offence intended but this is by far the worst forum input system I have ever seen kind regards
This forum doesn't accept HTML in its posts. For formatting, like many other forums, it uses BBCODE, see [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode).

To get blank lines between paragraphs, push "Enter" twice.

---

### Post by burge38 on 2013-04-07
just pressed enter 20 times no effect yes key works just fine ,no still no <br>

---

### Post by burge38 on 2013-04-07
sorry mate not learning another code hard enough getting to grips with Linux without having to use some obscure code to format in a Linux forum input page haven't got time any answers to important questions as I did state not having ago just a bit strange compared to the other 6 forums I am a member off if being different and harder to use than average forum gets you visits then fair paly. kind regards

---

### Post by burge38 on 2013-04-07
do you think that I am using wrong machine have a windows(URRRR) 7 installation as a desktop file server that connects to my router I use a shell to access server but always use the windows browser to configure 192.168.1.1 yxzel router could this be my route cause forgive the pun couldn't help it ps pressed my 3 enter buttons on key board 20 times each still no enter,return or (br)

---

### Post by burge38 on 2013-04-07
how to achieve this please yes Google was my friend I did find lovely tutorials just they were all for Linux Ubuntu 10 below, so I am using this as an excuse as to why I can not give my Linux webserver a static ip well can do that bit but cant get my routers external ip address the one the world sees to stay static. even though my port 80 is not blocked know this as I can reach server from outside network with what ever ip the dhcp has assigned. obviously every time it changes my site is lost to the world. now my isp dns servers are hidden not know were to be found on internet. so I sneaky obtained them as in the united states its against the law for the dns servers to be hidden so with a lot of messing around I finally got hold of all their information's dns server upv4,ASN num, ASN name ISP, IP range subnet but still even armed with this information I still failed to assign a static ip address to my router. ENTER NO MATER HOW MANY TIMES I PRESS IT DOSE NOT WORK IN THIS FORUM,<BR>

---

### Post by lisati on 2013-04-07
1) A static public IP address is something you have to organize with your ISP
2) Try using the "advanced" editor: the forum is switched so that HTML codes are disabled in posts.

---

### Post by lisati on 2013-04-07
Threads merged. Starting multiple threads for the same problem just confuses us, and dilutes the community's ability to help.

[s]Please don't use HTML tags in your posts, they have been disabled in this forum. Try using the "advanced" editor and BBCODE for your posts.[/s] (See next post)

---

### Post by coffeecat on 2013-04-07
> **burge38 said:**
> sorry mate not learning another code hard enough getting to grips with Linux without having to use some obscure code to format in a Linux forum input page haven't got time any answers to important questions as I did state not having ago just a bit strange compared to the other 6 forums I am a member off if being different and harder to use than average forum gets you visits then fair paly. kind regards

BBCode is standard to all forum software that I have come across. Please stop trying to use html - it won't work - for obvious reasons.

If you are not able to enter line breaks, the most likely explanations are that you have a browser issue, or you are blocking javascript on this forum

---

### Post by burge38 on 2013-04-07
I do not wish to contact my internet service providers over this as they no far far less about networking than me, proved in various networking trouble I had with them in the beginning they had to be told how to ping a <snip> ip address the call center they speak pigeon English like an exchange student learning English terrible

---

### Post by burge38 on 2013-04-07
yes windows desktop server not nice hate the <snip> thing but my Microsoft works database with 10 years worth of work is windows only you give me a program that can handle it in Linux and I will bin windows 7 yesterday replace it with mandrake if you know a work around

---

### Post by lisati on 2013-04-07
> **burge38 said:**
> I do not wish to contact my internet service providers over this as they no far far less about networking than me, proved in various networking trouble I had with them in the beginning they had to be told how to ping a <snip> ip address the call center they speak pigeon English like an exchange student learning English terrible

On your own network, organizing a static IP address for any (or all) of your machines is *your* business. There are different ways of achieving this, some of which involve changing settings in your router, and other involve changing settings on the devices connected to your router.

When it comes to organizing a static public IP address, you have no choice but to involve your ISP. They are in charge of the IP addresses assigned to devices connected to their network.

---

### Post by burge38 on 2013-04-07
I beg to differ brother the dhcp range is in charge of giving us ip address the ISP has no control over who receives what ip address they have a range the dhcp protocols invoke this range the router updates we get ip to get a static we need to know dns servers then when we apply from our router the dhcp protocls on network update to static then the static ip protocols kick in and I am given one from a pre defined range no humans need be involved.

---

### Post by burge38 on 2013-04-07
do you think their is a human their working this out lol

---

### Post by Cheesemill on 2013-04-07
If you want a static external IP address then this ***has*** to be arranged with your ISP.

Even if you do know the DHCP range, gateway address and name server addresses you can't just give yourself a static IP in this range.
First of all how do you know that someone else hasn't been assigned the address you are trying to use?
Also your ISP may well have a system in place where any device has to have been given an address by the DHCP server or it won't be allowed to connect to the network. Most ISP's that I know of have this sort of setup.

At the end of the day your ISP is in charge of all of the IP addresses that they own. It's up to them, not you, how they get assigned.
Your ISP will probably be happy to give you a static IP if you ask them, although they will probably charge you for it.

---

### Post by lisati on 2013-04-07
> **burge38 said:**
> I beg to differ brother the dhcp range is in charge of giving us ip address the ISP has no control over who receives what ip address they have a range the dhcp protocols invoke this range the router updates we get ip to get a static we need to know dns servers then when we apply from our router the dhcp protocls on network update to static then the static ip protocols kick in and I am given one from a pre defined range no humans need be involved.

Like it or not, the DHCP service that assigns your public IP address is operated by your ISP. It is beyond the control of your router. 

The DHCP service running on your router can only assign IP addresses to the computers on your local network. It cannot change your public IP address.

Your ISP would be very unhappy if your router interfered with the correct operation of their service, and you are unlikely to get help here with trying to violate your ISP's terms of service.

---

### Post by burge38 on 2013-04-07
Sorry if I sounded horrible then no seriously I was laughing wasn't until I read the thread again how it seem to others forgot I was not on social networking my apology's mod peace

---

### Post by burge38 on 2013-04-07
I know we are not given ip address on some humans qwim what happens is their is an SQL database containing the already given out ip addresses to the network ie bt may be using 10000 to 20000 well every time so the static server protocols access database and give the next available free address in the range how do you think a network admin would do this he would update my router to be static then the next time the network sends dhcp to router it returns static then the static protocols kick in on the server it accesses database recalls next ip address in range and assigns this to my router all I want to do is cut the operator out I get how it works brother > **Cheesemill said:**
> If you want a static external IP address then this ***has*** to be arranged with your ISP.

Even if you do know the DHCP range, gateway address and name server addresses you can't just give yourself a static IP in this range.
First of all how do you know that someone else hasn't been assigned the address you are trying to use?
Also your ISP may well have a system in place where any device has to have been given an address by the DHCP server or it won't be allowed to connect to the network. Most ISP's that I know of have this sort of setup.

At the end of the day your ISP is in charge of all of the IP addresses that they own. It's up to them, not you, how they get assigned.
Your ISP will probably be happy to give you a static IP if you ask them, although they will probably charge you for it.

---

### Post by lisati on 2013-04-07
[http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol](http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)

---

### Post by matt_symes on 2013-04-07
Closed for review.

---

### Post by burge38 on 2013-04-11
late Monday night I found a tutorial on how to get a static ip address from isp like the other tutorials I followed I didn't expect it to work. to be honest it didn't I went to bed defeated again. Turned of the router computer and the server in dismay. When I woke in the morning and switched pc on powered up the server I was amazed to discover the link I put on my websites main page [www.raveskool.com]("http://www.raveskool.com") were still pointing to the ip address I chose in the setup that didn't work after tutorial. So I switched router off (TEN) times now surely if dhcp was enabled my ip address would have changed, and what's the chance if dhcp assigning the ip I chose 24 hours later. Don't understand thought this was impossible according to this forum. anyways I did phone up isp and tell them I was moving and require business account witch is only 6gbp a month more. may be they gave me a static ip even if they did how did they choose the one I chose in the tutorial. yes I know you want links just looked at that many have to trawl my history shouldn't take long I post link to it in a bit. will some one please tell me what is going on as I thought I was getting to grips with Linux obviously wrong about that too kind regards  (full stops are for people who cant say what they got to say in one breath usually old people) that's my excuse

---

### Post by lisati on 2013-04-11
New thread merged with existing thread.

As has already been explained, your *public* IP address, which is what people visiting your website will use, is administered by your ISP. You will need to talk to your ISP if you want a static public IP address. 

You will need to configure your router to forward requests made via your *public* IP address to the *private* IP address assigned to your server by your router. This we can try to help with.

---

