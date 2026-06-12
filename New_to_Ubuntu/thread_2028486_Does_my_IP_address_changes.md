---
title: "Does my IP address changes"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by BSG Fan on 2012-07-18
when the computer system is reintalled?
Just curiosity.

---

### Post by CharlesA on 2012-07-18
Depends how you have your IP address assigned. If it is via DHCP, maybe, but because the MAC address doesn't change, as long as the lease is still active, the machine will get the same IP.

If it is set to static, you will have to set it yourself.

---

### Post by BSG Fan on 2012-07-18
> **CharlesA said:**
> Depends how you have your IP address assigned. If it is via DHCP, maybe, but because the MAC address doesn't change, as long as the lease is still active, the machine will get the same IP.

If it is set to static, you will have to set it yourself.

Okay, thank you for your answer.

Question # 1:
If I were to set it myself, how I do this?

Any sudo in the Terminal?
or any Add-On for Firefox?

======

question # 2:
I read somewhere that I can have 2 or 3 differents IP's,
is that truth?
if yes, how I do that?
Any sudo in the Terminal?
or any Add-On for Firefox?

---

### Post by audiomick on 2012-07-18
Wait on, let's just define a few things to avoid confusion.

Are you talking about the IP address that is you address in the internet?
How are you connected to the internet?
If you are using a router, the IP address of your computer in the local network is not the address that is visible to the internet.

As far as I know, the address that is visible to the internet is determined by your provider. Whether it changes or not depends on how the provider deals with it, and has nothing to do with your install. 
As far as I know, providers very often give you a 24hr lease on the IP. This could mean you have a new IP every day, but generally doesn't. General practice seems to be that you get a new lease every day, but get issued the same IP every day.

You can see what your address is in the internet by going here, for instance.
[http://www.whatismyip.com/]("http://www.whatismyip.com/")


Anyway, let us know how you get into the Internet, and if you mean the IP address for the internet, or perhaps the IP address in a local network.

---

### Post by BSG Fan on 2012-07-18
> **audiomick said:**
> Wait on, let's just define a few things to avoid confusion.

Are you talking about the IP address that is you address in the internet?
How are you connected to the internet?
If you are using a router, the IP address of your computer in the local network is not the address that is visible to the internet.

As far as I know, the address that is visible to the internet is determined by your provider. Whether it changes or not depends on how the provider deals with it, and has nothing to do with your install. 
As far as I know, providers very often give you a 24hr lease on the IP. This could mean you have a new IP every day, but generally doesn't. General practice seems to be that you get a new lease every day, but get issued the same IP every day.

You can see what your address is in the internet by going here, for instance.
[http://www.whatismyip.com/]("http://www.whatismyip.com/")


Anyway, let us know how you get into the Internet, and if you mean the IP address for the internet, or perhaps the IP address in a local network.

Thank you for the answer.

ok, when I mean "my IP address" is the IP, as by example, a page from China see me visiting them.
and the page says "Your IP is _______ and you are from Florida" by example.

---

### Post by audiomick on 2012-07-18
Ok, you are talking about the IP address visible to the Internet.

Whether or not that will change (or need to be re-configured) when you re-install depends on how you are connected to the internet. The only instance where a re-install of your Operating System could affect your Internet IP is if the computer is directly connected to the internet. If you have a router, or are using wireless, or have anything else between the computer and the device that actually makes the connection to the internet, nothing you do to the computer will change the IP that is visible to the Internet.

How are you connected to the internet?

---

### Post by BSG Fan on 2012-07-18
> **audiomick said:**
> Ok, you are talking about the IP address visible to the Internet.

Whether or not that will change (or need to be re-configured) when you re-install depends on how you are connected to the internet. The only instance where a re-install of your Operating System could affect your Internet IP is if the computer is directly connected to the internet. If you have a router, or are using wireless, or have anything else between the computer and the device that actually makes the connection to the internet, nothing you do to the computer will change the IP that is visible to the Internet.

How are you connected to the internet?

I am connected to internet with a cable modem, not a reuter.

Thank you again for your answer.

---

### Post by Redblade20XX on 2012-07-18
> **BSG Fan said:**
> I am connected to internet with a cable modem, not a reuter.

Thank you again for your answer.

The quickest way to find out if your isp has assigned you a static ip is to first go and find your supposedly current ip address using one of the ip address finding sites. Then just unplug your modem for a couple of hours. Reconnect your modem and recheck you ip address. 

If you have a static one, your previous and current ip will be the same. If not, you'll have a dynamic one.

- Red

---

### Post by audiomick on 2012-07-18
Ok. I haven't ever set up a cable modem, so I am guessing a bit, but according to what I read here

[https://en.wikipedia.org/wiki/Cable_modem#Network_architectural_functions]("https://en.wikipedia.org/wiki/Cable_modem#Network_architectural_functions")

it is possible that your modem has a built in router. 

If you can connect more that one computer at once to the modem, you can assume that there is a router in there (or read the manual of the modem...) and that the modem is taking care of the IP address visible to the internet.

If you can only connect one computer to the modem, then it is safe to assume there is no router in there, and I think your computer is dealing with the IP address for the internet directly. That brings us back to how the provider deals with things. If you re-install, you will have to re-do whatever configuration was neccessary to get the modem working. If that involved setting up a static IP, you will then have whatever address you configure after the re-install, obviously.

If you had not had to set up a static IP, then we are back to the provider and how the IP's are dealt with. There is a chance that, as CharlesA pointed out, you would get the same IP back, because your MAC address never changes, and the provider will see that when you plug the new install back in. There is also a chance that you would get a new IP.

You asked how you set up a static IP. The graphical way to do this is with the network manager. Click on the icon in the task bar that shows you that there is an active network connection, or search for "network connections" or something like that in the search box on the dash. Don't mess around in there unless you actively want to change the setup of your network connection. If you change the wrong thing, you could end up with no connection at all.

There is a way to set up an internet connection with the terminal, of course, but I don't know the commands. ;)

---

### Post by BSG Fan on 2012-07-18
> **Redblade20XX said:**
> The quickest way to find out if your isp has assigned you a static ip is to first go and find your supposedly current ip address using one of the ip address finding sites. Then just unplug your modem for a couple of hours. Reconnect your modem and recheck you ip address. 

If you have a static one, your previous and current ip will be the same. If not, you'll have a dynamic one.

- Red
Thank again

I called my cable-internet provider and they told me that the IP is dynamic.

---

### Post by audiomick on 2012-07-18
OK, that means that a re-install will have no effect on the IP at all. 

That is not to say that you will always have the same IP address from one day to the next. That depends entirely on whether the provider issues your computer with a new address each time, or gives it the same one each time. It is possible that they wont tell you this, for whatever reason. You can check by looking at the "whatismyIP" page periodically if you really want to know. Still, even if it stays the same for a period of time, it still depends entirely on the provider. "Dynamic" means it is not fixed, even if the provider does issue the same one all the time. They might decide to issue a new one any time.

---

### Post by BSG Fan on 2012-07-18
> **audiomick said:**
> OK, that means that a re-install will have no effect on the IP at all. 

That is not to say that you will always have the same IP address from one day to the next. That depends entirely on whether the provider issues your computer with a new address each time, or gives it the same one each time. It is possible that they wont tell you this, for whatever reason. You can check by looking at the "whatismyIP" page periodically if you really want to know. Still, even if it stays the same for a period of time, it still depends entirely on the provider. "Dynamic" means it is not fixed, even if the provider does issue the same one all the time. They might decide to issue a new one any time.

Thank you for your answers.
Let's see.

---

### Post by BSG Fan on 2012-07-18
Thank to all the users that replied to my question.

;)

---

