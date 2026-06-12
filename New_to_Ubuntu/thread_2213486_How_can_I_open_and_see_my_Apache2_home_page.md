---
title: "How can I open and see my Apache2 home page?"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by dizzy3 on 2014-03-26
So I have created a unbuntu server on vmware (for school). Our latest assignment asked us to ... Install Apache Web Server on your Server1 installation.  Once complete  open your web browser and navigate to the web site and screen shot and  submit the default Apache web server screen showing it works. So I have installed it. ([http://imgur.com/pkUAAOC,PL5Ycqm](http://imgur.com/pkUAAOC,PL5Ycqm)) screen shots. I'm totally lost about the browser part. I mean the server doesn't have a browser I can just open and go to local host. Please help.

---

### Post by steeldriver on 2014-03-26
If you have configured your VM's networking in *bridged mode*, you can simply point a browser on your host system to the virtual server's LAN IP address

---

### Post by mastablasta on 2014-03-27
server can have a browser. there are command line browser available such as lynx.

anyway that's nto what you are after. you need to set bridget networking adapter in virtual box.

then lanuch the virtualbox server, use ifconfig command to see your servers ip. then go to your host os (windows?!) and the in the IP you got into your browser of choice and **boom!** there's your apache. :-)

btw just for information there are preconfigured virtual images for various servers and programs such as the ones available at TurnkeyLinux or the Bitnami stack ... all require bridged networking adapter in virtual box if you want to access them from host OS via browser.

---

