---
title: "Configuring D-Link Router using Terminal"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by jshor on 2012-08-15
Does anyone know how to configure a D-Link DIR-655 router using only the terminal? I am working on an ubuntu server and I would like to know how I can change the port forwarding configuration without having to use an internet browser.

---

### Post by Cheesehead on 2012-08-15
That model is web-only.

Have you tried Lynx or other text-only browsers?

---

### Post by HermanAB on 2012-08-16
apt-get links
or
apt-get lynx

then
links [http://192.168.0.1](http://192.168.0.1)

---

### Post by jshor on 2012-08-23
That was a good idea - I had not tried them. However, Lynx and Elinks both failed to work. It appeared as though all buttons were disabled, including the login buttons. The Lynx output is shown below, and the Elinks output was similar. Any other thoughts? I am using SSH to remotely login to the server - any chance that could be useful?

 Firmware Version: 1.32
      Hardware Version: A4
      Product Page: DIR-655

     Reboot needed

        Your changes have been saved. The router must be rebooted for the
        changes to take effect. You can reboot now, or you can continue to make
        other changes and reboot later.
        [BUTTON Input] (not implemented)Reboot Now [BUTTON Input] (not
        implemented)Reboot Later

     Login

        WARNING: JavaScript is not enabled for this browser!

Log in to the router:

        User Name : [Admin]

        Password : ____________________ [BUTTON Input] (not implemented)Log In


     User Name :  [Admin]
     Password  :   ____________________
     Enter the correct password above and
     then type the characters you see in the
     picture below.  ____________________
     [auth.bmp] [BUTTON Input] (not implemented)Regenerate

     [BUTTON Input] (not implemented)      Log In      



   Copyright © 2004-2008 D-Link Systems, Inc.

---

### Post by mcduck on 2012-08-23
Try Links2, it should have a bit better JavaScript support than what ELinks has.

---

### Post by jshor on 2012-08-23
Links2 appears more normal - there is a line "Log in to the router:", but no active text area or active buttons. The only active link is to the product page, which works. Links2 seems to function fine on other websites, such as google.com.

In a different vein, I am able to view the html that the router produces using curl or wget. I have attached it to this post in the hopes that it might provide a solution.

Your help is much appreciated.

---

