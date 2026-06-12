---
title: "Trouble with VPN"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by Matthew_Skillman on 2014-05-31
Hello All.  I've got a problem here with my VPN.  I use a pay site privateinternetaccess.com, and have installed it on my androind phone and tablet with no problem.  I'm using a dual boot with Windows 8.1 and ubuntu 12.0.4.  The VPN works in windows but when I use the privateinternetaccess.com instructions for setting up the VPN in ubuntu no luck.  It looks like it worked but no connectivity.  The instructions I followed are the second alternative:


[LIST=1]
[*]Open a **Terminal**, and run: sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome.  This will prompt for both your password, and a Y/n answer, please provide it with your password, and Y 
[*]Once installed, open **System Settings**, then **Network** 
[*]Press the **+** symbol to add a new connection, and select the **VPN Interface**, then press **Create** 
[*]Choose **OpenVPN** as your VPN Connection Type, and press **Create** 
[*]The following will walk you though all configuration steps needed for the PIA VPN.
[LIST=1]
[*]**Gateway**:  Select one of the **Hostnames** provided on the [Network page]("https://www.privateinternetaccess.com/pages/network") 
[*]Authentication
[LIST=1]
[*]Type: Password 
[*]Username: The username provided with the PIA account 
[*]Password: The password provided with the PIA account 
[*]CA Certificate: Downloaded this [zip file ]("https://www.privateinternetaccess.com/openvpn/openvpn.zip") and extract the **ca.crt** file to somewhere it won't be deleted. We suggest your Home folder.  If you extract this to your home folder, when searching for it, please click on your username on the left side, which will take you right to the home folder, then select the ca.crt file from the options on the right. 
[/LIST]
  
[*]Advanced: Under the general tab, check the **Use LZO data compression** 
[*]IPv4 Settings:
[LIST=1]
[*]Method: **Automatic (VPN) Addresses Only** 
[/LIST]
   
[/LIST]
  
[*]Press **Save**.  If you chose to have your password saved it may ask for you to verify your password to open your keyring. 
[/LIST]

I followed these instructions to a T 

Any suggestions? [ Link to their client support page.]("https://www.privateinternetaccess.com/pages/client-support/#ubuntu_openvpn_installer")

---

### Post by Matthew_Skillman on 2014-05-31
bump

---

### Post by gordintoronto on 2014-06-01
You told us how you installed it, but how do you run it? If the crt is in your home folder, you should be able to open a terminal and:
sudo openvpn

---

### Post by Matthew_Skillman on 2014-06-01
> **gordintoronto said:**
> You told us how you installed it, but how do you run it? If the crt is in your home folder, you should be able to open a terminal and:
sudo openvpn

I run it by opening the network dropdown in the top bar:

[IMG]http://i64.photobucket.com/albums/h169/phoenix301301/screenshot1_zps34f9c620.png[/IMG]

Then I get this message:

[IMG]http://i64.photobucket.com/albums/h169/phoenix301301/Screenshot2_zps2abc70da.png[/IMG]

However at this point I will not be able to access the web.  If I turn off the VPN in the drop down menu then I immediately get my connection back.

---

### Post by gordintoronto on 2014-06-01
Sorry, I use VPN to connect to my office network, so I am not familiar with the type of connection you are using.

---

### Post by monkeybrain20122 on 2014-06-02
Since it is a paid service why don't you ask their tech support?

---

### Post by Vladlenin5000 on 2014-06-02
> **monkeybrain20122 said:**
> Since it is a paid service why don't you ask their tech support?

+1

---

### Post by fatmann66 on 2014-06-06
I have it setup and working  with out any issue. did you check to make sure you have the cert file specified.

select configure VPN then on the VPN tab  click edit
check on the VPN tab here to see if the cert is selected.

thinking back I think it didn't work when I first set it up.  did some troubleshooting and an NSLOOKUP wouldn't resolve. I assumed it was a DNS issue. 

within the editing the VPN on the IPv4 Settings tab you need to define the PIA DNS servers: **[B]209.222.18.222, 209.222.18.218**[/B]

---

