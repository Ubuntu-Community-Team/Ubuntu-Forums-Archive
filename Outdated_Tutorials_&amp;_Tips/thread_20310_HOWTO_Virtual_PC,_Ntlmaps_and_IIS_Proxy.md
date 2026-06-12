---
title: "HOWTO: Virtual PC, Ntlmaps and IIS Proxy"
date: 2005-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by dr.ed locks on 2005-03-16
Preamble: Although I run Ubuntu Warty at home, at work I am forced to use Windows XP and access the internet the a MS IIS Proxy Server. But I really wanted to be able to use Ubuntu Hoary at work. 

Q: How to install and test Ubuntu Hoary on Windows XP with internet access through a MS IIS Proxy Server.

A: Use MS Virtual PC 2004, Ubuntu Hoary CD Preview and Ntlmaps

(I didn't have the funds to buy to VMWare which I would have preferred to configure, but did have access to MS Virtual PC 2004).

Install MS Virtual PC 2004. Start-up MS Virtual PC 2004 (I used most default settings).

Pop-in the Ubuntu Hoary Preview CD and watch it install very slowly (I didn't have any dramas with the install - but your mileage may vary depending on your hardware, etc). 

Starup Ubuntu Hoary.

Enable Ethernet Connection (eth0) under Desktop-Administration->Networking.

Start-up Firefox and select Edit->Preferences->General->Connection Settings.

- Use Manual Proxy Configuration, or Automatic Proxy Url (if unsure just copy the settings in MS IE under Tools->Internet Options->Connections->LAN Settings) as Firefox 'understands' the MS NTLM protocol.

Download Ntlmaps from [http://ntlmaps.sourceforge.net](http://ntlmaps.sourceforge.net) (I used the ntlmaps-0.9.9.tar.gz).

Unpack the tar file and locate the server configuration file (server.cfg).

Modify the following server.cfg settings:
> 
[GENERAL]
LISTEN_PORT: 5865           // This is the default listen port
PARENT_PROXY: msiisproxy    // if DNS correctly configure in eth0, otherwise proxy IP
PARENT_PROXY_PORT: 8080     // Default (for MS IIS)

[NTLM_AUTH]
NT_HOSTNAME: myworkstation  // The name of your workstation ControlPanel-System->Computer Name in Windows XP
NT_DOMAIN: mywindowsDomain  // Name of windows domain
USER: mywindowsusername     // Windows logon user name 
PASSWORD: mywindowspassword // Windows password
LM_PART: 1                  // Windows 95/98 NTLM compatibility
NT_PART: 0                  // Windows NT NTLM compatibility
NTLM_TO_BASIC: 0            // Convert NTLM to basic authentication

Save the server.cfg file, open a command prompt and start Ntlmaps 
> 
./main.py

Firefox
=======
Startup up firefox and select Edit->Preferences->General->Connection Settings.
> 
- Manual proxy configuration
   - Use the same proxy for all protocols   // (Check this option)
     HTTP   Proxy: 127.0.0.1      Port 5865
     SSL    Proxy: 127.0.0.1      Port 5865
     FTP    Proxy: 127.0.0.1      Port 5865
     Gopher Proxy: 127.0.0.1      Port 5865


APT-Get
=======
Edit Apt.conf and add the following lines:
> 
Acquire
{
  // HTTP method configuration
  http
  {
    Proxy "http://127.0.0.1:5865";
  };
  // FTP method configuration
  ftp
  {
    Proxy "ftp://127.0.0.1:5865";
  };
};


Alternatively, you can use the export http_proxy command to set the Ntlmaps proxy.

Synaptic
========

Edit Settings->Preferences->Network
> 
Manual Proxy Configuration
       HTTP Proxy 127.0.0.1  Port 5865
       FTP  Proxy 127.0.0.1  Port5865


And surf and update Unbuntu from deep in the heart of Borg mothership!

Dr.ed locks
 :mrgreen:

---

### Post by Seer on 2005-09-07
You sir... are a god :)

I been fannying around with ubuntus appalling proxy options and configurations for days....

Then I tried one last slightly different search of the forums and voila.

Just wanted to take the opportunity to say thanks seeing as noone else has :D

---

### Post by TFX360 on 2006-06-13
Just for the people who don't know how to use http_proxy:

export http_proxy=http://127.0.0.1:5865

Don't **sudo** the export command.


Greets,


TFX

---

### Post by true_friend on 2006-08-05
NTLM is an http proxy server. would it be work with ftp also????
i think it was failed when i tried to connect to an ftp server using this tool ( i m currently also behind ISA server using ntlm to connect to internet do not access to ftp or socks, messenger is not working). socks via http a tool which supports NTLM proxy server also but i could not configure its client init.properties file. 
some can guide me in this regard????/
to configure it with NTLM proxy server???????
this progarm is too old and the official website is also over and i think there would be no support email address also now.:-( :-(

---

