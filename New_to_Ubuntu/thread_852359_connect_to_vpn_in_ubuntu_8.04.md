---
title: "connect to vpn in ubuntu 8.04"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by vanilla dream on 2008-07-07
Hello,

I am quite new to ubuntu & want to configure VPN there. I used to use windows to connect VPN and windows settings are as follows,

1. No encryption required (server will disconnect if it requires encryption)
2. Allow the protocols: Unencrypted password (PAP)

Please help me on this.

Thanks in advance,

Vanilla dream

---

### Post by cmnorton on 2008-07-07
First, do you have pptp installed? You have to install that through the menus. I am using Kubuntu currently, and cannot remember the path, but it's under settings, not preferences.

Once you do that, can you create a VPN connection from Network Manager? You should be able to right or left-click on the Network Manager icon, and select VPN connections.

Next, you'll need to walk through each screen and experiment with settings. I use a different VPN connector on Kubuntu, so my application and screens are not going to help you. 

The NetworkManager VPN works well and fairly easy to use. It's a matter of changing settings slowly, writing down the changes you made, and then trying a connection.

---

### Post by cosine352 on 2008-07-07
I do not know if this is of any help. But you can try like this. I am a student of Uninversity of Florida. This works for me.

> To connect to the UF VPN with Ubuntu, try the following:

1. install the packages vpnc and network-manager-vpnc using either
   using the synaptic package manager or one of the command line tools
   (apt-get or aptitude), e.g.,

      sudo apt-get install vpnc network-manager-vpnc

   This should also restart network-manager, so be prepared to
   momentarily lose your network connection (I would quit email before
   doing this).

2. Click on the network icon in your "system tray" area (the thing
   that looks like two computer monitors or like the bars on a cell
   phone if you're on wireless).  You should now see an entry for "VPN
   Connections".  Go into that menu and click "configure VPN".

3. This should open the "VPN Connections" window.  Click "Add".

4. I recommend using "UF VPN" as the Connection Name.  For the gateway
   use vpn.ufl.edu; for the group name use vpn-auth.

5. On the optional tab click "Override user name" and add your UF
   gatorlink email address (e.g., [email]yourgatorlinkusername@ufl.edu[/email]) and
   click forward and then apply.

6. You will need the UF VPN group password, which is contained in
   encrypted form in the VPN configuration file that you can download
   from:

      [http://net-services.ufl.edu/~ns/cgi-bin/vpn/vpn-clients.cgi](http://net-services.ufl.edu/~ns/cgi-bin/vpn/vpn-clients.cgi) 

   (Once you are logged in, scroll to the bottom of the page to
   download the configuration file).  The group password is given by
   the enc_GroupPwd field in the pcf file that you download.  The
   following web page will decrypt the password for use with vpnc:

      [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

7. Now you can connect to the vpn by clicking the network icon, going
   to VPN connections and clicking "UF VPN".  It will ask you for your
   password (your gatorlink password) and the group password.

8. I went ahead and clicked the button that adds the group password to
   my keyring so that I don't have to remember it in the future.  (I
   suppose that the group password might change from time to time
   though, so one might have to retrieve and enter a new one at some
   point.)

---

### Post by xirbuntu on 2008-07-17
Hi,

I have the same problem and have made sure the pptp, vpnc are installed using both the apt-get install as well as Synaptic Package Manager. I have ubuntu 8.0.4 and nm-applet 0.66, however, I am not able to see the "VPN Connections" item in the network-manager tool in system tray.

Thanks for the help.

---

