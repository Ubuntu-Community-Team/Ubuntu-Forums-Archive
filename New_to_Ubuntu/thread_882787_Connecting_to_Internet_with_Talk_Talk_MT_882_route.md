---
title: "Connecting to Internet with Talk Talk MT 882 router"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Mandy and Ted on 2008-08-07
Hi

We are a non-tech couple who have just installed Ubuntu 8.04 for the first time.

We have tried (and it is very trying) to install broadband via a Talk Talk MT882 router via an ethernt connection-no success so far!

the ADSL link light is solid green and the LAN light solid orange.

We have tried:-

1. Talk talk technical- they do not have experience with Ubuntu

2. Following the MAC route in the talk talk manual -using 192.168.1.1 as the IP address. This results in a page error message and browser unable to establish a connection message.

3. We have tried a manual configuration via Network Settings but have had difficulty choosing/completing fields. In CONNECTION TYPE we are not sure whether we have aPPPOE or GPRS/UMTS or serial modem- we have tried all three.
In INTERNET SERVICE PROVIDER- phone number we can get no information from Talk TALK. We have tried putting in 'admin' in both categories- without success.

4. wE HAVE TRIED ALSO INPUTTING OUR USER NAME AND PASSWORD as given by TALK TALK.

All our attempts have failed to activate the OK button at the page bottom.

We would be so grateful for any help that you ahve to offer.

Thaanks

Mandy and Ted

---

### Post by doug1212 on 2008-08-07
Hi Mandy and Ted,

There should be no need to alter any network settings in ubuntu as it is set up by default to look for a dhcp server (your router) by default.

The information given to you by your ISP has to be entered into the router setup pages, to do this you will have to start your browser (firefox) and enter 192.168.1.1 in the address bar this should take you to a log in page enter admin/admin you should then be taken to the setup page where your login/password details are entered.

Most routers have an auto mode to acquire the correct line settings etc.

Doug.

---

